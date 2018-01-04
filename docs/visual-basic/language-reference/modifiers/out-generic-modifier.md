---
title: "Out (generický modifikátor) (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4e54504cd65b78846af41692f39899140a6d99b5
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="out-generic-modifier-visual-basic"></a>Out (generický modifikátor) (Visual Basic)
Pro parametry obecného typu `Out` – klíčové slovo určuje, že typu je kovariant.  
  
## <a name="remarks"></a>Poznámky  
 Kovariance umožňuje používat více odvozený typ, než je určeno obecný parametr. To umožňuje implicitní převod tříd, které implementují rozhraní variant a implicitní převod typů delegátů.  
  
 Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="rules"></a>Pravidla  
 Můžete použít `Out` – klíčové slovo v obecném rozhraní a delegáti.  
  
 Obecná rozhraní parametr typu lze deklarovat kovariantní splňuje tyto podmínky:  
  
-   Parametr typu je použit pouze jako návratový typ metody rozhraní a nepoužívá jako typ metoda argumenty.  
  
    > [!NOTE]
    >  Existuje jedna výjimka tohoto pravidla. Pokud v kovariantní rozhraní máte obecný delegát kontravariant jako parametru metody, můžete jako parametr obecného typu kovariantní typ pro tento delegát. Další informace o kovariantní a obecní delegáti kontravariant, najdete v části [odchylky v delegátech](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [pomocí odchylky pro Func a obecní delegáti akce](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
-   Parametr typu není používána jako obecná omezení pro metody rozhraní.  
  
 V obecný delegát parametr typu lze deklarovat kovariantní, pokud je použit pouze jako návratový typ. metoda a nepoužívá se metoda argumenty.  
  
 Kovariance a kontravariance jsou podporovány pro odkazové typy, ale nejsou podporovány u typů hodnot.  
  
 V jazyce Visual Basic nelze deklarovat události v kovariantní rozhraní bez zadání typu delegáta. Navíc kovariantní rozhraní vnořené třídy, výčty a struktury, ale mohou mít vnořené rozhraní.  
  
## <a name="behavior"></a>Chování  
 Rozhraní, které má kovariantní typ parametru umožňuje její metody vrátit více odvozené typy než je zadáno v parametru typu. Například protože v rozhraní .NET Framework 4 v <xref:System.Collections.Generic.IEnumerable%601>T typu je kovariant, můžete přiřadit objekt `IEnumerabe(Of String)` typ na objekt `IEnumerable(Of Object)` typu bez použití žádné speciální převod metody.  
  
 Kovariantní delegát může být přiřazen jiné delegáta stejného typu, ale s více odvozené parametr obecného typu.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak deklarovat, rozšířit a kovariantní obecná rozhraní. Také ukazuje, jak používat implicitní převod pro třídy, které implementují rozhraní, které je kovariant.  
  
 [!code-vb[vbVarianceKeywords#3](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_1.vb)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak deklarování, vytváření instancí a vyvolání kovariantní obecný delegát. Také ukazuje, jak můžete použít implicitní převod pro typy delegáta.  
  
 [!code-vb[vbVarianceKeywords#4](../../../visual-basic/language-reference/modifiers/codesnippet/VisualBasic/out-generic-modifier_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Odchylky obecných rozhraní](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [V](../../../visual-basic/language-reference/modifiers/in-generic-modifier.md)
