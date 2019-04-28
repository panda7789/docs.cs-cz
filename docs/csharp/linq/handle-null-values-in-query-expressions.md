---
title: Zpracování hodnot null ve výrazech dotazů (LINQ v JAZYKU C#)
description: Zjistěte, jak zpracování hodnot null ve výrazech dotazů LINQ v jazyce C#.
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: 14609aee2bbd1fbb487589bb41683a1f3cad1362
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61659888"
---
# <a name="handle-null-values-in-query-expressions"></a>Zpracování hodnot Null ve výrazech dotazů

Tento příklad ukazuje, jak zpracování možných hodnot null ve zdrojové kolekce. Kolekci objektů, jako <xref:System.Collections.Generic.IEnumerable%601> může obsahovat elementy, jejichž hodnota je [null](../language-reference/keywords/null.md). Pokud zdrojová kolekce má hodnotu null nebo obsahuje prvek, jehož hodnota je null a dotaz ke zpracování hodnot null <xref:System.NullReferenceException> bude vyvolána výjimka při spouštění dotazu.

## <a name="example"></a>Příklad

Vám umožní kódování defenzivně, aby výjimka nulového odkazu, jak je znázorněno v následujícím příkladu:

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

V předchozím příkladu `where` klauzule vyfiltruje všechny prázdné prvky v sekvenci kategorií. Tato technika je nezávislé na kontrolu hodnot null v klauzuli join. Podmíněný výraz s hodnotou null v tomto příkladu funguje, protože `Products.CategoryID` je typu `int?` což je zkratka pro `Nullable<int>`.

## <a name="example"></a>Příklad

V klauzuli join Pokud pouze jeden z klíčů porovnání je typ s možnou hodnotou Null, můžete přetypovat jiné na typ připouštějící hodnotu Null ve výrazu dotazu. V následujícím příkladu se předpokládá, že `EmployeeID` je sloupec, který obsahuje hodnoty typu `int?`:

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a>Viz také:

- <xref:System.Nullable%601>
- [LINQ (Language Integrated Query)](index.md)
- [Typy s možnou hodnotou Null](../programming-guide/nullable-types/index.md)
