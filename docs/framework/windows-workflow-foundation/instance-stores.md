---
title: Úložiště instancí
ms.date: 03/30/2017
ms.assetid: f2629668-0923-4987-b943-67477131c1e0
ms.openlocfilehash: 352ffad56c77d0bd16f7e3b9aa1d82090f3a29b1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59323327"
---
# <a name="instance-stores"></a>Úložiště instancí
Úložiště instance je logický kontejner instancí. Je to místo, kde je uložena instance data a metadata. Úložiště instance neznamená vyhrazené fyzické úložiště. Úložiště instance může obsahovat trvalý informace v databázi serveru SQL Server nebo informace o stavu bez trvale v paměti. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Dodává s SQL Store Instance pracovního postupu, který je na konkrétní implementace úložiště instance, která umožňuje pracovní postupy pro zachování dat instance a metadat do databáze serveru SQL Server 2005 nebo SQL Server 2008. Windows Server App Fabric kromě toho také poskytuje konkrétní implementaci úložiště instancí. Další informace najdete v tématu [systému Windows Server App Fabric Instance Store, dotaz a poskytovatelé správy](https://go.microsoft.com/fwlink/?LinkID=201201&clcid=0x409).  
  
 Trvalost rozhraní API je rozhraní mezi hostitelem a úložiště instance, která umožňuje hostitele má odesílat požadavky na příkazu (například <xref:System.Activities.DurableInstancing.LoadWorkflowCommand> a <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>) do úložiště instancí. Konkrétní implementace tohoto rozhraní API se nazývá poskytovatele trvalého chování. Poskytovatel trvalého přijímat žádosti z hostitele a změní v úložišti instancí.  
  
 Hostitelé a úložiště instancí jsou modulární tak, aby hostitele je možné s mnoha úložiště instancí a úložiště instance je možné s mnoha hostitelích. Úložiště instance je obvykle optimalizované pro vzory používání konkrétního hostitele, i když ukládání instance a hostitele může vyvíjet na nezávislý životní cykly. Například **hostitele služby pracovního postupu** a **SqlWorkflowInstanceStore** jsou navrženy pro práci dobře spolupracovaly. Můžete vytvořit vlastní úložiště instance k zachování dat a metadat instance služby pracovního postupu a použít tuto instanci úložiště s **hostitele služby pracovního postupu**. Můžete například vytvořit OracleWorkflowInstanceStore, který umožňuje pracovní postupy zachování informací do databáze Oracle místo je ukládá do databáze SQL serveru.  
  
 Je běžné, že hostitelé mají být rozšířena o další funkce, která upravuje trvalé objekty. Například systém trvalých instancí může mít hostitele pracovního postupu, rozšíření, které podporuje "Pozastavené" operace a úložiště instance SQL.  Hostitele pracovního postupu můžou odesílat standardní příkaz například uložit nebo načíst, uložit nebo načíst z úložiště instance pracovního postupu a uložení do úložiště instance pracovního postupu. Pozastavit rozšíření může přidat další sémantiku příkazy pro ukládání a načítání instance pracovního postupu tak, aby nelze načíst instanci pracovního postupu pozastavené. Poskytovatele trvalého chování pro úložiště instancí SQL rozumí příkazy pro ukládání a načítání instance pracovního postupu a implementuje příkazy voláním příslušné uložené procedury, které se mění tabulky trvalé objekty v databázi SQL serveru.  
  
 Hostitel funguje jako vlastníka instance v úložišti instancí. Hostitel může fungovat jako více než jednoho vlastníka instance s více než jednu instanci úložiště ve stejnou dobu. Hostitel poskytuje identifikátory GUID pro instanci klíče asociované s instancí. Klíč instance s je jedinečný alias, který identifikuje instanci. Systém trvalých vytvoří, aktualizuje a odstraní informace vlastníka instance spouští příkazy požadoval hostitele.  
  
 Následující seznam obsahuje důležité kroky hostitele interakci s úložišti instancí:  
  
1. Získat **třídy InstanceStore** z poskytovatele trvalého chování.  

2. Získat popisovač instance voláním <xref:System.Runtime.DurableInstancing.InstanceStore.CreateInstanceHandle%2A> metodu **třídy InstanceStore**.  
  
3. Vyvolat příkazy spouštěly pro popisovač instance voláním <xref:System.Runtime.DurableInstancing.InstanceStore.Execute%2A> metodu **třídy InstanceStore**.  
  
4. Zkontrolujte <xref:System.Runtime.DurableInstancing.InstanceView> vrácený **InstanceStore.Execute** určit výsledky příkazů.
