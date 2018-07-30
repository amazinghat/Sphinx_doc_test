# Orchestration

Heat is a service to orchestrate composite cloud applications using a declarative template format through an OpenStack-native REST API.

- Heat provides a template based orchestration for describing a cloud application by executing appropriate OpenStack API calls to generate running cloud applications.
- A Heat template describes the infrastructure for a cloud application in text files which are readable and writable by humans, and can be managed by version control tools.
- Templates specify the relationships between resources (e.g. this volume is connected to this server). This enables Heat to call out to the OpenStack APIs to create all of your infrastructure in the correct order to completely launch your application.
- The software integrates other components of OpenStack. The templates allow creation of most OpenStack resource types (such as instances, floating ips, volumes, security groups, users, etc), as well as some more advanced functionality such as instance high availability, instance autoscaling, and nested stacks.
- Heat primarily manages infrastructure, but the templates integrate well with software configuration management tools such as Puppet and Ansible.
- Operators can customise the capabilities of Heat by installing plugins.
- **Compatible with AWS CFT** - you can import definitions of your infrastructure to Heat

## More resources:
- [Tempalte Guide](https://docs.openstack.org/heat/latest/template_guide/index.html)
- [Example templates](https://docs.openstack.org/heat/latest/templates/index.html)
- [API Reference](https://developer.openstack.org/api-ref/orchestration/v1/)
- [Python Heat client](https://docs.openstack.org/python-heatclient/latest/s)