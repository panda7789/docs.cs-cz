---
title: Rozšiřitelnost Store
ms.date: 03/30/2017
ms.assetid: 7c3f4a46-4bac-4138-ae6a-a7c7ee0d28f5
ms.openlocfilehash: 46c1ea40925a5c79180171da9a705d7e6b7c8b89
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57703258"
---
# <a name="store-extensibility"></a>Rozšiřitelnost Store

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> umožňuje zvýšit úroveň specifické pro aplikace, vlastní vlastnosti, které lze použít k dotazování pro instance databáze trvalosti. V rámci podpory vlastnosti způsobí, že hodnota, která má být k dispozici v rámci speciální zobrazení v databázi. Tyto propagované vlastnosti (vlastnosti, které lze použít v uživatelských dotazů) může být jednoduché typy, jako je například Int64, Guid, String a datum a čas nebo typ serializovaného binární (byte[]).

<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> Třída nemá <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.Promote%2A> metodu, která vám umožní podporovat vlastnost jako vlastnost, která můžete v dotazech použít nedají. V následujícím příkladu je příkladem začátku do konce rozšíření úložiště.

1. V tomto ukázkovém scénáři má dokument zpracování (DP) aplikací pracovních postupů, z nichž každý používá vlastní aktivity pro zpracování dokumentu. Tyto pracovní postupy mají sadu proměnných stavu, které je potřeba nastavena jako viditelná pro koncového uživatele. K dosažení tohoto distribučního bodu aplikace poskytuje rozšíření instance typu <xref:System.Activities.Persistence.PersistenceParticipant>, které používají aktivity slouží k poskytování proměnné stavu.

    ```csharp
    class DocumentStatusExtension : PersistenceParticipant
    {
        public string DocumentId;
        public string ApprovalStatus;
        public string UserName;
        public DateTime LastUpdateTime;
    }
    ```

2. Nové rozšíření se pak přidá do hostitele.

    ```csharp
    static Activity workflow = CreateWorkflow();
    WorkflowApplication application = new WorkflowApplication(workflow);
    DocumentStatusExtension documentStatusExtension = new DocumentStatusExtension ();
    application.Extensions.Add(documentStatusExtension);
    ```

     Další podrobnosti o přidání vlastního účastníka trvalosti najdete v článku [účastníci trvalosti](persistence-participants.md) vzorku.

3. Vlastní aktivity v aplikaci distribučního bodu naplnění různých polí stav v **Execute** metody.

    ```csharp
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

4. Instance pracovního postupu dosáhne bod trvalost **CollectValues** metodu **DocumentStatusExtension** trvalého účastníka trvalosti dat uloží tyto vlastnosti kolekce.

    ```csharp
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
    > Všechny tyto vlastnosti jsou předány **SqlWorkflowInstanceStore** rozhraním trvalost prostřednictvím **SaveWorkflowCommand.InstanceData** kolekce.

5. Distribučního bodu aplikace inicializuje Store Instance pracovního postupu SQL a vyvolá **povýšit** metoda podporovat tato data.

    ```csharp
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

    Na základě těchto informací povýšení **SqlWorkflowInstanceStore** umístí vlastnosti dat sloupců [InstancePromotedProperties](#InstancePromotedProperties) zobrazení.

6. Pro dotaz na podmnožinu dat z tabulky povýšení, distribučního bodu aplikace přidá vlastní zobrazení nad zobrazení povýšení.

    ```sql
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

## <a name="InstancePromotedProperties"></a> Zobrazení [System.Activities.DurableInstancing.InstancePromotedProperties]

|Název sloupce|Typ sloupce|Popis|
|-----------------|-----------------|-----------------|
|InstanceId|GUID|Instance pracovního postupu patřící do této propagační akce.|
|PromotionName|nvarchar(400)|Název povýšení, samotného.|
|Hodnota1, hodnota2, hodnota3,..., Value32|SQL_VARIANT|Hodnota samotné propagované vlastnosti. Většina primitivní datové typy SQL s výjimkou binární objekty BLOB a víc než 8 000 bajtů délku řetězce lze zobrazit v sql_variant.|
|Value33 Value34, Value35,..., Value64|Varbinary(max)|Hodnoty propagované vlastnosti, které jsou explicitně deklarovány jako varbinary(max).|
