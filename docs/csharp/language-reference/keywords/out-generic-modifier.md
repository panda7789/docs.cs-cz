---
title: out – klíčové slovo (obecný modifikátor C# ) – Referenční dokumentace
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: 121faf46f1c5ba50f132dc180e9d4f802ac91696
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422661"
---
# <a name="out-generic-modifier-c-reference"></a>out (generický modifikátor) (C# Referenční dokumentace)

Pro parametry obecného typu Určuje klíčové slovo `out`, že parametr typu je kovariantní. Klíčové slovo `out` lze použít v obecných rozhraních a delegátech.

Kovariance umožňuje použít více odvozený typ, než který je určen obecným parametrem. To umožňuje implicitní převod tříd, které implementují kovariantní rozhraní a implicitní převod typů delegátů. Kovariance a kontravariance jsou podporovány pro typy odkazů, ale nejsou podporovány pro typy hodnot.

Rozhraní, které má parametr kovariantního typu, umožňuje jeho metodám vracet více odvozených typů než hodnoty určené parametrem typu. Například vzhledem k tomu, že v .NET Framework 4 v <xref:System.Collections.Generic.IEnumerable%601>typ T je kovariantní, můžete přiřadit objekt `IEnumerable(Of String)`ho typu k objektu `IEnumerable(Of Object)` typu bez použití jakýchkoli speciálních metod převodu.

Spoluvariantnímu delegátu se dá přiřadit jiný delegát stejného typu, ale s více odvozeným parametrem obecného typu.

Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="example---covariant-generic-interface"></a>Příklad: kovariantní obecné rozhraní

Následující příklad ukazuje, jak deklarovat, rozšiřuje a implementovat kovariantní obecné rozhraní. Také ukazuje, jak použít implicitní převod pro třídy, které implementují kovariantní rozhraní.

[!code-csharp[csVarianceKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#3)]

V obecném rozhraní může být parametr typu deklarován kovariantou, pokud splňuje následující podmínky:

- Parametr typu se používá jenom jako návratový typ metod rozhraní a nepoužívá se jako typ argumentů metody.

    > [!NOTE]
    > Toto pravidlo obsahuje jednu výjimku. Pokud v kovariantovém rozhraní máte kontravariantního obecného delegáta jako parametr metody, můžete použít kovariantní typ jako parametr obecného typu pro tohoto delegáta. Další informace o kovariantních a kontravariantních obecných delegátech naleznete v tématu [Variance v delegátech](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [použití variance pro obecné delegáty Func a Action](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

- Parametr typu se nepoužívá jako obecné omezení pro metody rozhraní.

## <a name="example---covariant-generic-delegate"></a>Příklad – kovariance obecného delegáta

Následující příklad ukazuje, jak deklarovat, vytvářet instance a vyvolat kovariantní obecný delegát. Také ukazuje, jak implicitně převést typy delegátů.

[!code-csharp[csVarianceKeywords#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#4)]

V obecném delegátu může být typ deklarovaný jako kovariant, pokud se používá jenom jako návratový typ metody a nepoužívá se pro argumenty metody.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také:

- [Odchylky obecných rozhraní](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [in](in-generic-modifier.md)
- [Modifikátory](index.md)
