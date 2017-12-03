---
title: "Instance uzamčení výjimka akce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 164a5419-315c-4987-ad72-54cbdb88d402
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f3a52550624e93fb9d262f7df2d2e922369c90a8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="instance-locked-exception-action"></a>Instance uzamčení výjimka akce
<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore.InstanceLockedExceptionAction%2A> Vlastnost úložiště Instance pracovního postupu SQL umožňuje určit, jakou akci zprostředkovatele SQL trvalost má provést, pokud obdrží <xref:System.Runtime.DurableInstancing.InstanceLockedException>. Zprostředkovatel trvalost obdrží tuto výjimku při pokusu o uzamčení instance služby pracovního postupu, který je aktuálně uzamčen jiného hostitele služby. Hodnoty pro tuto vlastnost jsou <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>, <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry>, a <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>. Výchozí hodnota je <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>. Následující seznam popisuje tři možnosti:  
  
-   <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>. Hostitel služby nebude pokoušet o uzamčení instance služby pracovního postupu a předává <xref:System.Runtime.DurableInstancing.InstanceLockedException> volajícímu.  Pokud pracovní postup zůstává v paměti na dobu delší než 60 sekund, použijte <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry> jako opakovaném. Výchozí hodnota je <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.NoRetry>.  
  
-   <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry>. Hostitel služby reattempts k uzamčení k instanci pracovního postupu služby s lineární intervalem opakování pokusů a předává <xref:System.Runtime.DurableInstancing.InstanceLockedException> volajícího na konci pořadí. Pokud je pracovní postup zůstává v paměti přibližně mezi 5 – 60 sekund a doručování zpráv: v dávkách, kde je pravděpodobnější zprávy odesílané do stejné instance na stejném hostiteli zpracovat všechny zprávy před uvolnění pracovního postupu, použijte <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry> na dosažení nejlepší latence bez plýtvání prostředky.  
  
-   <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>. Hostitel služby reattempts k uzamčení instance služby pracovního postupu se v intervalu mezi pokusy o opakování exponenciálního omezení rychlosti a předá výjimku volajícího na konci pořadí. Je-li pracovní postup v paměti pro velmi krátké době (méně než 5 sekund) nebo webové farmy je velký a riziko další zprávu doručován na stejného hostitele není velmi vysoké, použijte <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry> k dosažení nejlepší latence.  
  
 Funkce Instance uzamčení výjimka akce podporuje následující scénáře. Ve všech scénářích, pokud vlastnost instanceLockedExceptionAction SqlWorkflowInstanceStore nastavena na <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.BasicRetry> nebo <xref:System.Activities.DurableInstancing.InstanceLockedExceptionAction.AggressiveRetry>, hostitel se transparentně pokusí získat zámek na instancích pravidelně.  
  
1.  **Povolení řádné vypnutí a překryté recyklace aplikační domény.** Předpokládejme, že **AppDomain** s hostitele služby pracovního postupu spuštění instance služby se recykluje a nové **AppDomain** zapínají zpracovat nové žádosti o paralelně při starý  **Doména AppDomain** je snížila řádně. Ukončení, dokud není instancí služby pracovních postupů jsou v nečinnosti a pak potrvají a uvolní instance. Všechny pokusy o hostitelů v novém **AppDomain** k uzamčení instance způsobí, že <xref:System.Runtime.DurableInstancing.InstanceLockedException>.  
  
2.  **Trvanlivý pracovních vodorovně škálování mezi homogenní farmy serverů.** Předpokládejme, že uzel serverové farmy, na kterém běží instance pracovního postupu dojde k chybě a hostitele pracovního postupu nelze odebrat zámky, na kterém je spuštěná instance. Když služba hostitele se systémem v jiném uzlu farmy přijme zprávu o u dané instance pracovního postupu, pokusí se získat zámek na těchto instancích se zobrazí <xref:System.Runtime.DurableInstancing.InstanceLockedException>. Zámky vyprší po určité době, protože už existuje hostitele, který se má obnovit zámek.  
  
     **Trvanlivý pracovních vodorovně škálování mezi homogenní farmy serverů.**  Předpokládejme, že chcete vodorovně škálování trvanlivý pracovní postup pomocí několika hostitelích za vyrovnávání zatížení sítě (Vyrovnávání zatížení sítě), hostitele pracovního postupu, který je spuštěn v jednom uzlu farmy načte instanci pracovního postupu a zpracovává zprávu a další zprávy k instanci se směruje na hostitele, který běží na jiném uzlu, protože Vyrovnávání zatížení sítě nemá směrování algoritmus pro doručování zpráv na hostitele, který je již spuštěna instance. Po přijetí zprávy, druhý hostitele, pokusí se načíst instanci pracovního postupu a přijímá <xref:System.Runtime.DurableInstancing.InstanceLockedException> protože prvního hostitele má zámek na instanci. Prvního hostitele odemkne instance po jeho dokončení se zpracováním první zprávu a druhý hostitele získá zámek při příštím opakování, načte instanci a o druhou zprávu zpracuje.
