---
title: v (obecný modifikátor) - C# Odkaz
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: 57da13f6dc6719166b9051afeb2532ba5fbeff3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713476"
---
# <a name="in-generic-modifier-c-reference"></a>in (generický modifikátor) (Referenční dokumentace jazyka C#)

Pro parametry obecného `in` typu klíčové slovo určuje, že parametr typu je kontravariantní. Klíčové `in` slovo můžete použít v obecných rozhraních a delegátech.

Contravariance umožňuje použít méně odvozený typ, než je zadán obecný parametr. To umožňuje implicitní převod tříd, které implementují rozhraní contravariant a implicitní převod typů delegátů. Kovariance a contravariance v parametrech obecného typu jsou podporovány pro typy odkazů, ale nejsou podporovány pro typy hodnot.

Typ může být deklarován jako contravariant v obecném rozhraní nebo delegát pouze v případě, že definuje typ parametrů metody a nikoli návratový typ metody. `In`, `ref`a `out` parametry musí být invariantní, což znamená, že nejsou ani kovariantní, ani kontravariantní.

Rozhraní, které má parametr typu contravariant umožňuje jeho metody přijímat argumenty méně odvozených typů, než které jsou určeny parametrem typu rozhraní. Například v <xref:System.Collections.Generic.IComparer%601> rozhraní, typ T je contravariant, můžete `IComparer<Person>` přiřadit objekt typu `IComparer<Employee>` k objektu typu bez `Employee` použití `Person`speciálních metod převodu, pokud dědí .

Contravariantní delegát může být přiřazen jiný delegát stejného typu, ale s méně odvozené obecný typ parametru.

Další informace naleznete [v tématu Kovariance a Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="contravariant-generic-interface"></a>Kontravariantní obecné rozhraní

Následující příklad ukazuje, jak deklarovat, rozšířit a implementovat kontravariantní obecné rozhraní. Také ukazuje, jak můžete použít implicitní převod pro třídy, které implementují toto rozhraní.

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a>Kontravariantní obecný delegát

Následující příklad ukazuje, jak deklarovat, instanci a vyvolat kontravariantní obecný delegát. Také ukazuje, jak můžete implicitně převést typ delegáta.

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [ven](out-generic-modifier.md)
- [Kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md)
- [Modifikátory](index.md)
