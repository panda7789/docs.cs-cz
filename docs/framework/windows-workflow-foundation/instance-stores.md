---
title: Úložiště instancí
ms.date: 03/30/2017
ms.assetid: f2629668-0923-4987-b943-67477131c1e0
ms.openlocfilehash: 69b50942c36406bd29147d243e0501b8048d56dc
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802554"
---
# <a name="instance-stores"></a>Úložiště instancí
Úložiště instancí je logický kontejner instancí. Je místo, kde jsou uložena data instance a metadata. Úložiště instancí neznamená vyhrazené fyzické úložiště. Úložiště instancí může obsahovat trvalé informace v databázi SQL Server nebo netrvalé informace o stavu v paměti. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] se dodává s úložištěm instance pracovního postupu SQL, což je konkrétní implementace úložiště instance, která umožňuje pracovním postupům zachovat data instance a metadata do databáze SQL Server 2005 nebo SQL Server 2008. Kromě prostředků Windows Server App Fabric také poskytuje konkrétní implementaci úložiště instancí. Další informace najdete v tématu [Zprostředkovatelé ukládání instancí, dotazování a řízení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ff383417(v=azure.10)).  
  
 Rozhraní API trvalosti je rozhraní mezi hostitelem a úložištěm instancí, které umožňuje hostiteli odeslat požadavky příkazu (například <xref:System.Activities.DurableInstancing.LoadWorkflowCommand> a <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>) do úložiště instancí. Konkrétní implementace tohoto rozhraní API se nazývá zprostředkovatel trvalosti. Zprostředkovatel trvalosti přijímá žádosti od hostitele a upravuje úložiště instancí.  
  
 Hostitelé a úložiště instancí jsou připojitelné, aby bylo možné použít hostitele s mnoha úložišti instancí a úložiště instancí lze použít s mnoha hostiteli. Úložiště instancí je obvykle optimalizované pro vzorce používání konkrétního hostitele, i když se instance úložiště a hostitele můžou vyvíjet na nezávislých cyklech životního cyklu. Například **Třída WorkflowServiceHost** a **Třída SqlWorkflowInstanceStore** jsou navržené tak, aby dobře spolupracovaly. Můžete vytvořit vlastní úložiště instancí, abyste zachovali data a metadata instancí služby pracovních postupů a používali toto úložiště instancí s **hostitelskou**službou. Můžete například vytvořit OracleWorkflowInstanceStore, který umožňuje pracovním postupům uchovávat informace v databázi Oracle místo jejich uložení do databáze SQL Server.  
  
 Je běžné, že se hostitelé rozšířili o další funkce, které upravují trvalé objekty. Například systém trvalosti instance může mít hostitele pracovního postupu, rozšíření, které podporuje operaci pozastavit a úložiště instance SQL.  Hostitel pracovního postupu může odeslat standardní příkaz, například Save nebo Load, a uložit nebo načíst pracovní postup z úložiště instancí nebo Uložit pracovní postup do úložiště instancí. Rozšíření pozastavení může přidat další sémantiku k příkazům pro ukládání a načítání instancí pracovního postupu, aby bylo možné načíst pozastavenou instanci pracovního postupu. Zprostředkovatel trvalosti pro úložiště instance SQL rozumí příkazy pro ukládání a načítání instancí pracovního postupu a implementuje příkazy voláním příslušných uložených procedur, které mění tabulky trvalých objektů v databázi SQL Server.  
  
 Hostitel funguje jako vlastník instance v rámci úložiště instancí. Hostitel může fungovat jako více než jeden vlastník instance s více než jedním úložištěm instancí současně. Hostitel poskytuje identifikátory GUID pro klíče instancí přidružené k instancím. Klíč instance je jedinečný alias, který identifikuje instanci. Systém Persistence vytvoří, aktualizuje a odstraní informace o vlastníkovi instance při provádění příkazů požadovaných hostiteli.  
  
 Následující seznam obsahuje důležité kroky týkající se interakce hostitele s úložištěm instancí:  
  
1. Získejte objekt **InstanceStore** od poskytovatele trvalosti.  

2. Získejte popisovač instance voláním metody <xref:System.Runtime.DurableInstancing.InstanceStore.CreateInstanceHandle%2A> v objektu **InstanceStore**.  
  
3. Vyvolat příkazy proti popisovači instance voláním metody <xref:System.Runtime.DurableInstancing.InstanceStore.Execute%2A> v objektu **InstanceStore**.  
  
4. Zkontrolujte <xref:System.Runtime.DurableInstancing.InstanceView> vrácených funkcí **InstanceStore. Execute** a určete výsledky příkazů.
