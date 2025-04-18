1. Lets say we want to install a specific version of python- `uv python install version`
2. Search for particular versions - `uv python find version`
3. If we want to uninstall a particular vversion - `uv python uninstall version`
4. To initialize a project we do - `uv init`. We get pyproject.toml, here will lie the dependencies. See .venv that is created. uv.lock file is also creaed. 
5. When we want to run a script - `uv run name_of_the_script` or - `uv run --python version_name_of_the_script`
6. To install dependencies on the go - `uv run --with module_name --python version_name name_of_the_script`
7. To add dependencies - `uv add module_name`. This will also modify the pyproject.toml file dependencies array. 
8. To remove a dependency - `uv remove module_name`. 
9. Lets say you are facing an installation error for a module, we can manually change the version of python in `pyproject.toml` and `python-version` and try readding, it is usually resolved and its very fast. 
10. Lets say you manually changed the dependencies array in `pyproject.toml` file and run `uv run module_name`, now what will happen is it will first run the `uv sync` and that will updated any libraries which is defined in the toml file and run the script. 
11. `uv lock` automatically generate the lock file. 

### Now some common senarios 
1. You have `req.in` file and you want to create a env using uv, `uv pip compile requirements.in --output requirements.txt` , now that will generate a `requirements.txt` file and we can use `uv pip install -r requirements.txt`. 
2. The repo you are truing to clone already manages dependencies using a  pyproject.toml (e.g., from Poetry or PEP 621) file, simply run  `uv pip install .`
3. Lets say you have a `pyproject.toml` and you want `requirements.txt` (for what ever reason, Docker, etc(we do not judge :) )) then run `uv pip compile pyproject.toml --upgrade --output requirements.txt`, `uv pip freeze > requirements.txt ` , `uv export --no-hashes --format requirements-txt > requirements.txt`
4. Lets say we have a req.txt and we want to install the dependencies and add it to toml file then run `uv add -r requirements.txt`. 
- Remember you can also do uv pip install but that wont sync the toml file so we can directly do uv add. Anyway when you do uv run, uv sync is called. 
Now recommendation is try using a pyproject.toml but at the end of the say who cares, just get shit done. 


