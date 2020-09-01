---
description: var – reference jazyka C#
title: var – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: 303a880a54a79e50515060e0ea28e8d021fa1b76
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141709"
---
# <a name="var-c-reference"></a>var (Referenční dokumentace jazyka C#)

Počínaje jazykem Visual C# 3,0 proměnné, které jsou deklarovány v oboru metody, mohou mít implicitní "typ" `var` . Implicitní typ lokální proměnné je silného typu, jako by byl typ deklarovaný sami, ale kompilátor určí typ. Následující dvě deklarace `i` jsou funkčně ekvivalentní:

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

Další informace naleznete v tématu [implicitně typované lokální proměnné](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) a [vztahy typů v operacích dotazu LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).

> [!IMPORTANT]
> Při `var` použití s povolenými typy odkazů s možnou hodnotou null vždy implikuje typ odkazu s možnou hodnotou null i v případě, že typ výrazu nemá hodnotu null.

## <a name="example"></a>Příklad

Následující příklad ukazuje dva výrazy dotazu. V prvním výrazu je použití `var` povoleno, ale není vyžadováno, protože typ výsledku dotazu lze explicitně uvést jako `IEnumerable<string>` . Ve druhém výrazu však může `var` být výsledkem kolekce anonymních typů a název tohoto typu není přístupný s výjimkou samotného kompilátoru. Použití `var` eliminuje požadavek na vytvoření nové třídy pro výsledek. Všimněte si, že v příkladu #2 `foreach` musí být proměnná iterace `item` také implicitně typu.

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Průvodce programováním v C#](../../programming-guide/index.md)
- [Implicitně typované lokální proměnné](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
