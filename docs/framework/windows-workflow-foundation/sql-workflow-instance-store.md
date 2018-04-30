---
title: Ukládání Instance pracovního postupu SQL
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8cd2f8a5-4bf8-46ea-8909-c7fdb314fabc
caps.latest.revision: 26
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 60eaef2bbbb2ff7653aeac832163276c32bc696b
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="sql-workflow-instance-store"></a>Ukládání Instance pracovního postupu SQL
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] Se dodává s SQL úložiště Instance pracovního postupu, která umožňuje pracovní postupy pro zachování stavu informace o instancí pracovních postupů v databázi systému SQL Server 2005 nebo SQL Server 2008. Tato funkce je primárně implementována ve formě <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> třídy, která je odvozena z abstraktní <xref:System.Runtime.DurableInstancing.InstanceStore> třídu rozhraní trvalost. Funkci SQL ukládání Instance pracovního postupu se považuje za trvalost zprostředkovatele SQL, který je konkrétní implementaci trvalost rozhraní API, které hostitel používá k odesílání příkazů trvalost do úložiště.  
  
 Ukládání Instance pracovního postupu SQL podporuje vlastním hostováním pracovních nebo služeb pracovních postupů, které používají <xref:System.Activities.WorkflowApplication> nebo <xref:System.ServiceModel.WorkflowServiceHost> a také služby hostované v používal <xref:System.ServiceModel.WorkflowServiceHost>. Funkci SQL ukládání Instance pracovního postupu pro samoobslužné hostované služby můžete nakonfigurovat programově pomocí objektového modelu, který je zveřejněný prostřednictvím funkce. Můžete nakonfigurovat tuto funkci pro služby hostované <xref:System.ServiceModel.WorkflowServiceHost> programově pomocí objektového modelu i taky pomocí konfiguračního souboru XML.  
  
 Funkci SQL ukládání Instance pracovního postupu (**SqlWorkflowInstanceStore** třída) neimplementuje <xref:System.ServiceModel.Persistence.PersistenceProviderFactory> a proto nenabízí podporu trvalosti pro trvalé služby WCF mimo pracovní postup. Také neimplementuje <xref:System.Workflow.Runtime.Hosting.WorkflowPersistenceService> a proto nenabízí podporu trvalost 3.x pracovních postupů. Tato funkce podporuje pracovních trvalosti pro pouze WF 4.0 (a novější) a služby pracovních postupů. Tato funkce taky nepodporuje žádné databáze než SQL Server 2005 a SQL Server 2008.  
  
 Témata v této části popisují vlastnosti a funkce ukládání Instance pracovního postupu SQL a poskytnout podrobné informace o konfiguraci úložiště.  
  
 Windows Server App Fabric poskytuje svou vlastní instanci úložiště a nástrojů zjednodušit konfiguraci a použití instance úložiště. Další informace najdete v tématu najdete v části [Windows Server App Fabric Instance Store](http://go.microsoft.com/fwlink/?LinkId=201201). Další informace o najdete trvalost databáze systému SQL Server App Fabric [trvalost databáze systému SQL Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201202)  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
-   [Vlastnosti úložiště instancí pracovních postupů SQL](../../../docs/framework/windows-workflow-foundation/properties-of-sql-workflow-instance-store.md)  
  
-   [Postupy: Povolení trvalosti SQL pro pracovní postupy a služby pracovních postupů](../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md)  
  
-   [Aktivace instance](../../../docs/framework/windows-workflow-foundation/instance-activation.md)  
  
-   [Podpora pro dotazy](../../../docs/framework/windows-workflow-foundation/support-for-queries.md)  
  
-   [Rozšiřitelnost úložiště](../../../docs/framework/windows-workflow-foundation/store-extensibility.md)  
  
-   [Zabezpečení](../../../docs/framework/windows-workflow-foundation/security.md)  
  
-   [Databáze trvalosti SQL Serveru](../../../docs/framework/windows-workflow-foundation/sql-server-persistence-database.md)  
  
## <a name="see-also"></a>Viz také  
 [Trvalost ukázky](http://go.microsoft.com/fwlink/?LinkID=177735)
