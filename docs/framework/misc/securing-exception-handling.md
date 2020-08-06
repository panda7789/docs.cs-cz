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
# <a name="securing-exception-handling"></a><span data-ttu-id="c5067-104">Zabezpečení zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="c5067-104">Securing Exception Handling</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="c5067-105">V Visual C++ a Visual Basic se výraz filtru podrobněji spouští před jakýmkoli `finally` příkazem.</span><span class="sxs-lookup"><span data-stu-id="c5067-105">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any `finally` statement.</span></span> <span data-ttu-id="c5067-106">Blok **catch** přidružený k tomuto filtru se spustí po `finally` příkazu.</span><span class="sxs-lookup"><span data-stu-id="c5067-106">The **catch** block associated with that filter runs after the `finally` statement.</span></span> <span data-ttu-id="c5067-107">Další informace najdete v tématu [použití uživatelem filtrovaných výjimek](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="c5067-107">For more information, see [Using User-Filtered Exceptions](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="c5067-108">V této části se prohlíží vlivem na zabezpečení tohoto pořadí.</span><span class="sxs-lookup"><span data-stu-id="c5067-108">This section examines the security implications of this order.</span></span> <span data-ttu-id="c5067-109">Vezměte v úvahu následující příklad pseudokódu, který ukazuje pořadí, ve kterém se spouštějí příkazy filtru a `finally` příkazy.</span><span class="sxs-lookup"><span data-stu-id="c5067-109">Consider the following pseudocode example that illustrates the order in which filter statements and `finally` statements run.</span></span>  
  
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
  
 <span data-ttu-id="c5067-110">Tento kód vytiskne následující.</span><span class="sxs-lookup"><span data-stu-id="c5067-110">This code prints the following.</span></span>  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="c5067-111">Filtr se spustí před `finally` příkazem, takže problémy se zabezpečením mohou být provedeny cokoli, co provede změnu stavu, kde může využít jiný kód.</span><span class="sxs-lookup"><span data-stu-id="c5067-111">The filter runs before the `finally` statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="c5067-112">Příklad:</span><span class="sxs-lookup"><span data-stu-id="c5067-112">For example:</span></span>  
  
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
  
 <span data-ttu-id="c5067-113">Tento pseudokódu umožňuje filtru zvýšit množství zásobníku tak, aby běžel libovolný kód.</span><span class="sxs-lookup"><span data-stu-id="c5067-113">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="c5067-114">Další příklady operací, které by měly podobný účinek, jsou dočasné zosobnění jiné identity, nastavení interního příznaku, který obchází určitou kontrolu zabezpečení nebo změnu jazykové verze přidružené k vláknu.</span><span class="sxs-lookup"><span data-stu-id="c5067-114">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="c5067-115">Doporučené řešení je zavedení obslužné rutiny výjimky pro izolaci změn kódu do stavu vlákna z bloků filtru volajících.</span><span class="sxs-lookup"><span data-stu-id="c5067-115">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="c5067-116">Je však důležité správně zavést obslužnou rutinu výjimky nebo tento problém nebude vyřešen.</span><span class="sxs-lookup"><span data-stu-id="c5067-116">However, it's important to properly introduce the exception handler or this problem won't be fixed.</span></span> <span data-ttu-id="c5067-117">Následující příklad přepne jazykovou verzi uživatelského rozhraní, ale jakýkoli druh změny stavu vlákna může být podobně vystavený.</span><span class="sxs-lookup"><span data-stu-id="c5067-117">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
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
  
 <span data-ttu-id="c5067-118">Správná oprava v tomto případě je zabalit existující blok **Try** / **finally** do bloku **Try** / **catch** .</span><span class="sxs-lookup"><span data-stu-id="c5067-118">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="c5067-119">Pouhým představením klauzule **catch-throw** do stávajícího bloku **Try** / **finally** nedojde k vyřešení problému, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c5067-119">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="c5067-120">Tím se problém nevyřeší, protože `finally` příkaz nebyl spuštěn před tím, než `FilterFunc` získá ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="c5067-120">This does not fix the problem because the `finally` statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="c5067-121">Následující příklad opravuje problém tím, že zajistí, že `finally` byla klauzule provedena před tím, než nabídka vyvolá výjimku v blocích filtru výjimky volajících.</span><span class="sxs-lookup"><span data-stu-id="c5067-121">The following example fixes the problem by ensuring that the `finally` clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c5067-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="c5067-122">See also</span></span>

- [<span data-ttu-id="c5067-123">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="c5067-123">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
