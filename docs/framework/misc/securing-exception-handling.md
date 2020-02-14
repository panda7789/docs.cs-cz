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
# <a name="securing-exception-handling"></a><span data-ttu-id="ebb44-102">Zabezpečení zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="ebb44-102">Securing Exception Handling</span></span>
<span data-ttu-id="ebb44-103">V vizuálů C++ a Visual Basic výraz filtru podrobněji sestaví běh před jakýmkoli příkazem **finally** .</span><span class="sxs-lookup"><span data-stu-id="ebb44-103">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any **finally** statement.</span></span> <span data-ttu-id="ebb44-104">Blok **catch** přidružený k tomuto filtru se spustí po příkazu **finally** .</span><span class="sxs-lookup"><span data-stu-id="ebb44-104">The **catch** block associated with that filter runs after the **finally** statement.</span></span> <span data-ttu-id="ebb44-105">Další informace najdete v tématu [použití uživatelem filtrovaných výjimek](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="ebb44-105">For more information, see [Using User-Filtered Exceptions](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="ebb44-106">V této části se prohlíží vlivem na zabezpečení tohoto pořadí.</span><span class="sxs-lookup"><span data-stu-id="ebb44-106">This section examines the security implications of this order.</span></span> <span data-ttu-id="ebb44-107">Vezměte v úvahu následující příklad pseudokódu, který znázorňuje pořadí, ve kterém se spouštějí příkazy filtru a příkazy **finally** .</span><span class="sxs-lookup"><span data-stu-id="ebb44-107">Consider the following pseudocode example that illustrates the order in which filter statements and **finally** statements run.</span></span>  
  
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
  
 <span data-ttu-id="ebb44-108">Tento kód vytiskne následující.</span><span class="sxs-lookup"><span data-stu-id="ebb44-108">This code prints the following.</span></span>  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="ebb44-109">Filtr se spustí před příkazem **finally** , takže problémy se zabezpečením mohou být provedeny cokoli, co provede změnu stavu, kde může využít jiný kód.</span><span class="sxs-lookup"><span data-stu-id="ebb44-109">The filter runs before the **finally** statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="ebb44-110">Například:</span><span class="sxs-lookup"><span data-stu-id="ebb44-110">For example:</span></span>  
  
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
  
 <span data-ttu-id="ebb44-111">Tento pseudokódu umožňuje filtru zvýšit množství zásobníku tak, aby běžel libovolný kód.</span><span class="sxs-lookup"><span data-stu-id="ebb44-111">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="ebb44-112">Další příklady operací, které by měly podobný účinek, jsou dočasné zosobnění jiné identity, nastavení interního příznaku, který obchází určitou kontrolu zabezpečení nebo změnu jazykové verze přidružené k vláknu.</span><span class="sxs-lookup"><span data-stu-id="ebb44-112">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="ebb44-113">Doporučené řešení je zavedení obslužné rutiny výjimky pro izolaci změn kódu do stavu vlákna z bloků filtru volajících.</span><span class="sxs-lookup"><span data-stu-id="ebb44-113">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="ebb44-114">Je však důležité, aby obslužná rutina výjimky byla správně zavedena, nebo tento problém nebude vyřešen.</span><span class="sxs-lookup"><span data-stu-id="ebb44-114">However, it is important that the exception handler be properly introduced or this problem will not be fixed.</span></span> <span data-ttu-id="ebb44-115">Následující příklad přepne jazykovou verzi uživatelského rozhraní, ale jakýkoli druh změny stavu vlákna může být podobně vystavený.</span><span class="sxs-lookup"><span data-stu-id="ebb44-115">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
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
  
 <span data-ttu-id="ebb44-116">Správná oprava v tomto případě je zabalit existující blok **try**/**finally** do bloku **Try**/**catch** .</span><span class="sxs-lookup"><span data-stu-id="ebb44-116">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="ebb44-117">Pouhým představením klauzule **catch-throw** do stávajícího bloku **Try**/**finally** problém neopraví, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ebb44-117">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="ebb44-118">Tím se problém nevyřeší, protože příkaz **finally** nebyl spuštěn dříve, než `FilterFunc` získá kontrolu.</span><span class="sxs-lookup"><span data-stu-id="ebb44-118">This does not fix the problem because the **finally** statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="ebb44-119">Následující příklad opravuje problém tím, že zajišťuje, že klauzule **finally** byla provedena před tím, než nabídka vyvolá výjimky v blocích filtru výjimky volajících.</span><span class="sxs-lookup"><span data-stu-id="ebb44-119">The following example fixes the problem by ensuring that the **finally** clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="ebb44-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="ebb44-120">See also</span></span>

- [<span data-ttu-id="ebb44-121">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="ebb44-121">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
