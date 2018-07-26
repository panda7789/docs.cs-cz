---
title: chráněné vnitřní (C# Reference)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 5ba2c811a1a4f095bcee65ed6678a7dc50fe94db
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244855"
---
# <a name="protected-internal-c-reference"></a>chráněné vnitřní (C# Reference)
`protected internal` – Kombinace klíčových slov je modifikátor přístupu členu. Chráněné vnitřní člen je přístupný z aktuálního sestavení nebo typy, které jsou odvozeny ze třídy obsahující. Porovnání `protected internal` jiných přístupu modifikátory přístupu, najdete v článku [úrovní přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md). 
   
## <a name="example"></a>Příklad  
 Chráněné vnitřní člena základní třídy je přístupný z libovolného typu v rámci jeho obsahujícího sestavení. Je také dostupná v odvozené třídě nachází v jiném sestavení pouze v případě, že dojde k přístup prostřednictvím proměnné typu odvozené třídy. Představte si třeba následující segment kódu:  

```csharp
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
  
```csharp  
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
 Tento příklad obsahuje dva soubory `Assembly1.cs` a `Assembly2.cs`. První soubor obsahuje veřejnou základní třídu, `BaseClass`a jiné třídy `TestAccess`. `BaseClass` vlastní chráněný interní člen `myValue`, který přistupuje `TestAccess` typu. V souboru druhý pokus o přístup k `myValue` prostřednictvím instance `BaseClass` dojde k chybě při přístupu do tohoto člena prostřednictvím instance třídy odvozená `DerivedClass` proběhne úspěšně. 

 Členy struktury nemůžou být `protected internal` protože struktury nelze dědit.  
  
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
 [Zajištění zabezpečení pro klíčových slov internal virtual](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))
