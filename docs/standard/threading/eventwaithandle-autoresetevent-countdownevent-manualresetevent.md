---
title: Eventwaithandle – CountdownEvent, ManualResetEvent
ms.date: 09/14/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- wait handles
- threading [.NET Framework], EventWaitHandle class
- event wait handles [.NET Framework]
ms.assetid: cd94fc34-ac15-427f-b723-a1240a4fab7d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c682fbcc09609a9a4e59b29d5c8997a5ae21d2bc
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266518"
---
# <a name="eventwaithandle-countdownevent-manualresetevent"></a>Eventwaithandle – CountdownEvent, ManualResetEvent

Obslužné rutiny události čekání povolit vláken pro synchronizaci činností signalizace mezi sebou a čeká se na druhé strany signálů. Tyto události synchronizace jsou založeny na obslužné rutiny čekání operačního systému a je možné rozdělit do dvou typů: ty, které obnovit automaticky, když se signál a ty, které jsou ručně obnovit.  
  
Obslužné rutiny čekání události jsou užitečné v mnoha stejné synchronizačních scénářů, jako <xref:System.Threading.Monitor> třídy. Obslužné rutiny čekání události jsou často jednodušší než <xref:System.Threading.Monitor.Wait%2A?displayProperty=nameWithType> a <xref:System.Threading.Monitor.Pulse%2A?displayProperty=nameWithType> metody a nabízí větší kontrolu nad signalizace. Obslužné rutiny čekání pojmenované události lze také synchronizovat aktivity napříč doménami aplikace a procesy, že monitorování jsou místní vůči doméně aplikace.  
  
## <a name="in-this-section"></a>V tomto oddílu

 [EventWaitHandle](eventwaithandle.md)  
 <xref:System.Threading.EventWaitHandle?displayProperty=nameWithType> Může představovat buď automatické nebo ruční resetování buď místní události a události nebo pojmenována jako událost systému.  
  
 [ManualResetEvent a ManualResetEventSlim](manualresetevent-and-manualreseteventslim.md)  
 <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> Třída odvozena z <xref:System.Threading.EventWaitHandle> a představuje místní událost, která musí být v továrním ručně. <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> Třída je jednoduché a rychlejší verzi, která lze použít pro události v rámci stejného procesu.  
  
 [CountdownEvent](countdownevent.md)  
 <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> Třída poskytuje zjednodušený způsob, jak implementovat rozvětvení/spojení paralelismu vzorů v kódu, že používá obslužné rutiny čekání.  

## <a name="see-also"></a>Viz také:

- <xref:System.Threading.WaitHandle?displayProperty=nameWithType>
- <xref:System.Threading.Barrier?displayProperty=nameWithType>
- [Práce s vlákny funkce a objekty](threading-objects-and-features.md)
- [Dělení na spravovaná vlákna základy](managed-threading-basics.md)
