---
title: 'Postupy: Použití příkazu ForEach k odebrání položek v kolekci BlockingCollection'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collectoin
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 44b71ed726af585259b015c608e49d8c81e4e22a
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44217149"
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a>Postupy: Použití příkazu ForEach k odebrání položek v kolekci BlockingCollection
Kromě odebírání položek z <xref:System.Collections.Concurrent.BlockingCollection%601> pomocí <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> a <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> metodu, můžete použít také [foreach](~/docs/csharp/language-reference/keywords/foreach-in.md) ([pro každou](~/docs/visual-basic/language-reference/statements/for-each-next-statement.md) v jazyce Visual Basic) k odebrání položek, dokud se přidání je dokončení a kolekce je prázdná. Tento postup se nazývá *mutace výčet* nebo *využívání výčet* proto, že na rozdíl od typické `foreach` (`For Each`) smyčky, výčet upraví tak, že odeberete zdrojové kolekce položky.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak odebrat všechny položky v <xref:System.Collections.Concurrent.BlockingCollection%601> pomocí `foreach` (`For Each`) smyčky.  
  
 [!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
 [!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]  
  
 Tento příklad používá `foreach` smyčky s <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> metoda v konzumním vlákně, což způsobí, že jednotlivé položky na odebrat z kolekce, protože je uveden. <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> Omezí maximální počet položek, které jsou v kolekci v každém okamžiku. Vytváření výčtu kolekce tímto způsobem blokuje vlákno příjemce, pokud žádné položky jsou k dispozici nebo pokud kolekce je prázdná. V tomto příkladu blokuje není důležité, protože vlákno výrobce přidá položky rychleji, než mohou být využívány.  
  
 Není zaručeno, že položky jsou uvedené ve stejném pořadí, ve které se přidají vlákny výrobce.  
  
 K vytvoření výčtu kolekce bez její změny, stačí použít `foreach` (`For Each`) bez <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metody. Je důležité pochopit, že tento druh výčtu představuje snímek kolekce na konkrétním místě v čase. Pokud jiná vlákna jsou přidávání a odebírání položek současně, zatímco spouštíte smyčky, nemusí představovat smyčky skutečný stav kolekce.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>  
- [Paralelní programování](../../../../docs/standard/parallel-programming/index.md)
