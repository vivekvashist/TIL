Show all the files currently trached under branch `main`

```python
git ls-tree -r master --name-only
or 
git ls-files
```
Show all the files currently untrached under branch 

```python
git ls-files --others --exclude-standard
or
git status -u
```
