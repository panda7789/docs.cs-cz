---
title: "Rozšíření úložiště"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7c3f4a46-4bac-4138-ae6a-a7c7ee0d28f5
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 12204ebe9720fb8f894046622d6bb81b1c7d5706
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="store-extensibility"></a>Rozšíření úložiště
<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>umožňuje uživatelům povýšit specifické pro aplikace, vlastní vlastnosti, které lze použít k dotazu pro instance v databázi trvalost. Operace povýšení vlastnost způsobí, že hodnota, která má být k dispozici v rámci speciální zobrazení v databázi. Tyto vlastnosti propagovaných (vlastnosti, které lze použít v dotazech uživatele) může být jednoduché typy, jako je například Int64, Guid, String a data a času nebo serializovaných binárního typu (byte[]).  
  
 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Třída má <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> metodu, kterou můžete použít ke zvýšení úrovně vlastnost jako vlastnost, která lze použít v dotazech. V následujícím příkladu je příkladem začátku do konce rozšíření úložiště.  
  
1.  V tomto ukázkovém scénáři dokumentu zpracování (DP) aplikace má pracovní postupy, z nichž každá používá vlastní aktivity pro zpracování dokumentu. Tyto pracovní postupy mají sadu proměnné stavu, které musí být viditelné pro koncového uživatele. K dosažení tohoto distribučního bodu aplikace poskytuje rozšíření instance typu <xref:System.Activities.Persistence.PersistenceParticipant>, který je využíván jiným aktivity k poskytování proměnné stavu.  
  
    ```  
    class DocumentStatusExtension : PersistenceParticipant  
    {  
        public string DocumentId;  
        public string ApprovalStatus;  
        public string UserName;  
        public DateTime LastUpdateTime;  
    }  
    ```  
  
2.  Nové rozšíření se pak přidá k hostiteli.  
  
    ```  
    static Activity workflow = CreateWorkflow();  
    WorkflowApplication application = new WorkflowApplication(workflow);  
    DocumentStatusExtension documentStatusExtension = new DocumentStatusExtension ();  
    application.Extensions.Add(documentStatusExtension);  
    ```  
  
     Další informace o přidání vlastního účastník najdete v tématu [trvalost účastníky](../../../docs/framework/windows-workflow-foundation/persistence-participants.md) ukázka.  
  
3.  Vlastní aktivity v aplikaci distribučního bodu naplnění různých polí stav v **Execute** metoda.  
  
    ```  
    public override void Execute(CodeActivityContext context)  
    {  
        // ...  
        context.GetExtension<DocumentStatusExtension>().DocumentId = Guid.NewGuid();  
        context.GetExtension<DocumentStatusExtension>().UserName = "John Smith";  
        context.GetExtension<DocumentStatusExtension>().ApprovalStatus = "Approved";  
        context.GetExtension<DocumentStatusExtension>().LastUpdateTime = DateTime.Now();  
        // ...  
    }  
    ```  
  
4.  Když bod trvalost dosáhne instanci pracovního postupu **CollectValues** metodu **DocumentStatusExtension** trvalost účastník uloží tyto vlastnosti do trvalosti dat kolekce.  
  
    ```  
    class DocumentStatusExtension : PersistenceParticipant  
    {  
        const XNamespace xNS = XNamespace.Get("http://contoso.com/DocumentStatus");  
  
        protected override void CollectValues(out IDictionary<XName, object> readWriteValues, out IDictionary<XName, object> writeOnlyValues)  
        {  
            readWriteValues = new Dictionary<XName, object>();  
            readWriteValues.Add(xNS.GetName("UserName"), this.UserName);  
            readWriteValues.Add(xNS.GetName("ApprovalStatus"), this.ApprovalStatus);  
            readWriteValues.Add(xNS.GetName("DocumentId"), this.DocumentId);  
            readWriteValues.Add(xNS.GetName("LastModifiedTime"), this.LastUpdateTime);  
  
            writeOnlyValues = null;  
        }  
        // ...  
    }  
    ```  
  
    > [!NOTE]
    >  Všechny tyto vlastnosti jsou předány **SqlWorkflowInstanceStore** rámcem trvalost prostřednictvím **SaveWorkflowCommand.InstanceData** kolekce.  
  
5.  Distribuční bod aplikace inicializuje ukládání Instance pracovního postupu SQL a vyvolá **povýšit** metoda zvýšení úrovně tato data.  
  
    ```  
    SqlWorkflowInstanceStore store = new SqlWorkflowInstanceStore(connectionString);  
  
    List<XName> variantProperties = new List<XName>()   
    {   
        xNS.GetName("UserName"),   
        xNS.GetName("ApprovalStatus"),   
        xNS.GetName("DocumentId"),   
        xNS.GetName("LastModifiedTime")   
    };  
  
    store.Promote("DocumentStatus", variantProperties, null);  
    ```  
  
     Na základě této informace povýšení **SqlWorkflowInstanceStore** umístí vlastnosti dat ve sloupcích [InstancePromotedProperties](#InstancePromotedProperties) zobrazení.
  
6.  Pro dotaz na podmnožinu dat z tabulky povýšení, přidá aplikace distribučního bodu přizpůsobené zobrazení nad zobrazení povýšení.  
  
    ```  
    create view [dbo].[DocumentStatus] with schemabinding  
    as  
        select  P.[InstanceId] as [InstanceId],  
            P.Value1 as [UserName],  
            P.Value2 as [ApprovalStatus],  
            P.Value3 as [DocumentId],  
            P.Value4 as [LastUpdatedTime]  
    from [System.Activities.DurableInstancing].[InstancePromotedProperties] as P  
    where P.PromotionName = N'DocumentStatus'  
    go  
    ```  
  
##  <a name="InstancePromotedProperties"></a>Zobrazení [System.Activities.DurableInstancing.InstancePromotedProperties]  
  
|Název sloupce|Typ sloupce|Popis|  
|-----------------|-----------------|-----------------|  
|identifikátor instanceId|GUID|K instanci pracovního postupu, které patří tato povýšení.|  
|PromotionName|Nvarchar(400)|Název povýšení sám sebe.|  
|Hodnota1, hodnota2, hodnota3,.., Value32|SQL_VARIANT|Hodnota propagovaných samotné vlastnosti. V sql_variant vejde na většině primitivní datové typy SQL s výjimkou binární objekty BLOB a více než 8 000 bajtů délku řetězce.|  
|Value33, Value34, Value35,..., Value64|Varbinary(max)|Hodnota propagovaných vlastnosti, které jsou explicitně deklarované jako varbinary(max).|
