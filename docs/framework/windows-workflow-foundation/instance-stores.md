---
title: "Instance úložiště"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f2629668-0923-4987-b943-67477131c1e0
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c794c6e20b479ea4686caba29704f8851d108432
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="instance-stores"></a>Instance úložiště
Instance úložiště je logický kontejner instancí. Je na místě, kde je uložena instance data a metadata. Instance úložiště neznamená vyhrazené fyzické úložiště. Instance úložiště může obsahovat trvanlivý informace v databázi systému SQL Server nebo informace o stavu netrvalý v paměti. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] Se dodává s SQL úložiště Instance pracovního postupu, který je na konkrétní implementace úložiště instance, které umožňuje pracovní postupy pro zachování dat instance a metadat do databáze systému SQL Server 2005 nebo SQL Server 2008. Windows Server App Fabric kromě poskytuje konkrétní implementaci instance úložiště. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Windows Server App Fabric Instance úložiště, dotazů a poskytovatelé řízení](http://go.microsoft.com/fwlink/?LinkID=201201&clcid=0x409).  
  
 Trvalost rozhraní API je rozhraní mezi hostitelem a úložiště instance, které umožňuje hostitele k odeslání příkazu požadavky (například <xref:System.Activities.DurableInstancing.LoadWorkflowCommand> a <xref:System.Activities.DurableInstancing.SaveWorkflowCommand>) do úložiště instance. Konkrétní implementaci toto rozhraní API se nazývá zprostředkovatele trvalost. Zprostředkovatel trvalost přijímá požadavky z hostitele a upraví ukládání instance.  
  
 Hostitelé a instance úložišť jsou modulární tak, aby hostitel lze použít s mnoha instance úložiště a úložišti instanci lze použít s mnoha hostitele. Instance úložiště je obvykle optimalizována pro způsobu použití konkrétního hostitele, i když ukládání instance a hostitele může vyvíjet na nezávislé životní cykly. Například **hostitele služby pracovního postupu** a **SqlWorkflowInstanceStore** jsou navrženy pro práci a současně. Můžete vytvořit vlastní úložiště instance zachovat data a metadata instancí služby pracovního postupu a používat toto úložiště instance s **hostitele služby pracovního postupu**. Můžete například vytvořit OracleWorkflowInstanceStore, která umožní pracovní postupy zachování informace do databáze Oracle místo jejich uložení do databáze systému SQL Server.  
  
 Je běžné pro hostitele potřeba rozšířit o další funkce, která upraví trvalé objekty. Například instanci trvalost systému může být hostitel pracovního postupu rozšíření, které podporuje "Pozastavit" operace a úložiště instance SQL.  Hostitele pracovního postupu může odeslat standardní příkaz například uložit nebo načíst, uložit nebo načíst z úložiště instance pracovního postupu a uložení do úložiště instanci pracovního postupu. Rozšíření pozastavit může přidat další sémantiku příkazy pro ukládání a načítání instance pracovního postupu tak, aby nelze načíst instanci pracovního postupu pozastavený. Trvalost zprostředkovatele pro ukládání instance SQL rozumí příkazy pro ukládání a načítání instance pracovního postupu a implementuje příkazy voláním příslušné uložené procedury, které mění tabulky trvalé objekty v databázi systému SQL Server.  
  
 Hostitel funguje jako vlastníka instance v rámci úložiště instance. Hostitel může fungovat jako více než jednoho vlastníka instance s více než jedno úložiště instance ve stejnou dobu. Hostitel poskytuje identifikátory GUID pro instanci klíče související s instancí. Klíčem instance je jedinečný odkaz, který identifikuje instance. Trvalost systém vytvoří, aktualizuje a odstraní instanci vlastníka informace, jak se spouští příkazy požadoval hostitele.  
  
 Následující seznam obsahuje důležité kroky hostitele interakci s instance úložiště:  
  
1.  Získat **InstanceStore** od zprostředkovatele trvalost.  

2.  Získat popisovač do instance voláním <xref:System.Runtime.DurableInstancing.InstanceStore.CreateInstanceHandle%2A> metodu **InstanceStore**.  
  
3.  Použít příkazy proti popisovač instance voláním <xref:System.Runtime.DurableInstancing.InstanceStore.Execute%2A> metodu **InstanceStore**.  
  
4.  Zkontrolujte <xref:System.Runtime.DurableInstancing.InstanceView> vrácený **InstanceStore.Execute** k určení výsledky příkazy.
