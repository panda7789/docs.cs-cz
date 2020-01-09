---
title: var- C# reference
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: ff8348a725f43fa8789c73fa58549da26126369c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712881"
---
# <a name="var-c-reference"></a>var (Referenční dokumentace jazyka C#)

Počínaje jazykem Visual C# 3,0 proměnné, které jsou deklarovány v oboru metody, mohou mít implicitní typ "type" `var`. Implicitní typ lokální proměnné je silného typu, jako by byl typ deklarovaný sami, ale kompilátor určí typ. Následující dvě deklarace `i` jsou funkčně ekvivalentní:

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

Další informace naleznete v tématu [implicitně typované lokální proměnné](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) a [vztahy typů v operacích dotazu LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje dva výrazy dotazu. V prvním výrazu je použití `var` povoleno, ale není vyžadováno, protože typ výsledku dotazu lze explicitně uvést jako `IEnumerable<string>`. Ve druhém výrazu ale `var` umožňuje, aby byl výsledek kolekcí anonymních typů, a název tohoto typu není přístupný s výjimkou samotného kompilátoru. Použití `var` eliminuje požadavek na vytvoření nové třídy pro výsledek. Všimněte si, že v příkladu #2 musí být také implicitně typované proměnné `foreach` iterace `item`.

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a>Viz také:

- [C#Odkaz](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Implicitně typované lokální proměnné](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
