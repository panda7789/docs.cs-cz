---
title: "Resume – příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Resume
- vb.ResumeNext
helpviewer_keywords:
- Next statement [Visual Basic], Resume
- Resume Next statement [Visual Basic]
- execution [Visual Basic], resuming
- run-time errors [Visual Basic], resuming after
- Resume statement [Visual Basic], syntax
- errors [Visual Basic], resuming after
- Error statement [Visual Basic], and Resume statement
- execution
- Resume statement [Visual Basic]
ms.assetid: e24d058b-1a5c-4274-acb9-7d295d3ea537
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3cb4334f302c07c81b6b8a7d0626be08cc69b1ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="resume-statement"></a><span data-ttu-id="38f7f-102">Resume – příkaz</span><span class="sxs-lookup"><span data-stu-id="38f7f-102">Resume Statement</span></span>
<span data-ttu-id="38f7f-103">Obnoví zpracování po dokončení rutiny chyba zpracování.</span><span class="sxs-lookup"><span data-stu-id="38f7f-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="38f7f-104">Doporučujeme použít strukturované zpracování výjimek ve vašem kódu, pokud je to možné, nikoli pomocí nestrukturovaných výjimek a `On Error` a `Resume` příkazy.</span><span class="sxs-lookup"><span data-stu-id="38f7f-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="38f7f-105">Další informace najdete v tématu [zkuste... Catch... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="38f7f-105">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38f7f-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38f7f-106">Syntax</span></span>  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="38f7f-107">Součásti</span><span class="sxs-lookup"><span data-stu-id="38f7f-107">Parts</span></span>  
 `Resume`  
 <span data-ttu-id="38f7f-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="38f7f-108">Required.</span></span> <span data-ttu-id="38f7f-109">Pokud k chybě došlo ve stejný postup jako obslužná rutina chyb, provádění obnoví pomocí příkazu, který způsobil chybu.</span><span class="sxs-lookup"><span data-stu-id="38f7f-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="38f7f-110">Pokud k chybě došlo v postupu názvem, provádění pokračuje v příkazu, který naposledy provedla volání mimo procedura obsahuje rutiny pro zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="38f7f-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="38f7f-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="38f7f-111">Optional.</span></span> <span data-ttu-id="38f7f-112">Pokud k chybě došlo ve stejný postup jako obslužná rutina chyb, provádění pokračuje s příkazem okamžitě následující příkaz, který chybu způsobil.</span><span class="sxs-lookup"><span data-stu-id="38f7f-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="38f7f-113">Pokud k chybě došlo v postupu názvem, provádění pokračuje s příkazem okamžitě následující příkaz, který naposledy provedla volání mimo procedura obsahuje rutiny pro zpracování chyb (nebo `On Error Resume Next` příkaz).</span><span class="sxs-lookup"><span data-stu-id="38f7f-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="38f7f-114">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="38f7f-114">Optional.</span></span> <span data-ttu-id="38f7f-115">Provádění pokračuje v řádku zadaný v požadovaných `line` argument.</span><span class="sxs-lookup"><span data-stu-id="38f7f-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="38f7f-116">`line` Argument je popisek čáry nebo číslo řádku a musí být v stejným způsobem jako obslužná rutina chyb.</span><span class="sxs-lookup"><span data-stu-id="38f7f-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="38f7f-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="38f7f-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38f7f-118">Doporučujeme použít strukturované zpracování výjimek ve vašem kódu, pokud je to možné, nikoli pomocí nestrukturovaných výjimek a `On Error` a `Resume` příkazy.</span><span class="sxs-lookup"><span data-stu-id="38f7f-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="38f7f-119">Další informace najdete v tématu [zkuste... Catch... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="38f7f-119">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="38f7f-120">Pokud používáte `Resume` příkaz kdekoli jinak než v rutiny zpracování chyb, dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="38f7f-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="38f7f-121">`Resume` Příkaz nelze použít v jakékoli postupu, který obsahuje `Try...Catch...Finally` příkaz.</span><span class="sxs-lookup"><span data-stu-id="38f7f-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38f7f-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="38f7f-122">Example</span></span>  
 <span data-ttu-id="38f7f-123">Tento příklad používá `Resume` příkaz k ukončení zpracování chyb v postupu a poté pokračovat v provádění pomocí příkazu, který způsobil chybu.</span><span class="sxs-lookup"><span data-stu-id="38f7f-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="38f7f-124">Číslo chyby 55 se vygeneruje pro ilustraci použití `Resume` příkaz.</span><span class="sxs-lookup"><span data-stu-id="38f7f-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/resume-statement_1.vb)]  
  
## <a name="requirements"></a><span data-ttu-id="38f7f-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="38f7f-125">Requirements</span></span>  
 <span data-ttu-id="38f7f-126">**Namespace:** [Microsoft.VisualBasic –](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="38f7f-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="38f7f-127">**Sestavení:** jazyka Visual Basic Runtime Library (v souboru Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="38f7f-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38f7f-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="38f7f-128">See Also</span></span>  
 [<span data-ttu-id="38f7f-129">Try... Catch... Finally – příkaz</span><span class="sxs-lookup"><span data-stu-id="38f7f-129">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="38f7f-130">Error – příkaz</span><span class="sxs-lookup"><span data-stu-id="38f7f-130">Error Statement</span></span>](../../../visual-basic/language-reference/statements/error-statement.md)  
 [<span data-ttu-id="38f7f-131">On Error – příkaz</span><span class="sxs-lookup"><span data-stu-id="38f7f-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
