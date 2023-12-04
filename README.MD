
# How to import `repos.yaml`

```bash
vcs import src < repos.yaml # change the file name
rosdep install --from-paths src --ignore-src -r -y
colcon build --symlink-install
```


