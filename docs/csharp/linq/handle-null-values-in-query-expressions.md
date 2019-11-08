---
title: Zpracování hodnot null ve výrazech dotazů (LINQ C#in)
description: Naučte se zpracovávat hodnoty null ve výrazech dotazů LINQ C#v.
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: c9a3aaec05fa029a8db66826bdcb4a1d106176e3
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736857"
---
# <a name="handle-null-values-in-query-expressions"></a>Zpracování hodnot Null ve výrazech dotazů

Tento příklad ukazuje, jak zpracovat možné hodnoty null ve zdrojových kolekcích. Kolekce objektů, jako je například <xref:System.Collections.Generic.IEnumerable%601> může obsahovat elementy, jejichž hodnota je [null](../language-reference/keywords/null.md). Pokud zdrojová kolekce má hodnotu null nebo obsahuje element, jehož hodnota je null, a dotaz nezpracovává hodnoty null, bude při spuštění dotazu vyvolána <xref:System.NullReferenceException>.

## <a name="example"></a>Příklad

Můžete kódovat defensively, aby se předešlo výjimce odkazu s hodnotou null, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

Klauzule `where` v předchozím příkladu vyfiltruje všechny prvky null v pořadí kategorií. Tato technika je nezávislá na vrácení hodnoty null v klauzuli JOIN. Podmíněný výraz s hodnotou null v tomto příkladu funguje, protože `Products.CategoryID` je typu `int?`, který je zkrácený pro `Nullable<int>`.

## <a name="example"></a>Příklad

Pokud je v klauzuli JOIN pouze jeden z porovnávacích klíčů, lze typ hodnoty s možnou hodnotou null přetypovat na typ s možnou hodnotou null ve výrazu dotazu. V následujícím příkladu Předpokládejme, že `EmployeeID` je sloupec, který obsahuje hodnoty typu `int?`:

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a>Viz také:

- <xref:System.Nullable%601>
- [LINQ (Language Integrated Query)](index.md)
- [Typy hodnot s možnou hodnotou null](../language-reference/builtin-types/nullable-value-types.md)
