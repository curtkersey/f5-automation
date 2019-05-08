These playbooks currently assume that the BIG-IP is at IP address 10.1.1.4

One way to show how ansible works with BIG-IP:

1. Create application by running the app.yml playbook

   # ansible-playbook -i inventory/hosts playbooks/app.yml

   => creates Virtual server named "app2_vs" that has pool named "app2_pl" and two pool members: 10.1.20.13, 10.1.20.14

2. Change state of pool member by taking it offline:

   # ansible-playbook -i inventory/hosts playbooks/pm-state.yml -e pool_name="app2_pl" -e pm_ipaddr="10.1.20.13" -e pm_port="80" -e pm_state="forced_offline"

   => Look at BIG-IP, and you will see pool member is now offline

3. Remove pool member from pool:

   # ansible-playbook -i inventory/hosts playbooks/pm-state.yml -e pool_name="app2_pl" -e pm_ipaddr="10.1.20.13" -e pm_port="80" -e pm_state="absent"

   => Look at BIG-IP, and you will see pool member has been removed 

4. Add the pool member back:

   # ansible-playbook -i inventory/hosts playbooks/pm-state.yml -e pool_name="app2_pl" -e pm_ipaddr="10.1.20.13" -e pm_port="80" -e pm_state="present"

   => Look at BIG-IP, and you will see pool member is back 

5. Delete the app:

   # ansible-playbook -i inventory/hosts playbooks/app.yml -e state="absent"

   ==> Look at BIG-IP, and virtual server is now gone

Another way to show this is by using the playbook 
