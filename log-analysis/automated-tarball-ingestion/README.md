# What we do step-by-step
- Place a log tarball in `./log-tarballs-to-ingest/` (currently not automating, you have to do this)
    * Having a directory like this gives us modularity and makes it easy to change. We can manually do this (`mv my.tgz ./log-tarballs-to-ingest/`) for now, and easily later add a script that does this for us, or even expose a web GUI for uploading it in. Then whatever we do, we place these tars in this directory
- Receive certain metadata about the tarball
    * don't count on this being extractable from the filename for now. Prompt user input.
    * What we need:
        - Company name (make this consistent for the company, for every company there should only be one)
        - incident time as a tarball id (or some other unique identifier that we can consistently use for this tarball)
        - hostname - what host this came from. Can be a domain name or IP address, but should stay consistent for that node (don't change back and forth between ip and domain name)
- Put in the folder we want it in
- Generate a filebeat.yml for this (will be v0.2; v0.1 just write this ourselves)
- start filebeat for one-off batch job that ingests these files into ELK 
    * Perhaps later we will just have filebeat running continually on our server, watching  whatever gets placed in

# Implantation decisions
- Python
    * Easy to use
    * Has a REPL for easy debugging
    * Can add modules/classes/a web gui etc later easily (much more easily than a bash script)
    * Most of us are familiar already