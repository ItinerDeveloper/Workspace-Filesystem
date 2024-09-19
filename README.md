# File Export Service

## Service Route
`/export/import/filesystem`

## Description
The File Export service allows data to be exported to a configured file system at a specific point in a workflow via a webhook. The export payload always includes a descriptor containing key information about the workflow, which can be in JSON or XML format depending on the service configuration (see Workflow Descriptor JSON and Workflow Descriptor XML). Additionally, based on the parameters of the Workspace webhook, the payload may include a list of all workflow parameters (also available in both JSON and XML formats, see Workflow Parameters JSON and Workflow Parameters XML).

All data exported from the worklow is located at:
`.../Export/[itinerTemplateUniqueName]/[reference]/[itinerId]/`

Where:
- `[reference]` is the reference value set in the Workspace webhook.
- `[itinerTemplateUniqueName]` is the unique identifier of the template (e.g., "T###").
- `[itinerId]` is the object ID generated for the workflow.

## Dedicated Template Variables

### Required Variables
- **reference**: The reference value set in the Workspace webhook.

## Example Payloads

### Workflow Descriptor JSON
```json
{
    "itinerTemplateId": "2b4ed9a5324fef119db900155d3ed31a",
    "itinerTemplateName": "Test Itiner",
    "itinerTemplateUniqueName": "T777",
    "itinerId": "3be9cf2fb854ef119db900155d3ed31a",
    "itinerUniqueName": "T777-3",
    "itinerTitle": "Test Itiner",
    "itinerManagerId": 1,
    "itinerManagerName": "Administrator",
    "itinerStartDateTime": "2024-08-07T12:26:03.4600000Z",
    "itinerInstanceId": "1542c43db854ef119db900155d3ed31a"
}
```

### Workflow Descriptor XML
```xml
<ItinerData>
    <ItinerTemplateId>2b4ed9a5324fef119db900155d3ed31a</ItinerTemplateId>
    <ItinerTemplateName>Test Itiner</ItinerTemplateName>
    <ItinerTemplateUniqueName>T777</ItinerTemplateUniqueName>
    <ItinerId>3be9cf2fb854ef119db900155d3ed31a</ItinerId>
    <ItinerUniqueName>T777-3</ItinerUniqueName>
    <ItinerTitle>Test Itiner</ItinerTitle>
    <ItinerManagerId>1</ItinerManagerId>
    <ItinerManagerName>Administrator</ItinerManagerName>
    <ItinerStartDateTime>2024-08-07T12:26:03.4600000Z</ItinerStartDateTime>
    <ItinerInstanceId>1542c43db854ef119db900155d3ed31a</ItinerInstanceId>
</ItinerData>
```

### Workflow Parameters JSON
```json
[
    {
        "name": "_Deadline",
        "dataType": 4,
        "valueDateTime": "2024-08-12T12:26:03.4470000Z"
    },
    {
        "name": "_ManagerName",
        "dataType": 1,
        "valueString": "Administrator"
    }
]
```

### Workflow Parameters XML
```xml
<ArrayOfImportVariable xmlns:i="http://www.w3.org/2001/XMLSchema-instance" xmlns="http://schemas.datacontract.org/2004/07/ProtocolFileSystemWebhook.ServiceModel">
    <ImportVariable>
        <CaptionForFalse i:nil="true"/>
        <CaptionForTrue i:nil="true"/>
        <DataType>4</DataType>
        <Name>_Deadline</Name>
        <ValueBoolean i:nil="true"/>
        <ValueDateTime>2024-08-12T12:26:03.4470000Z</ValueDateTime>
        <ValueDecimal i:nil="true"/>
        <ValueInt i:nil="true"/>
        <ValueString i:nil="true"/>
    </ImportVariable>
    <ImportVariable>
        <CaptionForFalse i:nil="true"/>
        <CaptionForTrue i:nil="true"/>
        <DataType>1</DataType>
        <Name>_ManagerName</Name>
        <ValueBoolean i:nil="true"/>
        <ValueDateTime i:nil="true"/>
        <ValueDecimal i:nil="true"/>
        <ValueInt i:nil="true"/>
        <ValueString>Administrator</ValueString>
    </ImportVariable>
</ArrayOfImportVariable>


```

---

This service is part of the Itiner Workspace integrations and is designed to facilitate scheduling and managing calendar events by interfacing with an Exchange server.
