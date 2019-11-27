---
title: Out (generický modifikátor)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
ms.openlocfilehash: 0460015b44971fa638dba47183690ffcc89ca55f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351425"
---
# <a name="out-generic-modifier-visual-basic"></a>Out (generický modifikátor) (Visual Basic)

Pro parametry obecného typu Určuje klíčové slovo `Out`, že typ je kovariantní.

## <a name="remarks"></a>Poznámky

Kovariance umožňuje použít více odvozený typ, než který je určen obecným parametrem. To umožňuje implicitní převod tříd, které implementují rozhraní variant a implicitní převod typů delegátů.

Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="rules"></a>Pravidla

Klíčové slovo `Out` lze použít v obecných rozhraních a delegátech.

V obecném rozhraní může být parametr typu deklarován kovariantou, pokud splňuje následující podmínky:

- Parametr typu se používá jenom jako návratový typ metod rozhraní a nepoužívá se jako typ argumentů metody.

    > [!NOTE]
    > Toto pravidlo obsahuje jednu výjimku. Pokud v kovariantovém rozhraní máte kontravariantního obecného delegáta jako parametr metody, můžete použít kovariantní typ jako parametr obecného typu pro tohoto delegáta. Další informace o kovariantních a kontravariantních obecných delegátech naleznete v tématu [Variance v delegátech](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [použití variance pro obecné delegáty Func a Action](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

- Parametr typu se nepoužívá jako obecné omezení pro metody rozhraní.

V obecném delegátu může být parametr typu deklarován kovariantou, pokud je použit pouze jako návratový typ metody a nepoužívá se pro argumenty metody.

Kovariance a kontravariance jsou podporovány pro typy odkazů, ale nejsou podporovány pro typy hodnot.

V Visual Basic nemůžete deklarovat události v kovariantních rozhraních bez určení typu delegáta. I kovariantní rozhraní nemohou mít vnořené třídy, výčty ani struktury, ale mohou mít vnořená rozhraní.

## <a name="behavior"></a>Chování

Rozhraní, které má parametr kovariantního typu, umožňuje jeho metodám vracet více odvozených typů než hodnoty určené parametrem typu. Například vzhledem k tomu, že v .NET Framework 4 v <xref:System.Collections.Generic.IEnumerable%601>typ T je kovariantní, můžete přiřadit objekt `IEnumerable(Of String)`ho typu k objektu `IEnumerable(Of Object)` typu bez použití jakýchkoli speciálních metod převodu.

Spoluvariantnímu delegátu se dá přiřadit jiný delegát stejného typu, ale s více odvozeným parametrem obecného typu.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak deklarovat, rozšiřuje a implementovat kovariantní obecné rozhraní. Také ukazuje, jak použít implicitní převod pro třídy, které implementují kovariantní rozhraní.

[!code-vb[vbVarianceKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#3)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak deklarovat, vytvářet instance a vyvolat kovariantní obecný delegát. Také ukazuje, jak lze použít implicitní převod pro typy delegátů.

[!code-vb[vbVarianceKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#4)]

## <a name="see-also"></a>Viz také:

- [Odchylky obecných rozhraní](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [Pro](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
