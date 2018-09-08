---
title: Plánování vláken
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 811a75c9f0350eefc98c32181e859b7583ff74ef
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44186289"
---
# <a name="scheduling-threads"></a>Plánování vláken

Každé vlákno má priorita vlákna přiřazené. Vlákna vytvořená v rámci common language runtime jsou původně přiřazený prioritu <xref:System.Threading.ThreadPriority.Normal?displayProperty=nameWithType>. Vlákna vytvořená mimo modul runtime zachovat priorita, která měly před jejich spravované prostředí. Můžete získat nebo nastavit prioritu jakékoli vlákno s <xref:System.Threading.Thread.Priority?displayProperty=nameWithType> vlastnost.  
  
 Vlákna jsou naplánovány k provedení na základě jejich priority. I když jsou vlákna provádění v modulu runtime, všechna vlákna jsou přiřazeny procesoru časových řezů v operačním systému. Podrobnosti o plánování algoritmus používaný k určení pořadí, ve kterém jsou spouštěny vlákna se liší podle každý operační systém. V některých operačních systémů vlákno s nejvyšší prioritou (tato vlákna, které mohou být provedeny) vždy je naplánováno spuštění první. Pokud více vláken se stejnou prioritou jsou k dispozici, Plánovač procházení vlákna důležitostí, poskytuje každé vlákno pevném časovém řezu v, který se má spustit. Za předpokladu, vlákno s vyšší prioritou je k dispozici ke spuštění, nižší priorita vlákna nelze získat ke spuštění. Pokud neexistují žádné další spustitelné vlákna daného důležitostí, Plánovač přesune na další nižší prioritu a naplánuje vláken v této prioritu pro spouštění. Pokud spustitelný přestane být vyšší priorita vlákna, dojde ke zrušení nižší priorita vlákna a vyšší priorita vlákna je povoleno spustit znovu. Nad všechny možnosti, které operačního systému můžete také nastavit priority vlákna dynamicky podle uživatelského rozhraní aplikace se přesune mezi popředí a pozadí. Použít jiný algoritmus plánování zvolit jiné operační systémy.  
  
## <a name="see-also"></a>Viz také:

- [Použití vláken a dělení na vlákna](../../../docs/standard/threading/using-threads-and-threading.md)  
- [Dělení na spravovaná a nespravovaná vlákna ve Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)
