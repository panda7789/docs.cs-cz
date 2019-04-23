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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173670"
---
# <a name="securing-exception-handling"></a><span data-ttu-id="8a72b-102">Zabezpečení zpracování výjimek</span><span class="sxs-lookup"><span data-stu-id="8a72b-102">Securing Exception Handling</span></span>
<span data-ttu-id="8a72b-103">V jazyce Visual C++ a Visual Basic, výraz filtru zásobníkem dále spouští před jakoukoli **nakonec** příkazu.</span><span class="sxs-lookup"><span data-stu-id="8a72b-103">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any **finally** statement.</span></span> <span data-ttu-id="8a72b-104">**Catch** bloku přidružené k tento filtr se spouští **nakonec** příkazu.</span><span class="sxs-lookup"><span data-stu-id="8a72b-104">The **catch** block associated with that filter runs after the **finally** statement.</span></span> <span data-ttu-id="8a72b-105">Další informace najdete v tématu [Using User-Filtered výjimky](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="8a72b-105">For more information, see [Using User-Filtered Exceptions](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="8a72b-106">Tento oddíl se zabývá bezpečnostních důsledcích tohoto pořadí.</span><span class="sxs-lookup"><span data-stu-id="8a72b-106">This section examines the security implications of this order.</span></span> <span data-ttu-id="8a72b-107">Vezměte v úvahu následující pseudokódu příklad, který znázorňuje pořadí, ve které příkazů filtru a **nakonec** příkazy.</span><span class="sxs-lookup"><span data-stu-id="8a72b-107">Consider the following pseudocode example that illustrates the order in which filter statements and **finally** statements run.</span></span>  
  
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
  
 <span data-ttu-id="8a72b-108">Tento kód zobrazí následující.</span><span class="sxs-lookup"><span data-stu-id="8a72b-108">This code prints the following.</span></span>  
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="8a72b-109">Filtr spuštěn dříve, než **nakonec** příkazu, takže problémy se zabezpečením může být zavedené prostřednictvím cokoli, z čeho změnu, ve kterém by mohla využívat spuštění jiného kódu stavu.</span><span class="sxs-lookup"><span data-stu-id="8a72b-109">The filter runs before the **finally** statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="8a72b-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="8a72b-110">For example:</span></span>  
  
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
  
 <span data-ttu-id="8a72b-111">Tato pseudokódu umožňuje vyšší zásobníkem spustit libovolný kód filtru.</span><span class="sxs-lookup"><span data-stu-id="8a72b-111">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="8a72b-112">Další příklady operace, které by obsahovat podobný vliv jsou dočasné zosobnění jiného identitu, nastavení interní příznak, který obchází některé kontroly zabezpečení nebo změna jazykové verze přidružené vlákno.</span><span class="sxs-lookup"><span data-stu-id="8a72b-112">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="8a72b-113">Doporučené řešení je zavést obslužná rutina výjimky k izolaci změn kódu stavu vlákna od bloky filtru volajícího.</span><span class="sxs-lookup"><span data-stu-id="8a72b-113">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="8a72b-114">Ale je důležité, aby obslužná rutina výjimky správně zavést nebo tento problém nebude vyřešen.</span><span class="sxs-lookup"><span data-stu-id="8a72b-114">However, it is important that the exception handler be properly introduced or this problem will not be fixed.</span></span> <span data-ttu-id="8a72b-115">V následujícím příkladu se přepne jazykové verze uživatelského rozhraní, ale libovolnému druhu změny stavu vlákno může být vystavena podobně.</span><span class="sxs-lookup"><span data-stu-id="8a72b-115">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
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
  
 <span data-ttu-id="8a72b-116">Správné opravy v tomto případě je zabalit existující **zkuste**/**nakonec** blokovat **zkuste**/**catch** blok.</span><span class="sxs-lookup"><span data-stu-id="8a72b-116">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="8a72b-117">Jednoduše Představujeme **catch throw** klauzuli do existujících **zkuste**/**nakonec** bloku problém neodstraní, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8a72b-117">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="8a72b-118">Tato akce neodstraní problém vzhledem k tomu **nakonec** ještě nebyl spuštěn příkaz `FilterFunc` získáním ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8a72b-118">This does not fix the problem because the **finally** statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="8a72b-119">V následujícím příkladu řeší problém tím, že zajišťuje, že **nakonec** klauzule byl proveden před nabízející bloky filtru výjimky volajícím.</span><span class="sxs-lookup"><span data-stu-id="8a72b-119">The following example fixes the problem by ensuring that the **finally** clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8a72b-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a72b-120">See also</span></span>

- [<span data-ttu-id="8a72b-121">Pokyny pro zabezpečené kódování</span><span class="sxs-lookup"><span data-stu-id="8a72b-121">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
