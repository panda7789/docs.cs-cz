---
description: in (generický modifikátor) – Referenční dokumentace jazyka C#
title: in (generický modifikátor) – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: feae17be7bdf29f6bc90e8c85b3878d4714699f4
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89118452"
---
# <a name="in-generic-modifier-c-reference"></a>in (generický modifikátor) (Referenční dokumentace jazyka C#)

Pro parametry obecného typu `in` Určuje klíčové slovo, že parametr typu je kontravariantní. Klíčové slovo lze použít `in` v obecných rozhraních a delegátech.

Kontravariance umožňuje použít méně odvozený typ, než který je určen obecným parametrem. To umožňuje implicitní převod tříd, které implementují kontravariantní rozhraní a implicitní převod typů delegátů. Kovariance a kontravariance v parametrech obecného typu jsou podporovány pro typy odkazů, ale nejsou podporovány pro typy hodnot.

Typ může být deklarovaný jako kontravariantní v obecném rozhraní nebo delegátu jenom v případě, že definuje typ parametrů metody a nikoli návratový typ metody. `In``ref`parametry, a `out` musí být invariantní, což znamená, že nejsou ani kovariantní nebo kontravariantní.

Rozhraní, které má parametr kontravariantního typu, umožňuje svým metodám přijímat argumenty méně odvozených typů než hodnoty určené parametrem typu rozhraní. Například v <xref:System.Collections.Generic.IComparer%601> rozhraní typ T je kontravariantní, můžete přiřadit objekt `IComparer<Person>` typu k objektu `IComparer<Employee>` typu bez použití jakýchkoli speciálních metod převodu, pokud `Employee` zdědí `Person` .

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

## <a name="see-also"></a>Viz také

- [mimo](out-generic-modifier.md)
- [Kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md)
- [Modifikátory](index.md)
