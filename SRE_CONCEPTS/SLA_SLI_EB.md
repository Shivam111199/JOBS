This is an compresnsive summary of SLI,SLO,ERROR BUDGEt, Incident managemnt

# SLA - * A buisness level agrrement with client that includes penalties if the targets SLO not matched.
      * It defines if you fail to meet SLO will apply penalty or give 10% of on your next bill.
      * The leagal and sales teams defines this.

# SLI - * Service level indicator - a meaure in numbers of services successful requests to total requests.
      * We defines these on API basis , Approval rate , Payment Success rate , latency , Successfull checkout.
      * You wrote the query to define on tools/portals with like (Approve and decline rate for an api)
      E.G >   What is a "good" event? (e.g., an HTTP request that returns a 200 OK status code).
              What is a "bad" event? (e.g., an HTTP request returning a 5xx server error).
              sum(rate(http_requests_total{service="checkout", status!~"5.."}[$__range])) / sum(rate(http_requests_total{service="checkout"}[$__range]))
              It counts all non-5xx requests (good) and divides them by all requests (total), giving you the current success rate.

# SLO - * Service level obejective (Targets) - measure of numbers given by merchant to meet SLI with them
      * For an API you set the success rate should be 99.9%. These are defined in various category like merchants 
      * if you miss the SLO, you stop launching new features until you fix it.

# Error Budget - * The % amount of reliabilty you to have fix the thing in downtime.
               * If you have budget left → launch features. If you burn all budget → stop launches and fix bugs.
               * Example: SLO = 99.9% → Error Budget = 0.1% (about 43 minutes per month). 
                 If your site is down for 10 minutes, you have 33 minutes left. If down for 50 minutes, you are over budget; CEO approves no new features this month.

                      How to caluculate remaining error budget 
                                E.G: Your time window is 30 days 
                                      > 30 Days * 24(Hours)= 720 hrs
                                      > 720 HR * 60 MIN = 43,200 MIN
     
                                     Your SLO Target is 99.9%
                                      > 0.1% Doowtime allowed
                                      > 43,200 × 0.001 = 43.2 minutes of downtime allowed per month.

                                     Your SLI is 99.95% 
                                      > 100% (Total) - 99.95%(SLI) = 0.05%.
                                      > 0.05% of 43,200 minutes =
                                      > 43,200 × 0.0005 = 21.6 minutes of actual downtime used.

                                     Error Budget
                                      > Total budget = 43.2 minutes
                                      > Used so far = 21.6 minutes
                                      > Remaining = 43.2 - 21.6 = 21.6 minutes
 
                                                       The dashboard rounds it to 22 minutes.
                                                       (If your SLO is 98 for 7 days then 7*24(hr)*60(min)=10,080 mins 
                                                       Your allowed error budget 2% from 100 [2/100=0.02]
                                                       0.02 of 10,080 = total allwed budget is 201.6 min
                                                       Now your SLI is 95 then 5% 
                                                       Total minutes 10080 * 0.05 =504 mins.
                                                       You consumed more than aloowed limit no new realses.


# MTTR - * Mean Time To Repair how much time you took to fix or keep back on stage (issue occured 02:10 - 02:15 issue resolved - 5 mins Low MTTR)

# MTBF - * (Mean Time Between Failures) you need high MTBF to show stability.

# incident management - Find , fix, communicate Example: "Page on-call engineer → Acknowledge within 5 min → Declare severity (P0/P1/P2) → Fix or rollback → Update status page."

# Toil Reduction  Meaning: Toil is manual, repetitive, automatable work that does not add long-term value (e.g., resetting passwords, restarting servers).






