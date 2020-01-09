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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711230"
---
# <a name="how-to-use-foreach-to-remove-items-in-a-blockingcollection"></a>Postupy: Použití příkazu ForEach k odebrání položek v kolekci BlockingCollection

Kromě přebírání položek z <xref:System.Collections.Concurrent.BlockingCollection%601> pomocí metody <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> a <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> můžete také použít [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([pro každý](../../../visual-basic/language-reference/statements/for-each-next-statement.md) v Visual Basic) k odebrání položek, dokud není přidávání dokončeno a kolekce je prázdná. To se označuje jako *obdobná výčet* nebo použití *výčtu* , protože na rozdíl od typické smyčky `foreach` (`For Each`) Tento enumerátor upraví zdrojovou kolekci odebráním položek.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak odebrat všechny položky v <xref:System.Collections.Concurrent.BlockingCollection%601> pomocí smyčky `foreach` (`For Each`).

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

V tomto příkladu se používá smyčka `foreach` s metodou <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> ve spotřebovávatelné vlákně, což způsobí, že každá položka bude z kolekce odebrána, protože je vyhodnocena. <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType> omezuje maximální počet položek, které jsou v kolekci kdykoli. Výčet kolekce tímto způsobem blokuje příjemce vlákna, pokud nejsou k dispozici žádné položky nebo pokud je kolekce prázdná. V tomto příkladu blokování není obavy, protože vlákno producenta přidává položky rychleji, než mohou být spotřebovány.

Není zaručeno, že se položky zobrazí ve stejném pořadí, ve kterém jsou přidány vlákny producenta.

Chcete-li vytvořit výčet kolekce bez změny, stačí použít `foreach` (`For Each`) bez metody <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A>. Je však důležité pochopit, že tento druh výčtu představuje snímek kolekce v přesném časovém bodě. Pokud jiné vlákna přidávají nebo odebírají položky souběžně při provádění smyčky, pak smyčka nemusí představovat skutečný stav kolekce.

## <a name="see-also"></a>Viz také:

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Paralelní programování](../../../../docs/standard/parallel-programming/index.md)
