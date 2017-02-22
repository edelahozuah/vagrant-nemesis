#OSCAP validation Scenario

Some useful commands to be used for testing:

##Check SCAP Content

```Shell
oscap info /usr/share/xml/scap/ssp/content/ssg-centos7-ds.xml
```

##User-friendly Presentation of SCAP Guide
```Shell
oscap xccdf generate guide --profile xccdf_org.ssgproject.content_profile_rht-ccp /usr/share/xml/scap/ssg/content/ssg-centos7-ds.xml > /vagrant/ssg-guide-centos7-rht-checklist.html
```

##Launch Evaluation 
```Shell
oscap xccdf eval --profile xccdf_org.ssgproject.content_profile_rht-ccp --results scan-xccdf-rht_ccp-results.xml /usr/share/xml/scap/ssg/content/ssg-centos7-ds.xml
```


##Generate Report
```Shell
oscap xccdf generate report scan-xccdf-rht_ccp-results.xml > /vagrant/scan-xccdf-rht_ccp-report.html
```
##Generate Fix for Detected Issues
```Shell
oscap xccdf generate fix --template urn:xccdf:fix:script:sh --profile xccdf_org.ssgproject.content_profile_rht-ccp --output /vagrant/remediation-script.sh /usr/share/xml/scap/ssg/content/ssg-centos7-ds.xml
```
##Apply Remediation Script
```Shell
sudo remediation-script.sh
```
##Re-evaluate
```Shell
oscap xccdf eval --profile xccdf_org.ssgproject.content_profile_rht-ccp --results scan-xccdf-rht_ccp-results-after.xml /usr/share/xml/scap/ssg/content/ssg-centos7-ds.xml
```
##Re-Generate Report to check the applied fixes
```Shell
oscap xccdf generate report scan-xccdf-rht_ccp-results-after.xml > /vagrant/scan-xccdf-rht_ccp-report-after.html
```


##References:

[National Checklist Program Repository] (https://web.nvd.nist.gov/view/ncp/repository)
[CIS Checklist for CentOS 7] (https://benchmarks.cisecurity.org/downloads/show-single/index.cfm?file=centos7.110)
[Hardening CentOS 7] (https://highon.coffee/blog/security-harden-centos-7/)
[Red Hat Enterprise Linux 7 Security Guide] (https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/7/pdf/Security_Guide/Red_Hat_Enterprise_Linux-7-Security_Guide-en-US.pdf)
[GovReady Initiative for promoting compliance using SCAP] : (https://github.com/GovReady/testmachines)
[Automated auditing the system using SCAP] (https://securityblog.redhat.com/2013/11/13/automated-auditing-the-system-using-scap-2/)
[OVAL System Characteristics Scan using OpenVAS] (http://www.greenbone.net/learningcenter/oval_sc.html)

