---
title: 'Postupy: Přidání funkcí ohraničování a blokování do kolekce'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
ms.openlocfilehash: 33c0b5a93a9c63e3e743a04e69bb7353ac69fa8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711282"
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a>Postupy: Přidání funkcí ohraničování a blokování do kolekce
Tento příklad ukazuje, jak přidat ohraničující a blokující <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> funkce do vlastní třídy kolekce implementací rozhraní <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>ve třídě a potom pomocí instance třídy jako mechanismu vnitřního úložiště pro . Další informace o ohraničování a blokování naleznete v [tématu BlockingCollection Overview](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).  
  
## <a name="example"></a>Příklad  
 Vlastní třída kolekce je základní fronty priorit, ve kterém jsou <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> úrovně priority reprezentovány jako pole objektů. V rámci každé fronty se neprovádí žádné další řazení.  
  
 V kódu klienta jsou spuštěny tři úkoly. První úkol pouze dotazování pro tahy klávesnice povolit zrušení v libovolném okamžiku během provádění. Druhým úkolem je podproces výrobce; přidá nové položky do kolekce blokování a dává každé položce prioritu na základě náhodné hodnoty. Třetí úkol odebere položky z kolekce, jakmile budou k dispozici.  
  
 Můžete upravit chování aplikace tím, že jeden z podprocesů spustit rychleji než ostatní. Pokud výrobce běží rychleji, všimnete si funkce ohraničování jako blokování kolekce zabraňuje položky, které jsou přidány, pokud již obsahuje počet položek, které jsou zadány v konstruktoru. Pokud spotřebitel běží rychleji, všimnete si blokování funkce jako příjemce čeká na novou položku, která má být přidána.  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 Ve výchozím nastavení <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> je <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>úložiště pro .  
  
## <a name="see-also"></a>Viz také

- [Kolekce se zabezpečenými vlákny](../../../../docs/standard/collections/thread-safe/index.md)
