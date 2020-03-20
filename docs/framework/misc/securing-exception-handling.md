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
# <a name="securing-exception-handling"></a><span data-ttu-id="769bf-102">Zabezpečení zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="769bf-102">Securing Exception Handling</span></span>
<span data-ttu-id="769bf-103">V jazyce Visual C++ a Visual Basic, výraz filtru dále do zásobníku běží před všechny **finally** prohlášení.</span><span class="sxs-lookup"><span data-stu-id="769bf-103">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any **finally** statement.</span></span> <span data-ttu-id="769bf-104">Blok **catch** přidružený k tomuto filtru se spustí po příkazu **finally.**</span><span class="sxs-lookup"><span data-stu-id="769bf-104">The **catch** block associated with that filter runs after the **finally** statement.</span></span> <span data-ttu-id="769bf-105">Další informace naleznete v tématu [Použití výjimek filtrovaných uživatelem](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="769bf-105">For more information, see [Using User-Filtered Exceptions](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="769bf-106">Tato část zkoumá bezpečnostní důsledky tohoto pořadí.</span><span class="sxs-lookup"><span data-stu-id="769bf-106">This section examines the security implications of this order.</span></span> <span data-ttu-id="769bf-107">Vezměme si následující pseudocode příklad, který ilustruje pořadí, ve kterém filter příkazy a **nakonec** příkazy spustit.</span><span class="sxs-lookup"><span data-stu-id="769bf-107">Consider the following pseudocode example that illustrates the order in which filter statements and **finally** statements run.</span></span>  
  
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
  
 <span data-ttu-id="769bf-108">Tento kód vytiskne následující.</span><span class="sxs-lookup"><span data-stu-id="769bf-108">This code prints the following.</span></span>  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="769bf-109">Filtr se spustí před **příkazem finally,** takže problémy se zabezpečením mohou být zavedeny čímkoli, co provede změnu stavu, kde by mohlo využití spuštění jiného kódu.</span><span class="sxs-lookup"><span data-stu-id="769bf-109">The filter runs before the **finally** statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="769bf-110">Například:</span><span class="sxs-lookup"><span data-stu-id="769bf-110">For example:</span></span>  
  
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
  
 <span data-ttu-id="769bf-111">Tento pseudokód umožňuje filtr vyšší nahoru zásobníku spustit libovolný kód.</span><span class="sxs-lookup"><span data-stu-id="769bf-111">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="769bf-112">Další příklady operací, které by měly podobný účinek, jsou dočasné zosobnění jiné identity, nastavení vnitřního příznaku, který obchází některé kontroly zabezpečení, nebo změna jazykové verze přidružené k vláknu.</span><span class="sxs-lookup"><span data-stu-id="769bf-112">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="769bf-113">Doporučené řešení je zavést obslužnou rutinu výjimky izolovat změny kódu do stavu vlákna z bloků filtrů volajících.</span><span class="sxs-lookup"><span data-stu-id="769bf-113">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="769bf-114">Je však důležité, aby obslužná rutina výjimky byla správně zavedena nebo tento problém nebude opraven.</span><span class="sxs-lookup"><span data-stu-id="769bf-114">However, it is important that the exception handler be properly introduced or this problem will not be fixed.</span></span> <span data-ttu-id="769bf-115">Následující příklad přepne jazykovou verzi uživatelského rozhraní, ale jakýkoli druh změny stavu vlákna může být podobně vystavena.</span><span class="sxs-lookup"><span data-stu-id="769bf-115">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
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
  
 <span data-ttu-id="769bf-116">Správná oprava v tomto případě je zabalit existující **try**/**finally** blokovat v bloku **try**/**catch.**</span><span class="sxs-lookup"><span data-stu-id="769bf-116">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="769bf-117">Jednoduše zavedení **catch-throw** klauzule do existující **houštiny try**/**finally** problém nevyřeší, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="769bf-117">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="769bf-118">Problém se tím nevyřeší, protože příkaz **finally** nebyl spuštěn před tím, než získá `FilterFunc` kontrolu.</span><span class="sxs-lookup"><span data-stu-id="769bf-118">This does not fix the problem because the **finally** statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="769bf-119">Následující příklad řeší problém tím, že zajistí, že **klauzule finally** byla spuštěna před nabídkou výjimky do bloků filtru výjimek volajících.</span><span class="sxs-lookup"><span data-stu-id="769bf-119">The following example fixes the problem by ensuring that the **finally** clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="769bf-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="769bf-120">See also</span></span>

- [<span data-ttu-id="769bf-121">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="769bf-121">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
