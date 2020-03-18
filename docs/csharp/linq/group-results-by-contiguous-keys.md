---
title: Seskupit výsledky podle sousedících klíčů (LINQ v c#)
description: Jak seskupit výsledky podle sousedících klíčů pomocí LINQ v C#.
ms.date: 08/14/2018
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: b5753c85bb07be4fc84b78a299eece961969ff9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "61659901"
---
# <a name="group-results-by-contiguous-keys"></a>Seskupení výsledků podle sousedních klíčů

Následující příklad ukazuje, jak seskupit prvky do bloků, které představují dílčí sekvence souvislých klíčů. Předpokládejme například, že jste dostali následující posloupnost párů klíč-hodnota:

|Klíč|Hodnota|
|---------|-----------|
|A|Jsme|
|A|Myslet|
|A|Že|
|B|Linq|
|C|is|
|A|Vážně|
|B|Cool|
|B|!|

V tomto pořadí budou vytvořeny následující skupiny:

1. My, myslím, že

2. Linq

3. is

4. Vážně

5. Cool!

Řešení je implementováno jako metoda rozšíření, která je bezpečná pro přístup z více vláken a která vrací jeho výsledky způsobem streamování. Jinými slovy vytváří své skupiny, když se pohybuje přes zdrojové sekvence. Na `group` rozdíl `orderby` od operátory nebo může začít vracet skupiny volajícímu před všechny sekvence byla přečtena.

Bezpečnost podprocesu se provádí vytvořením kopie každé skupiny nebo bloku, protože zdrojová sekvence je iterována, jak je vysvětleno v komentářích zdrojového kódu. Pokud má zdrojová sekvence velkou posloupnost sousedících položek, může <xref:System.OutOfMemoryException>běžný jazyk vyvolat .

## <a name="example"></a>Příklad

Následující příklad ukazuje metodu rozšíření i kód klienta, který ji používá:

[!code-csharp[cscsrefContiguousGroups#1](~/samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]

Chcete-li použít metodu rozšíření `MyExtensions` v projektu, zkopírujte statickou třídu do nového `using` nebo existujícího souboru zdrojového kódu a pokud je požadováno, přidejte direktivu pro obor názvů, kde je umístěn.

## <a name="see-also"></a>Viz také

- [LINQ (Language Integrated Query)](index.md)
