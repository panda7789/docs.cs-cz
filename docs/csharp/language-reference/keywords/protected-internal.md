---
title: chráněné vnitřní (C# referenční dokumentace)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: a2a649f0fdb924c26380e7261bd935be736f0665
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="protected-internal-c-reference"></a>chráněné vnitřní (C# referenční dokumentace)
`protected internal` – Kombinace klíčových slov je modifikátor přístupu členů. Chráněný člen interní je přístupný z aktuální sestavení nebo z typů, které jsou odvozeny od obsahující třídy. Porovnání `protected internal` s další modifikátory přístupu, přečtěte si téma [úrovní přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md). 
   
## <a name="example"></a>Příklad  
 Chráněný vnitřní člen základní třídy je přístupná z libovolného typu v rámci jeho obsahující sestavení. Je také přístupné v odvozené třídě nachází v jiném sestavení pouze v případě, že dojde k přístupu pomocí proměnné typu odvozené třídy. Zvažte například následující segment kódu:  

```
// Assembly1.cs  
// Compile with: /target:library  
public class BaseClass   
{  
   protected internal int myValue = 0;  
}

class TestAccess 
{
    void Access()
    {
        BaseClass baseObject = new BaseClass();
        baseObject.myValue = 5;
    }
}  
```  
  
```  
// Assembly2.cs  
// Compile with: /reference:Assembly1.dll  
class DerivedClass : BaseClass   
{  
    static void Main()
    {
        BaseClass baseObject = new BaseClass();
        DerivedClass derivedObject = new DerivedClass();

        // Error CS1540, because myValue can only be accessed by
        // classes derived from BaseClass.
        // baseObject.myValue = 10; 

        // OK, because this class derives from BaseClass.
        derivedObject.myValue = 10;
    }
} 
```  
 Tento příklad obsahuje dva soubory, `Assembly1.cs` a `Assembly2.cs`. První soubor obsahuje veřejný základní třídu, `BaseClass`a jinou třídu, `TestAccess`. `BaseClass` vlastní chráněný vnitřní člen, `myValue`, který přistupuje `TestAccess` typu. V souboru druhý pokus o přístup `myValue` prostřednictvím instance `BaseClass` vygeneruje chybu při přístupu do tohoto člena prostřednictvím instance odvozené třídy, `DerivedClass` bude úspěšné. 

 Struktura členové nemohou být `protected internal` protože struct nemůže být zděděno.  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)   
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)   
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)   
 [Modifikátory přístupu](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [Úrovně přístupnosti](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)   
 [Veřejné](../../../csharp/language-reference/keywords/public.md)   
 [Privátní](../../../csharp/language-reference/keywords/private.md)   
 [Interní](../../../csharp/language-reference/keywords/internal.md)   
 [Otázky zabezpečení pro interní virtuální klíčová slova](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))
