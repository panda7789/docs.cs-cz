---
title: In (generický modifikátor) (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: d8d503f0814a89c977cdc208eced026b2d8cb1fd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802457"
---
# <a name="in-generic-modifier-visual-basic"></a>In (generický modifikátor) (Visual Basic)
Pro parametry obecného typu `In` – klíčové slovo určuje, že parametr typu je kontravariant.  
  
## <a name="remarks"></a>Poznámky  
 Kontravariance umožňuje použít méně odvozený typ, než je určeno obecný parametr. To umožňuje implicitní převod z třídy, které implementují rozhraní variant a implicitní převod delegujících typů.  
  
 Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="rules"></a>pravidla  
 Můžete použít `In` – klíčové slovo v obecných rozhraních a delegátech.  
  
 Parametr typu mohou být deklarovány v obecné rozhraní nebo delegát Kontravariantní, pokud je použít jenom jako typ argumentů metody a nepoužívá se jako návratový typ metody. `ByRef` parametry nemohou být kovariantní nebo kontravariantní.  
  
 Kovariance a kontravariance jsou podporovány pro typy odkazů a nejsou podporovány pro typy hodnot.  
  
 V jazyce Visual Basic nelze deklarovat události v rozhraní kontravariantní bez zadání typu delegáta. Také kontravariantní rozhraní nemůžou být vnořené třídy, výčty a struktury, ale mohou být vnořené rozhraní.  
  
## <a name="behavior"></a>Chování  
 Rozhraní, která má parametr kontravariantního typu umožňuje její metody pro přijímání argumentů méně odvozené typy než je zadáno parametrem typu rozhraní. Například protože v rozhraní .NET Framework 4, v <xref:System.Collections.Generic.IComparer%601> rozhraní, typ T je kontravariantní, můžete přiřadit objektu `IComparer(Of Person)` typu na objekt `IComparer(Of Employee)` typ bez použití jakékoli speciální převod metody, pokud `Person` dědí `Employee`.  
  
 Kontravariantní delegát může být přiřazen jiný delegát stejného typu, ale s méně odvozený parametr obecného typu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak deklarovat, rozšíření a implementovat obecné rozhraní kontravariantní. Také ukazuje, jak můžete použít implicitní převod pro třídy, které toto rozhraní implementují.  
  
 [!code-vb[vbVarianceKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#1)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak deklarovat, vytváření instancí a vyvolání obecného delegátu kontravariantní. Profil také ukazuje, jak lze implicitně převést typ delegáta.  
  
 [!code-vb[vbVarianceKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Odchylky obecných rozhraní](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [navýšení kapacity](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
