---
title: Zabezpečení zpracování výjimek
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc8cd20a4183ffd002f1399b6b50c8956208a21b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61868796"
---
# <a name="securing-exception-handling"></a>Zabezpečení zpracování výjimek
V jazyce Visual C++ a Visual Basic, výraz filtru zásobníkem dále spouští před jakoukoli **nakonec** příkazu. **Catch** bloku přidružené k tento filtr se spouští **nakonec** příkazu. Další informace najdete v tématu [Using User-Filtered výjimky](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md). Tento oddíl se zabývá bezpečnostních důsledcích tohoto pořadí. Vezměte v úvahu následující pseudokódu příklad, který znázorňuje pořadí, ve které příkazů filtru a **nakonec** příkazy.  
  
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
  
 Tento kód zobrazí následující.  
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 Filtr spuštěn dříve, než **nakonec** příkazu, takže problémy se zabezpečením může být zavedené prostřednictvím cokoli, z čeho změnu, ve kterém by mohla využívat spuštění jiného kódu stavu. Příklad:  
  
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
  
 Tato pseudokódu umožňuje vyšší zásobníkem spustit libovolný kód filtru. Další příklady operace, které by obsahovat podobný vliv jsou dočasné zosobnění jiného identitu, nastavení interní příznak, který obchází některé kontroly zabezpečení nebo změna jazykové verze přidružené vlákno. Doporučené řešení je zavést obslužná rutina výjimky k izolaci změn kódu stavu vlákna od bloky filtru volajícího. Ale je důležité, aby obslužná rutina výjimky správně zavést nebo tento problém nebude vyřešen. V následujícím příkladu se přepne jazykové verze uživatelského rozhraní, ale libovolnému druhu změny stavu vlákno může být vystavena podobně.  
  
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
  
 Správné opravy v tomto případě je zabalit existující **zkuste**/**nakonec** blokovat **zkuste**/**catch** blok. Jednoduše Představujeme **catch throw** klauzuli do existujících **zkuste**/**nakonec** bloku problém neodstraní, jak je znázorněno v následujícím příkladu.  
  
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
  
 Tato akce neodstraní problém vzhledem k tomu **nakonec** ještě nebyl spuštěn příkaz `FilterFunc` získáním ovládacího prvku.  
  
 V následujícím příkladu řeší problém tím, že zajišťuje, že **nakonec** klauzule byl proveden před nabízející bloky filtru výjimky volajícím.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Pokyny pro zabezpečené kódování](../../../docs/standard/security/secure-coding-guidelines.md)
