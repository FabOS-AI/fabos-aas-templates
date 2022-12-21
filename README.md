# FabOS AAS Templates

AAS templates for the main components (services and resources) of FabOS. Their Asset Administration Shells consist of the following submodels:

Service submodels:

- IDTA [Software Nameplate (Version 1.0)](https://github.com/admin-shell-io/submodel-templates/tree/main/development/Software%20Nameplate/1/0) (in development)
- Custom [Requirements](#service-requirements-submodel)
- Custom [Deployment](#service-deployment-submodel)

Resource submodels:

- IDTA [ZVEI Digital Nameplate for industrial equipment (Version 1.0)](https://github.com/admin-shell-io/submodel-templates/tree/main/published/ZVEI_Digital_Nameplate/1/0)
- IDTA [Generic Frame for Technical Data for Industrial Equipment in Manufacturing (Version 1.1)](https://github.com/admin-shell-io/submodel-templates/tree/main/published/Technical_Data/1/1)
- IDTA Platform Resource (proposal submitted)

## Service Requirements Submodel

``` plantuml
@startuml
!theme plain
left to right direction
hide class circle
hide class methods
skinparam classAttributeIconSize 0
' skinparam linetype polyline
skinparam linetype ortho
mainframe SMT

mainframe SMT Requirements

class "Requirements" as ID00000001 <<Submodel>> {
  +Constraints : SMC
  +Any : SMC
}

class "Constraints" as ID00000002 <<SMC>> {
  +ProArc : string
}

class "Any" as ID00000003 <<SMC>> {
  +ProArc : string = "ARM11"
  +ProArc : string = "ARM Cortex-A "
}

ID00000001 *--  ID00000002
ID00000001 *--  ID00000003
@enduml
```

## Service Deployment Submodel

``` plantuml
@startuml
!theme plain
left to right direction
hide class circle
hide class methods
skinparam classAttributeIconSize 0
' skinparam linetype polyline
skinparam linetype ortho
mainframe SMT

mainframe SMT Deployment

class "Deployment" as ID00000001 <<Submodel>> {
  +DeploymentType : string
  +DockerContainerDeploymentDefinition : SMC
  +DockerComposeDeploymentDefinition : SMC
  +KubernetesDeploymentDefinition : SMC
}

class "DockerContainerDeploymentDefinition" as ID00000002 <<SMC>> {
  +ImageRepository : string
  +ImageTag : SMC
  +RestartProperty : string
  +EnvironmentVariables : SMC
  +Labels : SMC
  +PortMappings : SMC
  +Volumes : SMC
}

class "ImageTag" as ID00000003 <<SMC>> {
}

class "EnvironmentVariables" as ID00000004 <<SMC>> {
}

class "Labels" as ID00000005 <<SMC>> {
}

class "PortMappings" as ID00000006 <<SMC>> {
}

class "Volumes" as ID00000007 <<SMC>> {
}

class "DockerComposeDeploymentDefinition" as ID00000008 <<SMC>> {
  +ComposeFile : string
  +DotEnvFile : string
  +EnvFiles : SMC
}

class "EnvFiles" as ID00000009 <<SMC>> {
}

class "KubernetesDeploymentDefinition" as ID0000000A <<SMC>> {
  +ManifestFile : string
}

ID00000002 *--  ID00000003
ID00000002 *--  ID00000004
ID00000002 *--  ID00000005
ID00000002 *--  ID00000006
ID00000002 *--  ID00000007
ID00000001 *--  ID00000002
ID00000008 *--  ID00000009
ID00000001 *--  ID00000008
ID00000001 *--  ID0000000A
@enduml
```