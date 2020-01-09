---
title: in (generický modifikátor) – C# referenční informace
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: 57da13f6dc6719166b9051afeb2532ba5fbeff3a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713476"
---
# <a name="in-generic-modifier-c-reference"></a>in (generický modifikátor) (Referenční dokumentace jazyka C#)

Pro parametry obecného typu Určuje klíčové slovo `in`, že parametr typu je kontravariantní. Klíčové slovo `in` lze použít v obecných rozhraních a delegátech.

Kontravariance umožňuje použít méně odvozený typ, než který je určen obecným parametrem. To umožňuje implicitní převod tříd, které implementují kontravariantní rozhraní a implicitní převod typů delegátů. Kovariance a kontravariance v parametrech obecného typu jsou podporovány pro typy odkazů, ale nejsou podporovány pro typy hodnot.

Typ může být deklarovaný jako kontravariantní v obecném rozhraní nebo delegátu jenom v případě, že definuje typ parametrů metody a nikoli návratový typ metody. parametry `In`, `ref`a `out` musí být invariantní, což znamená, že nejsou ani kovariantní ani kontravariantní.

Rozhraní, které má parametr kontravariantního typu, umožňuje svým metodám přijímat argumenty méně odvozených typů než hodnoty určené parametrem typu rozhraní. Například v rozhraní <xref:System.Collections.Generic.IComparer%601> typ T je kontravariantní, můžete přiřadit objekt `IComparer<Person>` typu objektu `IComparer<Employee>`ho typu bez použití jakýchkoli speciálních metod převodu, pokud `Employee` dědí `Person`.

Kontravariantnímu delegátu lze přiřadit jiný delegát stejného typu, ale s menším odvozeným parametrem obecného typu.

Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="contravariant-generic-interface"></a>Kontravariantní obecné rozhraní

Následující příklad ukazuje, jak deklarovat, rozšiřuje a implementovat kontravariantní obecné rozhraní. Také ukazuje, jak lze použít implicitní převod pro třídy, které implementují toto rozhraní.

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a>Kontravariantní obecný delegát

Následující příklad ukazuje, jak deklarovat, vytvářet instance a vyvolat kontravariantního obecného delegáta. Také ukazuje, jak lze implicitně převést typ delegáta.

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [out](out-generic-modifier.md)
- [Kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md)
- [Modifikátory](index.md)
