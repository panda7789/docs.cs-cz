---
title: privátní chráněné (referenční dokumentace jazyka C#)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: ee36cc713dd5fdb90ae20ef992f8e75eca09597d
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
---
# <a name="private-protected-c-reference"></a>privátní chráněné (referenční dokumentace jazyka C#)
`private protected` – Kombinace klíčových slov je modifikátor přístupu členů. Privátní chráněného člena je přístupný pro typy odvozené od obsahující třídy, ale pouze v rámci jeho obsahující sestavení. Porovnání `private protected` s další modifikátory přístupu, přečtěte si téma [úrovní přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md). 
   
## <a name="example"></a>Příklad  
 Privátní chráněného člena základní třídy je přístupná ze odvozené typy v jeho obsahující sestavení, pouze je-li statické typ proměnné typu odvozené třídy. Zvažte například následující segment kódu:  
  
 ```csharp
 // Assembly1.cs  
 // Compile with: /target:library  
 public class BaseClass
 {
     private protected int myValue = 0;
 }
 
 public class DerivedClass1 : BaseClass
 {
     void Access()
     {
         BaseClass baseObject = new BaseClass();
 
         // Error CS1540, because myValue can only be accessed by
         // classes derived from BaseClass.
         // baseObject.myValue = 5;  
 
         // OK, accessed through the current derived class instance
         myValue = 5;
     }
 }
```  
  
```csharp  
 // Assembly2.cs  
 // Compile with: /reference:Assembly1.dll  
 class DerivedClass2 : BaseClass
 {
     void Access()
     {
         // Error CS0122, because myValue can only be
         // accessed by types in Assembly1
         // myValue = 10;
     }
 }
```  
 Tento příklad obsahuje dva soubory, `Assembly1.cs` a `Assembly2.cs`. První soubor obsahuje veřejný základní třídu, `BaseClass`a typ odvozený z něj `DerivedClass1`. `BaseClass` vlastní privátní chráněného člena `myValue`, které `DerivedClass1` pokusí o přístup k dvěma způsoby. První pokus o přístup k `myValue` prostřednictvím instance `BaseClass` způsobí chybu. Ale pokus můžete použít jako zděděného členu v `DerivedClass1` bude úspěšné.
V souboru druhý pokus o přístup `myValue` jako zděděné členem `DerivedClass2` způsobí chybu, protože se jedná pouze přístupný pro odvozené typy v Assembly1. 

 Struktura členové nemohou být `private protected` protože struct nemůže být zděděno.  
  
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
