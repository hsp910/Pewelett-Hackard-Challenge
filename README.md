# Background
Pewlett Hackard is a company that is currently very worried about a large retirement wave, also called the "silver tsunami" by some management, that is fast approaching their company. To check how many employees they might lose to this retirement wave they have asked an employee to get logs from a SQL database that includes every single employee's information including birth date, job start date, job end date, and their job title. We will be using that information to help decide how Pewlett Hackard should deal with this large scale retirement wave including how large of a population of employees they have to train and mentor the next generation of employees meant to replace the retiring ones at the moment. 

# Analysis and Results
From the data we were given we made a few tables to help determine the retirement info behind many of those that will be included in the "silver tsunami." The first table we created was to compile all the possible retirees and their job titles.

![Retirement Titles table without filtering for distinct values](https://i.imgur.com/RZ6jwqb.png)

This table was created to focus on all of the possible future retirees. The data given down was that we should only focus on those that were born betweeen the years of 1952 and 1955 as a part of this retirement wave. However there is one large issue with this table that we can see from the fact there are duplicate values. These duplicate values are due to employees changing their titles to different ones and retaining it in the system as a separate entry. To solve this we will need to filter out all the duplicates and only focus on the most recent titles.

![Retirement titles after making sure only a single employee id showed up with the most recent title](https://i.imgur.com/pKY4rwS.png)

Using the DISTINCT ON command and by filtering all the titles in a descending order, therefore putting the most recent title as the one to show on the table, we are able to now remove all the duplicate entries in the table and focus on the final titles these employees will have for their upcoming retirement.

![Counting the unique ids per each final job title for the retirees](https://i.imgur.com/lXUHhHY.png)

This table was created using the COUNT and GROUPBY functions to show the number of employees in each job title retiring. This is most important to let the company know how many employees need to be trained into each role, even if not direclty the senior versions of each role depending on market availability. This table will become even more important later once we are able to establish the amount of mentors available.

![Mentorship Eligibility table that is far too narrow](https://i.imgur.com/e2y1Jgs.png)

This table is the table of employees "qualified" to be mentors by using the company standards. In this case the company wants mentors to be employees born in the year of 1965 to be exact. What is not exactly shown in this screenshot is how much shorter this list is compared to the retirees in the previous tables.

# Summary
## Mentor Issues
Now there are some fairly large issues with the mentorship eligibility that Pewlett Hackard wants to use, largely the lack of mentors for the number of roles that need to be filled.

![Total number of retirees according ot the unique titles table](https://i.imgur.com/B0B9dZJ.png)

This number was found using the COUNT function on the unique titles table that was shown above. Now as we can see there is over 90000 retirees in this up coming wave. Assuming that roughly the same number retire per year Pewlett Hackard would have to onboard roughly 30000 new employees over the course of 3 years to not have staffing issues hit them in the middle. However the number of eligible mentors leaves a lot to be desired.

![Total number of mentors eligible according to the eligibility table](https://i.imgur.com/1lY1Zb1.png)

This was also found using the COUNT function on the mentor eligibility table. Even if you were to assume each and every single employee that is eligible can mentor in any role for the incoming employees each employee would be responsible for at least 58 newcomers for the next 3 years. In other words each mentor would need to on board roughly 19 new employees a year during this retirement wave to replace staffing as quickly as Pewlett Hackard is projecting they will lose it. However, this does not include the entire story either. If we were to look at the number of mentors in each unique title we would notice another large issue on the horizon.

![Unique titles per eligible mentor](https://i.imgur.com/adoElsu.png)

This table was found using the same process as the third table under the Analysis and Results tab. As we can already see there are not the same distribution of employees in the menotrs as the retirees. In fact the arrangement would make the staffing issues worse for onboarding the most in demand roles. 722 employees in the eligible mentors are a part of the general staff, ignoring seniority for the sake for training, There are 749 available engineers, again combining the normal engineers with the senior and assitant titles, for the nearly 45,397 total engineers that need to be filled in the upcoming 3 years. While it does not increase the number of new employees per mentor much, it does increase the total number per mentor to 60 new employees per mentor in the next 3 years. We also are lacking any managers to mentor the 2 that need to replace the current retirees.

## Conclusion
If we were to consider the amount of work to onboard a new employee as at the very least a 2 month process, a relatively low estimate, it is very unlikely that the current eligible mentors will be able to complete the onboarding requirements Pewlett Hackard is looking for. I think the most reasonable way to expand the amount of mentors to match the number of incoming new employees would be to expand the number of years they are looking for in the eligible mentors. Possibly all employees born betweeen 1965 and 1968 to match the 3 years of employees leaving the company in this retirement wave. If Pewlett Hackard does not expand the number of mentors they are planning on using it is highly likely they will not be able to train new employees in time to take over the responsibilities of the retiring generation of workers. They also risk burning out their mentors by asking them to do even more work than would be expected at most companies which could lead to a domino effect of losing an even larger portion of their workforce.
