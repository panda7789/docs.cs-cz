---
title: Používání obslužných rutin uživatelsky filtrovaných výjimek
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
ms.openlocfilehash: 5537404178b746310f720c5b0c075c77287dda4c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708450"
---
# <a name="using-user-filtered-exception-handlers"></a><span data-ttu-id="66650-102">Používání obslužných rutin uživatelsky filtrovaných výjimek</span><span class="sxs-lookup"><span data-stu-id="66650-102">Using User-Filtered Exception Handlers</span></span>

<span data-ttu-id="66650-103">V současné době jazyk Visual Basic podporuje výjimky filtrované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="66650-103">Currently, Visual Basic supports user-filtered exceptions.</span></span> <span data-ttu-id="66650-104">Uživatelem filtrované obslužné rutiny výjimek zachycují a zpracovávají výjimky na základě požadavků, které definujete pro výjimku.</span><span class="sxs-lookup"><span data-stu-id="66650-104">User-filtered exception handlers catch and handle exceptions based on requirements you define for the exception.</span></span> <span data-ttu-id="66650-105">Tyto obslužné rutiny používají **Catch** prohlášení s **When** klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="66650-105">These handlers use the **Catch** statement with the **When** keyword.</span></span>  
  
 <span data-ttu-id="66650-106">Tato technika je užitečná, když konkrétní objekt výjimky odpovídá více chybám.</span><span class="sxs-lookup"><span data-stu-id="66650-106">This technique is useful when a particular exception object corresponds to multiple errors.</span></span> <span data-ttu-id="66650-107">V tomto případě objekt má obvykle vlastnost, která obsahuje konkrétní kód chyby spojené s chybou.</span><span class="sxs-lookup"><span data-stu-id="66650-107">In this case, the object typically has a property that contains the specific error code associated with the error.</span></span> <span data-ttu-id="66650-108">Vlastnost kódu chyby ve výrazu můžete použít k výběru pouze konkrétní chyby, kterou chcete zpracovat v této klauzuli **Catch.**</span><span class="sxs-lookup"><span data-stu-id="66650-108">You can use the error code property in the expression to select only the particular error you want to handle in that **Catch** clause.</span></span>  
  
 <span data-ttu-id="66650-109">Následující příklad jazyka znázorňuje **catch/When** prohlášení.</span><span class="sxs-lookup"><span data-stu-id="66650-109">The following Visual Basic example illustrates the **Catch/When** statement.</span></span>  
  
```vb
Try  
    'Try statements.  
    Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try  
```  
  
 <span data-ttu-id="66650-110">Výraz uživatelem filtrované klauzule není žádným způsobem omezen.</span><span class="sxs-lookup"><span data-stu-id="66650-110">The expression of the user-filtered clause is not restricted in any way.</span></span> <span data-ttu-id="66650-111">Pokud dojde k výjimce během provádění výrazu filtrovaného uživatelem, je tato výjimka zahozena a výraz filtru je považován za vyhodnocený jako nepravdivý.</span><span class="sxs-lookup"><span data-stu-id="66650-111">If an exception occurs during execution of the user-filtered expression, that exception is discarded and the filter expression is considered to have evaluated to false.</span></span> <span data-ttu-id="66650-112">V tomto případě za běhu společného jazyka pokračuje hledání obslužné rutiny pro aktuální výjimku.</span><span class="sxs-lookup"><span data-stu-id="66650-112">In this case, the common language runtime continues the search for a handler for the current exception.</span></span>  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a><span data-ttu-id="66650-113">Kombinace konkrétní výjimky a klauzulí filtrovaných uživatelem</span><span class="sxs-lookup"><span data-stu-id="66650-113">Combining the Specific Exception and the User-Filtered Clauses</span></span>  
 <span data-ttu-id="66650-114">Příkaz catch může obsahovat konkrétní výjimku a klauzule filtrované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="66650-114">A catch statement can contain both the specific exception and the user-filtered clauses.</span></span> <span data-ttu-id="66650-115">Za běhu nejprve testuje konkrétní výjimku.</span><span class="sxs-lookup"><span data-stu-id="66650-115">The runtime tests the specific exception first.</span></span> <span data-ttu-id="66650-116">Pokud je konkrétní výjimka úspěšná, runtime spustí filtr uživatele.</span><span class="sxs-lookup"><span data-stu-id="66650-116">If the specific exception succeeds, the runtime executes the user filter.</span></span> <span data-ttu-id="66650-117">Obecný filtr může obsahovat odkaz na proměnnou deklarovanou ve filtru třídy.</span><span class="sxs-lookup"><span data-stu-id="66650-117">The generic filter can contain a reference to the variable declared in the class filter.</span></span> <span data-ttu-id="66650-118">Všimněte si, že pořadí dvou klauzulí filtru nelze stornovat.</span><span class="sxs-lookup"><span data-stu-id="66650-118">Note that the order of the two filter clauses cannot be reversed.</span></span>  
  
 <span data-ttu-id="66650-119">Následující příklad jazyka znázorňuje `ClassLoadException` konkrétní výjimku v **Catch** prohlášení, stejně jako uživatelem filtrované klauzule pomocí **When** klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="66650-119">The following Visual Basic example shows the specific exception `ClassLoadException` in the **Catch** statement as well as the user-filtered clause using the **When** keyword.</span></span>  
  
```vb
Try  
    'Try statements.
    Catch cle As ClassLoadException When cle.IsRecoverable()  
    'Catch statements.
End Try  
```  

## <a name="see-also"></a><span data-ttu-id="66650-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="66650-120">See also</span></span>

- [<span data-ttu-id="66650-121">Výjimky</span><span class="sxs-lookup"><span data-stu-id="66650-121">Exceptions</span></span>](index.md)
