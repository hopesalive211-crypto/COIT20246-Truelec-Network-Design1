# COIT20246-Truelec-Network-Design1
# COIT20246 Project: Truelec Network Design and Security Assessment

## Project Overview
This project involves designing a comprehensive network solution for Truelec, an electrical contracting business, including network design, cloud services evaluation, cybersecurity risk assessment, and security control recommendations.

## Group Members
- **Student A**: [Name], ID: [Student ID]
- **Student B**: [Name], ID: [Student ID]

## Project Structure
- `plan.md` - Project plan and communication schedule
- `network.md` - Network design and diagrams
- `cloud.md` - Cloud services analysis
- `security.md` - Cybersecurity risk assessment
- `ethics.md` - Ethical and social issues analysis
- `reflection.md` - Project reflection and team contributions
- `risk_assessment.xlsx` - Complete risk assessment matrix

## Key Features
- Hierarchical network design (Core-Distribution-Access)
- Redundant WAN connections
- Cloud migration strategy analysis
- Comprehensive security risk assessment
- Professional video presentation

## Tools Used
- Diagrams.net for network diagrams
- GitHub for version control
- Microsoft Excel for risk assessment
- Zoom for team meetings and presentation recording

## How to View This Report
1. View each Markdown file in GitHub
2. Open diagrams in the `diagrams/` folder
3. Check cloud pricing exports in `cloud_pricing/` folder
 width="2044" height="2964" alt="image" src="https://github.com/user-attachments/assets/f047956c-b2e7-4d26-a19e-f3b3fd37eed9" />
# Project Plan

## Group Information
- **Group Number**: [Your Group Number]
- **Course**: COIT20246
- **Start Date**: [Date]
- **End Date**: [Date]

## Communication Plan
### Meeting Schedule
- **Weekly Meetings**: Every Sunday, 7:00 PM - 8:30 PM (AEST)
- **Mid-week Check-ins**: Every Wednesday, 8:00 PM - 8:30 PM (AEST)
- **Emergency Meetings**: As needed via WhatsApp group

### Communication Tools
- **Primary**: Zoom for video meetings
- **Secondary**: Microsoft Teams for chat
- **File Sharing**: GitHub Repository
- **Task Management**: Trello board

### Team Roles
- **Student A**: Network Design Lead, Documentation Manager
- **Student B**: Security Assessment Lead, Cloud Services Analyst

## Project Timeline
| Week | Tasks | Responsible | Status |
|------|-------|-------------|--------|
| 1-2 | Project Planning, Repository Setup | Both | Complete |
| 3-4 | Network Design and Diagrams | Student A | Complete |
| 5-6 | Cloud Services Analysis | Student B | Complete |
| 7-8 | Security Risk Assessment | Both | Complete |
| 9-10 | Ethical Analysis and Report Writing | Both | Complete |
| 11-12 | Final Review and Presentation | Both | In Progress |

## Milestones
1. ✅ Week 4: Network Design Completed
2. ✅ Week 6: Cloud Analysis Completed
3. ✅ Week 8: Risk Assessment Completed
4. ✅ Week 10: First Draft of Report
5. ⏳ Week 12: Final Submission

## Risk Management
| Risk | Probability | Impact | Mitigation Strategy |
|------|------------|--------|---------------------|
| Team member unavailability | Medium | High | Regular check-ins, clear task allocation |
| Technical difficulties | Low | Medium | Backup files, regular commits |
| Scope creep | Medium | Medium | Clear requirements, regular review |
| Time constraints | High | High | Strict timeline, priority-based work |

## Success Criteria
1. All tasks completed by deadline
2. Professional quality report
3. Effective team collaboration
4. Meeting all project requirements

# Network Design

## Assumptions
1. **Headquarters Location**: Melbourne, Victoria
2. **Branch Locations**: Brisbane (QLD), Perth (WA), Adelaide (SA)
3. **Headquarters Staff**: 65 employees
4. **Branch Staff (Brisbane)**: 25 employees

## Network Diagrams
### Headquarters Network
![Headquarters Network Diagram](diagrams/headquarters_network.png)

### Branch Office Network
![Branch Network Diagram](diagrams/branch_network.png)

## Design Justification

### Hierarchical Design Approach
We selected a three-tier hierarchical design (Core-Distribution-Access) because:
- **Scalability**: Easy to add new branches or expand existing ones
- **Performance**: Reduces broadcast domains, improves speed
- **Manageability**: Clear separation of duties and troubleshooting
- **Redundancy**: Multiple paths for critical connections

### Key Design Decisions
1. **Dual ISP Connections**: For redundancy and load balancing
2. **Core Switches in Stack**: Provides hardware redundancy
3. **Separate VLANs**: For security segmentation (servers, users, management, guests)
4. **Centralized WiFi Management**: Using wireless controllers
5. **VPN Tunnels**: For secure branch connections

## WiFi Design
### Configuration Settings
| Setting | Value | Justification |
|---------|-------|---------------|
| SSID (Corporate) | Truelec-Corp | Easy identification |
| Security | WPA3-Enterprise | Latest security standard |
| Authentication | 802.1X with RADIUS | Centralized user management |
| Guest Network | Truelec-Guest | Isolated from internal network |
| Band Steering | Enabled | Prefers 5GHz for better performance |
| Minimum RSSI | -75 dBm | Improves roaming efficiency |
| Channel Width | 20MHz (2.4G), 80MHz (5G) | Balance of speed and reliability |

### Access Point Placement
- Headquarters: 15 APs (1 per 100m²)
- Branch Office: 6 APs (1 per 80m²)
- Placement: Ceiling mounted, evenly distributed

## IP Addressing Scheme
Based on Student IDs: 12345678 and 12234506

### Headquarters Addressing
| Network | IP Range | Subnet Mask | Purpose | Gateway |
|---------|----------|-------------|---------|---------|
| Core Network | 78.10.0.0/16 | 255.255.0.0 | Backbone | 78.10.0.1 |
| Server VLAN | 78.10.10.0/24 | 255.255.255.0 | Servers | 78.10.10.1 |
| User VLAN | 78.10.20.0/24 | 255.255.255.0 | Workstations | 78.10.20.1 |
| WiFi VLAN | 78.10.30.0/24 | 255.255.255.0 | Wireless | 78.10.30.1 |
| Management VLAN | 78.10.100.0/24 | 255.255.255.0 | Equipment | 78.10.100.1 |
| Guest VLAN | 78.10.200.0/24 | 255.255.255.0 | Visitors | 78.10.200.1 |

### Branch Office (Brisbane) Addressing
| Network | IP Range | Subnet Mask | Purpose | Gateway |
|---------|----------|-------------|---------|---------|
| Branch LAN | 6.20.0.0/16 | 255.255.0.0 | Main network | 6.20.0.1 |
| User VLAN | 6.20.10.0/24 | 255.255.255.0 | Workstations | 6.20.10.1 |
| WiFi VLAN | 6.20.20.0/24 | 255.255.255.0 | Wireless | 6.20.20.1 |

## Recommended Hardware

### Headquarters Equipment
| Equipment | Model | Quantity | Unit Price (AUD) | Total (AUD) | Justification |
|-----------|-------|----------|------------------|-------------|---------------|
| Core Switch | Cisco Catalyst 9500-24Y4C | 2 | $15,000 | $30,000 | Redundant backbone |
| Distribution Switch | Cisco Catalyst 9300-48T | 4 | $8,000 | $32,000 | Layer 3 aggregation |
| Access Switch | Cisco Catalyst 9200-48P | 10 | $4,500 | $45,000 | PoE for APs and phones |
| Router/Firewall | FortiGate 600E | 2 | $8,000 | $16,000 | HA pair for uptime |
| Wireless Controller | Cisco 8540 | 1 | $12,000 | $12,000 | Centralized management |
| Access Points | Cisco 2802i | 15 | $1,200 | $18,000 | High-density coverage |
| **Total** | | | | **$153,000** | |

### Branch Office Equipment
| Equipment | Model | Quantity | Unit Price (AUD) | Total (AUD) | Justification |
|-----------|-------|----------|------------------|-------------|---------------|
| Layer 3 Switch | Cisco Catalyst 9200L-48P | 2 | $3,500 | $7,000 | Stackable for redundancy |
| Router/Firewall | FortiGate 100F | 1 | $3,000 | $3,000 | Security and VPN |
| Access Points | Cisco 1800i | 6 | $800 | $4,800 | Sufficient coverage |
| **Total** | | | | **$14,800** | |

## Network Services
1. **DHCP**: Centralized server at HQ, relay agents at branches
2. **DNS**: Internal DNS servers with external forwarding
3. **NTP**: Synchronized time across all devices
4. **Syslog**: Centralized logging server
5. **Backup**: Automated configuration backups

## Redundancy Features
1. **Power**: Dual power supplies on critical devices
2. **Links**: EtherChannel for switch interconnections
3. **Routing**: HSRP for default gateway redundancy
4. **Internet**: Dual ISP connections with BGP
5. **Servers**: Virtualization with live migration

## Implementation Phases
1. **Phase 1**: Core infrastructure installation
2. **Phase 2**: Access layer deployment
3. **Phase 3**: WiFi implementation
4. **Phase 4**: Security policy enforcement
5. **Phase 5**: Testing and optimization<img width="2044" height="2964" alt="image" src="https://github.com/user-attachments/assets/8a611f9e-dafc-45db-85d8-82e35cd35fe8" />
