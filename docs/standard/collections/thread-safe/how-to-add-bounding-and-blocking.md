---
title: 'Postupy: Přidání funkcí ohraničování a blokování do kolekce'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3f52d1067a8aa907c8f1cf8b550eec82d1133b3f
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46516818"
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a>Postupy: Přidání funkcí ohraničování a blokování do kolekce
Tento příklad ukazuje, jak k přidání funkcí ohraničování a blokování do vlastní třídu kolekce implementací <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> rozhraní ve třídě a pak pomocí instance třídy jako mechanismus pro interní úložiště <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>. Další informace o funkcí ohraničování a blokování najdete v tématu [BlockingCollection – přehled](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).  
  
## <a name="example"></a>Příklad  
 Vlastní kolekce třída je základní prioritní fronty, do které úrovně priority jsou reprezentovány ve formě pole <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> objekty. Žádné další řazení se provádí v rámci jednotlivých front.  
  
 Tři úkoly jsou spuštěny v kódu klienta. První úkol právě dotazuje tahy klávesnice k povolení zrušení kdykoli během provádění. Druhá úloha je výrobce podprocesu. Přidá nové položky do blokující kolekce a poskytuje prioritu na základě náhodné hodnoty každé položky. Třetí úloha odebere položky z kolekce, jakmile budou k dispozici.  
  
 Chování aplikace můžete upravit tak, že jedno z vláken rychleji než ten druhý. Pokud výrobce běží rychleji, si všimnete ohraničující funkce blokující kolekce zabraňuje přidávání Pokud již obsahuje počet položek, která je určená v konstruktoru položky. Pokud takový příjemce běží rychleji, můžete si všimnout, blokování funkce jako příjemce čeká na nové položky, který chcete přidat.  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 Ve výchozím nastavení úložiště pro <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> je <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:

- [Kolekce se zabezpečenými vlákny](../../../../docs/standard/collections/thread-safe/index.md)
