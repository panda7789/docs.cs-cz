---
title: "private (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d9cc8f86166888b47a758e200182d319c68ca6d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="private-c-reference"></a>private (Referenční dokumentace jazyka C#)
`private` – Klíčové slovo je modifikátor přístupu členů. 
   
 > Tato stránka popisuje `private` přístup. `private` – Klíčové slovo je také součástí [ `private protected` ](./private-protected.md) – modifikátor přístupu.
  
Soukromý přístup je omezenou úroveň přístupu. Soukromé členy jsou přístupné pouze v rámci tělo třídě nebo struktuře, ve které jsou deklarovány, jako v následujícím příkladu:  
  
```  
class Employee  
{  
    private int i;  
    double d;   // private access by default  
}  
```  

 Vnořené typy v těle stejné lze rovněž použít tyto soukromé členy.  
  
 Jedná o chybu kompilace tak, aby odkazovaly privátního člena mimo třídě nebo struktuře, ve kterém je deklarovaná.  
  
 Porovnání `private` s další modifikátory přístupu, přečtěte si téma [úrovní přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md) a [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `Employee` třída obsahuje dva private členy `name` a `salary`. Jako soukromé členy k nim být přístup s výjimkou metody člen. Veřejné metody s názvem `GetName` a `Salary` jsou přidány do povolit řízené přístup k soukromé členy. `name` Člen přistupuje prostřednictvím veřejná metoda a `salary` člen přistupuje prostřednictvím veřejné vlastnosti jen pro čtení. (Viz [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md) Další informace.)  
  
 [!code-csharp[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modifikátory přístupu](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Úrovně přístupnosti](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)  
 [veřejné](../../../csharp/language-reference/keywords/public.md)  
 [chráněný](../../../csharp/language-reference/keywords/protected.md)  
 [interní](../../../csharp/language-reference/keywords/internal.md)
