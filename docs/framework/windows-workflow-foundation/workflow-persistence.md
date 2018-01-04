---
title: "Trvalost pracovního postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9e65f07fc01d0d364d7271c4f1378b968b687881
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-persistence"></a>Trvalost pracovního postupu
Trvalost pracovního postupu je trvanlivý zaznamenávání stavu instance pracovního postupu, nezávisle na informace o procesu nebo počítače. To se provádí nabízí dobře známé bod obnovení pro instanci pracovního postupu v případě selhání systému, nebo zachovat paměti uvolnění instancí pracovního postupu, které nejsou aktivně věnovat práci nebo přesunout stav instance pracovního postupu z jednoho uzlu do jiného uzel ve farmě serverů.  
  
 Trvalost umožňuje proces flexibility, škálovatelnost, obnovení při krátkodobém selhání a možnosti správy paměti efektivněji. Proces trvalost zahrnuje identifikace bod trvalost, shromažďování dat pro ukládaný a nakonec delegování skutečné úložiště dat k poskytovateli trvalost.  
  
 Chcete-li zapnout stálost pro pracovní postup, je potřeba přidružit ukládání instance s **WorkflowApplication** nebo **hostitele služby pracovního postupu** jak je uvedeno v [postup: Povolit trvalost pro Pracovní postupy a pracovní postup služby](../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md). **WorkflowApplication** a **hostitele služby pracovního postupu** použití instance úložiště s nimi spojených povolit zachování instancí pracovního postupu do úložiště trvalosti a načítání instance pracovního postupu do paměť podle data instance pracovního postupu, který je uložen v úložišti trvalost.  
  
 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Se dodává s verzí **SqlWorkflowInstanceStore** třídy, která umožňuje trvalosti dat a metadata o instance pracovního postupu do databáze systému SQL Server 2005 nebo SQL Server 2008. V tématu [úložiště Instance pracovního postupu SQL](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) další podrobnosti.  
  
 K ukládání a načíst vaše data specifické pro aplikaci společně s informace týkající se instance pracovního postupu, můžete vytvořit trvalost účastníci, které rozšiřují <xref:System.Activities.Persistence.PersistenceParticipant> třídy. Trvalost účastník účastní procesu trvalost vlastní serializovatelný data uložit do úložiště trvalosti, načítání dat z úložiště instance do paměti a provádět žádné další logiku v rámci transakce trvalost. Další informace najdete v tématu [trvalost účastníky](../../../docs/framework/windows-workflow-foundation/persistence-participants.md).  
  
 Windows Server App Fabric zjednodušuje proces konfigurace trvalosti. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Trvalost koncepty pomocí systému Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201200)  
  
## <a name="implicit-persistence-points"></a>Implicitní trvalost body  
 Následující seznam obsahuje příklady podmínek, na kterých je trvalá pracovního postupu, pokud je instance úložiště spojeno s pracovním postupem.  
  
-   Když **TransactionScope** dokončení aktivity nebo **TransactedReceiveScope** dokončení aktivity.  
  
-   Když se změní na nečinnosti instanci pracovního postupu a **WorkflowIdleBehavior** je nastavený na hostitele pracovního postupu. K tomu dojde, například při zasílání zpráv aktivity nebo **zpoždění** aktivity.  
  
-   Když se změní na nečinnosti WorkflowApplication a **PersistableIdle** aplikace je nastavena na **PersistableIdleAction.Persist**.  
  
-   Když je hostitelskou aplikaci pokyn k zachování nebo odinstalování instanci pracovního postupu.  
  
-   Pokud instance pracovního postupu je ukončeno, nebo dokončí.  
  
-   Když **zachovat** provádí aktivity.  
  
-   Instance pracovního postupu vyvinuté pomocí předchozí verze Windows Workflow Foundation, když zaznamená bod trvalost během provádění umožňuje vzájemnou spolupráci.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
-   [Úložiště instancí pracovních postupů SQL](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)  
  
-   [Úložiště instancí](../../../docs/framework/windows-workflow-foundation/instance-stores.md)  
  
-   [Účastníci trvalosti](../../../docs/framework/windows-workflow-foundation/persistence-participants.md)  
  
-   [Osvědčené postupy pro trvalost](../../../docs/framework/windows-workflow-foundation/persistence-best-practices.md)  
  
-   [Netrvalé instance pracovních postupů](../../../docs/framework/windows-workflow-foundation/non-persisted-workflow-instances.md)  
  
-   [Pozastavení a obnovení pracovního postupu](../../../docs/framework/windows-workflow-foundation/pausing-and-resuming-a-workflow.md)
