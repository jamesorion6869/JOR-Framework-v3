# DoD Deployment Quick-start

This project is designed for rapid evaluation and deployment inside STIG-compliant DoD environments with minimal accreditation overhead.

## Platform Assumptions

RHEL 8.x (STIG applied), offline or restricted-network environment, no elevated runtime privileges.

## Environment Setup

Python 3.10 from EPEL (STIG ID: RHEL-08-00-010292)

### Install Python 3.10 and pip
sudo dnf install python3.10 python3-pip -y

### Create isolated virtual environment
python3.10 -m venv /opt/jor

### Install dependencies in the virtual environment
/opt/jor/bin/pip install -r requirements.txt --no-deps --no-cache

## Runtime Controls

Run as unprivileged service account: `jor_svc`  
Output directory permissions: 755  
CSV output files: 644

## Security Notes

No compiled C/C++ extensions  
No SUID binaries  
No network listeners  
No external callbacks

This configuration supports expedited ATO review and is compatible with standard DoD software assurance workflows.
