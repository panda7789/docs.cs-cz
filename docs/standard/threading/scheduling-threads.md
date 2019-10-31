---
title: Plánování vláken
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
ms.openlocfilehash: abcdf56b90513b937adefc38583e0312fec69785
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73106233"
---
# <a name="scheduling-threads"></a>Plánování vláken

Každé vlákno má přiřazenou prioritu vlákna. K vláknům vytvořeným v modulu CLR (Common Language Runtime) se zpočátku přiřadí priorita <xref:System.Threading.ThreadPriority.Normal?displayProperty=nameWithType>. Vlákna vytvořená mimo modul runtime uchovávají prioritu, kterou měly předtím, než se do spravovaného prostředí zadala. Můžete získat nebo nastavit prioritu libovolného vlákna s vlastností <xref:System.Threading.Thread.Priority?displayProperty=nameWithType>.  
  
 Vlákna mají naplánované spouštění na základě jejich priority. I když jsou vlákna spouštěna v modulu runtime, jsou všechna vlákna přiřazena časová období procesoru operačním systémem. Podrobnosti o algoritmu plánování použitého k určení pořadí, ve kterém jsou vlákna spouštěny, se liší u jednotlivých operačních systémů. V některých operačních systémech je vlákno s nejvyšší prioritou (u těchto vláken, které lze spustit) vždy naplánováno na spuštění jako první. Pokud je k dispozici více vláken se stejnou prioritou, Plánovač cyklicky projde vlákna s touto prioritou, přičemž každé vlákno provede pevný časový úsek, ve kterém se má provést. Pokud je pro spuštění k dispozici vlákno s vyšší prioritou, nespustí se podprocesy s nižší prioritou. Pokud v dané prioritě neexistují žádná další spustitelný vlákna, Plánovač se přesune k další nižší prioritě a naplánuje vlákna v této prioritě pro provedení. Pokud se vlákno s vyšší prioritou změní na spustitelný, vlákno s nižší prioritou je přerušeno a vlákno s vyšší prioritou je povoleno znovu spustit. Nad všemi možnostmi může operační systém dynamicky upravovat priority vláken, protože uživatelské rozhraní aplikace je přesunuto mezi popředí a pozadí. Jiné operační systémy se můžou rozhodnout použít jiný algoritmus plánování.  
  
## <a name="see-also"></a>Viz také:

- [Použití vláken a dělení na vlákna](../../../docs/standard/threading/using-threads-and-threading.md)
- [Dělení na spravovaná a nespravovaná vlákna ve Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)
