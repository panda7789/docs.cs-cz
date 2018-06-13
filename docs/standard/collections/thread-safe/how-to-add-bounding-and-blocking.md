---
title: 'Postupy: Přidání funkcí ohraničování a blokování do kolekce'
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- thread-safe collections, custom blocking collections
ms.assetid: 4c2492de-3876-4873-b5a1-000bb404d770
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6262822e0916e142c7c543d2e2546c8540cb73a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568573"
---
# <a name="how-to-add-bounding-and-blocking-functionality-to-a-collection"></a>Postupy: Přidání funkcí ohraničování a blokování do kolekce
Tento příklad ukazuje postup přidání funkcí ohraničování a blokování do vlastní kolekce třídy implementací <xref:System.Collections.Concurrent.IProducerConsumerCollection%601?displayProperty=nameWithType> rozhraní ve třídě a pak pomocí instance třídy jako mechanismus pro interní úložiště <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>. Další informace o funkcí ohraničování a blokování najdete v tématu [BlockingCollection – přehled](../../../../docs/standard/collections/thread-safe/blockingcollection-overview.md).  
  
## <a name="example"></a>Příklad  
 Třída vlastní kolekce je základní prioritou fronty, ve kterém jsou úroveň priority vyjádřené pole <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> objekty. Žádné další řazení se provádí v rámci každé fronty.  
  
 V kódu klienta tři úlohy spustí. První úlohou právě zjišťuje klávesnice tahy povolit zrušení kdykoli během provádění. V druhé úloze je proto, že vlákno; Přidá nové položky blokující kolekce a poskytuje každou položku prioritu podle náhodná hodnota. Třetí úloh odebere položky z kolekce, jakmile budou k dispozici.  
  
 Chování aplikace můžete upravit tak, že některé z vláken rychleji probíhají rychleji než ostatní. Pokud autor rychleji spustí, si všimnete funkci ohraničující blokující kolekce brání položky přidání Pokud již obsahuje počet položek, který je uveden v konstruktoru. Pokud se příjemce rychleji spustí, si všimnete blokování funkce jako příjemce čeká na novou položku Přidat.  
  
 [!code-csharp[CDS_BlockingCollection#06](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/prodcon.cs#06)]  
  
 Ve výchozím nastavení úložiště pro <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> je <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také  
 [Kolekce se zabezpečenými vlákny](../../../../docs/standard/collections/thread-safe/index.md)
