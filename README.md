# 10_cleanup_in_ISLE_one_please
This `isle-docker-compose` project obliterates unnecessary directories and files found in Islandora/ISLE.

## Attention!  
If you found this file, and/or one named `OBLITERATED.md`, lurking inside your Islandora stack, then it was put here to replace some files/folders that were deemed "unnecessary".  If you're confused by this statement, please read on.

*Use this module with caution!*  It has been, and continues to be, tested with ISLE instances of Islandora, but there's always the possibility that it might obliterate something you really do need.

## Overview
This project introduces the `docker-compose.95.cleanup-in-ISLE-one-please.yml` file that essentially _obliterates_ unnecessary files and folders by replacing them with the `./BOMB/OBLITERATED.md` file found in this project.  `OBLITERATED.md` essentially does *NOTHING*, it just documents its reason for being.

## Why Do I Need This?
If you have ever peeked under the hood at Islandora, or more specifically, at FEDORA and FGSearch, you may have seen confusing directory structures and repetition like this example:

```
root@9c166be40ab6:/# find /usr/local/tomcat -name foxmlToSolr.xslt
/usr/local/tomcat/webapps/fedoragsearch/FgsConfig/DrupalModuleForIslandora/islandora_gsearch/FgsConfigIndexTemplate/Solr/foxmlToSolr.xslt
/usr/local/tomcat/webapps/fedoragsearch/FgsConfig/FgsConfigIndexTemplate/Solr/foxmlToSolr.xslt
/usr/local/tomcat/webapps/fedoragsearch/FgsConfig/configDemoOnSolr/index/FgsIndex/foxmlToSolr.xslt
/usr/local/tomcat/webapps/fedoragsearch/FgsConfig/configForIslandora/fgsconfigFinal/index/FgsIndex/foxmlToSolr.xslt
/usr/local/tomcat/webapps/fedoragsearch/WEB-INF/classes/fgsconfigFinal/index/FgsIndex/foxmlToSolr.xslt
```
Hmmm, 5 copies of the same file?  Which one is "significant" and in-control?  Are the others even necessary?  What happens if I remove the "others"?

I cannot definitively answer the last two questions... hence the note about using this module with CAUTION!  However, this module can help you do some investigation, and maybe save your sanity if/when you do encounter any duplicates like this, or you positively identify a file/folder that is just useless cruft.

## The isle-docker-compose Command
See https://github.com/DigitalGrinnell/ISLE_docker_compose for details.

## How Is This Used?
It's easy, assuming the `isle-docker-compose` command is already defined, just follow these steps...

  1) Open a terminal to your ISLE host, and in that terminal...  
  2) Navigate (`cd`) your working directory to ISLE, the directory that holds your `docker-compose.yml` file. Probably `cd /opt/ISLE`.
  3) Navigate (`cd`) into your `ISLE_docker_compose` directory with: `cd ISLE_docker_compose`.
  4) `git clone` this repository to your ISLE host using `git clone https://github.com/DigitalGrinnell/10_cleanup_in_ISLE_one_please.git; cd ..`.  
  5) Spin up your ISLE instance using our special form of `docker-compose up`, like so: `./isle-docker-compose`.
  6) Your ISLE instance should spin up just as if you had issued `docker-compose up -d`, but with this feature engaged.
