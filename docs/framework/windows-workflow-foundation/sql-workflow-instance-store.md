---
title: Store Instance pracovních postupů SQL
ms.date: 03/30/2017
ms.assetid: 8cd2f8a5-4bf8-46ea-8909-c7fdb314fabc
ms.openlocfilehash: 680a233ca721cd8a0c620b797832419f460b13b6
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192051"
---
# <a name="sql-workflow-instance-store"></a>Store Instance pracovních postupů SQL
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Se dodává s SQL Store Instance pracovního postupu, který umožňuje pracovní postupy pro zachování informací o stavu instance pracovního postupu v databázi serveru SQL Server 2005 nebo SQL Server 2008. Tato funkce jsou primárně implementované ve formě <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> třída, která je odvozena z abstraktní <xref:System.Runtime.DurableInstancing.InstanceStore> třídy rozhraní trvalosti. Funkce SQL Store Instance pracovního postupu se považuje za SQL poskytovatele trvalého chování, které je konkrétní implementace rozhraní API, které hostitel používá k odesílání příkazů trvalost do úložiště trvalosti.  
  
 Store Instance pracovního postupu SQL podporuje pracovních postupů v místním prostředí nebo služeb pracovních postupů, které používají <xref:System.Activities.WorkflowApplication> nebo <xref:System.ServiceModel.WorkflowServiceHost> a také služeb hostovaných v používal <xref:System.ServiceModel.WorkflowServiceHost>. Funkce SQL Store Instance pracovního postupu služby v místním prostředí můžete nakonfigurovat prostřednictvím kódu programu pomocí objektového modelu vystavené funkci. Můžete nakonfigurovat tuto funkci pro služby hostované <xref:System.ServiceModel.WorkflowServiceHost> jak prostřednictvím kódu programu pomocí objektového modelu a taky pomocí konfiguračního souboru XML.  
  
 Funkce SQL pracovního postupu Instance Store (**SqlWorkflowInstanceStore** třídy) neimplementuje <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> a proto se nebude poskytovat podpora trvalosti pro trvalé služby WCF – pracovní postup. Také neimplementuje <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> a proto se nebude poskytovat podpora trvalosti pro pracovní postupy 3.x. Tato funkce podporuje pracovní postupy trvalosti pro pouze WF 4.0 (a novější) a služby pracovních postupů. Tato funkce také nepodporuje všechny databáze než SQL Server 2005 a SQL Server 2008.  
  
 Témata v této části popisují vlastnosti a funkce Store Instance pracovního postupu SQL a poskytují podrobné informace o konfiguraci úložiště.  
  
 Windows Server App Fabric poskytuje své vlastní úložiště instancí a nástrojů pro zjednodušení konfigurace a použití v úložišti instancí. Další informace najdete v tématu naleznete v tématu [systému Windows Server App Fabric Instance Store](https://go.microsoft.com/fwlink/?LinkId=201201). Další informace viz databáze trvalosti SQL serveru v aplikaci Fabric [databáze trvalosti SQL serveru v aplikaci Fabric](https://go.microsoft.com/fwlink/?LinkId=201202)  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
-   [Vlastnosti úložiště instancí pracovních postupů SQL](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md)  
  
-   [Postupy: Povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů](../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
-   [Aktivace instance](../../../docs/framework/windows-workflow-foundation/instance-activation.md)  
  
-   [Podpora pro dotazy](../../../docs/framework/windows-workflow-foundation/support-for-queries.md)  
  
-   [Rozšiřitelnost úložiště](../../../docs/framework/windows-workflow-foundation/store-extensibility.md)  
  
-   [Zabezpečení](../../../docs/framework/windows-workflow-foundation/security.md)  
  
-   [Databáze trvalosti SQL Serveru](../../../docs/framework/windows-workflow-foundation/sql-server-persistence-database.md)  
  
## <a name="see-also"></a>Viz také  
 [Ukázky trvalosti](https://go.microsoft.com/fwlink/?LinkID=177735)
