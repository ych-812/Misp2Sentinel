# Misp2Sentinel
Serverless Azure Function that automatically forwards threat indicators from MISP to Microsoft Sentinel every 2 hours

# MISP to Microsoft Sentinel Integration

Automated threat intelligence sync from MISP to Microsoft Sentinel using Azure Functions.

## Project Overview

This project automatically forwards threat indicators from a MISP instance on a Ubuntu Server to Microsoft Sentinel (Defender) Threat Intelligence platform using Azure Functions and Python.

**Architecture:**
- MISP server hosted on Ubuntu Server 24.04
- Azure Function (Python 3.11) with timer trigger
- Microsoft Sentinel workspace for threat intelligence

## What It Does

- Pulls published threat indicators from MISP every 2 hours
- Converts MISP events to STIX 2.1 format
- Uploads indicators to Microsoft Sentinel via Upload Indicators API
- Processes 40,000+ indicators automatically

## Technologies Used

- **MISP** - Threat intelligence platform
- **Azure Functions** - Serverless compute
- **Python 3.11** - Runtime environment
- **Microsoft Sentinel (Defender)** - SIEM and threat intelligence
- **STIX 2.1** - Threat intelligence format

## Results

+ Successfully deployed and tested  
+ Processes 40,000+ threat indicators per sync  
+ Automated sync every 2 hours via timer trigger  
+ Handles pagination for large datasets  

## Screenshots

- Sentinel Threat Intelligence dashboard
<img width="1635" height="914" alt="threat dash" src="https://github.com/user-attachments/assets/0709115b-ab22-4ef6-949c-d5210011ea37" />

  
- MISP2Sentinel connector status
  
  <img width="460" height="260" alt="connected" src="https://github.com/user-attachments/assets/51e175d3-f223-48c1-a5e2-3b86c222928b" />


## Challenges Solved

- **Python 3.12 compatibility** - Downgraded to Python 3.11 for legacy STIX library support
- **Function timeout** - Increased timeout settings for large datasets
- **Infinite loop bug** - Fixed recursive function calls
- **Environment configuration** - Properly configured Azure application settings

## Setup Requirements

- Azure subscription with Sentinel
- MISP instance with API access
- Azure App Registration with Sentinel Contributor role
- VS Code with Azure Functions extension

## Key Files

- `MISP2Sentinel/__init__.py` - Main function logic
- `config.py` - Configuration (uses environment variables)
- `requirements.txt` - Python dependencies
- `function.json` - Timer trigger configuration

## Acknowledgments

Based on [cudeso/misp2sentinel](https://github.com/cudeso/misp2sentinel)
