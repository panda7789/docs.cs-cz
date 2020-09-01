---
description: let – Referenční dokumentace jazyka C#
title: let – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
f1_keywords:
- let_CSharpKeyword
- let
helpviewer_keywords:
- let keyword [C#]
- let clause [C#]
ms.assetid: 13c9c1a4-ce57-48ef-8e1b-4c2a59b99fb4
ms.openlocfilehash: 3767b9745cccd9802374a8100de19f286c9b55ea
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139590"
---
# <a name="let-clause-c-reference"></a>let – klauzule (Referenční dokumentace jazyka C#)

Ve výrazu dotazu je někdy užitečné ukládat výsledek dílčího výrazu, aby jej bylo možné použít v dalších klauzulích. Můžete to provést pomocí `let` klíčového slova, které vytvoří novou proměnnou rozsahu a inicializuje ji s výsledkem výrazu, který zadáte. Po inicializaci s hodnotou nelze proměnnou rozsahu použít k uložení jiné hodnoty. Nicméně pokud proměnná rozsahu obsahuje typ Queryable, může se dotazovat.

## <a name="example"></a>Příklad

V následujícím příkladu `let` se používá dvěma způsoby:

1. Pro vytvoření vyčíslitelného typu, který se může dotazovat sám na sebe.

2. Aby dotaz mohl volat `ToLower` pouze jednou pro proměnnou rozsahu `word` . Bez použití by bylo `let` nutné zavolat `ToLower` do každého predikátu v `where` klauzuli.

[!code-csharp[cscsrefQueryKeywords#28](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsCsrefQueryKeywords/CS/Let.cs#28)]

## <a name="see-also"></a>Viz také

- [Reference jazyka C#](../index.md)
- [Klíčová slova dotazu (LINQ)](query-keywords.md)
- [LINQ v jazyku C#](../../linq/index.md)
- [LINQ (Language Integrated Query)](../../programming-guide/concepts/linq/index.md)
- [Zpracování výjimek ve výrazech dotazů](../../linq/handle-exceptions-in-query-expressions.md)
