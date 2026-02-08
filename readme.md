# lesson_6_helm
lesson_6_helm

שיעורי בית – שיעור 6 – HELM
Part 1 – Create Helm Chart
PS C:\Users\Herzel\lesson6\helm_lesson6> dir -s
    Directory: C:\Users\Herzel\lesson6\helm_lesson6
Mode                 LastWriteTime         Length Name
d-----          2/7/2026   9:18 PM                charts

    Directory: C:\Users\Herzel\lesson6\helm_lesson6\charts
Mode                 LastWriteTime         Length Name
d-----          2/7/2026  10:04 PM                myapp

    Directory: C:\Users\Herzel\lesson6\helm_lesson6\charts\myapp
Mode                 LastWriteTime         Length Name
d-----          2/7/2026   9:57 PM                templates
-a----          2/7/2026   9:22 PM            136 Chart.yaml
-a----          2/7/2026   9:59 PM            237 values.yaml

    Directory: C:\Users\Herzel\lesson6\helm_lesson6\charts\myapp\templates
Mode                 LastWriteTime         Length Name
-a----          2/7/2026  10:00 PM            141 configmap.yaml
-a----          2/7/2026  10:02 PM            409 cronjob.yaml
-a----          2/7/2026  10:01 PM            402 daemonset.yaml
-a----          2/7/2026  10:00 PM            753 deployment.yaml
-a----          2/7/2026  10:01 PM            326 job.yaml
-a----          2/7/2026  10:00 PM            155 secret.yaml
-a----          2/7/2026  10:01 PM            195 service.yaml





Part 2 – Deploy the Chart
PS C:\Users\Herzel\lesson6\helm_lesson6> helm upgrade --install myapp ./charts/myapp
Release "myapp" does not exist. Installing it now.
NAME: myapp
LAST DEPLOYED: Sat Feb  7 22:11:38 2026
NAMESPACE: default
STATUS: deployed
REVISION: 1
DESCRIPTION: Install complete
TEST SUITE: None

Part 3 – Image Version Upgrade
Release "myapp" has been upgraded. Happy Helming!
NAME: myapp
LAST DEPLOYED: Sat Feb  7 22:57:11 2026
NAMESPACE: default
STATUS: deployed
REVISION: 3
DESCRIPTION: Upgrade complete
TEST SUITE: None











Part 4 – Helm History & Rollback
REVISION	UPDATED                 	STATUS    	CHART      	APP VERSION	DESCRIPTION     
1       	Sat Feb  7 22:52:18 2026	superseded	myapp-0.1.0	1.36       	Install complete
2       	Sat Feb  7 22:52:44 2026	superseded	myapp-0.1.0	1.36       	Upgrade complete
3       	Sat Feb  7 22:57:11 2026	superseded	myapp-0.1.1	1.37       	Upgrade complete
4       	Sat Feb  7 22:59:12 2026	deployed  	myapp-0.1.0	1.36       	Rollback to 1   

Rollback was a success! Happy Helming!

Part 5 – ConfigMap and Secret Usage
ב CONFIGMAP שומרים מידע רגיל , כמו הגדרות שלא אכפת לנו שכולם יראו. למשל הודעת פתיחה של האפליקציה או מידע כללי אחר.
ב SECRET  שומרים מידע רגיש שצריך להיות מוגן , כמו סיסמאות, מפתחות ,api token וכדומה.




