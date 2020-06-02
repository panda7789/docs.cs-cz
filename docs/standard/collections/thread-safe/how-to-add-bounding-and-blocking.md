---
title: 'Postupy: Přidání funkcí ohraničování a blokování do kolekce'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
ms.openlocfilehash: 57a01726e897f4ddbf8df5ede53609c198012d80
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287871"
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a>Postupy: Přidání funkcí ohraničování a blokování do kolekce
Tento příklad ukazuje, jak přidat funkci ohraničování a blokování do vlastní třídy kolekce implementací <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> rozhraní ve třídě a následnou použitím instance třídy jako mechanismu interního úložiště pro <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> . Další informace o ohraničování a blokování najdete v tématu [blokujícícollection – přehled](blockingcollection-overview.md).  
  
## <a name="example"></a>Příklad  
 Vlastní třída kolekce je základní a prioritní frontou, ve které jsou úrovně priority reprezentované jako pole <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> objektů. V každé frontě se neprovádí žádné další řazení.  
  
 V kódu klienta se spouští tři úkoly. První úkol se pouze dotazuje na tahy klávesnice, aby bylo možné zrušit v jakémkoli okamžiku během provádění. Druhým úkolem je vlákno producenta; přidává nové položky do blokující kolekce a dává každé položce prioritu na základě náhodné hodnoty. Třetí úkol odebere položky z kolekce, jakmile budou k dispozici.  
  
 Chování aplikace můžete upravit tak, že jeden z vláken běží rychleji než druhý. Pokud producent pracuje rychleji, všimnete si, že funkce pro zablokování brání v přidání položek, pokud již obsahuje počet položek, které jsou zadány v konstruktoru. Pokud příjemce pracuje rychleji, všimnete si, že funkce blokování přestane být přidána, protože příjemce čeká na přidání nové položky.  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 Ve výchozím nastavení je úložiště pro <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Viz také

- [Kolekce bezpečné pro přístup z více vláken](index.md)
