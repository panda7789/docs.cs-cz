---
title: Chybové zprávy (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- errors [Visual Basic]
- error messages
- trappable errors
- errors [Visual Basic], trappable
ms.assetid: f2dda05b-baef-41f5-8bb1-598bd7cf239f
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f7f5138d430e6737a4a8a47d4a800905dedff660
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="error-messages-visual-basic"></a><span data-ttu-id="e3af5-102">Chybové zprávy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e3af5-102">Error Messages (Visual Basic)</span></span>
<span data-ttu-id="e3af5-103">Při zápisu, kompilaci nebo spuštění aplikace Visual Basic, se může objevit následující typy chyb:</span><span class="sxs-lookup"><span data-stu-id="e3af5-103">When you write, compile, or run a Visual Basic application, the following types of errors can occur:</span></span>  
  
1.  <span data-ttu-id="e3af5-104">Chyby při návrhu, ke kterým dochází při psaní aplikace v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e3af5-104">Design-time errors, which occur when you write an application in Visual Studio.</span></span>  
  
2.  <span data-ttu-id="e3af5-105">Chyby při kompilaci, ke kterým dochází při kompilaci aplikace v sadě Visual Studio nebo na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="e3af5-105">Compile-time errors, which occur when you compile an application in Visual Studio or at a command prompt.</span></span>  
  
3.  <span data-ttu-id="e3af5-106">Běhové chyby, ke kterým dochází při spuštění aplikace v sadě Visual Studio nebo samostatný spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="e3af5-106">Run-time errors, which occur when you run an application in Visual Studio or as a stand-alone executable file.</span></span>  
  
 <span data-ttu-id="e3af5-107">Informace o řešení potíží s konkrétní chyby najdete v tématu [další zdroje pro programátory v jazyce Visual Basic](../../../visual-basic/getting-started/additional-resources.md).</span><span class="sxs-lookup"><span data-stu-id="e3af5-107">For information about how to troubleshoot a specific error, see [Additional Resources for Visual Basic Programmers](../../../visual-basic/getting-started/additional-resources.md).</span></span>  
  
## <a name="run-time-errors"></a><span data-ttu-id="e3af5-108">Chyby runtime</span><span class="sxs-lookup"><span data-stu-id="e3af5-108">Run Time Errors</span></span>  
 <span data-ttu-id="e3af5-109">Pokud aplikace Visual Basic se pokusí provést akce, která systém nemůže spustit, dojde k chybě běhu, a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] vyvolá `Exception` objektu.</span><span class="sxs-lookup"><span data-stu-id="e3af5-109">If a Visual Basic application tries to perform an action that the system can't execute, a run-time error occurs, and [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] throws an `Exception` object.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="e3af5-110">může generovat vlastní chyby o všech datech typ, včetně `Exception` objekty, pomocí `Throw` příkaz.</span><span class="sxs-lookup"><span data-stu-id="e3af5-110"> can generate custom errors of any data type, including `Exception` objects, by using the `Throw` statement.</span></span> <span data-ttu-id="e3af5-111">Aplikace můžete identifikovat chyba zobrazením číslo chyby a zprávy zachycení výjimky.</span><span class="sxs-lookup"><span data-stu-id="e3af5-111">An application can identify the error by displaying the error number and message of a caught exception.</span></span> <span data-ttu-id="e3af5-112">Pokud není zachycena chybu, aplikace se ukončí.</span><span class="sxs-lookup"><span data-stu-id="e3af5-112">If an error isn't caught, the application ends.</span></span>  
  
 <span data-ttu-id="e3af5-113">Kód můžete depeše a zkontrolujte chyby.</span><span class="sxs-lookup"><span data-stu-id="e3af5-113">The code can trap and examine run-time errors.</span></span> <span data-ttu-id="e3af5-114">Pokud je kód, který generuje chyby v uzavřít `Try` blok, můžete zachytit chyby výjimce dojde v rámci odpovídající `Catch` bloku.</span><span class="sxs-lookup"><span data-stu-id="e3af5-114">If you enclose the code that produces the error in a `Try` block, you can catch any thrown error within a matching `Catch` block.</span></span> <span data-ttu-id="e3af5-115">Informace o tom, jak depeše chyby za běhu a reagovat na ně ve vašem kódu najdete v tématu [zkuste... Catch... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="e3af5-115">For information about how to trap errors at run time and respond to them in your code, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="compile-time-errors"></a><span data-ttu-id="e3af5-116">Čas chyby kompilace</span><span class="sxs-lookup"><span data-stu-id="e3af5-116">Compile Time Errors</span></span>  
 <span data-ttu-id="e3af5-117">Pokud Visual Basic – kompilátor narazí na problém v kódu, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="e3af5-117">If the Visual Basic compiler encounters a problem in the code, a compile-time error occurs.</span></span> <span data-ttu-id="e3af5-118">V editoru kódu můžete snadno identifikovat které řádek kódu způsobil chybu, protože vlnovka se zobrazí v části tohoto řádku kódu.</span><span class="sxs-lookup"><span data-stu-id="e3af5-118">In the Code Editor, you can easily identify which line of code caused the error because a wavy line appears under that line of code.</span></span> <span data-ttu-id="e3af5-119">Pokud jste buď bodu vlnovkou nebo otevřené, zobrazí se chybová zpráva **seznam chyb**, který také ukazuje další zprávy.</span><span class="sxs-lookup"><span data-stu-id="e3af5-119">The error message appears if you either point to the wavy underline or open the **Error List**, which also shows other messages.</span></span>  
  
 <span data-ttu-id="e3af5-120">Pokud má identifikátor vlnovkou a posledního znaku podtržen krátký, můžete vygenerovat zástupnou proceduru pro třídu, konstruktor, metoda, vlastnost, pole nebo výčet.</span><span class="sxs-lookup"><span data-stu-id="e3af5-120">If an identifier has a wavy underline and a short underline appears under the rightmost character, you can generate a stub for the class, constructor, method, property, field or enum.</span></span> <span data-ttu-id="e3af5-121">Další informace najdete v tématu [generování před využitím](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage).</span><span class="sxs-lookup"><span data-stu-id="e3af5-121">For more information, see [Generate From Usage](/visualstudio/ide/visual-csharp-intellisense#generate-from-usage).</span></span>
  
 <span data-ttu-id="e3af5-122">Vyřešte upozornění kompilátoru jazyka Visual Basic, je možné napsat kód, který běží rychleji a má méně chyby.</span><span class="sxs-lookup"><span data-stu-id="e3af5-122">By resolving warnings from the Visual Basic compiler, you might be able to write code that runs faster and has fewer bugs.</span></span> <span data-ttu-id="e3af5-123">Tato upozornění identifikovat kód, který může způsobit chyby, pokud je aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="e3af5-123">These warnings identify code that may cause errors when the application is run.</span></span> <span data-ttu-id="e3af5-124">Například kompilátor varuje, můžete Pokud se pokusíte volají člena nepřiřazené objektové proměnné, vraťte zpět z funkce bez nastavení návratovou hodnotu nebo spuštění `Try` bloku s chybami v logika pro zachycení výjimky.</span><span class="sxs-lookup"><span data-stu-id="e3af5-124">For example, the compiler warns you if you try to invoke a member of an unassigned object variable, return from a function without setting the return value, or execute a `Try` block with errors in the logic to catch exceptions.</span></span> <span data-ttu-id="e3af5-125">Další informace o upozornění, včetně toho, jak je zapnout a vypnout, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="e3af5-125">For more information about warnings, including how to turn them on and off, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>
