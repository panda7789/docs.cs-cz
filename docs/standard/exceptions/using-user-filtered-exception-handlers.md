---
title: Používání obslužných rutin uživatelsky filtrovaných výjimek
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d1e771a95542153dfad0981d3198e6b4c31cdeb9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43890649"
---
# <a name="using-user-filtered-exception-handlers"></a><span data-ttu-id="53acb-102">Používání obslužných rutin uživatelsky filtrovaných výjimek</span><span class="sxs-lookup"><span data-stu-id="53acb-102">Using User-Filtered Exception Handlers</span></span>
<span data-ttu-id="53acb-103">Visual Basic v současné době podporuje uživatelsky filtrovaných výjimek.</span><span class="sxs-lookup"><span data-stu-id="53acb-103">Currently, Visual Basic supports user-filtered exceptions.</span></span> <span data-ttu-id="53acb-104">Obslužných rutin uživatelsky filtrovaných výjimek zachytit a zpracovat výjimky založené na požadavcích, které definujete pro výjimku.</span><span class="sxs-lookup"><span data-stu-id="53acb-104">User-filtered exception handlers catch and handle exceptions based on requirements you define for the exception.</span></span> <span data-ttu-id="53acb-105">Použijte tyto obslužné rutiny **Catch** příkaz **při** – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="53acb-105">These handlers use the **Catch** statement with the **When** keyword.</span></span>  
  
 <span data-ttu-id="53acb-106">Tato technika je užitečná, když určitý objekt výjimky odpovídá více chyb.</span><span class="sxs-lookup"><span data-stu-id="53acb-106">This technique is useful when a particular exception object corresponds to multiple errors.</span></span> <span data-ttu-id="53acb-107">V takovém případě objekt obvykle má vlastnost, která obsahuje chybový kód, který je přidružený k chybě.</span><span class="sxs-lookup"><span data-stu-id="53acb-107">In this case, the object typically has a property that contains the specific error code associated with the error.</span></span> <span data-ttu-id="53acb-108">Chcete-li vybrat pouze konkrétní chyba zpracování v, který můžete použít vlastnost chybového kódu ve výrazu **Catch** klauzuli.</span><span class="sxs-lookup"><span data-stu-id="53acb-108">You can use the error code property in the expression to select only the particular error you want to handle in that **Catch** clause.</span></span>  
  
 <span data-ttu-id="53acb-109">Ukazuje následující příklad jazyka Visual Basic **Catch/když** příkazu.</span><span class="sxs-lookup"><span data-stu-id="53acb-109">The following Visual Basic example illustrates the **Catch/When** statement.</span></span>  
  
```  
Try  
      'Try statements.  
   Catch When Err = VBErr_ClassLoadException  
      'Catch statements.  
End Try  
```  
  
 <span data-ttu-id="53acb-110">Výraz v klauzuli filtrované uživatele není omezeno žádným způsobem.</span><span class="sxs-lookup"><span data-stu-id="53acb-110">The expression of the user-filtered clause is not restricted in any way.</span></span> <span data-ttu-id="53acb-111">Pokud dojde k výjimce během zpracování výrazu uživatelsky filtrovaných, tato výjimka se zahodí a považován za výraz filtru má být vyhodnocen na hodnotu false.</span><span class="sxs-lookup"><span data-stu-id="53acb-111">If an exception occurs during execution of the user-filtered expression, that exception is discarded and the filter expression is considered to have evaluated to false.</span></span> <span data-ttu-id="53acb-112">V tomto případě common language runtime pokračuje v hledání pro obslužnou rutinu pro aktuální výjimku.</span><span class="sxs-lookup"><span data-stu-id="53acb-112">In this case, the common language runtime continues the search for a handler for the current exception.</span></span>  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a><span data-ttu-id="53acb-113">Kombinování specifické výjimky a uživatelsky filtrovaných klauzule</span><span class="sxs-lookup"><span data-stu-id="53acb-113">Combining the Specific Exception and the User-Filtered Clauses</span></span>  
 <span data-ttu-id="53acb-114">Příkaz catch může obsahovat určité výjimky a uživatelsky filtrovaných klauzule.</span><span class="sxs-lookup"><span data-stu-id="53acb-114">A catch statement can contain both the specific exception and the user-filtered clauses.</span></span> <span data-ttu-id="53acb-115">Modul runtime nejprve ověřuje určité výjimky.</span><span class="sxs-lookup"><span data-stu-id="53acb-115">The runtime tests the specific exception first.</span></span> <span data-ttu-id="53acb-116">Pokud bude úspěšné konkrétní výjimky, modul runtime spustí filtr uživatelů.</span><span class="sxs-lookup"><span data-stu-id="53acb-116">If the specific exception succeeds, the runtime executes the user filter.</span></span> <span data-ttu-id="53acb-117">Obecný filtr může obsahovat odkaz na proměnné deklarované ve třídě filtru.</span><span class="sxs-lookup"><span data-stu-id="53acb-117">The generic filter can contain a reference to the variable declared in the class filter.</span></span> <span data-ttu-id="53acb-118">Všimněte si, že pořadí dvou klauzulí filtru je nevratná.</span><span class="sxs-lookup"><span data-stu-id="53acb-118">Note that the order of the two filter clauses cannot be reversed.</span></span>  
  
 <span data-ttu-id="53acb-119">Ukazuje následující příklad jazyka Visual Basic specifickou výjimku `ClassLoadException` v **Catch** příkaz jako použití klauzule filtrované uživatelem **při** – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="53acb-119">The following Visual Basic example shows the specific exception `ClassLoadException` in the **Catch** statement as well as the user-filtered clause using the **When** keyword.</span></span>  
  
```  
Try  
      'Try statements.  
   Catch cle As ClassLoadException When cle.IsRecoverable()  
      'Catch statements.  
End Try  
```  

## <a name="see-also"></a><span data-ttu-id="53acb-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53acb-120">See also</span></span>

- [<span data-ttu-id="53acb-121">Výjimky</span><span class="sxs-lookup"><span data-stu-id="53acb-121">Exceptions</span></span>](index.md)
