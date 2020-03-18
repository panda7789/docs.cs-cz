---
title: Vnořené typy – programovací příručka jazyka C#
ms.date: 02/08/2020
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 12e44ccc1254424c152a238c8390f133550fa54c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626487"
---
# <a name="nested-types-c-programming-guide"></a>Vnořené typy (Průvodce programováním v C#)

Typ definovaný v rámci [třídy](../../language-reference/keywords/class.md), [struktury](../../language-reference/builtin-types/struct.md)nebo [rozhraní](../../language-reference/keywords/interface.md) se nazývá vnořený typ. Například

[!code-csharp[DeclareNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedClass)]

Bez ohledu na to, zda vnější typ je třída, rozhraní nebo struktura, vnořené typy výchozí [private](../../language-reference/keywords/private.md); jsou přístupné pouze z jejich obsahujícího typu. V předchozím příkladu `Nested` je třída nepřístupná pro externí typy.

Můžete také určit [modifikátor přístupu](../../language-reference/keywords/access-modifiers.md) k definování přístupnosti vnořeného typu následujícím způsobem:

- Vnořené typy **třídy** mohou být [veřejné](../../language-reference/keywords/public.md), [chráněné](../../language-reference/keywords/protected.md), [interní](../../language-reference/keywords/internal.md), [chráněné interní](../../language-reference/keywords/protected-internal.md), [soukromé](../../language-reference/keywords/private.md) nebo [soukromé chráněné](../../language-reference/keywords/private-protected.md).

   `protected`Definování třídy nebo `protected internal` `private protected` vnořené třídy uvnitř [zapečetěné třídy](../../language-reference/keywords/sealed.md) však generuje upozornění kompilátoru [CS0628](../../misc/cs0628.md), "nový chráněný člen deklarovaný v zapečetěné třídě".
  
- Vnořené typy **struktury** mohou být [veřejné](../../language-reference/keywords/public.md), [interní](../../language-reference/keywords/internal.md)nebo [soukromé](../../language-reference/keywords/private.md).

Následující příklad zpřístupňuje třídu: `Nested`

[!code-csharp[PublicNestedClass](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#PublicNestedClass)]

Vnořený nebo vnitřní, typ může přistupovat k obsahující nebo vnější, typ. Chcete-li získat přístup k obsahujícímu typu, předajte jej jako argument konstruktoru vnořeného typu. Například:

[!code-csharp[DeclareNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#DeclareNestedInstance)]

Vnořený typ má přístup ke všem členům, které jsou přístupné pro jeho obsahující typ. Může přistupovat k soukromým a chráněným členům obsahujícího typu, včetně všech zděděných chráněných členů.

V předchozím prohlášení je `Nested` `Container.Nested`úplný název třídy . Toto je název použitý k vytvoření nové instance vnořené třídy takto:

[!code-csharp[UseNestedInstance](~/samples/snippets/csharp/objectoriented/nestedtypes.cs#UseNestedInstance)]

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Třídy a struky](./index.md)
- [Modifikátory přístupu](./access-modifiers.md)
- [Konstruktory](./constructors.md)
