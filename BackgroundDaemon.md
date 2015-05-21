# Introduction #

The daemon consists of basic Perl code which forks a background process and periodically polls the NWS's FTP site for updated radar images.


# Details #

Files used in daemon:
  * **radarwatch.sh** - Bash wrapper script to start/stop daemon
  * **radarwatch.conf** - Configuration file for Perl daemon.  Mostly self-documenting.
  * **radarwatchd.pl** - Actual Perl daemon.  Uses LWP::Simple, Proc::Daemon, Proc::PID::File and ConfigReader::Simple modules.