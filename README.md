<img src="cadenceml.svg?raw=true" alt="CadenceML" width="200" />

CadenceML is a generalized, machine-readable, human-friendly format (based on [YAML](https://en.wikipedia.org/wiki/YAML)) for describing [outreach cadences](https://www.saastr.com/a-hands-on-guide-to-creating-your-own-sales-development-process/) for salespeople, customer success managers, and other teams that need to reach people on a predefined schedule.

## The CadenceML format

```yaml
# Example CadenceML file
# Any text following a # are comments and can be ignored.
# -----------------------------------------------------------------------------
# Start with a nickname for the cadence
7x7:
  # Indicate which days constitute the "business week." In most cases M-F is
  # the default and can be omitted. 1 = Monday, 2 = Tuesday, etc.
  eligible_days: [2, 3, 4, 5] # Skip Mondays
  # For `holiday_region` use a region code from
  # https://github.com/holidays/holidays/tree/master/definitions or use "none"
  # to disable regional holidays
  holiday_region: us
  # You can also specify additional holidays that may not be traditionally
  # observed in your region. Use a custom list of readily parseable dates like
  # "Dec 20, 2016" which will get added on top of regional holidays.
  holidays:
    - "Mar 14, 2017" # Pi day
  cadence:
    1: # The first day of the cadence—potentially today if it's a business day
        # Allowed values for `channel` are: `call`, `meeting`, `task`,
        # `deadline`, `email`, `social`
      - channel: email
        title: Intro email
        notes: Short and sweet email looking for a referral
      - channel: call
        title: Intro call
        notes: Leave a voicemail if no answer
    2:
      - channel: call
        title: Day 2 follow-up call
        notes: Don't leave a voicemail
    3:
      - channel: call
        title: Day 3 (AM) follow-up call
        notes: Don't leave a voicemail
      - channel: call
        title: Day 3 (PM) follow-up call
        notes: Leave a voicemail
    4:
      - channel: email
        title: Follow-up email
        notes: Try something funny?
    # Nothing on days 5 and 6
    7:
      - channel: email
        title: Breakup email
        notes: This is it!
# You can define multiple cadences in a single file like so:
8x8:
  # ...

```

## Examples

We have collected many popular cadences in the CadenceML format at the [Dealbot cadence library](../cadences).

## Tools that use CadenceML

* **[Dealbot](../dealbot)**: Open-source sales automation for Pipedrive

*Do you mantain a tool that uses CadenceML? Please open a Pull Request to add it to the list!*

## Contributing

We're actively seeking refinements to the format that 1) make it more broadly applicable and 2) clarify ambiguities. We're considerably more hesitant with backwards-incompatible changes.

Please do not contribute specific cadences here, although they're gladly accepted at the [Dealbot cadence library](../cadences)!

### To contribute

Simply make your proposed change to this README and submit a Pull Request.

## Brought to you by Faraday

![Faraday](https://cdn.rawgit.com/rossmeissl/9ca9523390a01aeb5458b520cd2b1252/raw/6367682fc0157c1a00d65f32ee399373cee03b96/faraday_logo.svg)

[Faraday](http://www.faraday.io) is a beautiful, map-driven customer outreach and analytics platform. Visualize your customers and explore hundreds of built-in household level attributes. Build audiences of customers, leads, and brand new prospects, then reach them online and off.

Faraday started the [Dealbot](../dealbot) project to share the open-source sales automation system we built on top of Pipedrive. Having a universal way to describe our cadences was a key prerequisite for this project, so we created CadenceML.