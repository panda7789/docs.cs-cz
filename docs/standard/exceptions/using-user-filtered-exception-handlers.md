---
title: "Používání obslužných rutin uživatelsky filtrovaných výjimek"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a71a722063448fb0d568f4bfb4f71d4e01c57454
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="using-user-filtered-exception-handlers"></a><span data-ttu-id="778fa-102">Používání obslužných rutin uživatelsky filtrovaných výjimek</span><span class="sxs-lookup"><span data-stu-id="778fa-102">Using User-Filtered Exception Handlers</span></span>
<span data-ttu-id="778fa-103">Visual Basic v současné době podporuje uživatelem filtrované výjimky.</span><span class="sxs-lookup"><span data-stu-id="778fa-103">Currently, Visual Basic supports user-filtered exceptions.</span></span> <span data-ttu-id="778fa-104">Obslužných rutin uživatelsky filtrovaných výjimek catch a zpracování výjimek na základě požadavků, které definujete pro výjimku.</span><span class="sxs-lookup"><span data-stu-id="778fa-104">User-filtered exception handlers catch and handle exceptions based on requirements you define for the exception.</span></span> <span data-ttu-id="778fa-105">Použijte tyto obslužné rutiny **Catch** příkaz s **při** – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="778fa-105">These handlers use the **Catch** statement with the **When** keyword.</span></span>  
  
 <span data-ttu-id="778fa-106">Tato metoda je užitečná, když určitý objekt výjimky odpovídá více chybám.</span><span class="sxs-lookup"><span data-stu-id="778fa-106">This technique is useful when a particular exception object corresponds to multiple errors.</span></span> <span data-ttu-id="778fa-107">V takovém případě objekt obvykle má vlastnost, která obsahuje kód chyby související s chybou.</span><span class="sxs-lookup"><span data-stu-id="778fa-107">In this case, the object typically has a property that contains the specific error code associated with the error.</span></span> <span data-ttu-id="778fa-108">Můžete vlastnost kódu chyby ve výrazu a vyberte pouze konkrétní chyby chcete zpracovávat v tom, že **Catch** klauzule.</span><span class="sxs-lookup"><span data-stu-id="778fa-108">You can use the error code property in the expression to select only the particular error you want to handle in that **Catch** clause.</span></span>  
  
 <span data-ttu-id="778fa-109">Ukazuje následující příklad jazyka Visual Basic **Catch/When** příkaz.</span><span class="sxs-lookup"><span data-stu-id="778fa-109">The following Visual Basic example illustrates the **Catch/When** statement.</span></span>  
  
```  
Try  
      'Try statements.  
   Catch When Err = VBErr_ClassLoadException  
      'Catch statements.  
End Try  
```  
  
 <span data-ttu-id="778fa-110">Výraz klauzule uživatelem filtrované není omezena žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="778fa-110">The expression of the user-filtered clause is not restricted in any way.</span></span> <span data-ttu-id="778fa-111">Pokud dojde k výjimce během zpracování výrazu uživatelem filtrované, je tato výjimka zahozena a výraz filtru je považován za vyhodnocení na hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="778fa-111">If an exception occurs during execution of the user-filtered expression, that exception is discarded and the filter expression is considered to have evaluated to false.</span></span> <span data-ttu-id="778fa-112">V tomto případě common language runtime pokračuje v hledání pro obslužnou rutinu pro aktuální výjimku.</span><span class="sxs-lookup"><span data-stu-id="778fa-112">In this case, the common language runtime continues the search for a handler for the current exception.</span></span>  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a><span data-ttu-id="778fa-113">Kombinování specifických výjimek a klauzulích uživatelem filtrované</span><span class="sxs-lookup"><span data-stu-id="778fa-113">Combining the Specific Exception and the User-Filtered Clauses</span></span>  
 <span data-ttu-id="778fa-114">Příkaz catch může obsahovat specifických výjimek a uživatelem filtrované klauzule.</span><span class="sxs-lookup"><span data-stu-id="778fa-114">A catch statement can contain both the specific exception and the user-filtered clauses.</span></span> <span data-ttu-id="778fa-115">Modul runtime nejprve testuje specifickou výjimku.</span><span class="sxs-lookup"><span data-stu-id="778fa-115">The runtime tests the specific exception first.</span></span> <span data-ttu-id="778fa-116">Pokud je specifická výjimka úspěšná, modul runtime provede filtru uživatelů.</span><span class="sxs-lookup"><span data-stu-id="778fa-116">If the specific exception succeeds, the runtime executes the user filter.</span></span> <span data-ttu-id="778fa-117">Obecný filtr může obsahovat odkaz na proměnnou uvedenou ve filtru třídy.</span><span class="sxs-lookup"><span data-stu-id="778fa-117">The generic filter can contain a reference to the variable declared in the class filter.</span></span> <span data-ttu-id="778fa-118">Všimněte si, že pořadí dvou klauzulí filtru nelze vrátit zpět.</span><span class="sxs-lookup"><span data-stu-id="778fa-118">Note that the order of the two filter clauses cannot be reversed.</span></span>  
  
 <span data-ttu-id="778fa-119">Následující příklad jazyka Visual Basic ukazuje specifickou výjimku `ClassLoadException` v **Catch** prohlášení, jakož i pomocí klauzule uživatelem filtrované **při** – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="778fa-119">The following Visual Basic example shows the specific exception `ClassLoadException` in the **Catch** statement as well as the user-filtered clause using the **When** keyword.</span></span>  
  
```  
Try  
      'Try statements.  
   Catch cle As ClassLoadException When cle.IsRecoverable()  
      'Catch statements.  
End Try  
```  

## <a name="see-also"></a><span data-ttu-id="778fa-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="778fa-120">See Also</span></span>
[<span data-ttu-id="778fa-121">Výjimky</span><span class="sxs-lookup"><span data-stu-id="778fa-121">Exceptions</span></span>](index.md)
