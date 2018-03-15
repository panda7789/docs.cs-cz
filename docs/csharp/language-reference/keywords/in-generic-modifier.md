---
title: "in (generický modifikátor) (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2af4e27034af0067e81a52c81991edaf5a5415d8
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2018
---
# <a name="in-generic-modifier-c-reference"></a>in (generický modifikátor) (Referenční dokumentace jazyka C#)

Pro parametry obecného typu `in` – klíčové slovo určuje, že parametr typu je kontravariant. Můžete použít `in` – klíčové slovo v obecném rozhraní a delegáti.  
  
 Kontravariance umožňuje používat méně odvozený typ, než je určeno obecný parametr. To umožňuje implicitní převod tříd, které implementují rozhraní variant a implicitní převod typů delegátů. Kovariance a kontravariance v parametry obecného typu jsou podporovány pro odkazové typy, ale nejsou podporovány u typů hodnot.  
  
 Typ lze deklarovat kontravariant v obecné rozhraní nebo delegáta, pouze v případě, že definuje typ parametry metody a ne návratový typ metody. `In`, `ref`, a `out` parametry musí být výchozí, což znamená, ani jeden z nich jsou kovariantní nebo kontravariant.
  
 Rozhraní, které má parametr typu kontravariant umožňuje její metody tak, aby přijímal argumenty odvozených typů menší než je zadáno v parametru typu rozhraní. Například v <xref:System.Collections.Generic.IComparer%601> rozhraní T typu je kontravariant, můžete jim přiřadit objekt `IComparer<Person>` typ na objekt `IComparer<Employee>` typu bez použití žádné speciální převod metody, pokud `Employee` dědí `Person`.  
  
 Delegát kontravariant může být přiřazen jiný delegát stejného typu, ale s méně odvozený parametr obecného typu.  
  
 Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="contravariant-generic-interface"></a>Kontravariant obecné rozhraní   

 Následující příklad ukazuje, jak deklarovat, rozšířit a implementovat obecné rozhraní kontravariant. Také ukazuje, jak můžete použít implicitní převod pro třídy, které toto rozhraní implementovat.  
  
 [!code-csharp[csVarianceKeywords#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_1.cs)]  
  
## <a name="contravariant-generic-delegate"></a>Kontravariant – obecný delegát  

 Následující příklad ukazuje, jak deklarování, vytváření instancí a vyvolání obecný delegát kontravariant. Také ukazuje, jak můžete implicitně převést typem delegáta.  
  
 [!code-csharp[csVarianceKeywords#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/in-generic-modifier_2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [out](../../../csharp/language-reference/keywords/out-generic-modifier.md)  
 [Kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)  
