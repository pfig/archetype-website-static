[Maven][4] Archetype For Static Websites
===

Overview
---

This archetype builds a skeleton directory structure and some initial code for a static website. It is tailored for **my** needs (e.g., I want to use [HTML 5][1] and [Dojo][2]), but it's trivial to change it to whatever you usually start your sites with.

Installation
---

After cloning the git repo, cd into its directory and run 'mvn install'. If you have a remote repository, you might want to run 'mvn deploy'.

Usage
---

Once installed, a new archetype will show up on the list when you run 'mvn archetype:generate', which you should select. Alternatively you can run

    mvn archetype:generate \
      -DarchetypeGroupId=org.pedrofigueiredo.archetypes \
      -DarchetypeArtifactId=website-static-archetype \
      -DarchetypeVersion=$VERSION_YOU_HAVE_INSTALLED

Maven will then prompt you for a few values to fill in the gaps:

    Define value for property 'groupId': : org.pedrofigueiredo.web
    Define value for property 'artifactId': : web-personal-site
    Define value for property 'version':  1.0-SNAPSHOT: : 
    Define value for property 'package':  org.pedrofigueiredo.web: : 
    Define value for property 'website-description': : Personal Website
    Define value for property 'website-id': : pedrofigueiredo.org
    Define value for property 'website-name': : Pedro Figueiredo
    Define value for property 'website-url': : http://pedrofigueiredo.org/

groupId, artifactId, version, and package will be used by Maven to identify the artefact you're creating.
website-description will go in the POM's &lt;description> tag, and website-url in the &lt;url> tag.
website-name will be the project's &lt;name> in the POM, and will also be inserted as the &lt;title> tag of the skeleton's
index.html.
website-id will be inserted in the generated POM in the &lt;scm> section, (which by the way is one thing you'll have to change, as it currently points to my GitHub account), so if, e.g., it's 'my-website', your &lt;scm> will point to

    scm:git:git@github.com:pfig/my-website.git

You need to adjust this in the generated POM, or better yet change the archetype's template POM to use whatever you use for version control (and while you're at it, also do the same in the archetype's POM for SCM and artefact repository, if you don't want to run your own Nexus or Archiva, [here's a post about using GitHub as a Maven artefact repository][3]).

Enjoy!

Other
---

If you're new to Maven, the [Sonatype books][5] are an excellent way to get started.

[1]: http://www.w3.org/TR/html5/ "HTML 5 at the W3C"
[2]: http://dojotoolkit.org/ "Dojo Toolkit"
[3]: http://cemerick.com/2010/08/24/hosting-maven-repos-on-github/ "Using GitHub as a Maven repo"
[4]: http://maven.apache.org/ "Maven homepage"
[5]: http://www.sonatype.com/books.html "Maven books by Sonatype"