---
title: Použití příkazu foreach k odebrání položek v Blokujícícollection
ms.date: 05/04/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- thread-safe collections, how to enumerate blocking collection
ms.assetid: 2096103c-22f7-420d-b631-f102bc33a6dd
ms.openlocfilehash: 1255fcda89396ea8ff9abf6cf111e6dd9ea5a87d
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/06/2020
ms.locfileid: "82861010"
---
# <a name="use-foreach-to-remove-items-in-a-blockingcollection"></a>Použití příkazu foreach k odebrání položek v Blokujícícollection

<xref:System.Collections.Concurrent.BlockingCollection%601> Kromě pořizování položek z a pomocí metody <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> a <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> můžete také použít [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([pro každý](../../../visual-basic/language-reference/statements/for-each-next-statement.md) z Visual Basic) s příkazem <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> pro odebrání položek, dokud není přidání dokončeno a kolekce je prázdná. To se označuje jako *obdobná výčet* nebo použití *výčtu* , protože na rozdíl od typické `foreach` (`For Each`) smyčky tento enumerátor upraví zdrojovou kolekci odebráním položek.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak odebrat všechny položky v a <xref:System.Collections.Concurrent.BlockingCollection%601> pomocí smyčky `foreach` (`For Each`).

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

V tomto příkladu se `foreach` používá smyčka <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> s metodou ve vybírající vlákně, což způsobí, že každá položka bude z kolekce odebrána, protože je vytvořena její výčet. <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>omezí maximální počet položek, které jsou v kolekci v každém okamžiku. Výčet kolekce tímto způsobem blokuje příjemce vlákna, pokud nejsou k dispozici žádné položky nebo pokud je kolekce prázdná. V tomto příkladu blokování není obavy, protože vlákno producenta přidává položky rychleji, než mohou být spotřebovány.

<xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> Vrátí `IEnumerable<T>`, takže pořadí nemůže být zaručeno. Interně a <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> se ale používá jako typ podkladové kolekce – což způsobí, že se objekty odřadí z fronty po řazení FIFO (First-in-first-out). Pokud <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> jsou souběžná volání provedena, budou konkurovat. Jedna položka spotřebované (ve frontě) v jednom výčtu nemůže být zjištěna v druhé položce.

Chcete-li vytvořit výčet kolekce bez změny, stačí `foreach` použít`For Each`() bez <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metody. Je však důležité pochopit, že tento druh výčtu představuje snímek kolekce v přesném časovém bodě. Pokud jiné vlákna přidávají nebo odebírají položky souběžně při provádění smyčky, pak smyčka nemusí představovat skutečný stav kolekce.

## <a name="see-also"></a>Viz také

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Paralelní programování](../../../../docs/standard/parallel-programming/index.md)
