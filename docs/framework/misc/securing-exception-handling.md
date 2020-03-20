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
ms.openlocfilehash: ad27e62197f6fdaa6b5e706f4ae02c03fecae9f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181142"
---
# <a name="securing-exception-handling"></a>Zabezpečení zpracování výjimek
V jazyce Visual C++ a Visual Basic, výraz filtru dále do zásobníku běží před všechny **finally** prohlášení. Blok **catch** přidružený k tomuto filtru se spustí po příkazu **finally.** Další informace naleznete v tématu [Použití výjimek filtrovaných uživatelem](../../standard/exceptions/using-user-filtered-exception-handlers.md). Tato část zkoumá bezpečnostní důsledky tohoto pořadí. Vezměme si následující pseudocode příklad, který ilustruje pořadí, ve kterém filter příkazy a **nakonec** příkazy spustit.  
  
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
  
 Tento kód vytiskne následující.  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 Filtr se spustí před **příkazem finally,** takže problémy se zabezpečením mohou být zavedeny čímkoli, co provede změnu stavu, kde by mohlo využití spuštění jiného kódu. Například:  
  
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
  
 Tento pseudokód umožňuje filtr vyšší nahoru zásobníku spustit libovolný kód. Další příklady operací, které by měly podobný účinek, jsou dočasné zosobnění jiné identity, nastavení vnitřního příznaku, který obchází některé kontroly zabezpečení, nebo změna jazykové verze přidružené k vláknu. Doporučené řešení je zavést obslužnou rutinu výjimky izolovat změny kódu do stavu vlákna z bloků filtrů volajících. Je však důležité, aby obslužná rutina výjimky byla správně zavedena nebo tento problém nebude opraven. Následující příklad přepne jazykovou verzi uživatelského rozhraní, ale jakýkoli druh změny stavu vlákna může být podobně vystavena.  
  
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
  
 Správná oprava v tomto případě je zabalit existující **try**/**finally** blokovat v bloku **try**/**catch.** Jednoduše zavedení **catch-throw** klauzule do existující **houštiny try**/**finally** problém nevyřeší, jak je znázorněno v následujícím příkladu.  
  
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
  
 Problém se tím nevyřeší, protože příkaz **finally** nebyl spuštěn před tím, než získá `FilterFunc` kontrolu.  
  
 Následující příklad řeší problém tím, že zajistí, že **klauzule finally** byla spuštěna před nabídkou výjimky do bloků filtru výjimek volajících.  
  
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

- [Pokyny pro zabezpečené kódování](../../standard/security/secure-coding-guidelines.md)
