---
title: in (generický modifikátor) - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: f736540a37d3226bccfc07749dcf06ca018663e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661461"
---
# <a name="in-generic-modifier-c-reference"></a>in (generický modifikátor) (Referenční dokumentace jazyka C#)

Pro parametry obecného typu `in` – klíčové slovo určuje, že parametr typu je kontravariant. Můžete použít `in` – klíčové slovo v obecných rozhraních a delegátech.

Kontravariance umožňuje použít méně odvozený typ, než je určeno obecný parametr. To umožňuje implicitní převod z třídy, které implementují rozhraní kontravariantní a implicitní převod delegujících typů. Kovariance a kontravariance v parametrech obecného typu jsou podporovány pro typy odkazů, ale nejsou podporovány pro typy hodnot.

Typ mohou být deklarovány kontravariantní v obecné rozhraní nebo delegát pouze v případě, že definuje typ parametrů, metody a ne návratový typ metody. `In`, `ref`, a `out` parametry musí být neutrální, to znamená jsou ani kovariantní nebo kontravariantní.

Rozhraní, která má parametr kontravariantního typu umožňuje její metody pro přijímání argumentů méně odvozené typy než je zadáno parametrem typu rozhraní. Například v <xref:System.Collections.Generic.IComparer%601> rozhraní, typ T je kontravariantní, můžete přiřadit objektu `IComparer<Person>` typu na objekt `IComparer<Employee>` typ bez použití jakékoli speciální převod metody, pokud `Employee` dědí `Person`.

Kontravariantní delegát může být přiřazen jiný delegát stejného typu, ale s méně odvozený parametr obecného typu.

Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="contravariant-generic-interface"></a>Kontravariantní obecné rozhraní

Následující příklad ukazuje, jak deklarovat, rozšíření a implementovat obecné rozhraní kontravariantní. Také ukazuje, jak můžete použít implicitní převod pro třídy, které toto rozhraní implementují.

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a>Kontravariantní obecného delegáta

Následující příklad ukazuje, jak deklarovat, vytváření instancí a vyvolání obecného delegátu kontravariantní. Profil také ukazuje, jak lze implicitně převést typ delegáta.

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [out](out-generic-modifier.md)
- [Kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md)
- [Modifikátory](modifiers.md)
