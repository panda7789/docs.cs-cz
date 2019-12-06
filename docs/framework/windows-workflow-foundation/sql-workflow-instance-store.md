---
title: Úložiště instancí pracovních postupů SQL
ms.date: 03/30/2017
ms.assetid: 8cd2f8a5-4bf8-46ea-8909-c7fdb314fabc
ms.openlocfilehash: 1764017369e82cfbed38be06b4a36847576b5fc0
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837633"
---
# <a name="sql-workflow-instance-store"></a>Úložiště instancí pracovních postupů SQL
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] se dodává s úložištěm instance pracovního postupu SQL, které umožňuje pracovním postupům zachovat informace o stavu pracovních postupů v databázi SQL Server 2005 nebo SQL Server 2008. Tato funkce je primárně implementována ve formě <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> třídy, která je odvozena z abstraktní <xref:System.Runtime.DurableInstancing.InstanceStore> třídy rozhraní Persistence. Funkce úložiště instance pracovního postupu SQL představuje poskytovatele trvalosti SQL, což je konkrétní implementace rozhraní API trvalosti, kterou hostitel používá k odeslání příkazů trvalosti do úložiště.  
  
 Úložiště instancí pracovních postupů SQL podporuje pracovní postupy v místním prostředí nebo služby pracovních postupů, které používají <xref:System.Activities.WorkflowApplication> nebo <xref:System.ServiceModel.WorkflowServiceHost>, jakož i služby hostované službou používaly <xref:System.ServiceModel.WorkflowServiceHost>. Funkci úložiště instance pracovního postupu SQL pro samoobslužné služby můžete nakonfigurovat programově pomocí modelu objektu vystaveného funkcí. Tuto funkci můžete nakonfigurovat pro služby hostované <xref:System.ServiceModel.WorkflowServiceHost> programově pomocí objektového modelu a také pomocí konfiguračního souboru XML.  
  
 Funkce úložiště instance pracovního postupu SQL (třída**SqlWorkflowInstanceStore** ) neimplementuje <xref:System.ServiceModel.Persistence.PersistenceProviderFactory>, a proto nenabízí podporu trvalosti pro odolné služby WCF bez pracovního postupu. Neimplementuje také <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService>, a proto nenabízí podporu trvalého pracovního postupu 3. x. Funkce podporuje stálost jenom pro pracovní postupy WF 4,0 (a novější) a služby pracovních postupů. Tato funkce také nepodporuje žádné jiné databáze než SQL Server 2005 a SQL Server 2008.  
  
 Témata v této části popisují vlastnosti a funkce úložiště instancí pracovních postupů SQL a poskytují podrobné informace o konfiguraci úložiště.  
  
 Windows Server App Fabric nabízí vlastní ukládání instancí a nástroje, které zjednodušují konfiguraci a používání úložiště instancí. Další informace najdete v tématu [úložiště instancí Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10)). Další informace o SQL Server databáze trvalosti App Fabric najdete v tématu [App fabric SQL Server Persistence Database](https://docs.microsoft.com/previous-versions/appfabric/ee790819(v=azure.10)) .  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
- [Vlastnosti úložiště instancí pracovních postupů SQL](properties-of-sql-workflow-instance-store.md)  
  
- [Postupy: Povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů](how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
- [Aktivace instance](instance-activation.md)  
  
- [Podpora pro dotazy](support-for-queries.md)  
  
- [Rozšiřitelnost úložiště](store-extensibility.md)  
  
- [Zabezpečení](security.md)  
  
- [Databáze trvalosti SQL Serveru](sql-server-persistence-database.md)  
  
## <a name="see-also"></a>Viz také:

- [Ukázky trvalosti](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/dd699769(v=vs.100))
