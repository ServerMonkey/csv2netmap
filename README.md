csv2netmap(1) -- Convert a CSV file to graphviz format
=============================================

## SYNOPSIS

`csv2netmap <FILE_IN> <FILE_OUT> [<CELLS_TO_IGNORE>] `

## DESCRIPTION

Create maps of computer networks or similar.  
A custom graphviz design will be applied.

## OPTIONS

 * `-h`, `--help` :
   Displays the help screen.

## EXAMPLES

### Example 1:

Convert a map of a network.  
Create a csv file 'network.csv' with the following content:

	jacks-pc,home-lan
	jills-laptop,home-lan
	sysadmin-pc,home-lan
	sysadmin-pc,DMZ
	webserver,DMZ
	evilhacker,home-lan
	evilhacker,DMZ
	evilhacker,4G-modem

or this format works just as well:

	jacks-pc,home-lan
	jills-laptop,home-lan
	sysadmin-pc,home-lan,DMZ
	webserver,DMZ
	evilhacker,home-lan,DMZ,4G-modem

Then run:

    $ csv2netmap network.csv network.gv

After that you can convert the .gv file to an image.  
As list graph:

	$ dot -Gcharset=latin1 -Ecolor="#22222255" network.gv -Tsvg >network.svg

As undirected graph:

	$ neato -Gcharset=latin1 -Ecolor="#22222255" network.gv -Tsvg >network.svg

### Example 2:

Convert a map of a network and exclude the networks 'DMZ' and '4G-modem'

    $ csv2netmap network.csv network.gv "DMZ,4G-modem"

## COPYRIGHT

See license file

## SEE ALSO

graphviz(1), dot(1), neato(1), https://github.com/artemanufrij/graphui
