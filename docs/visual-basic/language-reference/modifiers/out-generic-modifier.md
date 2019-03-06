---
title: Out (generický modifikátor) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
ms.openlocfilehash: fa14e83af16cd30a72ca1c165596fa9320842fce
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379221"
---
# <a name="out-generic-modifier-visual-basic"></a>Out (generický modifikátor) (Visual Basic)

Pro parametry obecného typu `Out` – klíčové slovo určuje, že typ je kovariantní.

## <a name="remarks"></a>Poznámky

Kovariance umožňuje použít více odvozený typ, než je určeno obecný parametr. To umožňuje implicitní převod z třídy, které implementují rozhraní variant a implicitní převod delegujících typů.

Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="rules"></a>pravidla

Můžete použít `Out` – klíčové slovo v obecných rozhraních a delegátech.

Obecná rozhraní mohou být deklarovány parametr typu kovariantní, pokud splňuje následující podmínky:

- Parametr typu je použít jenom jako návratový typ metody rozhraní a nelze použít jako typ argumentů metody.

    > [!NOTE]
    > Existuje jedna výjimka tohoto pravidla. Pokud kovariantní rozhraní mají kontravariantní obecného delegáta jako parametr metody, můžete jako parametr obecného typu kovariantního typu pro tohoto delegáta. Další informace o kovariantního a obecných delegátů kontravariantní, naleznete v tématu [odchylky v delegátech](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [pomocí odchylku pro delegáty Func a Action obecný](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

- Parametr typu se nepoužívá jako obecná omezení pro metody rozhraní.

V obecného delegátu parametr typu mohou být deklarovány kovariantní, pokud je použita pouze jako návratový typ metody a není možné použít u argumenty metody.

Kovariance a kontravariance jsou podporovány pro typy odkazů, ale nejsou podporovány pro typy hodnot.

V jazyce Visual Basic nelze deklarovat události v kovariantní rozhraní bez zadání typu delegáta. Také kovariantní rozhraní nemůžou být vnořené třídy, výčty a struktury, ale mohou být vnořené rozhraní.

## <a name="behavior"></a>Chování

Rozhraní, které má parametr kovariantního typu umožňuje její metody k vrácení více odvozené typy než je zadáno parametrem typu. Například protože v rozhraní .NET Framework 4, v <xref:System.Collections.Generic.IEnumerable%601>, typ T je kovariantní, můžete přiřadit objektu `IEnumerable(Of String)` typu na objekt `IEnumerable(Of Object)` typ bez použití jakékoli speciální převod metody.

Kovariantní delegát může být přiřazen jiný delegát stejného typu, ale s více odvozeného parametr obecného typu.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak deklarovat, rozšíření a implementovat kovariantní obecné rozhraní. Také ukazuje, jak použít implicitní převod pro třídy, které implementují kovariantního rozhraní.

[!code-vb[vbVarianceKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#3)]

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak deklarovat, vytváření instancí a vyvolání kovariantního obecného delegáta. Také ukazuje, jak můžete použít implicitní převod pro typy delegátů.

[!code-vb[vbVarianceKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#4)]

## <a name="see-also"></a>Viz také:

- [Odchylky obecných rozhraní](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [V](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
