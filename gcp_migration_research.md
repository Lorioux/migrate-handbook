# Google Cloud Migration Research

## Source: https://cloud.google.com/architecture/migration-to-gcp-getting-started

### Overview
This document helps plan, design, and implement the process of migrating workloads to Google Cloud. Moving apps from one environment to another is a challenging task, even for experienced teams, requiring careful planning and execution.

### Multi-part Migration Series
1. Migrate to Google Cloud: Get started (main document)
2. Assess and discover your workloads
3. Plan and build your foundation
4. Transfer your large datasets
5. Deploy your workloads
6. Migrate from manual deployments to automated, containerized deployments
7. Optimize your environment
8. Best practices for validating a migration plan
9. Minimize costs

### Environment Types

#### Starting Environments:
1. **On-premises environment**: Full ownership and responsibility, complete control over cooling, physical security, hardware maintenance
2. **Private hosting environment**: Outsourced physical infrastructure (colocation), shared between customers, managed physical security and power/network cabling
3. **Public cloud environment**: No physical infrastructure management, focus on valuable stack aspects, fully managed services available

#### Responsibility Matrix:
| Resources | On-premises | Private hosting | Public cloud |
|-----------|-------------|-----------------|--------------|
| Physical security and safety | You | Service provider | Service provider |
| Power and network cabling | You | Service provider | Service provider |
| Hardware (incl. maintenance) | You | Depends on service provider | Service provider |
| Virtualization platform | You | You | Service provider |
| App resources | You | You | You (with managed services) |

### Workload Types
1. **Legacy workloads**: Developed without cloud consideration, difficult to modify, expensive to run/maintain, no scalability support
2. **Cloud-optimized workloads**: Natively scalable, portable, available, secure; increase developer productivity and agility

### Migration Types

#### 1. Rehost: Lift and Shift
- Move workloads with minor/no modifications
- Minimum changes needed for target environment operation
- Ideal when workload can operate as-is or little business need for change
- Quickest migration type, least refactoring
- Uses same tools and skills
- Supports ready-made software
- **Limitation**: Workloads not optimized for cloud, don't leverage cloud features

#### 2. Replatform: Lift and Optimize
- Lift existing workloads and optimize for new environment
- More optimization than rehost but less than refactor



### Starting Situations
1. On-premises or private hosting environment with legacy workloads and operations
2. On-premises or private hosting environment with cloud-optimized workloads and operations  
3. Public cloud or private hosting environment with legacy workloads and operations
4. Public cloud or private hosting environment with cloud-optimized workloads and operations

**Key Insight**: Migrating from legacy on-premises to cloud-optimized environment can be challenging and risky. Successful migrations change workloads as little as possible during migration operations. Moving legacy on-premises apps often requires multiple migration steps.

### Detailed Migration Types

#### 1. Rehost: Lift and Shift
- **Definition**: Move workloads from source to target environment with minor/no modifications
- **Modifications**: Only minimum changes needed for target environment operation
- **Ideal When**: 
  - Workload can operate as-is in target environment
  - Little or no business need for change
  - Cannot refactor workload or cannot decommission
  - Difficult/impossible to modify source code
  - Build process isn't straightforward
- **Advantages**:
  - Easiest to perform
  - Same tools and skills can be used
  - Supports ready-made software
  - Quickest compared to refactor/rebuild
- **Limitations**: 
  - Workloads not optimized for cloud
  - Don't take advantage of cloud features (horizontal scalability, fine-grained pricing, managed services)


#### 2. Replatform: Lift and Optimize
- **Definition**: Lift existing workloads and optimize them for new cloud environment
- **Best For**: Organizations wanting to take advantage of core cloud competencies
- **Benefits**: Elastic computing, redundancy, improved performance and security
- **Example**: Replatform to use cloud-based microservice architecture or containers in Google Kubernetes Engine
- **Considerations**: 
  - More work than rehost migrations
  - Different underlying codebase requires testing rounds
  - Need to ensure optimal performance

#### 3. Refactor: Move and Improve
- **Definition**: Modify workloads to take advantage of cloud capabilities, not just make them work
- **Purpose**: Improve performance, features, cost, and user experience
- **Timing**: Can modify during migration or before migration
- **When to Use**:
  - Current architecture/infrastructure not supported in target environment
  - Major workload update needed in addition to migration
- **Benefits**: 
  - Take advantage of cloud platform features (scalability, high availability)
  - Architect improvements for increased portability
- **Considerations**:
  - Takes longer than rehost migrations
  - Workloads must be refactored for app to migrate
  - Requires learning new skills

#### 4. Re-architect: Continue to Modernize
- **Definition**: Similar to refactor but changes how code functions rather than how it works
- **Purpose**: Optimize workload and take advantage of cloud-optimized properties
- **Benefits**: Scalability, security, agility improvements
- **Example**: Take large monolithic workload and turn into independent microservices for Google Cloud
- **Considerations**:
  - More complex than refactor migration
  - Takes more time and effort
  - Can introduce bugs or security issues
  - Requires several testing rounds

#### 5. Rebuild: Remove and Replace
- **Definition**: Decommission existing app and completely redesign/rewrite as fully cloud-optimized app
- **When to Use**:
  - Current app not meeting goals
  - Don't want to maintain existing app
  - Too costly to migrate using other approaches
  - App not supported on Google Cloud
- **Benefits**: 
  - Full advantage of Google Cloud features (horizontal scalability, managed services, high availability)
  - Remove technical debt from legacy version
- **Considerations**:
  - Can take longer than rehost/refactor migrations
  - Not suitable for ready-made apps
  - Requires rewriting the app
  - Requires new skills and toolchains

#### 6. Repurchase
- **Definition**: Move from purchased on-premises workload to cloud-hosted SaaS equivalent
- **Example**: Move from on-premises collaboration software and local storage to Google Workspace
- **Benefits**: Easier than refactoring, rebuilding, or re-architecting
- **Considerations**: 
  - Might be more expensive
  - May not get granular features of controlling own cloud environments

## Google Cloud Adoption Framework

### Purpose
- Evaluate organization's maturity in adopting cloud technologies
- Serves as map for determining current business information technology capabilities
- Guide to where you want to be
- Assess readiness for Google Cloud and identify gaps to fill

### Four Themes Assessment

#### 1. Learn
- **Focus**: Quality and scale of learning programs
- **Phases**:
  - **Tactical**: Self-taught, third-party reliance
  - **Strategic**: Organized training, third-party assisted
  - **Transformational**: Peer learning and sharing, third-party staff augmentation only

#### 2. Lead  
- **Focus**: Extent of IT department support with leadership mandate to migrate to Google Cloud
- **Phases**:
  - **Tactical**: Teams by function, heroic project manager
  - **Strategic**: New cross-functional cloud team
  - **Transformational**: Cross-functional feature teams, centralized platform team

#### 3. Scale
- **Focus**: Extent of cloud-optimized services usage and operational automation
- **Phases**:
  - **Tactical**: Change is slow and risky, ops heavy
  - **Strategic**: Templates ensure good governance without manual toil
  - **Transformational**: All change is consistent, low risk, and quickly fixed

#### 4. Secure
- **Focus**: Capability to protect current environment from unauthorized and inappropriate access
- **Phases**:
  - **Tactical**: Fear of public internet, but trust in private network
  - **Strategic**: Central identity, hybrid network
  - **Transformational**: Trust only the right people, devices, and services

### Three Maturity Phases

#### Tactical Phase
- No coherent plans covering all individual workloads
- Mostly interested in quick return on investments
- Little disruption to IT organization

#### Strategic Phase  
- Plan in place to develop individual workloads with eye to future scaling needs
- Interested in mid-term goal to streamline operations
- More efficient than current state

#### Transformational Phase
- Cloud operations work smoothly
- Use data from operations to improve IT business
- Interested in long-term goal of making IT department engine of innovation


## The Migration Path

### Overview
Migration is a journey from point A (existing infrastructure and environments) to point B (target state). You can choose any of the migration options previously described.

### Four Migration Phases

#### 1. Assess
- **Purpose**: Thorough assessment and discovery of existing environment
- **Activities**:
  - Understand app and environment inventory
  - Identify app dependencies and requirements
  - Perform total cost of ownership calculations
  - Establish app performance benchmarks
- **Resources**: 
  - Migrate to Google Cloud: Assess and discover your workloads
  - Migrate to Google Cloud: Best practices
  - Migration Center: Start an asset discovery

#### 2. Plan
- **Purpose**: Create basic cloud infrastructure for workloads and plan app movement
- **Activities**:
  - Identity management setup
  - Organization and project structure
  - Networking configuration
  - Sorting apps and developing prioritized migration strategy
- **Resources**: Migrate to Google Cloud: Plan and build your foundation

#### 3. Deploy
- **Purpose**: Design, implement and execute deployment process to move workloads to Google Cloud
- **Activities**:
  - Move workloads to Google Cloud
  - Refine cloud infrastructure for new needs
  - Data migration to Google Cloud
- **Resources**: 
  - Migrate to Google Cloud: Deploy your workloads
  - Migrate to Google Cloud: Migrate from manual deployments to automated, containerized deployments
  - Migrate to Google Cloud: Transfer your large datasets

#### 4. Optimize
- **Purpose**: Take full advantage of cloud-optimized technologies and capabilities
- **Activities**:
  - Expand business potential (performance, scalability, disaster recovery, costs, training)
  - Open doors to machine learning and artificial intelligence integrations
- **Resources**: 
  - Migrate to Google Cloud: Optimize your environment
  - Migrate to Google Cloud: Minimize costs

## Finding Help

Google Cloud offers various options and resources for finding necessary help and support to best take advantage of Google Cloud services.

### Self-Service Resources

#### Product Documentation
- Google Cloud provides documentation for each product and service
- Includes APIs documentation

#### Architecture Center Documentation  
- Migration section covers many migration scenarios
- Migration resources provide guidance about migration journey to Google Cloud

#### Tools
- **Google Cloud Migration Center**: Unified platform to accelerate end-to-end cloud journey from current on-premises or cloud environments to Google Cloud
- **Migrate to Virtual Machines**: Product for migrating physical servers and virtual machines from on-premises and cloud environments to Google Cloud
  - Migrate VMs in few minutes with data copied in background while VMs remain operational
- **Storage Transfer Service**: Brings data to Cloud Storage from other cloud providers, online resources, or local data
- **Database Migration Service**: Helps migrate databases to Google Cloud
- **Transfer Appliance**: Hardware appliance for migrating large volumes of data (hundreds of terabytes up to 1 petabyte) without disrupting business operations
- **BigQuery Migration Service**: Comprehensive solution for migrating data warehouse to BigQuery

#### Additional Resources
- **Whitepapers**: Reference architectures, case studies, best practices, and advanced tutorials
- **Media Content**: 
  - Google Cloud podcast
  - Google Cloud YouTube channel with wide range of topics from product explanations to development strategies
- **Online Courses and Labs**: 
  - Coursera courses with video content, reading materials, and labs
  - Google Cloud Skills Boost for hands-on labs
  - Live online classes participation

### Technology Partners
- Google Cloud has partnered with multiple companies to enable use of their products
- Some offerings might be free to use
- Ask company and Google Cloud account manager for details

### System Integrators
- Google Cloud partners with system integrators for hands-on-keyboard assistance
- Specialized in cloud migrations
- List of system integrators available in partners directory

### Google Cloud Professional Services
- Direct support from Google Cloud team
- Specialized expertise for complex migration scenarios

