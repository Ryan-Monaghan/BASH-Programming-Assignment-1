#!/bin/bash

#OS Bash Shell Programming Assignment 1
#Name: Ryan Monaghan
#ID: R00115129
#Class: ITS2-A

echo -n "Please enter the Source Directory of the file you wish to copy: "
read srcDirectory
echo

if test -z ${srcDirectory}
	then
		
		echo "${0}:ERROR: No  directory name entered." 1>&2
		echo "${0}:USAGE: Please your Directory name." 1>&2
		exit 1 
fi

if test ! -d "${srcDirectory}"
	then
		echo "${0}:ERROR: Source directory '${srcDirectory}' does not exist!" 1>&2
		echo "${0}:USAGE: Enter a correct directory." 1>&2
		exit 2
fi

echo -n "Please enter the name of the file you wish to copy: "
read srcFile 
echo

if test -z "${srcFile}" 
	then
		echo "${0}:ERROR: No file name entered." 1>&2
		echo "${0}:USAGE: Enter a file name." 1>&2
		exit 3
fi

if test ! -e "${srcDirectory}/${srcFile}"
	then
		echo "${0}:ERROR: File named '${srcFile}' does not exist." 1>&2
		echo "${0}:USAGE: Enter a valid file name." 1>&2
		exit 4
fi

echo -n "Please enter the name of the Destination Directory you wish to create: "
read destDirectory
echo

if test -z ${destDirectory}
	then
		echo "${0}:ERROR: No name entered for Destination Directory entered." 1>&2
		echo "${0}:USAGE: Please enter a Destination Directory." 1>&2
		exit 5
fi

if test  -d "${destDirectory}"
	then
		echo "${0}:ERROR: Destination named '${destDirectory}' already exists." 1>&2
		echo "${0}:USAGE: Please enter a new Destination Directory name." 1>&2
		exit 6
fi

mkdir ${destDirectory}
cp "${srcDirectory}/${srcFile}" "${destDirectory}"
echo "The file titled "${srcFile}" has successfully been copied from "${srcDirectory}" and placed into "${destDirectory}"!"