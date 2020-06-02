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
ms.openlocfilehash: 46638d2cd8078fefebc0eacc4b8f7798ffe178ff
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288898"
---
# <a name="use-foreach-to-remove-items-in-a-blockingcollection"></a>Použití příkazu foreach k odebrání položek v Blokujícícollection

Kromě pořizování položek z a pomocí <xref:System.Collections.Concurrent.BlockingCollection%601> <xref:System.Collections.Concurrent.BlockingCollection%601.Take%2A> <xref:System.Collections.Concurrent.BlockingCollection%601.TryTake%2A> metody a můžete také použít [foreach](../../../csharp/language-reference/keywords/foreach-in.md) ([pro každý](../../../visual-basic/language-reference/statements/for-each-next-statement.md) z Visual Basic) s příkazem <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> pro odebrání položek, dokud není přidání dokončeno a kolekce je prázdná. To se označuje jako *obdobná výčet* nebo použití *výčtu* , protože na rozdíl od typické `foreach` ( `For Each` ) smyčky tento enumerátor upraví zdrojovou kolekci odebráním položek.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak odebrat všechny položky v a <xref:System.Collections.Concurrent.BlockingCollection%601> pomocí `foreach` `For Each` smyčky ().

[!code-csharp[CDS_BlockingCollection#03](../../../../samples/snippets/csharp/VS_Snippets_Misc/cds_blockingcollection/cs/example03.cs#03)]
[!code-vb[CDS_BlockingCollection#03](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/cds_blockingcollection/vb/enumeratebc.vb#03)]

V tomto příkladu `foreach` se používá smyčka s <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> metodou ve vybírající vlákně, což způsobí, že každá položka bude z kolekce odebrána, protože je vytvořena její výčet. <xref:System.Collections.Concurrent.BlockingCollection%601?displayProperty=nameWithType>omezí maximální počet položek, které jsou v kolekci v každém okamžiku. Výčet kolekce tímto způsobem blokuje příjemce vlákna, pokud nejsou k dispozici žádné položky nebo pokud je kolekce prázdná. V tomto příkladu blokování není obavy, protože vlákno producenta přidává položky rychleji, než mohou být spotřebovány.

<xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType>Vrátí `IEnumerable<T>` , takže pořadí nemůže být zaručeno. Interně a <xref:System.Collections.Concurrent.ConcurrentQueue%601?displayProperty=nameWithType> se ale používá jako typ podkladové kolekce – což způsobí, že se objekty odřadí z fronty po řazení FIFO (First-in-first-out). Pokud jsou souběžná volání <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A?displayProperty=nameWithType> provedena, budou konkurovat. Jedna položka spotřebované (ve frontě) v jednom výčtu nemůže být zjištěna v druhé položce.

Chcete-li vytvořit výčet kolekce bez změny, stačí použít `foreach` ( `For Each` ) bez <xref:System.Collections.Concurrent.BlockingCollection%601.GetConsumingEnumerable%2A> metody. Je však důležité pochopit, že tento druh výčtu představuje snímek kolekce v přesném časovém bodě. Pokud jiné vlákna přidávají nebo odebírají položky souběžně při provádění smyčky, pak smyčka nemusí představovat skutečný stav kolekce.

## <a name="see-also"></a>Viz také

- <xref:System.Collections.Concurrent?displayProperty=nameWithType>
- [Paralelní programování](../../parallel-programming/index.md)
