---
title: Vnořené typy – Průvodce programováním v C#
description: Typ definovaný v rámci třídy, struktury nebo rozhraní se nazývá vnořený typ v jazyce C#.
ms.date: 02/08/2020
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 9e1c6c1e8b22b5447d43915ab02984aa13146301
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864940"
---
# <a name="nested-types-c-programming-guide"></a>Vnořené typy (Průvodce programováním v C#)

Typ definovaný v rámci [třídy](../../language-reference/keywords/class.md), [struktury](../../language-reference/builtin-types/struct.md)nebo [rozhraní](../../language-reference/keywords/interface.md) se nazývá vnořený typ. Například

[!code-csharp[DeclareNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedClass)]

Bez ohledu na to, zda je vnější typ třída, rozhraní nebo struktura, jsou vnořené typy standardně [soukromé](../../language-reference/keywords/private.md); jsou přístupné pouze z jejich nadřazeného typu. V předchozím příkladu `Nested` je třída nepřístupná externím typům.

Můžete také zadat [modifikátor přístupu](../../language-reference/keywords/access-modifiers.md) pro definování přístupnosti vnořeného typu, a to následujícím způsobem:

- Vnořené typy **třídy** můžou být [veřejné](../../language-reference/keywords/public.md), [chráněné](../../language-reference/keywords/protected.md), [interní](../../language-reference/keywords/internal.md), [chráněné interní](../../language-reference/keywords/protected-internal.md), [privátní](../../language-reference/keywords/private.md) nebo [privátní](../../language-reference/keywords/private-protected.md).

   Nicméně definování `protected` `protected internal` nebo `private protected` vnořená třída v [zapečetěné třídě](../../language-reference/keywords/sealed.md) vygeneruje upozornění kompilátoru [CS0628](../../misc/cs0628.md), v zapečetěné třídě je deklarovaný nový chráněný člen.
  
- Vnořené typy **struktury** můžou být [veřejné](../../language-reference/keywords/public.md), [interní](../../language-reference/keywords/internal.md)nebo [soukromé](../../language-reference/keywords/private.md).

Následující příklad nastaví třídu jako `Nested` veřejnou:

[!code-csharp[PublicNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#PublicNestedClass)]

Vnořený nebo vnitřní typ může přistupovat k typu, který obsahuje, nebo vnějšímu typu. Chcete-li získat přístup k nadřazenému typu, předejte jej jako argument konstruktoru vnořeného typu. Příklad:

[!code-csharp[DeclareNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedInstance)]

Vnořený typ má přístup ke všem členům, kteří mají přístup k jeho nadřazenému typu. Má přístup k soukromým a chráněným členům nadřazeného typu, včetně všech zděděných chráněných členů.

V předchozí deklaraci je úplný název třídy `Nested` `Container.Nested` . Toto je název, který se používá k vytvoření nové instance vnořené třídy následujícím způsobem:

[!code-csharp[UseNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#UseNestedInstance)]

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Třídy a struktury](./index.md)
- [Modifikátory přístupu](./access-modifiers.md)
- [Konstruktory](./constructors.md)
