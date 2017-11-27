---
title: "Zabezpečení zpracování výjimek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a028fcdfb6c85e456c8722decdb1bca8fd907a9f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="securing-exception-handling"></a>Zabezpečení zpracování výjimek
V jazyce Visual Basic a Visual C++, výraz filtru další až stack spouští před spuštěním **nakonec** příkaz. **Catch** bloku přidružený tento filtr se spouští **nakonec** příkaz. Další informace najdete v tématu [Using User-Filtered výjimky](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md). Tento oddíl se zabývá bezpečnostních důsledcích tohoto pořadí. Vezměte v úvahu následující příklad pseudokódu, který znázorňuje pořadí, ve které příkazy filtru a **nakonec** příkazy spustit.  
  
```cpp  
void Main()   
{  
    try   
    {  
        Sub();  
    }   
    except (Filter())   
    {  
        Console.WriteLine("catch");  
    }  
}  
bool Filter () {  
    Console.WriteLine("filter");  
    return true;  
}  
void Sub()   
{  
    try   
    {  
        Console.WriteLine("throw");  
        throw new Exception();  
    }   
    finally   
    {  
        Console.WriteLine("finally");  
    }  
}                        
```  
  
 Tento kód vypíše následující.  
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 Filtr se spouští před **nakonec** prohlášení, takže problémy se zabezpečením mohou být způsobeny všechno, co způsobuje změnu, kde může využít provádění jiný kód stavu. Příklad:  
  
```cpp  
try   
{  
    Alter_Security_State();  
    // This means changing anything (state variables,  
    // switching unmanaged context, impersonation, and   
    // so on) that could be exploited if malicious   
    // code ran before state is restored.  
    Do_some_work();  
}   
finally   
{  
    Restore_Security_State();  
    // This simply restores the state change above.  
}  
```  
  
 Tento pseudokód umožňuje vyšší nahoru v zásobníku spustit libovolný kód filtru. Další příklady operací, které by mělo podobné účinek jsou dočasné zosobnění jiného identitu, nastavení interní příznak, který obchází některé kontroly zabezpečení nebo změna jazykovou verzi přidružené vlákno. Doporučené řešení je zavedení obslužné rutiny výjimek izolovat změny kódu stavu vlákna od bloky filtru volajícího. Je důležité, aby byla správně zavedena obslužná rutina výjimky nebo však tento problém nebude vyřešen. Následující příklad změní jazyková verze uživatelského rozhraní, ale může podobně zveřejněné libovolnému druhu změny stavu přístup z více vláken.  
  
```cpp  
YourObject.YourMethod()  
{  
   CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
   try {  
      Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
      // Do something that throws an exception.  
}  
   finally {  
      Thread.CurrentThread.CurrentUICulture = saveCulture;  
   }  
}  
```  
  
```vb  
Public Class UserCode  
   Public Shared Sub Main()  
      Try  
         Dim obj As YourObject = new YourObject  
         obj.YourMethod()  
      Catch e As Exception When FilterFunc  
         Console.WriteLine("An error occurred: '{0}'", e)  
         Console.WriteLine("Current Culture: {0}",   
Thread.CurrentThread.CurrentUICulture)  
      End Try  
   End Sub  
  
   Public Function FilterFunc As Boolean  
      Console.WriteLine("Current Culture: {0}", Thread.CurrentThread.CurrentUICulture)  
      Return True  
   End Sub  
  
End Class  
```  
  
 V takovém případě je správná oprava zabalit existující **zkuste**/**nakonec** blokovat **zkuste**/**catch** blok. Jednoduché zavedení **catch-throw** klauzule do existujících **zkuste**/**nakonec** bloku problém neodstraní, jak je znázorněno v následujícím příkladu.  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
  
    try   
    {  
        Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
        // Do something that throws an exception.  
    }  
    catch { throw; }  
    finally   
    {  
        Thread.CurrentThread.CurrentUICulture = saveCulture;  
    }  
}  
```  
  
 Tato akce neodstraní problém protože **nakonec** ještě nebyl spuštěn příkaz `FilterFunc` získá ovládacího prvku.  
  
 Následující příklad odstraňuje problém, přičemž zajistí, aby **nakonec** klauzule provedla před nabízející bloky filtru výjimek volajícího.  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
    try    
    {  
        try   
        {  
            Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
            // Do something that throws an exception.  
        }  
        finally   
        {  
            Thread.CurrentThread.CurrentUICulture = saveCulture;  
        }  
    }  
    catch { throw; }  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
