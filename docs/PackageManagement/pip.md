# Python Package Manager (pip)

## virtualenv
Create and use virtualenvs by running

    python3 -m venv myvenv
    source myvenv/bin/activate
    pip install -U pip

This may require installing these packages prior

    apt-get install python3-pip python3-venv

## virturalenvwrapper

    pip install virtualenvwrapper

Add to `.bash_profile` or `.bashrc`   

    mkvirtualenv depthAI -p python3

List envs

    lsvirtualenv

    

## References
- [pip Cheat Sheet](https://opensource.com/sites/default/files/gated-content/cheat_sheet_pip.pdf)

- [Official Guide to virtualenv](https://docs.python.org/3/tutorial/venv.html)

- [Virtualenvwrapper](https://virtualenvwrapper.readthedocs.io/en/latest/) documentation