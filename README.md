## PolyRest

The app itself is viewable and running at http://polyrest.datafundamentals.com
2 minute youtube demo at https://youtu.be/ydklb9T_8Bs

## To Run This Code:

This source code was originally designed to work with the full version of 
PolymerStarterKit, but was reconfigured to work with the light version, 
due to repeated NPM hangs on several occassions, months apart, and lasting 
for days at a time. 
Friends don't let friends depend on NPM? Dunno. Not waiting around to find out.

To install and run this app, copy the following bash script to a location
 in your project folder, and run it. This will download everything you need,
  create a polyrest app and then run it as a python app as 
  http://localhost:8080
  
You may have to answer Y/N to a few prompts on random .md files, but otherwise
 it should work on your local 'nix box without modification. (???). Tested on 
 macosx and ubuntu, that's about it.
 
`
echo "About to create and run polyrest"
polydir=$1
if [ $# -eq 0 ]
  then echo "You did not specify a directory. Using polyrest";polydir="polyrest"
fi
mkdir $polydir
cd $polydir
curl -O http://docs.datafundamentals.com/lib/polymer-starter-kit-light-1.2.1.zip
ls
unzip polymer-starter-kit-light-1.2.1.zip
git clone https://github.com/datafundamentals/polyrest.git
rm -rf app/elements
rm -rf app/test/my*
rm app/index.html
rm app/styles/app*
mv -f polyrest/* app/
mv -f polyrest/.* app/
mv polyrest/styles/* app/styles
rm -rf __MACOSX
rm -rf polyrest
mv app polyrest
cd polyrest
python -m SimpleHTTPServer 8080
`

