# Generate Nagios Configigurations for all AWS EC2 Instances

### Usage

Update global vars as needed

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

Use boto to query all ec2 instnaces, then use jinja2 to render nagios config files.

Each time you run it, all the old config files are removed from the nagios config directory, then generate all the new confg files and restart.

If for some reason you don't want a specific ec2 instance to be managed by nagios, just add a "Nagios": "ignore" tag into the ec2 instance and it will be ignored.

### Dependencies

boto, jinja2

### Release Note

v0.1    20170823    First edition.

