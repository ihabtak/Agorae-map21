AGORAE – Participative knowledge management
===========================================

License: [GNU Affero General Public License](http://www.gnu.org/licenses/agpl.html)

Contact: <aurelien.benel@utt.fr>

Home page: <https://github.com/Hypertopic/Agorae>

Notice
------

Agorae is a server software. There is no need to install it on your own computer to use it. The usual way is to be "hosted" by one's own institution (ask your system administrator). If your use cases meet our research interests, we can also host your data on our community server.

Installation requirements
-------------------------

* Git client
* [Argos](https://github.com/Hypertopic/Argos)

Installation procedure
----------------------

Argos has been installed at ``http://127.0.0.1:5984/argos``

* Type:

        git clone https://github.com/Hypertopic/Agorae.git
        cd Agorae

* Copy `agorae.sample.json` as `agorae.json`.
* Edit ``agorae.json`` to fit your settings:
  * change HTML ``footer`` and ``header`` if necessary,
  * a set of servers (e.g. ``http://127.0.0.1:5984/argos/_design/agorae/_rewrite/argos/``),
  * a set of ``corpora`` (IDs),
  * a set of ``viewpoints`` (IDs),
  * ``auth``, an authentication service (e.g. ``http://127.0.0.1:5984/_session``),
   * ``homesite``, Agorae homesite link.

* Go to http://127.0.0.1:5984/argos/_design/agorae/_rewrite/

Installation on a different domain
----------------------------------

Agorae and Argos does not need to be installed in the same database nor
on the same server.
For the latter, the CouchDB server hosting Argos must be set to allow
"cross-origin resource sharing".

```ini
[cors]
origins = *
headers = accept, authorization, content-type, origin
[httpd]
enable_cors = true
```

Tests requirements
------------------

* Ruby
* PhantomJS

Tests installation procedure
----------------------------

* In any folder:

        sudo gem install poltergeist rspec


Tests running
-------------

* In the `Agorae` folder:

        rspec spec/features/*

* Enable comments

  1. [Sign up to Disqus](https://disqus.com/profile/signup/),
  2. Choose `Install Disqus on my site`,
  3. Set your Website data and **create site**. Remember its `short name`.
  4. Edit `couchdb/_attachments/agorae.json` and paste the short name as the value of `disqus` setting.