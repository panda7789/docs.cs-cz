---
title: Implicitně typované pole – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 36ca18adc392643107b43a947656846f3b94a2eb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69597340"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a>Implicitně typovaná pole (Průvodce programováním v C#)

Můžete vytvořit implicitně typované pole, ve kterém je typ instance pole odvozen z prvků zadaných v inicializátoru pole. Pravidla pro všechny implicitně typované proměnné platí také pro implicitně typované pole. Další informace naleznete v tématu [implicitně typované lokální proměnné](../classes-and-structs/implicitly-typed-local-variables.md).

Implicitně typované pole se obvykle používají ve výrazech dotazů společně s anonymními typy a Inicializátory objektů a kolekcí.

Následující příklady ukazují, jak vytvořit implicitně typované pole:

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

V předchozím příkladu si všimněte, že s implicitně typovými poli nejsou na levé straně příkazu Initialization použity žádné hranaté závorky. Všimněte si také, že vícenásobná pole jsou inicializována pomocí `new []` stejně jako pole s jednou dimenzí.

## <a name="implicitly-typed-arrays-in-object-initializers"></a>Implicitně typované pole v inicializátorech objektů

Při vytváření anonymního typu, který obsahuje pole, musí být pole implicitně zadáno v inicializátoru objektu typu. V následujícím příkladu `contacts` je implicitně typované pole anonymních typů, z nichž každý obsahuje pole s názvem `PhoneNumbers`. Všimněte si, `var` že klíčové slovo se v inicializátorech objektů nepoužívá.

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Implicitně typované lokální proměnné](../classes-and-structs/implicitly-typed-local-variables.md)
- [Pole](./index.md)
- [Anonymní typy](../classes-and-structs/anonymous-types.md)
- [Inicializátory objektu a kolekce](../classes-and-structs/object-and-collection-initializers.md)
- [var](../../language-reference/keywords/var.md)
- [Výrazy dotazů LINQ](../linq-query-expressions/index.md)
