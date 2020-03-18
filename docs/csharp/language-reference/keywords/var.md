---
title: var - C# Odkaz
ms.date: 07/20/2015
f1_keywords:
- var
- var_CSharpKeyword
helpviewer_keywords:
- var keyword [C#]
ms.assetid: 0777850a-2691-4e3e-927f-0c850f5efe15
ms.openlocfilehash: ff8348a725f43fa8789c73fa58549da26126369c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712881"
---
# <a name="var-c-reference"></a>var (Referenční dokumentace jazyka C#)

Počínaje Visual C# 3.0 proměnné, které jsou deklarovány v `var`oboru metody může mít implicitní "typ" . Implicitně zadaný místní proměnná je silně zadaný, stejně jako kdybyste deklarovali typ sami, ale kompilátor určuje typ. Následující dvě prohlášení `i` jsou funkčně rovnocenná:

```csharp
var i = 10; // Implicitly typed.
int i = 10; // Explicitly typed.
```

Další informace naleznete [v tématu Implicitně zadané místní proměnné](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md) a vztahy typu v [operacích dotazů LINQ](../../programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).

## <a name="example"></a>Příklad

Následující příklad ukazuje dva výrazy dotazu. V prvním výrazu `var` je použití povoleno, ale není vyžadováno, protože typ výsledku `IEnumerable<string>`dotazu lze explicitně uvést jako . Však ve druhém `var` výrazu umožňuje výsledek je kolekce anonymní chod a název tohoto typu není přístupný s výjimkou kompilátoru samotného. Použití `var` eliminuje požadavek na vytvoření nové třídy pro výsledek. Všimněte si, že `foreach` v `item` příkladu #2 musí být implicitně zadána také proměnná iterace.

[!code-csharp[csrefKeywordsTypes#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#18)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../index.md)
- [Programovací příručka jazyka C#](../../programming-guide/index.md)
- [Implicitně typované lokální proměnné](../../programming-guide/classes-and-structs/implicitly-typed-local-variables.md)
