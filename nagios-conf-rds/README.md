# Generate Nagios Configigurations for all AWS EC2 Instances

More or less the same as `nagios-conf-ec2`.

The reason that the shared functions are not extracted into a library is to keep each script runnable standalone without other dependencies what so ever.

### Usage

Update global vars and nagios templates as needed

Example:

```
REGION = 'eu-west-2'
NAGIOS_CFG_DIR = '/usr/local/nagios/etc/cfgs/hosts'
NAGIOS_CFG_TEMPLATE = 'example_host.cfg.j2'
NAGIOS_VALIDATE_CMD = '/usr/local/nagios/bin/nagios -v /usr/local/nagios/etc/nagios.cfg'
NAGIOS_RESTART_CMD = 'service nagios restart'
```

Install dependencies `pip install -r requirements.txt`

Then `python generate-nagios-conf-for-aws-instances.py`

### How it works

Use boto3 to query all rds instnaces, then use jinja2 to render nagios config files.

Each time you run it, all the old config files are removed from the nagios config directory, then generate all the new confg files and restart.

### Dependencies

boto3, jinja2

### Release Note

v0.1    20170908    First edition.
