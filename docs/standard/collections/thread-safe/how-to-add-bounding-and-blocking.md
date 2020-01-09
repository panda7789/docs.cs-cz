---
title: 'Postupy: Přidání funkcí ohraničování a blokování do kolekce'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
ms.openlocfilehash: 33c0b5a93a9c63e3e743a04e69bb7353ac69fa8a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711282"
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a>Postupy: Přidání funkcí ohraničování a blokování do kolekce
Tento příklad ukazuje, jak přidat funkci ohraničování a blokování do vlastní třídy kolekce implementací rozhraní <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> ve třídě a následnou použitím instance třídy jako mechanismu interního úložiště pro <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>. Další informace o ohraničování a blokování najdete v tématu [blokujícícollection – přehled](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).  
  
## <a name="example"></a>Příklad  
 Vlastní třída kolekce je základní frontou priorit, ve které jsou úrovně priority reprezentované jako pole <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> objektů. V každé frontě se neprovádí žádné další řazení.  
  
 V kódu klienta se spouští tři úkoly. První úkol se pouze dotazuje na tahy klávesnice, aby bylo možné zrušit v jakémkoli okamžiku během provádění. Druhým úkolem je vlákno producenta; přidává nové položky do blokující kolekce a dává každé položce prioritu na základě náhodné hodnoty. Třetí úkol odebere položky z kolekce, jakmile budou k dispozici.  
  
 Chování aplikace můžete upravit tak, že jeden z vláken běží rychleji než druhý. Pokud producent pracuje rychleji, všimnete si, že funkce pro zablokování brání v přidání položek, pokud již obsahuje počet položek, které jsou zadány v konstruktoru. Pokud příjemce pracuje rychleji, všimnete si, že funkce blokování přestane být přidána, protože příjemce čeká na přidání nové položky.  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 Ve výchozím nastavení je <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>úložiště pro <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:

- [Kolekce se zabezpečenými vlákny](../../../../docs/standard/collections/thread-safe/index.md)
