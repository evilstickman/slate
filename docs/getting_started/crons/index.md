Background jobs allowing you to run an action, query, or external URL request on a schedule that you define. Simply set the schedule's time and frequency, and the desired task will be executed automatically by Backand's servers. Through this mechanism, you can run periodic queries for things like reports, recurring actions to control you application's behavior, or you can regularly post to external services that support your application's behavior.

## Create a job

To create a new Background job, click on "+ New Job" in the "Background jobs" section of the navigation bar. Simply add a name, a description, a start time or frequency, and set the type of job (Action, Query, External URL) to execute.

#### Advanced Options

In the advanced options, you can configure the job to operate via either GET request, or via a POST. The GET request allows you to configure the query string used in the request, as well as modify the headers sent - allowing you to send additional parameters to the job when it executes. For POST requests, you get both the headers and the query string to modify, but you are also given the Request Data field which you can use to send additional parameter formats, like long text.

This can be very useful in distinguishing between two jobs that run the same action. For each job, you can send a "type" parameter to indicate the specific job being run. You can accomplish this by setting the "Query String" field to the appropriate value: 'parameters={type:1}' for job 1, and 'parameters={type:2}' for job 2.

## Update an existing job

You can update existing job by selecting the background job from the navigation menu and pressing the "Edit" button. This gives you the capability to change all aspects of the job.

## Test a job

You can test both new and existing job using the Test buttons on the right hand side of the page. These buttons execute the job on Backand's servers, displaying the request sent and the response received. In addition to simple verification, Testing should be used to verify that advanced parameters function properly, and that the job responds as expected.

## Run background job using REST API
 Background Jobs are useful for long running tasks such as integrating with external sites where the response time could be slow, or sending out batched push notifications. If you commonly encounter timeout errors running on-demand actions then you should consider using a Background Job.
 All messages and errors are logged into the console messages available under Log --> Console menu.

 Use this REST API to call the job:

 ```
 https://api.backand.com/1/jobs/run/{id}
 ```

 Use this code to call the job from an action:

 ```javascript

    var response = $http({
        method: "GET",
        url: CONSTS.apiUrl + "/1/jobs/run/" + cronId
    });
 ```