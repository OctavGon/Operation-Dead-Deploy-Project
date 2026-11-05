# Operation-Dead-Deploy-Project
# <h1><h1>Investigating a junior intern with contributor access and no governance knowledg

## <h1><h1>Scenario
Junior intern was given temporary contributor access to start up a test environment to experiment in. The intern does not have knowledge in the company's governance standards and took shortcuts deploying and left the environment for the weekend. 

## <h1><h1>Environment
Azure Portal, live multi-user Azure training tenant, Reader access.

## <h1><h1>Investigation

Step 1-Looked for subscriptions.

<img width="609" height="194" alt="image" src="https://github.com/user-attachments/assets/85bd256f-c334-4b29-98c8-9bdc62895ab3" />

Step 2-Found and viewed subscription.

<img width="1852" height="457" alt="image" src="https://github.com/user-attachments/assets/3a8b4829-a1fc-4413-9ed1-180a2aab9f86" />

Step 3-Looked for Resource group blade.

<img width="1553" height="776" alt="image" src="https://github.com/user-attachments/assets/70e2afa9-708e-490d-b344-386850891f08" />

Step 4-Look for out of place or anything that doesn't follow naming conventions.

<img width="1542" height="918" alt="image" src="https://github.com/user-attachments/assets/640dd083-add7-408c-9d49-f1ad49e4b64b" />

Step 5-Inspect the offending resource group and see what it contains.

<img width="1868" height="717" alt="image" src="https://github.com/user-attachments/assets/009b3787-300c-4216-bf7c-afc398203b7a" />

Step 6-Open the resource and look tags too see what was going on.

<img width="1846" height="714" alt="image" src="https://github.com/user-attachments/assets/1da7b55f-a7f7-47f0-a12e-a2a569a01fb9" />

Step 7-Trace where it was deployed so i check the record in the resource group's deployments blade back at the resource group's overview.

<img width="1871" height="802" alt="image" src="https://github.com/user-attachments/assets/fae26549-600e-4364-a4b6-10df1c25671c" />

Step 8-Find the intern's resource that got created.

<img width="1849" height="788" alt="image" src="https://github.com/user-attachments/assets/dd176abd-a4bd-4417-b0cf-4cbe00a38811" />

Step 9-Find why the reason why the intern's resource group that's non-compliant slipped through policy that enforces naming conventions in the policies blade.

<img width="1852" height="915" alt="image" src="https://github.com/user-attachments/assets/204f8ae6-0684-4589-8a71-5906c6fee3d0" />

Step 10-I look and find under compliance state that there's a policy that was supposed to enforce naming that is flagged "non compliant" so i go to the "Assignments" on the left hand side to see the policy assignments listed for this resource.

<img width="1822" height="651" alt="image" src="https://github.com/user-attachments/assets/810124a9-54b7-460b-bfa9-5f6a13f0dc41" />

Step 11-I click on the Naming convention policy then go to the parameters tab and notice that the Effect parameter is set to audit which should have been set to deny which blocks non-compliant requests. This why the intern's resource was able to exist even through naming policys. 

<img width="1825" height="630" alt="image" src="https://github.com/user-attachments/assets/c4f35d13-7abb-46c2-bb6a-364ee7568ed3" /> <img width="1831" height="559" alt="image" src="https://github.com/user-attachments/assets/10740c93-e97f-4fd8-b8c3-a18ba4afd06a" />

Step 12-Change the parameter value to deny to enforce Naming convention policy.

## <h1><h1>What broke / what surprised me
Things that surprised me are how effective following and keeping naming conventions help us find things out of place in the environment. I did get lost a couple of times trying to find policy assignments since there is a couple blades with that title. I also was surprised that the something important such as naming policies would have a oversight that could easily let very obvious resources deploy with little to no governance standards.

## <h1><h1>Findings and recommendations
I would report to the owner that policy was set to audit and not deny which caused a interns deployment to slip through. I would explain the reasons why it should be changed and ask if it was intentional or was it for testing.

## <h1><h1>What I learned
- I would first from now on think if i saw a resource group or anything that is named so differently compared to anything else in the list assume that a policy failed to enforce regular and efficient practice. I would this new info to speed up and find this kin of issue allot faster.
- I also learned that there's 2 kinds of assignment blades and now know which one takes me to the Policy assignments with the info for the values. I wont get those confused again.
- I from now on will be making sure that configurations are in line with our policies inline with our security guidlines.
- Lastly now i know how to stop bad things from being created and or prevent things from being removed.
