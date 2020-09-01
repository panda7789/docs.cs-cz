---
description: out – klíčové slovo (obecný modifikátor) – Referenční dokumentace jazyka C#
title: out – klíčové slovo (obecný modifikátor) – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: 84f3647309c0772f6ae61d3614f8649fe277f153
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142333"
---
# <a name="out-generic-modifier-c-reference"></a>out (generický modifikátor) (Referenční dokumentace jazyka C#)

Pro parametry obecného typu `out` Určuje klíčové slovo, že parametr typu je kovariantní. Klíčové slovo lze použít `out` v obecných rozhraních a delegátech.

Kovariance umožňuje použít více odvozený typ, než který je určen obecným parametrem. To umožňuje implicitní převod tříd, které implementují kovariantní rozhraní a implicitní převod typů delegátů. Kovariance a kontravariance jsou podporovány pro typy odkazů, ale nejsou podporovány pro typy hodnot.

Rozhraní, které má parametr kovariantního typu, umožňuje jeho metodám vracet více odvozených typů než hodnoty určené parametrem typu. Například vzhledem k tomu, že v .NET Framework 4 <xref:System.Collections.Generic.IEnumerable%601> je typ T typu kovariance, můžete přiřadit objekt `IEnumerable(Of String)` typu k objektu `IEnumerable(Of Object)` typu bez použití jakýchkoli speciálních metod převodu.

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

## <a name="see-also"></a>Viz také

- [Odchylky obecných rozhraní](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [pro](in-generic-modifier.md)
- [Modifikátory](index.md)
