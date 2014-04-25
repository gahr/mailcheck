mailcheck
=========

This small Tcl script can be used to test whether relaying to email addresses is OK by connecting to their MX and getting to the RCPT TO: point.  Email addresses are read from stdin, one on each line.

This software depends on the <a href="http://tcllib.sourceforge.net/doc/tcllib_dns.html">dns</a> package from <a href="http://core.tcl.tk/tcllib/home">tcllib</a> and optionally on <a href="http://tcludp.sourceforge.net/">tcludp</a>, for UDP queries.


    Usage ./mailcheck [option ...]
    
    Options:
        --nameserver <host>     DNS
        --protocol   [tcp|udp]  Protocol for querying the DNS (default: tcp)
        --mailfrom   <email>    Envelop from email (default: user@hostname)
        --timeout    <seconds>  Connect timeout to the MX server (default: 3)
        --firstOnly             Stop iterating MX servers at the first OK

    Example:
        $ echo gahr@gahr.ch | ./mailcheck --nameserver 8.8.8.8 --mailfrom gahr@gahr.ch --timeout 4
        gahr@gahr.ch: gahr.ch => ok.
