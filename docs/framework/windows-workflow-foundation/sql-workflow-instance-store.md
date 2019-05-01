---
title: Úložiště instancí pracovních postupů SQL
ms.date: 03/30/2017
ms.assetid: 8cd2f8a5-4bf8-46ea-8909-c7fdb314fabc
ms.openlocfilehash: 8314781f46d9cd4eddd06f6be95f8e952feef1b9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004624"
---
# <a name="sql-workflow-instance-store"></a>Úložiště instancí pracovních postupů SQL
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Se dodává s SQL Store Instance pracovního postupu, který umožňuje pracovní postupy pro zachování informací o stavu instance pracovního postupu v databázi serveru SQL Server 2005 nebo SQL Server 2008. Tato funkce jsou primárně implementované ve formě <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> třída, která je odvozena z abstraktní <xref:System.Runtime.DurableInstancing.InstanceStore> třídy rozhraní trvalosti. Funkce SQL Store Instance pracovního postupu se považuje za SQL poskytovatele trvalého chování, které je konkrétní implementace rozhraní API, které hostitel používá k odesílání příkazů trvalost do úložiště trvalosti.  
  
 Store Instance pracovního postupu SQL podporuje pracovních postupů v místním prostředí nebo služeb pracovních postupů, které používají <xref:System.Activities.WorkflowApplication> nebo <xref:System.ServiceModel.WorkflowServiceHost> a také služeb hostovaných v používal <xref:System.ServiceModel.WorkflowServiceHost>. Funkce SQL Store Instance pracovního postupu služby v místním prostředí můžete nakonfigurovat prostřednictvím kódu programu pomocí objektového modelu vystavené funkci. Můžete nakonfigurovat tuto funkci pro služby hostované <xref:System.ServiceModel.WorkflowServiceHost> jak prostřednictvím kódu programu pomocí objektového modelu a taky pomocí konfiguračního souboru XML.  
  
 Funkce SQL pracovního postupu Instance Store (**SqlWorkflowInstanceStore** třídy) neimplementuje <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> a proto se nebude poskytovat podpora trvalosti pro trvalé služby WCF – pracovní postup. Také neimplementuje <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> a proto se nebude poskytovat podpora trvalosti pro pracovní postupy 3.x. Tato funkce podporuje pracovní postupy trvalosti pro pouze WF 4.0 (a novější) a služby pracovních postupů. Tato funkce také nepodporuje všechny databáze než SQL Server 2005 a SQL Server 2008.  
  
 Témata v této části popisují vlastnosti a funkce Store Instance pracovního postupu SQL a poskytují podrobné informace o konfiguraci úložiště.  
  
 Windows Server App Fabric poskytuje své vlastní úložiště instancí a nástrojů pro zjednodušení konfigurace a použití v úložišti instancí. Další informace najdete v tématu [systému Windows Server App Fabric Instance Store](https://go.microsoft.com/fwlink/?LinkId=201201). Další informace viz databáze trvalosti SQL serveru v aplikaci Fabric [databáze trvalosti SQL serveru v aplikaci Fabric](https://go.microsoft.com/fwlink/?LinkId=201202)  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
- [Vlastnosti úložiště instancí pracovních postupů SQL](properties-of-sql-workflow-instance-store.md)  
  
- [Postupy: Povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů](how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
- [Aktivace instance](instance-activation.md)  
  
- [Podpora pro dotazy](support-for-queries.md)  
  
- [Rozšiřitelnost úložiště](store-extensibility.md)  
  
- [Zabezpečení](security.md)  
  
- [Databáze trvalosti SQL Serveru](sql-server-persistence-database.md)  
  
## <a name="see-also"></a>Viz také:

- [Ukázky trvalosti](https://go.microsoft.com/fwlink/?LinkID=177735)
