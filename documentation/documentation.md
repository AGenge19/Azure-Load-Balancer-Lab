# Azure Load Balancer with Multiple Virtual Machines

## Project Overview

This project demonstrates how I deployed a web infrastructure in Microsoft Azure using two Virtual Machines behind an Azure Load Balancer. The Load Balancer distributes incoming HTTP traffic across the two VMs and uses a health probe to ensure traffic is only sent to available instances.

## Objective

The goal of this lab was to build and test a simple load-balanced web infrastructure in Azure, while gaining practical experience with Azure networking, Virtual Machines, backend pools, health probes, and load-balancing rules.

## Azure Resources Deployed

* **Resource Group** - Used to organise and manage all resources for the project.
* **Virtual Network (VNet)** - Provided the network infrastructure for the Virtual Machines.
* **2 Virtual Machines** - Configured as backend web servers. Each VM hosted a simple web page to identify which instance responded to a request.
* **Azure Load Balancer** - Used to distribute incoming HTTP traffic across the two Virtual Machines.
* **Public IP Address** - Provided a single public entry point for accessing the application.

## Load Balancer Configuration

The Azure Load Balancer was configured with the following components:

* **Frontend IP Configuration** - A public IP address was assigned as the external entry point.
* **Backend Pool** - Both Virtual Machines were added as backend targets.
* **Health Probe** - Configured to regularly check whether the backend VMs were available.
* **Load Balancing Rule** - Configured to forward incoming HTTP traffic to the backend pool.

## Testing

To verify that the Load Balancer was working correctly, I used PowerShell to send multiple HTTP requests to the public IP address:

```powershell
1..10 | ForEach-Object { (Invoke-WebRequest -Uri "<public-ip>").Content }
```

All 10 requests returned successful HTTP responses, confirming that the Load Balancer was able to receive requests and route traffic to a healthy backend instance.

The individual web pages on the VMs were also configured to identify which VM responded, allowing the backend servers to be distinguished during testing.

## Outcome

This project gave me practical experience with Azure networking and load-balancing concepts. I configured a Virtual Network, deployed multiple Virtual Machines, created a backend pool, configured a health probe and load-balancing rule, and used automated PowerShell requests to verify connectivity and traffic distribution.

## Key Skills Demonstrated

* Microsoft Azure
* Azure Virtual Machines
* Azure Load Balancer
* Azure Virtual Network (VNet)
* Public IP configuration
* Backend pool configuration
* Health probes
* Load-balancing rules
* PowerShell
* Network connectivity testing
* Cloud infrastructure deployment
