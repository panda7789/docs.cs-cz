---
title: Používání obslužných rutin uživatelsky filtrovaných výjimek
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
ms.openlocfilehash: 5537404178b746310f720c5b0c075c77287dda4c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708450"
---
# <a name="using-user-filtered-exception-handlers"></a><span data-ttu-id="b9d1b-102">Používání obslužných rutin uživatelsky filtrovaných výjimek</span><span class="sxs-lookup"><span data-stu-id="b9d1b-102">Using User-Filtered Exception Handlers</span></span>

<span data-ttu-id="b9d1b-103">V současné době Visual Basic podporuje výjimky filtrované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="b9d1b-103">Currently, Visual Basic supports user-filtered exceptions.</span></span> <span data-ttu-id="b9d1b-104">Uživatelsky filtrované obslužné rutiny výjimek zachytí a zpracovávají výjimky na základě požadavků, které definujete pro výjimku.</span><span class="sxs-lookup"><span data-stu-id="b9d1b-104">User-filtered exception handlers catch and handle exceptions based on requirements you define for the exception.</span></span> <span data-ttu-id="b9d1b-105">Tyto obslužné rutiny používají příkaz **catch** s klíčovým slovem **when** .</span><span class="sxs-lookup"><span data-stu-id="b9d1b-105">These handlers use the **Catch** statement with the **When** keyword.</span></span>  
  
 <span data-ttu-id="b9d1b-106">Tato technika je užitečná, když konkrétní objekt výjimky odpovídá více chybám.</span><span class="sxs-lookup"><span data-stu-id="b9d1b-106">This technique is useful when a particular exception object corresponds to multiple errors.</span></span> <span data-ttu-id="b9d1b-107">V takovém případě má objekt obvykle vlastnost, která obsahuje konkrétní kód chyby spojený s chybou.</span><span class="sxs-lookup"><span data-stu-id="b9d1b-107">In this case, the object typically has a property that contains the specific error code associated with the error.</span></span> <span data-ttu-id="b9d1b-108">Vlastnost kód chyby ve výrazu můžete použít k výběru pouze konkrétní chyby, kterou chcete v této klauzuli **catch** zpracovat.</span><span class="sxs-lookup"><span data-stu-id="b9d1b-108">You can use the error code property in the expression to select only the particular error you want to handle in that **Catch** clause.</span></span>  
  
 <span data-ttu-id="b9d1b-109">Následující příklad Visual Basic ukazuje příkaz **catch/when** .</span><span class="sxs-lookup"><span data-stu-id="b9d1b-109">The following Visual Basic example illustrates the **Catch/When** statement.</span></span>  
  
```vb
Try  
    'Try statements.  
    Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try  
```  
  
 <span data-ttu-id="b9d1b-110">Výraz klauzule filtrované uživatelem není nijak omezen.</span><span class="sxs-lookup"><span data-stu-id="b9d1b-110">The expression of the user-filtered clause is not restricted in any way.</span></span> <span data-ttu-id="b9d1b-111">Pokud při provádění výrazu filtrovaného uživatelem dojde k výjimce, je tato výjimka zahozena a výraz filtru je považován za vyhodnocený jako NEPRAVDA.</span><span class="sxs-lookup"><span data-stu-id="b9d1b-111">If an exception occurs during execution of the user-filtered expression, that exception is discarded and the filter expression is considered to have evaluated to false.</span></span> <span data-ttu-id="b9d1b-112">V takovém případě modul CLR (Common Language Runtime) pokračuje v hledání obslužné rutiny pro aktuální výjimku.</span><span class="sxs-lookup"><span data-stu-id="b9d1b-112">In this case, the common language runtime continues the search for a handler for the current exception.</span></span>  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a><span data-ttu-id="b9d1b-113">Kombinování konkrétní výjimky a uživatelem filtrovaných klauzulí</span><span class="sxs-lookup"><span data-stu-id="b9d1b-113">Combining the Specific Exception and the User-Filtered Clauses</span></span>  
 <span data-ttu-id="b9d1b-114">Příkaz catch může obsahovat konkrétní výjimku i klauzule filtrované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="b9d1b-114">A catch statement can contain both the specific exception and the user-filtered clauses.</span></span> <span data-ttu-id="b9d1b-115">Modul runtime nejprve testuje specifickou výjimku.</span><span class="sxs-lookup"><span data-stu-id="b9d1b-115">The runtime tests the specific exception first.</span></span> <span data-ttu-id="b9d1b-116">Pokud je specifická výjimka úspěšná, modul runtime spustí filtr uživatele.</span><span class="sxs-lookup"><span data-stu-id="b9d1b-116">If the specific exception succeeds, the runtime executes the user filter.</span></span> <span data-ttu-id="b9d1b-117">Obecný filtr může obsahovat odkaz na proměnnou deklarovanou ve filtru třídy.</span><span class="sxs-lookup"><span data-stu-id="b9d1b-117">The generic filter can contain a reference to the variable declared in the class filter.</span></span> <span data-ttu-id="b9d1b-118">Všimněte si, že pořadí dvou klauzulí filtru nelze vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="b9d1b-118">Note that the order of the two filter clauses cannot be reversed.</span></span>  
  
 <span data-ttu-id="b9d1b-119">Následující příklad Visual Basic ukazuje konkrétní výjimku `ClassLoadException` v příkazu **catch** a také klauzuli filtrovanou uživatelem pomocí klíčového slova **when** .</span><span class="sxs-lookup"><span data-stu-id="b9d1b-119">The following Visual Basic example shows the specific exception `ClassLoadException` in the **Catch** statement as well as the user-filtered clause using the **When** keyword.</span></span>  
  
```vb
Try  
    'Try statements.
    Catch cle As ClassLoadException When cle.IsRecoverable()  
    'Catch statements.
End Try  
```  

## <a name="see-also"></a><span data-ttu-id="b9d1b-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9d1b-120">See also</span></span>

- [<span data-ttu-id="b9d1b-121">Výjimky</span><span class="sxs-lookup"><span data-stu-id="b9d1b-121">Exceptions</span></span>](index.md)
