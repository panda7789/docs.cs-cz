---
title: () – operátor - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 656a1ca7a992df43ff857d2c4ecb62b044f7e06f
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333275"
---
# <a name="-operator-c-reference"></a>() – operátor (C# odkaz)

Kromě používá k určení pořadí operací ve výrazu závorky slouží k provádění následujících úloh:

1. Zadejte přetypování a převody typů.

    [!code-csharp[csRefOperators#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#1)]

2. Vyvolání metod a delegátů.

    [!code-csharp[csRefOperators#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#2)]

## <a name="remarks"></a>Poznámky

Přetypování vyvolá explicitní operátor převodu z jednoho typu na jiný; přetypování selže, pokud není definován žádný převod operátor. Chcete-li definice operátora převodu, přečtěte si téma [explicitní](../keywords/explicit.md) a [implicitní](../keywords/implicit.md).

 `()` Operátor nelze přetížit.

 Další informace najdete v tématu [přetypování a převody typů](../../programming-guide/types/casting-and-type-conversions.md).

 Další informace o volání metody, naleznete v tématu [metody](../../programming-guide/classes-and-structs/methods.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Operátory jazyka C#](index.md)