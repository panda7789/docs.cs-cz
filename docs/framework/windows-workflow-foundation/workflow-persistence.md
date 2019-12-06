---
title: Trvalost pracovního postupu
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
ms.openlocfilehash: c49e287c6132103d4bb85a8ae892a76f9b582274
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837529"
---
# <a name="workflow-persistence"></a>Trvalost pracovního postupu
Trvalost pracovního postupu je trvalé zachycení stavu instance pracovního postupu, nezávisle na informacích o procesu nebo počítači. K tomu je potřeba zajistit dobře známý bod obnovení instance pracovního postupu v případě selhání systému nebo zachovat paměť uvolněním instancí pracovních postupů, které aktivně nepracují, nebo přesunutím stavu instance pracovního postupu z jednoho uzlu do druhého. uzel v serverové farmě.  
  
 Trvalost umožňuje zpracovat flexibilitu, škálovatelnost, obnovení při selhání a možnost efektivněji spravovat paměť. Proces trvalosti zahrnuje identifikaci trvalého bodu, shromažďování dat, která mají být uložena, a nakonec delegace skutečného úložiště dat k poskytovateli trvalosti.  
  
 Chcete-li povolit trvalost pro pracovní postup, je třeba přidružit úložiště instancí k aplikaci **WorkflowApplication** nebo **WorkflowServiceHost** , jak je uvedeno v tématu [Postupy: povolení trvalosti pro pracovní postupy a služby pracovních postupů](how-to-enable-persistence-for-workflows-and-workflow-services.md). Aplikace **WorkflowApplication** a **WorkflowServiceHost** používají úložiště instancí, které jsou k nim přidružené, aby bylo možné replikovat instance pracovních postupů do úložiště trvalosti a načítat instance pracovního postupu do paměti na základě dat instance pracovního postupu, která jsou uložená v úložišti trvalosti.  
  
 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] dodává se třídou **SqlWorkflowInstanceStore** , která umožňuje Trvalost dat a metadat o instancích pracovního postupu do databáze SQL Server 2005 nebo SQL Server 2008. Další podrobnosti najdete v tématu [úložiště instancí pracovních postupů SQL](sql-workflow-instance-store.md) .  
  
 Chcete-li uložit a načíst data specifická pro aplikaci spolu s informacemi souvisejícími s instancí pracovního postupu, můžete vytvořit účastníky trvalého chování, které rozšiřuje třídu <xref:System.Activities.Persistence.PersistenceParticipant>. Účastník trvalosti se účastní procesu trvalosti, aby ušetřil vlastní serializovatelný data do úložiště Persistence, načetla data z úložiště instance do paměti a prováděla další logiku v rámci transakce trvalosti. Další informace najdete v tématu [trvalé účastníky](persistence-participants.md).  
  
 Windows Server App Fabric zjednodušuje proces konfigurace trvalosti. Další informace najdete v tématu [Koncepty trvalosti s Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677272(v=azure.10)) .  
  
## <a name="implicit-persistence-points"></a>Implicitní trvalé body trvalosti  
 Následující seznam obsahuje příklady podmínek, při kterých je pracovní postup trvale uložený v případě, že je k pracovnímu postupu přidruženo úložiště instancí.  
  
- Po dokončení aktivity **TransactionScope** nebo dokončení aktivity **TransactedReceiveScope** .  
  
- Když instance pracovního postupu vznikne nečinný a v hostiteli pracovního postupu je nastavená možnost **WorkflowIdleBehavior** . K tomu dochází například při použití aktivity zasílání zpráv nebo aktivity **zpoždění** .  
  
- Když je aplikace WorkflowApplication v nečinnosti a vlastnost **PersistableIdle** aplikace je nastavena na **PersistableIdleAction. trvalá**.  
  
- Pokud je hostitelská aplikace pokyn k uchování nebo uvolnění instance pracovního postupu.  
  
- Když se instance pracovního postupu ukončí nebo dokončí.  
  
- Když se spustí **trvalá** aktivita.  
  
- Když instance pracovního postupu vyvinutá v předchozí verzi programovací model Windows Workflow Foundation narazí na bod trvalosti během vzájemně ovladatelného provádění.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
- [Úložiště instancí pracovních postupů SQL](sql-workflow-instance-store.md)  
  
- [Úložiště instancí](instance-stores.md)  
  
- [Účastníci trvalosti](persistence-participants.md)  
  
- [Osvědčené postupy pro trvalost](persistence-best-practices.md)  
  
- [Netrvalé instance pracovních postupů](non-persisted-workflow-instances.md)  
  
- [Pozastavení a obnovení pracovního postupu](pausing-and-resuming-a-workflow.md)
