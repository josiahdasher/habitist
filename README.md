# habitist [![Code Climate](https://codeclimate.com/github/amitness/habitist/badges/gpa.svg)](https://codeclimate.com/github/amitness/habitist)
An automation to enable habit tracking in todoist. 

It integrates Seinfield's "[Don't Break the Chain](https://lifehacker.com/281626/jerry-seinfelds-productivity-secret)" method into [todoist](http://todoist.com/). Once it's setup, you can forget about it and it works seamlessly.

## Usage

![Habitist Screenshot](https://i.imgur.com/q4h2QGv.png)

1. You add habits you want to form as task on todoist with schedule `every day`

2. Add `[day 0]` to the task

3. When you complete the task, the [day 0] will become [day 1]

4. If you fail to complete the task and it becomes overdue, the script will schedule it to today and reset [day X] to [day 0].

## Installation
1. Fork and clone the repo
    ```
    git clone https://github.com/yourgithubusername/habitist
    ```
2. Create a heroku app.
    ```
    heroku create appname
    ```
3. Set environment variable with your todost API key. You'll find API key under `Settings > Integrations` on [todoist.com](https://todoist.com).
    ```
     heroku config:set TODOIST_APIKEY='XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX'
    ``` 

4. Push the app
    ```
    git push heroku master
    ```
5. Find your timezone difference from UTC. We need to trigger this API when it's 12:00 AM in UTC. You need to find the local time when it's 12:00 AM in UTC.     
    `
    For example, Nepal is 5:45 hrs ahead of UTC. For 12:00AM in UTC, we have 5:45AM here. So, we need to trigger this API anytime after 5:45AM. Do the same calculation for your timezone and set that time in step 6.
    `

6. On [IFTTT](http://ifttt.com/), [create](https://ifttt.com/create) a new applet.
    - On THIS, select datetime > 'Every Day At' > `Time from step 5`
    - On THAT, select Webhooks > `Make a web request`
    - Set URL to your heroku app URL
    - Set METHOD to GET
    - Hit Create Action

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details
