A/B Testing to Determine an Effective Approach to Reduce Early Udacity Course Cancellation
==========================================================================================

Experiment Overview
----------------------

At the time of this experiment, Udacity courses currently have two options on the home page: "start free trial", and "access course materials". If the student clicks "start free trial", they will be asked to enter their credit card information, and then they will be enrolled in a free trial for the paid version of the course. After 14 days, they will automatically be charged unless they cancel first. If the student clicks "access course materials", they will be able to view the videos and take the quizzes for free, but they will not receive coaching support or a verified certificate, and they will not submit their final project for feedback.

In the experiment, Udacity tested a change where if the student clicked "start free trial", they were asked how much time they had available to devote to the course. If the student indicated 5 or more hours per week, they would be taken through the checkout process as usual. If they indicated fewer than 5 hours per week, a message would appear indicating that Udacity courses usually require a greater time commitment for successful completion, and suggesting that the student might like to access the course materials for free. At this point, the student would have the option to continue enrolling in the free trial, or access the course materials for free instead. The experiment looks like: ![Experiment Screenshot](exp_screenshot.png)

The hypothesis was that this might set clearer expectations for students upfront, thus reducing the number of frustrated students who left the free trial because they didn't have enough time—without significantly reducing the number of students to continue past the free trial and eventually complete the course. If this hypothesis held true, Udacity could improve the overall student experience and improve coaches' capacity to support students who are likely to complete the course.

The unit of diversion is a cookie, although if the student enrolls in the free trial, they are tracked by user-id from that point forward. The same user-id cannot enroll in the free trial twice. For users that do not enroll, their user-id is not tracked in the experiment, even if they were signed in when they visited the course overview page.

Experimental Design
-------------------

### All Metrics

* **Number of cookies**: Number of unique cookies to view course overview page.
* **Number of clicks**: Number of unique cookies to click the "Start Free Trial" button (which happens before the free trial screener is triggered).
* **Number of user-ids**: Number of users who enroll in the free trial.
* **Click-through-probability**: Number of unique cookies to click the "Start Free Trial" button divided by number of unique cookies to view the course overview page.
* **Gross conversion**: Number of user-ids to complete checkout and enroll in free trial divided by number of unique cookies to click "Start Free Trial" button.
* **Retention**: Number of user-ids to remain enrolled past the 14-day boundary (and thus make atleast one payment) divided by number of users to enroll in the free trial.
* **Net conversion**: Number of user-ids to remain enrolled past the 14-day boundary divided by the number of unique cookies to click the "Start Free Trial" button.

### Metric Choice

Invariant metrics are those should not be affected by experiment. One could expect a similar result of such metrics both on control and experiment groups.
The invariant metrics for the given test are as follow:
#### Invariant metrics:
  1. **Number of cookies**: This is the unit of diversion and since the visits to the course page happen before the experiment, we should expect similar metrics between control and experiment groups.

  2. **Number of clicks**: Since the clicks happen before the screener, the metric is independent of the test. So, the metric should be evenly distributed among the control and experiment groups.

  3. **Click-through-probability**: This metric is the ratio between the two metrics above. Since the two metrics above are not affected by the experiment, the ratio should not be affected too.


#### Evaluation metrics:
The evaluation metrics are used to measure which variation is better. Each evaluation metric is associated with a minimum difference (dmin) that must be observed for consideration in the decision to launch the experiment.
  1. **Gross conversion**: Ideally, we expect to the decreased gross conversion rate in the experiment group, because students will be deferred to enroll in the free trial if they know they don’t have enough studying. 

  2. **Rentention**: We expect the retention rate to go up because students have clearer expectation of the course time requirements and thus more likely to stay in the course after they enrolled.

  3. **Net conversion**: Ideally, net conversion rate would remain similar or increase in the experiment group. Students remain enrolled past the 14-day boundary might be similar between the control and experiment groups. The difference is that unprepared students in the experiment would enroll after they the screener while the unprepared students in the control group would drop within the first 14 days. On the other hand, since students are well informed, the students in the experiment may plan accordingly and still choose to enroll with fewer dropouts. So, the net conversion rate might go up. 


#### Unused metrics:

  1. **Number of user-ids**: User-ids are tracked only after enrolling in the free trial and equal distribution between the control and experimental branches would not be expected. User-id count could be used to evaluate how many enrollments stayed beyond the 14 day free trial boundary, but it is not normalized which means the number of cookies could have effect (Gross conversion would be better as it is normalized)



