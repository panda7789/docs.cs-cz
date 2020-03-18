---
title: 'Postupy: Použití příkazu ForEach k odebrání položek v kolekci BlockingCollection'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collection
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
ms.openlocfilehash: f9a858dea74be63634f887c4204aefa8ac338ad0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711230"
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a>Postupy: Použití příkazu ForEach k odebrání položek v kolekci BlockingCollection

Kromě přijímání položek z <xref:System.Collections.Concurrent.BlockingCollection%601> pomocí <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> metody <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> a můžete také použít [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) v jazyce Visual Basic) k odebrání položek, dokud není přidání dokončeno a kolekce je prázdná. To se nazývá *mutující výčt* nebo *spotřebovává výčtu,* `foreach` protože`For Each`na rozdíl od typické ( ) smyčky tento čítač výčtu upravuje zdrojové kolekce odebráním položek.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak odebrat <xref:System.Collections.Concurrent.BlockingCollection%601> všechny položky v a pomocí `foreach` smyčky (`For Each`).

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

Tento příklad `foreach` používá smyčku s <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> metodou v náročnévlákno, což způsobí, že každá položka má být odebrána z kolekce, jak je uveden. <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>omezuje maximální počet položek, které jsou v kolekci kdykoli. Výčet kolekce tímto způsobem blokuje vlákno příjemce, pokud nejsou k dispozici žádné položky nebo pokud je kolekce prázdná. V tomto příkladu blokování není problém, protože vlákno výrobce přidá položky rychleji, než mohou být spotřebovány.

Neexistuje žádná záruka, že položky jsou uvedeny ve stejném pořadí, ve kterém jsou přidány podprocesy výrobce.

Chcete-li vytvořit výčet kolekce bez úpravy, stačí použít `foreach` (`For Each`) bez <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metody. Je však důležité si uvědomit, že tento druh výčtu představuje snímek kolekce v přesném okamžiku v čase. Pokud ostatní vlákna přidávají nebo odebírají položky souběžně při provádění smyčky, smyčka nemusí představovat skutečný stav kolekce.

## <a name="see-also"></a>Viz také

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Paralelní programování](../../../../docs/standard/parallel-programming/index.md)
