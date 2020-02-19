.. include:: ../cyverse_rst_defined_substitutions.txt

|CyVerse_logo2|_

|Home_Icon2|_
`Learning Center Home <http://learning.cyverse.org/>`_

**GitHub Action and EHT Demo**
===============================

**Introduction**
----------------

Building Docker images on your machine and then push it to DockerHub
manually can be time consuming.  Since we use Git and GitHub to keep
track of all our source codes, it will be great to ask GitHub to
automatically build and push docker images for us whenever we change
our codes.

We will use the Event Horizon Telescope (EHT)'s imaging pipeline as an
example.  The EHT is an international collaboration with a science
goal to take pictures of black holes.  The EHT published its
visibility data on
`CyVerse <https://datacommons.cyverse.org/browse/iplant/home/shared/commons_repo/curated/EHTC_FirstM87Results_Apr2019>`_
and its software pipeline on
`GitHub <https://github.com/eventhorizontelescope/2019-D01-02>`_ .

**Fork the EHT Pipeline**
------------------------------------------

When you are on the EHT pipeline GitHub repository, first, click the
"Fork" badge/button to create your own repository.

In your own repository, go to "Settings" to rename your repository to
something readable for human, e.g., "eht-demo".

Because we will need to connect to DockerHub to publish our image, go
to the "Secerts" tab in setting and add the following two secrets:

- `DOCKERHUB_USERNAME`: your Docker Hub username

- `DOCKERHUB_PASSWORD`: your Docker Hub password

**Create a Dockerfile**
------------------------------------------

To edit your version of the pipeline repository, let's clone it to
your "local" machines (laptop, desktop, atmosphere VM, etc).

.. code-block:: bash

    git clone git@github.com:[GITHUB_USERNAME]/eht-demo.git

Then, change-directory into your local repository and create a
`wrapper.sh` script:

.. code-block::

   #!/bin/bash

   python /usr/local/src/eht-imaging_pipeline.py "$@"

Turn it into an run-able script by

.. code-block:: bash

   chmod 755 wrapper.sh

Then, add a new `Dockerfile` with the follow content:

.. code-block::

   FROM eventhorizontelescope/img-env

   COPY eht-imaging/eht-imaging_pipeline.py /usr/local/src/
   COPY wrapper.sh /usr/bin

   WORKDIR /img
   ENTRYPOINT ["/usr/bin/wrapper.sh"]

Commit all your files and push to GitHub:

.. code-block:: bash

   git add .
   git commit -m 'For building FOSS demo Docker image'
   git push
