# Pattern Atlas documentation

Documentation for the Pattern Atlas project, realized with ReadTheDocs.

### Extend the documentation

For a live preview in the browser, you can run:

`docker run --rm -it -p 127.0.0.1:8000:8000 -v "`pwd`/docs":/docs sphinxdoc/sphinx bash -c "pip install sphinx-autobuild sphinx_rtd_theme && sphinx-autobuild --host 0.0.0.0 source build/html"`

