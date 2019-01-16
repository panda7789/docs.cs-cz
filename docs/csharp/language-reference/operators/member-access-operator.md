---
title: . Operator - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: a59f69d0349a054c8c2a5b701b8f63df113a6580
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333717"
---
# <a name="-operator-c-reference"></a>. operator (Referenční dokumentace jazyka C#)

Tečka – operátor (`.`) se používá pro přístup ke členu. Operátor tečky Určuje typ nebo obor názvů. Například operátor tečky slouží k přístupu k určité metody v rámci knihovny tříd rozhraní .NET Framework:

[!code-csharp[csRefOperators#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#16)]

Představte si třeba následující třídy:

[!code-csharp[csRefOperators#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#17)]

[!code-csharp[csRefOperators#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#18)]

Proměnná `s` se dvěma členy `a` a `b`; pokud ho chcete přistupovat k nim, použijte operátor tečky:

[!code-csharp[csRefOperators#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#19)]

Tečka slouží také k vytvoření kvalifikované názvy, které jsou názvy, které určují obor názvů nebo rozhraní, například, ke kterému patří.

[!code-csharp[csRefOperators#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#20)]

Using – direktiva provádí některé kvalifikace názvu volitelné:

[!code-csharp[csRefOperators#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#21)]

Ale pokud identifikátor je dvojznačný, musí být kvalifikován:

[!code-csharp[csRefOperators#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#22)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)