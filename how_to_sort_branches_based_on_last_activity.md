To sort branches based on last activity use:

```python
git branch --sort=-committerdate --format="%(committerdate:relative)%09%(refname:short)"
```

To create an alias for long commands use:

```python
git config --global alias.recent 'branch --sort=-committerdate --format="%(committerdate:relative)%09%(refname:short)"'
```
