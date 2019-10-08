---
title: In (generický modifikátor) – Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: 9c0f7d454767112e1e309af81407b5fdef22eee9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004866"
---
# <a name="in-generic-modifier-visual-basic"></a>In (generický modifikátor) (Visual Basic)

Pro parametry obecného typu Určuje klíčové slovo `In`, že parametr typu je kontravariantní.

## <a name="remarks"></a>Poznámky

Kontravariance umožňuje použít méně odvozený typ, než který je určen obecným parametrem. To umožňuje implicitní převod tříd, které implementují rozhraní variant a implicitní převod typů delegátů.

Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="rules"></a>Pravidly

V obecných rozhraních a delegátech můžete použít klíčové slovo `In`.
  
Parametr typu může být deklarovaný jako kontravariantní v obecném rozhraní nebo delegátu, pokud se používá jenom jako typ argumentů metody a nepoužívá se jako návratový typ metody. parametry `ByRef` nemohou být kovariantní nebo kontravariantní.

Kovariance a kontravariance jsou podporovány pro typy odkazů a nejsou podporovány pro typy hodnot.

V Visual Basic nelze deklarovat události v kontravariantních rozhraních bez určení typu delegáta. Také kontravariantní rozhraní nemohou mít vnořené třídy, výčty nebo struktury, ale mohou mít vnořená rozhraní.

## <a name="behavior"></a>Předvídatelně

Rozhraní, které má parametr kontravariantního typu, umožňuje svým metodám přijímat argumenty méně odvozených typů než hodnoty určené parametrem typu rozhraní. Například vzhledem k tomu, že v .NET Framework 4 v rozhraní <xref:System.Collections.Generic.IComparer%601> typ T je kontravariantní, můžete přiřadit objekt typu `IComparer(Of Person)` k objektu typu `IComparer(Of Employee)` bez použití jakýchkoli speciálních metod převodu, pokud `Employee` dědí z `Person`.

Kontravariantnímu delegátu lze přiřadit jiný delegát stejného typu, ale s menším odvozeným parametrem obecného typu.

## <a name="example---contravariant-generic-interface"></a>Příklad – kontravariantní obecné rozhraní

Následující příklad ukazuje, jak deklarovat, rozšiřuje a implementovat kontravariantní obecné rozhraní. Také ukazuje, jak lze použít implicitní převod pro třídy, které implementují toto rozhraní.

[!code-vb[vbVarianceKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#1)]

## <a name="example---contravariant-generic-delegate"></a>Příklad – kontravariantní obecný delegát

Následující příklad ukazuje, jak deklarovat, vytvářet instance a vyvolat kontravariantního obecného delegáta. Také ukazuje, jak lze implicitně převést typ delegáta.

[!code-vb[vbVarianceKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#2)]

## <a name="see-also"></a>Viz také:

- [Odchylky obecných rozhraní](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [Mimo](out-generic-modifier.md)
