---
title: out klíčové slovo (obecný modifikátor) - C# Reference
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: 97ddae2efe55be89840f7a483c18d61259020283
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713291"
---
# <a name="out-generic-modifier-c-reference"></a>out (obecný modifikátor) (Odkaz Jazyka C#)

Pro parametry obecného `out` typu klíčové slovo určuje, že parametr typu je kovariantní. Klíčové `out` slovo můžete použít v obecných rozhraních a delegátech.

Kovariance umožňuje použít více odvozený typ, než je určen obecný parametr. To umožňuje implicitní převod tříd, které implementují kovariantní rozhraní a implicitní převod typů delegátů. Kovariance a contravariance jsou podporovány pro typy odkazů, ale nejsou podporovány pro typy hodnot.

Rozhraní, které má parametr kovariantního typu, umožňuje jeho metodám vrátit více odvozených typů, než jaké jsou určeny parametrem typu. Například protože v rozhraní .NET <xref:System.Collections.Generic.IEnumerable%601>Framework 4 je typ T v aplikaci kovariantní, můžete objekt `IEnumerable(Of String)` typu přiřadit objektu `IEnumerable(Of Object)` typu bez použití speciálních metod převodu.

Kovariantní delegát může být přiřazen jiný delegát stejného typu, ale s více odvozené obecný typ parametru.

Další informace naleznete [v tématu Kovariance a Contravariance](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="example---covariant-generic-interface"></a>Příklad - kovariantní obecné rozhraní

Následující příklad ukazuje, jak deklarovat, rozšířit a implementovat kovariantní obecné rozhraní. Také ukazuje, jak použít implicitní převod pro třídy, které implementují kovariantní rozhraní.

[!code-csharp[csVarianceKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#3)]

V obecném rozhraní může být parametr typu deklarován jako kovariantní, pokud splňuje následující podmínky:

- Parametr type se používá pouze jako návratový typ metod rozhraní a není použit jako typ argumentů metody.

    > [!NOTE]
    > Existuje jedna výjimka z tohoto pravidla. Pokud v kovariantní rozhraní máte kontravariantní obecný delegát jako parametr metody, můžete použít kovariantní typ jako parametr obecného typu pro tohoto delegáta. Další informace o kovariantních a kontravariantních obecných delegátech naleznete [v tématu Odchylka v delegátech](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [Použití odchylky pro obecné delegáty aplikace Func a Obecné akce](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

- Parametr type se nepoužívá jako obecné omezení pro metody rozhraní.

## <a name="example---covariant-generic-delegate"></a>Příklad - kovariantní obecný delegát

Následující příklad ukazuje, jak deklarovat, instanci a vyvolat kovariantní obecný delegát. Také ukazuje, jak implicitně převést typy delegátů.

[!code-csharp[csVarianceKeywords#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#4)]

V obecné delegáta typ lze deklarovat kovariantní, pokud se používá pouze jako metoda návratový typ a není použit pro argumenty metody.

## <a name="c-language-specification"></a>specifikace jazyka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Viz také

- [Odchylky obecných rozhraní](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [In](in-generic-modifier.md)
- [Modifikátory](index.md)
