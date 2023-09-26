Create user - 

```bash
elasticsearch-users useradd basu -p basu123 -r network,monitoring

# Now, the user file will have an entry like this - 
basu:$2a$10$DLBZZgtwBLk6nO8T93a6hueAUriqME8I0Uh6352pQh2sT43uhfeF6
```

Update user_roles.yml if needed

```yaml

# user_roles.yml

admins:basu
monitor:basu
monitoring:basu
network:basu
```

Update roles.yml. In case of clean installation it should be empty

```yaml
# roles.yml

admins:
  cluster:
    - all
  indices:
    - names:
        - "*"
      privileges:
        - all
devs:
  cluster:
    - manage
  indices:
    - names:
        - "*"
      privileges:
        - write
        - delete
        - create_index
```

Run Elasticsearch and try accessing [localhost:9200](http://localhost:9200). Provide the username and password