---
title: 'Postupy: Použití příkazu ForEach k odebrání položek v BlockingCollection'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collection
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 10fa77f6948a10959db5f79c37692eba67d47ecd
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666543"
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a>Postupy: Použití příkazu ForEach k odebrání položek v BlockingCollection

Kromě pořizování <xref:System.Collections.Concurrent.BlockingCollection%601> položek z <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> a pomocí metody a <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> můžete také použít [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([pro každý](../../../visual-basic/language-reference/statements/for-each-next-statement.md) z Visual Basic) k odebrání položek, dokud není přidávání dokončeno a kolekce je prázdná. To se označuje jako *obdobná výčet* nebo použití *výčtu* , protože na rozdíl od typické `foreach` (`For Each`) smyčky tento enumerátor upraví zdrojovou kolekci odebráním položek.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak odebrat všechny položky v a <xref:System.Collections.Concurrent.BlockingCollection%601> `foreach` pomocí smyčky (`For Each`).

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

V tomto příkladu <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> se `foreach` používá smyčka s metodou ve vybírající vlákně, což způsobí, že každá položka bude z kolekce odebrána, protože je vytvořena její výčet. <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>omezí maximální počet položek, které jsou v kolekci v každém okamžiku. Výčet kolekce tímto způsobem blokuje příjemce vlákna, pokud nejsou k dispozici žádné položky nebo pokud je kolekce prázdná. V tomto příkladu blokování není obavy, protože vlákno producenta přidává položky rychleji, než mohou být spotřebovány.

Není zaručeno, že se položky zobrazí ve stejném pořadí, ve kterém jsou přidány vlákny producenta.

Chcete-li vytvořit výčet kolekce bez změny, stačí `foreach` použít`For Each`() bez <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metody. Je však důležité pochopit, že tento druh výčtu představuje snímek kolekce v přesném časovém bodě. Pokud jiné vlákna přidávají nebo odebírají položky souběžně při provádění smyčky, pak smyčka nemusí představovat skutečný stav kolekce.

## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Paralelní programování](../../../../docs/standard/parallel-programming/index.md)
