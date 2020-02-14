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
ms.openlocfilehash: e0465f2eb6be61e161f5e6b8cadf629a53f11906
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215791"
---
# <a name="securing-exception-handling"></a>Zabezpečení zpracování výjimek
V vizuálů C++ a Visual Basic výraz filtru podrobněji sestaví běh před jakýmkoli příkazem **finally** . Blok **catch** přidružený k tomuto filtru se spustí po příkazu **finally** . Další informace najdete v tématu [použití uživatelem filtrovaných výjimek](../../standard/exceptions/using-user-filtered-exception-handlers.md). V této části se prohlíží vlivem na zabezpečení tohoto pořadí. Vezměte v úvahu následující příklad pseudokódu, který znázorňuje pořadí, ve kterém se spouštějí příkazy filtru a příkazy **finally** .  
  
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
  
 Filtr se spustí před příkazem **finally** , takže problémy se zabezpečením mohou být provedeny cokoli, co provede změnu stavu, kde může využít jiný kód. Například:  
  
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
  
 Tento pseudokódu umožňuje filtru zvýšit množství zásobníku tak, aby běžel libovolný kód. Další příklady operací, které by měly podobný účinek, jsou dočasné zosobnění jiné identity, nastavení interního příznaku, který obchází určitou kontrolu zabezpečení nebo změnu jazykové verze přidružené k vláknu. Doporučené řešení je zavedení obslužné rutiny výjimky pro izolaci změn kódu do stavu vlákna z bloků filtru volajících. Je však důležité, aby obslužná rutina výjimky byla správně zavedena, nebo tento problém nebude vyřešen. Následující příklad přepne jazykovou verzi uživatelského rozhraní, ale jakýkoli druh změny stavu vlákna může být podobně vystavený.  
  
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
  
 Správná oprava v tomto případě je zabalit existující blok **try**/**finally** do bloku **Try**/**catch** . Pouhým představením klauzule **catch-throw** do stávajícího bloku **Try**/**finally** problém neopraví, jak je znázorněno v následujícím příkladu.  
  
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
  
 Tím se problém nevyřeší, protože příkaz **finally** nebyl spuštěn dříve, než `FilterFunc` získá kontrolu.  
  
 Následující příklad opravuje problém tím, že zajišťuje, že klauzule **finally** byla provedena před tím, než nabídka vyvolá výjimky v blocích filtru výjimky volajících.  
  
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
