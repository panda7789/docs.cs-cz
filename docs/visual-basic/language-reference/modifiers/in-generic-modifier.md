---
title: "In (generický modifikátor) (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 83e9aab4fc361754cfd750ae68f04b36dce13d0a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="in-generic-modifier-visual-basic"></a>In (generický modifikátor) (Visual Basic)
Pro parametry obecného typu `In` – klíčové slovo určuje, že parametr typu je kontravariant.  
  
## <a name="remarks"></a>Poznámky  
 Kontravariance umožňuje používat méně odvozený typ, než je určeno obecný parametr. To umožňuje implicitní převod tříd, které implementují rozhraní variant a implicitní převod typů delegátů.  
  
 Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="rules"></a>Pravidla  
 Můžete použít `In` – klíčové slovo v obecném rozhraní a delegáti.  
  
 Parametr typu lze deklarovat kontravariant v obecné rozhraní nebo delegáta, pokud je použit pouze jako typ metoda argumenty a nejsou používány jako návratový typ. metoda. `ByRef`parametry nemohou mít kovariantní nebo kontravariant.  
  
 Kovariance a kontravariance jsou podporovány pro odkazové typy a není podporována u typů hodnot.  
  
 V jazyce Visual Basic nelze deklarovat události v rozhraní kontravariant bez zadání typu delegáta. Navíc kontravariant rozhraní vnořené třídy, výčty a struktury, ale mohou mít vnořené rozhraní.  
  
## <a name="behavior"></a>Chování  
 Rozhraní, které má parametr typu kontravariant umožňuje její metody tak, aby přijímal argumenty odvozených typů menší než je zadáno v parametru typu rozhraní. Například protože v rozhraní .NET Framework 4 v <xref:System.Collections.Generic.IComparer%601> rozhraní T typu je kontravariant, můžete jim přiřadit objekt `IComparer(Of Person)` typ na objekt `IComparer(Of Employee)` typu bez použití žádné speciální převod metody, pokud `Person` dědí `Employee`.  
  
 Delegát kontravariant může být přiřazen jiný delegát stejného typu, ale s méně odvozený parametr obecného typu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak deklarovat, rozšířit a implementovat obecné rozhraní kontravariant. Také ukazuje, jak můžete použít implicitní převod pro třídy, které toto rozhraní implementovat.  
  
 [!code-vb[vbVarianceKeywords#1](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak deklarování, vytváření instancí a vyvolání obecný delegát kontravariant. Také ukazuje, jak můžete implicitně převést typem delegáta.  
  
 [!code-vb[vbVarianceKeywords#2](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/in-generic-modifier_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Odchylky obecných rozhraní](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [Na více systémů](../../../visual-basic/language-reference/modifiers/out-generic-modifier.md)
