---
title: Trvalost pracovního postupu
ms.date: 03/30/2017
helpviewer_keywords:
- programming [WF], persistence
ms.assetid: 39e69d1f-b771-4c16-9e18-696fa43b65b2
ms.openlocfilehash: 0a938f2f4d4cc790fe03db1e2b57862e54af48a7
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43748564"
---
# <a name="workflow-persistence"></a>Trvalost pracovního postupu
Trvalost pracovního postupu je trvalý zachycení stavu instance pracovního postupu, nezávisle na informace o procesu nebo počítač. To se provádí k poskytování známého bodu obnovení pro instanci pracovního postupu v případě selhání systému, nebo pro zachování paměti podle uvolnění instancí pracovních postupů, které nejsou aktivně provádějící práce nebo přesunout do jiného stavu instance pracovního postupu z jednoho uzlu uzel v serverové farmě.  
  
 Trvalost umožňuje procesu flexibilitu, škálovatelnost, zotavení i v případě selhání a možnost spravovat efektivněji paměť. Proces trvalého zahrnuje identifikaci bod trvalost, shromažďují data, která mají být uloženy a nakonec delegování skutečnou velikost úložiště dat do poskytovatele trvalého chování.  
  
 K povolení trvalosti pro pracovní postup, je nutné přidružit úložiště instance s **WorkflowApplication** nebo **hostitele služby pracovního postupu** jak je uvedeno v [postupy: povolení trvalosti pro Pracovní postupy a služby pracovních postupů](../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md). **WorkflowApplication** a **hostitele služby pracovního postupu** použití v úložišti instancí, které jsou k nim má přiřazené k povolení uchování instance pracovního postupu do trvalého úložiště a načtení instance pracovního postupu do paměť podle data instance pracovního postupu, který je uložen v úložišti stálost.  
  
 [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Se dodává s **SqlWorkflowInstanceStore** třídu, která umožňuje trvalost dat a metadata o instance pracovního postupu do databáze serveru SQL Server 2005 nebo SQL Server 2008. Zobrazit [Store Instance pracovního postupu SQL](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md) další podrobnosti.  
  
 K ukládání a načítání dat specifické pro aplikaci společně s informace související s instancí pracovního postupu, můžete vytvořit účastníci trvalosti, které rozšiřují <xref:System.Activities.Persistence.PersistenceParticipant> třídy. Trvalého účastníka se účastní procesu trvalost uložit vlastní serializovat data do trvalého úložiště, načtení dat z úložiště instancí do paměti a provádět žádná další logika v rámci transakce trvalosti. Další informace najdete v tématu [účastníci trvalosti](../../../docs/framework/windows-workflow-foundation/persistence-participants.md).  
  
 Windows Server App Fabric zjednodušuje proces konfigurace trvalosti. Další informace najdete v tématu [koncepty trvalosti pomocí systému Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201200)  
  
## <a name="implicit-persistence-points"></a>Implicitní body trvalosti  
 Následující seznam obsahuje příklady podmínek, na kterých je trvalá pracovního postupu při úložiště instance je přiřazen pracovní postup.  
  
-   Když **TransactionScope** dokončení aktivity nebo **TransactedReceiveScope** dokončení aktivity.  
  
-   Jakmile se instance pracovního postupu změní nečinnosti a **WorkflowIdleBehavior** je nastavena na hostitele pracovního postupu. K tomu dojde, například při použití zasílání zpráv aktivity nebo **zpoždění** aktivity.  
  
-   Když aplikace WorkflowApplication změní na nečinnosti a **PersistableIdle** aplikace je nastavena na **PersistableIdleAction.Persist**.  
  
-   Pokud hostitelská aplikace je nastaven na zachovat nebo uvolnit instance pracovního postupu.  
  
-   Když instance pracovního postupu je ukončen nebo dokončení.  
  
-   Když **trvalého** aktivity spustí.  
  
-   Instance pracovního postupu vyvinuté pomocí předchozí verze Windows Workflow Foundation Pokud nalezne bod trvalost během interoperabilní provádění.  
  
## <a name="in-this-section"></a>V tomto oddílu  
  
-   [Úložiště instancí pracovních postupů SQL](../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md)  
  
-   [Úložiště instancí](../../../docs/framework/windows-workflow-foundation/instance-stores.md)  
  
-   [Účastníci trvalosti](../../../docs/framework/windows-workflow-foundation/persistence-participants.md)  
  
-   [Osvědčené postupy pro trvalost](../../../docs/framework/windows-workflow-foundation/persistence-best-practices.md)  
  
-   [Netrvalé instance pracovních postupů](../../../docs/framework/windows-workflow-foundation/non-persisted-workflow-instances.md)  
  
-   [Pozastavení a obnovení pracovního postupu](../../../docs/framework/windows-workflow-foundation/pausing-and-resuming-a-workflow.md)
