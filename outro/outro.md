<!SLIDE>
# Summary #######################################################################


<!SLIDE small incremental transition=uncover>
# Trema: "OpenFlow like Rails" ##################################################

* <i>Run It Quick</i>: Tight loops of coding, run, and debug
  * Virtual network DSL
  * `trema {run, send_packets, show_stats, up, kill}`
* <i>Coding by Convention</i>: Write it short
  * Auto handler dispatch by naming convention
  * Class attributes: `periodic_timer_event`
  * Syntactic sugars: `ExactMatch.from`
  * Default options: `send_flow_mod_add`
* <i>Useful Sub-commands</i>
  * `trema {dump_flows, ruby}`


<!SLIDE small>
# Next Step For Developers #####################################################

* `[trema]/src/examples`
  * Simple samples demonstrating API usage
  * Good references for understanding both Ruby and C APIs
* Trema/Apps <http://github.com/trema/apps>
  * Practical/experimental controllers developed on top of Trema
  * Good starting point for developing real-world controllers


<!SLIDE>
# Love Ruby? ###################################################################


<!SLIDE>
# Love C? ######################################################################


<!SLIDE small>
# Trema C ######################################################################

* It's your choice ... Trema provides libraries for both Ruby and C
* Trema C is also simple as Trema Ruby

<br />

	$ gcc myapp.c `trema-config -c -l` -o myapp
	$ trema run myapp


<!SLIDE small>
# Sources ######################################################################

* This Tutorial: <http://github.com/trema/GEC13/>
* Trema: <http://github.com/trema/>
* Trema/Apps: <http://github.com/trema/apps/>
* Web Page: <http://trema.github.com/trema/>
* Twitter: <http://twitter.com/trema_news>
* Mailing List: <https://groups.google.com/group/trema-dev>
* Bugs: <https://github.com/trema/trema/issues>


<!SLIDE small>
# Contributors! ################################################################

* Free Trema T-shirt for contributors!
  * Patch (New features/apps, enhancements, bug-fixes)
  * Bug report
  * Documentation etc.
* Send pull-requests and get the T!


<!SLIDE>
# Questions? ###################################################################


