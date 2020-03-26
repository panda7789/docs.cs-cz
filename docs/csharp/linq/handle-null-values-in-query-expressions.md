---
title: Zpracování nulových hodnot ve výrazech dotazu (LINQ v c#)
description: Zjistěte, jak zpracovat hodnoty null ve výrazech dotazu LINQ v c#.
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: 3da490b72bd518df7be8c14b34655af8c6f84929
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249302"
---
# <a name="handle-null-values-in-query-expressions"></a>Zpracování hodnot Null ve výrazech dotazů

Tento příklad ukazuje, jak zpracovat možné hodnoty null ve zdrojových kolekcích. Kolekce objektů, jako <xref:System.Collections.Generic.IEnumerable%601> je například může obsahovat prvky, jejichž hodnota je [null](../language-reference/keywords/null.md). Pokud zdrojkolekce je null nebo obsahuje prvek, jehož hodnota je null <xref:System.NullReferenceException> a dotaz nezpracovává hodnoty null, bude vyvolána při spuštění dotazu.

## <a name="example"></a>Příklad

Můžete kód defenzivně, aby se zabránilo výjimku nulového odkazu, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

V předchozím příkladu `where` klauzule filtruje všechny prvky null v pořadí kategorií. Tato technika je nezávislá na nulové kontrole v klauzuli join. Podmíněný výraz s hodnotou null `Products.CategoryID` v `int?` tomto příkladu `Nullable<int>`funguje, protože je typu, který je zkratka pro .

## <a name="example"></a>Příklad

V join klauzuli, pokud pouze jeden z porovnávacích klíčů je typ hodnoty s možnou hodnotou s hodnotou, můžete přetypovat druhý na typ hodnoty s hodnotou null ve výrazu dotazu. V následujícím příkladu `EmployeeID` předpokládejme, že se `int?`jedná o sloupec, který obsahuje hodnoty typu :

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a>Viz také

- <xref:System.Nullable%601>
- [LINQ (Language Integrated Query)](index.md)
- [Typy hodnot s možnou hodnotou s hodnotou Null](../language-reference/builtin-types/nullable-value-types.md)
