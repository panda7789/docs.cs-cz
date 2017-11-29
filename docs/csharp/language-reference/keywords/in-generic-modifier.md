---
title: "in (generický modifikátor) (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.assetid: 3a778c36-8aed-4ebe-aa8b-39f4057215b1
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 84773fca826b5a25679f1385a11c51b590ea20f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="in-generic-modifier-c-reference"></a>in (generický modifikátor) (Referenční dokumentace jazyka C#)
Pro parametry obecného typu `in` – klíčové slovo určuje, že parametr typu je kontravariant. Můžete použít `in` – klíčové slovo v obecném rozhraní a delegáti.  
  
 Kontravariance umožňuje používat méně odvozený typ, než je určeno obecný parametr. To umožňuje implicitní převod tříd, které implementují rozhraní variant a implicitní převod typů delegátů. Kovariance a kontravariance v parametry obecného typu jsou podporovány pro odkazové typy, ale nejsou podporovány u typů hodnot.  
  
 Typ lze deklarovat kontravariant v obecné rozhraní nebo delegáta, pokud je použit pouze jako typ metoda argumenty a nejsou používány jako návratový typ. metoda. `Ref`a `out` parametry nemůže být typu variant.  
  
 Rozhraní, které má parametr typu kontravariant umožňuje její metody tak, aby přijímal argumenty odvozených typů menší než je zadáno v parametru typu rozhraní. Například protože v rozhraní .NET Framework 4 v <xref:System.Collections.Generic.IComparer%601> rozhraní T typu je kontravariant, můžete jim přiřadit objekt `IComparer(Of Person)` typ na objekt `IComparer(Of Employee)` typu bez použití žádné speciální převod metody, pokud `Employee` dědí `Person`.  
  
 Delegát kontravariant může být přiřazen jiný delegát stejného typu, ale s méně odvozený parametr obecného typu.  
  
 Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak deklarovat, rozšířit a implementovat obecné rozhraní kontravariant. Také ukazuje, jak můžete použít implicitní převod pro třídy, které toto rozhraní implementovat.  
  
 [!code-csharp[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_1.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak deklarování, vytváření instancí a vyvolání obecný delegát kontravariant. Také ukazuje, jak můžete implicitně převést typem delegáta.  
  
 [!code-csharp[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [na více systémů](../../../csharp/language-reference/keywords/out-generic-modifier.md)  
 [Kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)
