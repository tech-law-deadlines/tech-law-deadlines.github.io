# Tech-Law Deadlines Countdown

<!-- TOC start (generated with https://github.com/derlin/bitdowntoc) -->

- [Tech-Law Deadlines Countdown](#tech-law-deadlines-countdown)
   * [Adding or Updating a Conference](#adding-or-updating-a-conference)
   * [New Post: Fields Detail](#new-post-fields-detail)
      + [Deadline format](#deadline-format)
      + [Timezones](#timezones)
   * [Credits ](#credits)
   * [Notable resources](#notable-resources)

<!-- TOC end -->

## Adding or Updating a Conference

> :warning: **HELP ME**: If you find the following steps and directions hard to parse, send me an email with a conference you are interested in adding! nathan.reitinger@gmail.com

You will need to: (1) fork the repo; (2) find the `_data/conferences.yml` file; and (3) add to that file a new entry that is formatted like this:

```
- name: GenLaw
  description: Generative AI and Law
  year: 2024
  link: https://genlaw.org/2024-icml/cfp.html
  deadline: ["2024-06-10 23:59"]
  date: July 27
  place: Vienna, Austria
  tags: [AI, IP, PRIV]
  comment: rolling deadline
```

More details on creating the pull request may be found [here](https://www.digitalocean.com/community/tutorials/how-to-create-a-pull-request-on-github). In brief, one way to do this is to:

```
git branch test_branch
git checkout test_branch
<<<make your changes locally>>>
git add .
git commit -m 'test commit message here (please replace me)'
git push --set-upstream origin test_branch
git fetch upstream
git remote -v (just checking if output looks right, no need to enter this one)
git remote add upstream https://github.com/technology-law/tech-law-deadlines.github.io.git
git fetch upstream
git checkout main
git merge upstream/main
```

## New Post: Fields Detail



Required fileds include: `title`, `year`, `id`, `link`, `deadline`, `timezone`, `date`, `place`, `sub` attributes

Read the data format description below. ***Note that the timezone format sign is inverted*** (e.g., UTC+7 is written as `Etc/GMT-7`). It is not a bug; this is inherited from the other sites I cloned. Everyone agrees this is poor formatting. I'd be happy to move to a different timezone JavaScript library that uses a friendlier format, but I don't have time for that.

Descriptions of the fields:

| Field name          | Description                                                  |
| ------------------- | ------------------------------------------------------------ |
| `title`\*           | Short conference name, without year                          |
| `year`\*            | Year the conference is happening                             |
| `id`\*              | Title as lower case + last two digits of year                |
| `full_name`         | Description, or long name                                    |
| `note`              | Additional comments, e.g., co-located conference, rolling deadline |
| `link`\*            | URL to the conference home page                              |
| `deadline`\*        | A list of deadlines. (details below)                         |
| `abstract_deadline` | When the abstract is due (may be different from full paper)  |
| `timezone`\*        | Timezone in tz format. By default is UTC-12 (AoE) >>> see below for deadline formation |
| `date`\*            | When the conference is happening (month, day)                |
| `start`             | When the conference or workshop starts                       |
| `end`               | When the conference or workshop ends                         |
| `place`\*           | Where the conference is happening (city, state or country)   |
| `sub`\*             | One or multiple tags: `PRIV`, `IP`, `SEC`, or `AI` (topic); `JUNIOR` (junior faculty only) |

Fields marked with asterisk (\*) are required, otherwise the field is optional and may not be included.


### Deadline format

The *deadline* field can contain:

1. The simplest option: a date and time in ISO format. Example: `["2017-08-19 23:59"]` (Note that you need to wrap even a single deadline in a list).
2. If a deadline is rolling, you can use a template date, just substitute the
   year with `%y` and the year before the conference with `%Y`. Example:
   `["%y-01-15 23:59"]` means there is a deadline on the 15th January in the
   same year as the conference.
2. A list of (1) or (2). Example of two rolling deadlines, with one in the end
   of October in the year prior to the conference year, and the second in the
   end of February in the same year as the conference:
  ```
  - "%Y-10-31 23:59"
  - "%y-02-28 23:59"
  ```

On the page, all deadlines are displayed in viewer's local time (that's a feature).

*Note:* If the deadline hour is `{h}:00`, it will be automatically translated into `{h-1}:59:59` to avoid pain and confusion when it happens to be midnight in local time.

### Timezones

The timezone is specified in `tz format`. For the text-version, use this link [timezones](https://www.healthstream.com/hlchelp/Administrator/Classes/HLC_Time_Zone_Abbreviations.htm), and enter the `livemeetings` column as the timezone in quotes. Unlike abbreviations (e.g. EST), these are un-ambiguous. Here are tz codes for some common timezones:

| Common name                   | tz                                                                 |
|-------------------------------|--------------------------------------------------------------------|
| UTC                           | `Etc/UTC`                                                          |
| America Pacific Time          | `America/Los_Angeles`                                              |
| Pacific Standard Time (UTC-8) | `Etc/GMT+8` (Yes, the sign is inverted for some weird reason)      |
| America Eastern Time          | `America/New_York`                                                 |
| Eastern Standard Time (UTC-5) | `Etc/GMT+5`                                                        |
| American Samoa Time (UTC-11)  | `Pacific/Samoa` or `Etc/GMT+11`. This timezone does not use DST.   |
| Aleutian Islands              | `America/Adak`                                                     |

## Credits 

Website based on [ai-deadlines](https://aideadlin.es) by @abshkdz and [sec-deadlines](https://sec-deadlines.github.io ) by Bogdan Kulynych (maintained by [Clement Fung](https://clementfung.github.io/)).

## Notable resources

- Tiffany Li, https://tiffanyli.com/tech-ip-law-professor-resources/
- David A. Simon, https://www.davidasimon.us/conferences
