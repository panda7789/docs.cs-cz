---
title: "Postupy: Použití příkazu ForEach k odebrání položek v kolekci BlockingCollection"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: thread-safe collections, how to enumerate blocking collectoin
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7683e295bd1d898e112a754b06993dabf4483871
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a>Postupy: Použití příkazu ForEach k odebrání položek v kolekci BlockingCollection
Kromě přijímání položek z <xref:System.Collections.Concurrent.BlockingCollection%601> pomocí <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> a <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> metodu, můžete také použít [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([pro každou](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) v jazyce Visual Basic) odebrat položky, dokud nebude přidání byla dokončena a kolekce je prázdná. Tento postup se nazývá *mutace – výčet* nebo *využívání – výčet* proto, že na rozdíl od typické `foreach` (`For Each`) ve smyčce, výčet upraví zdrojové kolekci odebráním položky.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak odebrat všechny položky v <xref:System.Collections.Concurrent.BlockingCollection%601> pomocí `foreach` (`For Each`) smyčky.  
  
 [!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
 [!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]  
  
 Tento příklad používá `foreach` cykly s <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> metoda ve vláknu, což způsobí, že každá položka má být odebrán z kolekce, jak je uvedené. <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>omezuje maximální počet položek, které jsou v kolekci kdykoli. Procházení kolekce tímto způsobem blokuje vlákno příjemce, pokud žádné položky jsou k dispozici nebo pokud je kolekce prázdná. V tomto příkladu blokování není důležité, protože vlákno výrobce přidává položky rychleji, než mohou být využívány.  
  
 Není zaručeno, že položky jsou uvedené ve stejném pořadí, ve kterém budou přidány vlákny výrobce.  
  
 Výčet kolekce beze změny ji, použijte `foreach` (`For Each`) bez <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metoda. Je ale důležité si uvědomit, že tento druh výčtu představuje snímek kolekce na přesné bodu v čase. Pokud jiná vlákna se přidávání nebo odebírání položek současně, zatímco jsou prováděny smyčky, nemusí smyčky reprezentovat skutečný stav kolekce.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
 [Paralelní programování](../../../../docs/standard/parallel-programming/index.md)
