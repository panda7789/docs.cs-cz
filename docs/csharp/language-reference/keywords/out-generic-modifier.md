---
title: out (generický modifikátor) (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: 95ccbe3ab5bf2d326e1154af0b169972a24f7e38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="out-generic-modifier-c-reference"></a>out (generický modifikátor) (Referenční dokumentace jazyka C#)
Pro parametry obecného typu `out` – klíčové slovo určuje, že parametr typu je kovariant. Můžete použít `out` – klíčové slovo v obecném rozhraní a delegáti.  
  
 Kovariance umožňuje používat více odvozený typ, než je určeno obecný parametr. To umožňuje implicitní převod tříd, které implementují rozhraní variant a implicitní převod typů delegátů. Kovariance a kontravariance jsou podporovány pro odkazové typy, ale nejsou podporovány u typů hodnot.  
  
 Rozhraní, které má kovariantní typ parametru umožňuje její metody vrátit více odvozené typy než je zadáno v parametru typu. Například protože v rozhraní .NET Framework 4 v <xref:System.Collections.Generic.IEnumerable%601>T typu je kovariant, můžete přiřadit objekt `IEnumerable(Of String)` typ na objekt `IEnumerable(Of Object)` typu bez použití žádné speciální převod metody.  
  
 Kovariantní delegát může být přiřazen jiné delegáta stejného typu, ale s více odvozené parametr obecného typu.  
  
 Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak deklarovat, rozšířit a kovariantní obecná rozhraní. Také ukazuje, jak používat implicitní převod pro třídy, které implementují rozhraní, které je kovariant.  
  
 [!code-csharp[csVarianceKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_1.cs)]  
  
 Obecná rozhraní parametr typu lze deklarovat kovariantní splňuje tyto podmínky:  
  
-   Parametr typu je použit pouze jako návratový typ metody rozhraní a nepoužívá jako typ metoda argumenty.  
  
    > [!NOTE]
    >  Existuje jedna výjimka tohoto pravidla. Pokud v kovariantní rozhraní máte obecný delegát kontravariant jako parametru metody, můžete jako parametr obecného typu kovariantní typ pro tento delegát. Další informace o kovariantní a obecní delegáti kontravariant, najdete v části [odchylky v delegátech](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [pomocí odchylky pro Func a obecní delegáti akce](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
-   Parametr typu není používána jako obecná omezení pro metody rozhraní.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak deklarování, vytváření instancí a vyvolání kovariantní obecný delegát. Také ukazuje, jak implicitně převést typů delegátů.  
  
 [!code-csharp[csVarianceKeywords#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_2.cs)]  
  
 V obecný delegát typu lze deklarovat kovariantní, pokud je použit pouze jako návratový typ. metoda a nepoužívá se metoda argumenty.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Odchylky obecných rozhraní](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [in](../../../csharp/language-reference/keywords/in-generic-modifier.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)
