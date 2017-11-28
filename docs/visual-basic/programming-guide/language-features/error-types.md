---
title: Typy chyb (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- exceptions, types
- errors [Visual Basic], types
- errors [Visual Basic], logic
- errors [Visual Basic], syntax
- logic errors [Visual Basic], Visual Basic
- run-time errors [Visual Basic], types of errors
- syntax errors [Visual Basic], Visual Basic
ms.assetid: 3048aabf-8c97-4e13-9150-853769cb5f6f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e01ed588d284a475a537a5fcf5ca506d25ca69f1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="error-types-visual-basic"></a><span data-ttu-id="71940-102">Typy chyb (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="71940-102">Error Types (Visual Basic)</span></span>
<span data-ttu-id="71940-103">V [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], chyby (také nazývané *výjimky*) spadají do tří kategorií: chyby syntaxe, chyby a logiku chyby.</span><span class="sxs-lookup"><span data-stu-id="71940-103">In [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], errors (also called *exceptions*) fall into one of three categories: syntax errors, run-time errors, and logic errors.</span></span>  
  
## <a name="syntax-errors"></a><span data-ttu-id="71940-104">Chyby syntaxe</span><span class="sxs-lookup"><span data-stu-id="71940-104">Syntax Errors</span></span>  
 <span data-ttu-id="71940-105">*Chyby syntaxe* jsou ty, které se zobrazí při psaní kódu.</span><span class="sxs-lookup"><span data-stu-id="71940-105">*Syntax errors* are those that appear while you write code.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="71940-106">zkontroluje váš kód při psaní do **Editor kódu** okno a upozorní vás, pokud došlo k chybě, třeba Chyba v pravopisu slovo nebo element jazyk nesprávně.</span><span class="sxs-lookup"><span data-stu-id="71940-106"> checks your code as you type it in the **Code Editor** window and alerts you if you make a mistake, such as misspelling a word or using a language element improperly.</span></span> <span data-ttu-id="71940-107">Chyby syntaxe jsou nejběžnější typ chyby.</span><span class="sxs-lookup"><span data-stu-id="71940-107">Syntax errors are the most common type of errors.</span></span> <span data-ttu-id="71940-108">Můžete je vyřešit je snadno v kódování prostředí Jakmile k nim dojde.</span><span class="sxs-lookup"><span data-stu-id="71940-108">You can fix them easily in the coding environment as soon as they occur.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="71940-109">`Option Explicit` Příkaz je jeden z prostředků k zamezení chyby syntaxe.</span><span class="sxs-lookup"><span data-stu-id="71940-109">The `Option Explicit` statement is one means of avoiding syntax errors.</span></span> <span data-ttu-id="71940-110">Vynutí předem, deklarovat všechny proměnné, který se má použít v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="71940-110">It forces you to declare, in advance, all the variables to be used in the application.</span></span> <span data-ttu-id="71940-111">Proto když tyto proměnné se používají v kódu, typografické chyby jsou zachyceny okamžitě a odstraněny.</span><span class="sxs-lookup"><span data-stu-id="71940-111">Therefore, when those variables are used in the code, any typographic errors are caught immediately and can be fixed.</span></span>  
  
## <a name="run-time-errors"></a><span data-ttu-id="71940-112">Běhové chyby</span><span class="sxs-lookup"><span data-stu-id="71940-112">Run-Time Errors</span></span>  
 <span data-ttu-id="71940-113">*Běhové chyby* jsou ty, které zobrazují, jenom když zkompilování a spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="71940-113">*Run-time errors* are those that appear only after you compile and run your code.</span></span> <span data-ttu-id="71940-114">To zahrnuje kód, který může zdají být správná, v tom má žádné chyby syntaxe, ale nelze jej provést.</span><span class="sxs-lookup"><span data-stu-id="71940-114">These involve code that may appear to be correct in that it has no syntax errors, but that will not execute.</span></span> <span data-ttu-id="71940-115">Například může správně zapsat řádek kódu a otevřete soubor.</span><span class="sxs-lookup"><span data-stu-id="71940-115">For example, you might correctly write a line of code to open a file.</span></span> <span data-ttu-id="71940-116">Pokud soubor je poškozený, aplikace nelze provést, ale `Open` funkce a zastaví se.</span><span class="sxs-lookup"><span data-stu-id="71940-116">But if the file is corrupted, the application cannot carry out the `Open` function, and it stops running.</span></span> <span data-ttu-id="71940-117">Většina běhové chyby lze vyřešit přepsáním chybného kód a pak nutnosti rekompilace a znovu ji spustit.</span><span class="sxs-lookup"><span data-stu-id="71940-117">You can fix most run-time errors by rewriting the faulty code, and then recompiling and rerunning it.</span></span>  
  
## <a name="logic-errors"></a><span data-ttu-id="71940-118">Logické chyby</span><span class="sxs-lookup"><span data-stu-id="71940-118">Logic Errors</span></span>  
 <span data-ttu-id="71940-119">*Logické chyby* jsou ty, které je zaprotokolována jednou aplikace je používána.</span><span class="sxs-lookup"><span data-stu-id="71940-119">*Logic errors* are those that appear once the application is in use.</span></span> <span data-ttu-id="71940-120">Jsou většina nežádoucí nebo neočekávané výsledky v odpovědi na akce uživatele.</span><span class="sxs-lookup"><span data-stu-id="71940-120">They are most often unwanted or unexpected results in response to user actions.</span></span> <span data-ttu-id="71940-121">Například chybným klíč nebo jiných vnějších vliv může způsobit, že aplikace přestane fungovat v rámci očekávané parametry, nebo úplně.</span><span class="sxs-lookup"><span data-stu-id="71940-121">For example, a mistyped key or other outside influence might cause your application to stop working within expected parameters, or altogether.</span></span> <span data-ttu-id="71940-122">Logické chyby jsou obvykle nejtěžší typ opravit, protože není vždy jasné, které pocházejí.</span><span class="sxs-lookup"><span data-stu-id="71940-122">Logic errors are generally the hardest type to fix, since it is not always clear where they originate.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71940-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="71940-123">See Also</span></span>  
 [<span data-ttu-id="71940-124">Try... Catch... Finally – příkaz</span><span class="sxs-lookup"><span data-stu-id="71940-124">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="71940-125">Základy ladicího programu</span><span class="sxs-lookup"><span data-stu-id="71940-125">Debugger Basics</span></span>](/visualstudio/debugger/debugger-basics)
