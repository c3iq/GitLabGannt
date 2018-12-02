# GitLabGannt
# Owen Williams
# 2018

A Gantt chart from GitLab

This spreadsheet will take issues/tasks against Milestones in GitLab and create a Gantt chart from them.

I have GitLab installed in a Docker container. This is how I retrieve the issues:

*    $ docker exec -i -t gitlab_web_1 bash
*    $ gitlab-psql -d gitlabhq_production
*    $ Copy (select issues.iid, m.title, issues.title, issues.description, time_estimate, issues.due_date from issues, milestones as m where issues.state = 'opened' and issues.time_estimate > 0 and issues.milestone_id = m.id ORDER BY issues.due_date ASC) To '/tmp/issues.csv' With CSV DELIMITER ';';

Back at the host:
*    docker cp gitlab_web_1:/tmp/issues.csv .

I then delete everything in the "issues" sheet of the spreadsheet and make sure there is a row at the top that can say anything but I label them in bold:

*    Issues
*    Milestone
*    Title
*    Description
*    Estimate
*    Due date

The Gantt sheet describes everything in a milestone that has an estimate greater than zero.

See the LICENCE.md
