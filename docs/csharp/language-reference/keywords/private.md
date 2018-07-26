---
title: private (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: 89bc23e91bf693f0a95b75dffe2399cb7e865b50
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2018
ms.locfileid: "37960804"
---
# <a name="private-c-reference"></a>private (Referenční dokumentace jazyka C#)
`private` – Klíčové slovo je modifikátor přístupu členu. 
   
 > Tato stránka popisuje `private` přístup. `private` – Klíčové slovo je také součástí [ `private protected` ](./private-protected.md) modifikátor přístupu.
  
Soukromý přístup je omezenou úroveň přístupu. Privátní členy jsou přístupné jenom v rámci třídy nebo struktury, ve kterém jsou deklarovány, jako v následujícím příkladu:  
  
```csharp  
class Employee  
{  
    private int i;  
    double d;   // private access by default  
}  
```  

 Vnořené typy ve stejné tělo se dostanete také tyto soukromé členy.  
  
 Je chyba kompilace tak, aby odkazovaly soukromý člen mimo třídy nebo struktury, ve kterém je deklarována.  
  
 Porovnání `private` jiných přístupu modifikátory přístupu, najdete v článku [úrovní přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md) a [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `Employee` třída obsahuje dva soukromé datové členy `name` a `salary`. Jako soukromé členy k nim nelze přistupovat s výjimkou metody člena. Veřejné metody s názvem `GetName` a `Salary` přidávají povolit řízený přístup k soukromým členům. `name` Člen přistupuje prostřednictvím veřejnou metodu a `salary` člen přistupuje prostřednictvím veřejné vlastnosti jen pro čtení. (Viz [vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md) Další informace.)  
  
 [!code-csharp[csrefKeywordsModifiers#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/private_1.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modifikátory přístupu](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Úrovně přístupnosti](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)
