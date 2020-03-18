---
title: let klauzule - C# Reference
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 3ce2b663e5678de6b53db610b489f85ab1427b9d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173585"
---
# <a name="let-clause-c-reference"></a>let – klauzule (Referenční dokumentace jazyka C#)

Ve výrazu dotazu je někdy užitečné uložit výsledek dílčího výrazu, aby bylo možné jej použít v následujících klauzulích. Můžete to provést `let` pomocí klíčového slova, které vytvoří novou proměnnou rozsahu a inicializuje ji s výsledkem výrazu, který zadáte. Po inicializování s hodnotou nelze proměnnou rozsahu použít k uložení jiné hodnoty. Pokud však proměnná rozsahu obsahuje dotazovatelný typ, může být dotazován.

## <a name="example"></a>Příklad

V následujícím `let` příkladu se používá dvěma způsoby:

1. Chcete-li vytvořit výčet typu, který může být sám dotazován.

2. Chcete-li povolit `ToLower` dotaz volat pouze `word`jednou na proměnné rozsahu . Bez `let`použití , budete `ToLower` muset volat v každém `where` predikátu v klauzuli.

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a>Viz také

- [Odkaz jazyka C#](../../language-reference/index.md)
- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [LINQ v jazyce C#](../../linq/index.md)
- [LINQ (Language Integrated Query)](../../programming-guide/concepts/linq/index.md)
- [Zpracování výjimek ve výrazech dotazů](../../linq/handle-exceptions-in-query-expressions.md)
