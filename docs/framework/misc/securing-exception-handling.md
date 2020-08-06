---
title: Zabezpečení zpracování výjimek
description: Přečtěte si, jak v kódu .NET zajistit zabezpečení zpracování výjimek. Zkontrolujte pořadí, ve kterém kód běží, pokud existují příkazy try, EXCEPT, Catch a finally.
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
ms.openlocfilehash: c7643bb34da0cbcbd267fc90e6294bc0b565985e
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855774"
---
# <a name="securing-exception-handling"></a>Zabezpečení zpracování výjimek

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

V Visual C++ a Visual Basic se výraz filtru podrobněji spouští před jakýmkoli `finally` příkazem. Blok **catch** přidružený k tomuto filtru se spustí po `finally` příkazu. Další informace najdete v tématu [použití uživatelem filtrovaných výjimek](../../standard/exceptions/using-user-filtered-exception-handlers.md). V této části se prohlíží vlivem na zabezpečení tohoto pořadí. Vezměte v úvahu následující příklad pseudokódu, který ukazuje pořadí, ve kterém se spouštějí příkazy filtru a `finally` příkazy.  
  
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
  
 Filtr se spustí před `finally` příkazem, takže problémy se zabezpečením mohou být provedeny cokoli, co provede změnu stavu, kde může využít jiný kód. Příklad:  
  
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
  
 Tento pseudokódu umožňuje filtru zvýšit množství zásobníku tak, aby běžel libovolný kód. Další příklady operací, které by měly podobný účinek, jsou dočasné zosobnění jiné identity, nastavení interního příznaku, který obchází určitou kontrolu zabezpečení nebo změnu jazykové verze přidružené k vláknu. Doporučené řešení je zavedení obslužné rutiny výjimky pro izolaci změn kódu do stavu vlákna z bloků filtru volajících. Je však důležité správně zavést obslužnou rutinu výjimky nebo tento problém nebude vyřešen. Následující příklad přepne jazykovou verzi uživatelského rozhraní, ale jakýkoli druh změny stavu vlákna může být podobně vystavený.  
  
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
  
 Správná oprava v tomto případě je zabalit existující blok **Try** / **finally** do bloku **Try** / **catch** . Pouhým představením klauzule **catch-throw** do stávajícího bloku **Try** / **finally** nedojde k vyřešení problému, jak je znázorněno v následujícím příkladu.  
  
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
  
 Tím se problém nevyřeší, protože `finally` příkaz nebyl spuštěn před tím, než `FilterFunc` získá ovládací prvek.  
  
 Následující příklad opravuje problém tím, že zajistí, že `finally` byla klauzule provedena před tím, než nabídka vyvolá výjimku v blocích filtru výjimky volajících.  
  
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
