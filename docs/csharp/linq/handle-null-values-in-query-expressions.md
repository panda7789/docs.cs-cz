---
title: Zpracování hodnot null ve výrazech dotazů (LINQ v JAZYKU C#)
description: Zjistěte, jak zpracování hodnot null ve výrazech dotazů LINQ v jazyce C#.
ms.date: 12/1/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: 2c477ef371dbb424c72fb9d34948760b7e3f5609
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43561376"
---
# <a name="handle-null-values-in-query-expressions"></a>Zpracování hodnot null ve výrazech dotazů

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
