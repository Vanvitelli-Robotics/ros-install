
# How to import `repos.yaml`

```bash
vcs import src < repos.yaml # change the file name
rosdep install --from-paths src --ignore-src -r -y
colcon build --symlink-install
```

# Allow a user to set real-time permissions for its processes

After the PREEMPT_RT kernel is installed and running, add a group named realtime and add the user controlling your robot to this group:
```bash
sudo addgroup realtime
sudo usermod -a -G realtime $(whoami)
```

Afterwards, add the following limits to the realtime group in /etc/security/limits.conf:
```bash
@realtime soft rtprio 99
@realtime soft priority 99
@realtime soft memlock 102400
@realtime hard rtprio 99
@realtime hard priority 99
@realtime hard memlock 102400
```
