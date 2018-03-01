---
title: "Zabezpečení zpracování výjimek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 548606a0196012fdd21bf5512e8ea7b089c723ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="securing-exception-handling"></a><span data-ttu-id="6b6bc-102">Zabezpečení zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="6b6bc-102">Securing Exception Handling</span></span>
<span data-ttu-id="6b6bc-103">V jazyce Visual Basic a Visual C++, výraz filtru další až stack spouští před spuštěním **nakonec** příkaz.</span><span class="sxs-lookup"><span data-stu-id="6b6bc-103">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any **finally** statement.</span></span> <span data-ttu-id="6b6bc-104">**Catch** bloku přidružený tento filtr se spouští **nakonec** příkaz.</span><span class="sxs-lookup"><span data-stu-id="6b6bc-104">The **catch** block associated with that filter runs after the **finally** statement.</span></span> <span data-ttu-id="6b6bc-105">Další informace najdete v tématu [Using User-Filtered výjimky](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="6b6bc-105">For more information, see [Using User-Filtered Exceptions](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="6b6bc-106">Tento oddíl se zabývá bezpečnostních důsledcích tohoto pořadí.</span><span class="sxs-lookup"><span data-stu-id="6b6bc-106">This section examines the security implications of this order.</span></span> <span data-ttu-id="6b6bc-107">Vezměte v úvahu následující příklad pseudokódu, který znázorňuje pořadí, ve které příkazy filtru a **nakonec** příkazy spustit.</span><span class="sxs-lookup"><span data-stu-id="6b6bc-107">Consider the following pseudocode example that illustrates the order in which filter statements and **finally** statements run.</span></span>  
  
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
  
 <span data-ttu-id="6b6bc-108">Tento kód vypíše následující.</span><span class="sxs-lookup"><span data-stu-id="6b6bc-108">This code prints the following.</span></span>  
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="6b6bc-109">Filtr se spouští před **nakonec** prohlášení, takže problémy se zabezpečením mohou být způsobeny všechno, co způsobuje změnu, kde může využít provádění jiný kód stavu.</span><span class="sxs-lookup"><span data-stu-id="6b6bc-109">The filter runs before the **finally** statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="6b6bc-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6b6bc-110">For example:</span></span>  
  
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
  
 <span data-ttu-id="6b6bc-111">Tento pseudokód umožňuje vyšší nahoru v zásobníku spustit libovolný kód filtru.</span><span class="sxs-lookup"><span data-stu-id="6b6bc-111">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="6b6bc-112">Další příklady operací, které by mělo podobné účinek jsou dočasné zosobnění jiného identitu, nastavení interní příznak, který obchází některé kontroly zabezpečení nebo změna jazykovou verzi přidružené vlákno.</span><span class="sxs-lookup"><span data-stu-id="6b6bc-112">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="6b6bc-113">Doporučené řešení je zavedení obslužné rutiny výjimek izolovat změny kódu stavu vlákna od bloky filtru volajícího.</span><span class="sxs-lookup"><span data-stu-id="6b6bc-113">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="6b6bc-114">Je důležité, aby byla správně zavedena obslužná rutina výjimky nebo však tento problém nebude vyřešen.</span><span class="sxs-lookup"><span data-stu-id="6b6bc-114">However, it is important that the exception handler be properly introduced or this problem will not be fixed.</span></span> <span data-ttu-id="6b6bc-115">Následující příklad změní jazyková verze uživatelského rozhraní, ale může podobně zveřejněné libovolnému druhu změny stavu přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="6b6bc-115">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
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
  
 <span data-ttu-id="6b6bc-116">V takovém případě je správná oprava zabalit existující **zkuste**/**nakonec** blokovat **zkuste**/**catch** blok.</span><span class="sxs-lookup"><span data-stu-id="6b6bc-116">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="6b6bc-117">Jednoduché zavedení **catch-throw** klauzule do existujících **zkuste**/**nakonec** bloku problém neodstraní, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6b6bc-117">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="6b6bc-118">Tato akce neodstraní problém protože **nakonec** ještě nebyl spuštěn příkaz `FilterFunc` získá ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="6b6bc-118">This does not fix the problem because the **finally** statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="6b6bc-119">Následující příklad odstraňuje problém, přičemž zajistí, aby **nakonec** klauzule provedla před nabízející bloky filtru výjimek volajícího.</span><span class="sxs-lookup"><span data-stu-id="6b6bc-119">The following example fixes the problem by ensuring that the **finally** clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6b6bc-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b6bc-120">See Also</span></span>  
 [<span data-ttu-id="6b6bc-121">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="6b6bc-121">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
