---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "grafana_oncall_escalation Resource - terraform-provider-grafana"
subcategory: ""
description: |-
  Official documentation https://grafana.com/docs/grafana-cloud/oncall/escalation-policies/HTTP API https://grafana.com/docs/grafana-cloud/oncall/oncall-api-reference/escalation_policies/
---

# grafana_oncall_escalation (Resource)

* [Official documentation](https://grafana.com/docs/grafana-cloud/oncall/escalation-policies/)
* [HTTP API](https://grafana.com/docs/grafana-cloud/oncall/oncall-api-reference/escalation_policies/)

## Example Usage

```terraform
resource "grafana_oncall_escalation_chain" "default" {
  provider = grafana.oncall
  name     = "default"
}

data "grafana_oncall_user" "alex" {
  username = "alex"
}

// Notify step
resource "grafana_oncall_escalation" "example_notify_step" {
  escalation_chain_id = grafana_oncall_escalation_chain.default.id
  type                = "notify_persons"
  persons_to_notify = [
    data.grafana_oncall_user.alex.id
  ]
  position = 0
}

// Wait step
resource "grafana_oncall_escalation" "example_notify_step" {
  escalation_chain_id = grafana_oncall_escalation_chain.default.id
  type                = "wait"
  duration            = 300
  position            = 1
}

// Important step
resource "grafana_oncall_escalation" "example_notify_step" {
  escalation_chain_id = grafana_oncall_escalation_chain.default.id
  type                = "notify_persons"
  important           = true
  persons_to_notify = [
    data.grafana_oncall_user.alex.id
  ]
  position = 0
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `escalation_chain_id` (String) The ID of the escalation chain.
- `position` (Number) The position of the escalation step (starts from 0).

### Optional

- `action_to_trigger` (String) The ID of an Action for trigger_action type step.
- `duration` (Number) The duration of delay for wait type step.
- `group_to_notify` (String) The ID of a User Group for notify_user_group type step.
- `important` (Boolean) Will activate "important" personal notification rules. Actual for steps: notify_persons, notify_on_call_from_schedule and notify_user_group
- `notify_if_time_from` (String) The beginning of the time interval for notify_if_time_from_to type step in UTC (for example 08:00:00Z).
- `notify_if_time_to` (String) The end of the time interval for notify_if_time_from_to type step in UTC (for example 18:00:00Z).
- `notify_on_call_from_schedule` (String) ID of a Schedule for notify_on_call_from_schedule type step.
- `persons_to_notify` (Set of String) The list of ID's of users for notify_persons type step.
- `persons_to_notify_next_each_time` (Set of String) The list of ID's of users for notify_person_next_each_time type step.
- `type` (String) The type of escalation policy. Can be wait, notify_persons, notify_person_next_each_time, notify_on_call_from_schedule, trigger_action, notify_user_group, resolve, notify_whole_channel, notify_if_time_from_to

### Read-Only

- `id` (String) The ID of this resource.

## Import

Import is supported using the following syntax:

```shell
terraform import grafana_oncall_escalation.escalation_name {{escalation_id}}
```