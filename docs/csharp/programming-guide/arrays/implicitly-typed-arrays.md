---
title: Implicitně zadaný pole – průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], implicitly-typed
- implicitly-typed arrays [C#]
- C# language, implicitly typed arrays
ms.assetid: e05be95c-6732-403d-ae42-b35f057cbbea
ms.openlocfilehash: 943760af30422cd333fdff65cdf678108c9d9564
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705714"
---
# <a name="implicitly-typed-arrays-c-programming-guide"></a>Implicitně typovaná pole (Průvodce programováním v C#)

Můžete vytvořit implicitně zadané pole, ve kterém je typ instance pole odvozen z prvků určených v inicializátoru pole. Pravidla pro všechny implicitně zadané proměnné platí také pro implicitně zadaných polí. Další informace naleznete [v tématu Implicitně zadané místní proměnné](../classes-and-structs/implicitly-typed-local-variables.md).

Implicitně zadávaná pole se obvykle používají ve výrazech dotazu spolu s anonymními typy a inicializátory objektů a kolekcí.

Následující příklady ukazují, jak vytvořit implicitně zadané pole:

[!code-csharp[csProgGuideLINQ#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#37)]

V předchozím příkladu všimněte si, že s implicitně zadanými poli se na levé straně inicializačního příkazu nepoužívají žádné hranaté závorky. Všimněte si také, že zubaté pole jsou inicializovány pomocí `new []` stejně jako jednorozměrné pole.

## <a name="implicitly-typed-arrays-in-object-initializers"></a>Implicitně zadaný pole v inicializátorech objektů

Při vytváření anonymnítyp, který obsahuje pole, musí být pole implicitně zadáno do inicializátoru objektu. V následujícím příkladu `contacts` je implicitně zadané pole anonymních typů, z `PhoneNumbers`nichž každý obsahuje pole s názvem . Všimněte `var` si, že klíčové slovo se nepoužívá uvnitř inicializátory objektu.

[!code-csharp[csProgGuideLINQ#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#38)]

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Implicitně typované lokální proměnné](../classes-and-structs/implicitly-typed-local-variables.md)
- [Pole](./index.md)
- [Anonymní typy](../classes-and-structs/anonymous-types.md)
- [Inicializátory objektu a kolekce](../classes-and-structs/object-and-collection-initializers.md)
- [Var](../../language-reference/keywords/var.md)
- [LINQ v jazyce C#](../../linq/index.md)
