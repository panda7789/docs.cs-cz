---
title: Seskupení výsledků podle sousedních klíčů (LINQ v JAZYKU C#)
description: Jak seskupení výsledků podle sousedních klíčů pomocí jazyka LINQ v jazyce C#.
ms.date: 08/14/2018
ms.assetid: cbda9c08-151b-4c9e-82f7-c3d7f3dac66b
ms.openlocfilehash: b5753c85bb07be4fc84b78a299eece961969ff9d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61659901"
---
# <a name="group-results-by-contiguous-keys"></a>Seskupení výsledků podle sousedních klíčů

Následující příklad ukazuje, jak seskupit elementy do bloků dat, které představují dílčích sekvencí, které ze sousedních klíčů. Předpokládejme například, že budete mít k následujícímu pořadí páry klíč hodnota:

|Key|Value|
|---------|-----------|
|OBJEKT|Jsme|
|OBJEKT|přemýšlení|
|OBJEKT|který|
|B|LINQ|
|C|is|
|OBJEKT|Vážně|
|B|Cool|
|B|!|

Tyto skupiny se vytvoří v tomto pořadí:

1. Myslíme si, že

2. LINQ

3. is

4. Vážně

5. studené!

Toto řešení je implementované jako metodu rozšíření, které je bezpečné pro vlákna a, který vrátí výsledky v podobě datových proudů. Jinými slovy vytvoří jeho skupiny při jejich přesunu přes zdrojové sekvence. Na rozdíl od `group` nebo `orderby` operátory, ji můžete začít vracet skupiny volajícímu před všechny pořadí čtení.

Zabezpečení vlákna je možné díky kopii každého bloku nebo skupiny jako zdrojové sekvence je provést iteraci, jak je vysvětleno v komentářích zdrojového kódu. Pokud zdrojové sekvence má velký posloupnost položek souvislé, modul common language runtime může vyvolat <xref:System.OutOfMemoryException>.

## <a name="example"></a>Příklad

Následující příklad ukazuje metodu rozšíření a klientský kód, který se používá:

[!code-csharp[cscsrefContiguousGroups#1](~/samples/snippets/csharp/concepts/linq/how-to-group-results-by-contiguous-keys_1.cs)]

Chcete-li použít metodu rozšíření ve vašem projektu, zkopírujte `MyExtensions` statická třída pro nové nebo existující zdrojový soubor kódu a je-li vyžadován, přidejte `using` direktivu pro obor názvů, ve kterém se nachází.

## <a name="see-also"></a>Viz také:

- [LINQ (Language Integrated Query)](index.md)
