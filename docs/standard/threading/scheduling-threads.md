---
title: Plánování vláken
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], scheduling
- scheduling threads
ms.assetid: 67e4a0eb-3095-4ea7-b20f-908faa476277
ms.openlocfilehash: abcdf56b90513b937adefc38583e0312fec69785
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106233"
---
# <a name="scheduling-threads"></a>Plánování vláken

Každé vlákno má přiřazenou prioritu vlákna. Vláknům vytvořeným v rámci běžného jazykového <xref:System.Threading.ThreadPriority.Normal?displayProperty=nameWithType>běhu je zpočátku přiřazena priorita rozhraní . Vlákna vytvořená mimo zaběhu si zachovávají prioritu, kterou měli před vstupem do spravovaného prostředí. Můžete získat nebo nastavit prioritu libovolného vlákna s vlastností. <xref:System.Threading.Thread.Priority?displayProperty=nameWithType>  
  
 Podprocesy jsou naplánovány pro spuštění na základě jejich priority. I když vlákna jsou spuštěny v rámci modulu runtime, všechna vlákna jsou přiřazeny časové úseky procesoru operačním systémem. Podrobnosti o algoritmu plánování, který slouží k určení pořadí, ve kterém jsou spouštěna vlákna se liší s každým operačním systémem. V některých operačních systémech je vždy naplánováno spuštění podprocesu s nejvyšší prioritou (z těch vláken, které lze spustit). Pokud více podprocesů se stejnou prioritou jsou k dispozici, plánovač cykly prostřednictvím podprocesů na tuto prioritu, dává každé vlákno pevný časový řez, ve kterém chcete provést. Tak dlouho, dokud vlákno s vyšší prioritou je k dispozici ke spuštění, podprocesy s nižší prioritou nedostanou ke spuštění. Pokud neexistují žádné další spustitelné podprocesy v dané prioritě, plánovač přesune na další nižší prioritu a naplánuje vlákna na tuto prioritu pro spuštění. Pokud vlákno s vyšší prioritou se stane spustitelným, vlákno s nižší prioritou je předptoňováno a vlákno s vyšší prioritou může být znovu spuštěno. Kromě toho operační systém může také dynamicky upravit priority podprocesů, protože uživatelské rozhraní aplikace se přesouvá mezi popředí maže a pozadí. Jiné operační systémy se mohou rozhodnout použít jiný algoritmus plánování.  
  
## <a name="see-also"></a>Viz také

- [Použití vláken a zřetězení](../../../docs/standard/threading/using-threads-and-threading.md)
- [Dělení na spravovaná a nespravovaná vlákna ve Windows](../../../docs/standard/threading/managed-and-unmanaged-threading-in-windows.md)
