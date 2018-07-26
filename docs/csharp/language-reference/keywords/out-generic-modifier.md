---
title: out (generický modifikátor) (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: 95ccbe3ab5bf2d326e1154af0b169972a24f7e38
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245083"
---
# <a name="out-generic-modifier-c-reference"></a>out (generický modifikátor) (Referenční dokumentace jazyka C#)
Pro parametry obecného typu `out` – klíčové slovo určuje, že parametr typu je kovariant. Můžete použít `out` – klíčové slovo v obecných rozhraních a delegátech.  
  
 Kovariance umožňuje použít více odvozený typ, než je určeno obecný parametr. To umožňuje implicitní převod z třídy, které implementují rozhraní variant a implicitní převod delegujících typů. Kovariance a kontravariance jsou podporovány pro typy odkazů, ale nejsou podporovány pro typy hodnot.  
  
 Rozhraní, které má parametr kovariantního typu umožňuje její metody k vrácení více odvozené typy než je zadáno parametrem typu. Například protože v rozhraní .NET Framework 4, v <xref:System.Collections.Generic.IEnumerable%601>, typ T je kovariantní, můžete přiřadit objektu `IEnumerable(Of String)` typu na objekt `IEnumerable(Of Object)` typ bez použití jakékoli speciální převod metody.  
  
 Kovariantní delegát může být přiřazen jiný delegát stejného typu, ale s více odvozeného parametr obecného typu.  
  
 Další informace najdete v tématu [kovariance a kontravariance](../../programming-guide/concepts/covariance-contravariance/index.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak deklarovat, rozšíření a implementovat kovariantní obecné rozhraní. Také ukazuje, jak použít implicitní převod pro třídy, které implementují kovariantního rozhraní.  
  
 [!code-csharp[csVarianceKeywords#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_1.cs)]  
  
 Obecná rozhraní mohou být deklarovány parametr typu kovariantní, pokud splňuje následující podmínky:  
  
-   Parametr typu je použít jenom jako návratový typ metody rozhraní a nelze použít jako typ argumentů metody.  
  
    > [!NOTE]
    >  Existuje jedna výjimka tohoto pravidla. Pokud kovariantní rozhraní mají kontravariantní obecného delegáta jako parametr metody, můžete jako parametr obecného typu kovariantního typu pro tohoto delegáta. Další informace o kovariantního a obecných delegátů kontravariantní, naleznete v tématu [odchylky v delegátech](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) a [pomocí odchylku pro delegáty Func a Action obecný](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).  
  
-   Parametr typu se nepoužívá jako obecná omezení pro metody rozhraní.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak deklarovat, vytváření instancí a vyvolání kovariantního obecného delegáta. Také ukazuje, jak pro implicitní převod na typy delegátů.  
  
 [!code-csharp[csVarianceKeywords#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/out-generic-modifier_2.cs)]  
  
 V obecný delegát typu mohou být deklarovány kovariantní, pokud je použita pouze jako návratový typ metody a není možné použít u argumenty metody.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Odchylky obecných rozhraní](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)  
 [in](../../../csharp/language-reference/keywords/in-generic-modifier.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)
