---
title: Resume – příkaz (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 796342d17b0d0f1a642aff381274746d1fda3559
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783913"
---
# <a name="resume-statement"></a><span data-ttu-id="0a553-102">Resume – příkaz</span><span class="sxs-lookup"><span data-stu-id="0a553-102">Resume Statement</span></span>
<span data-ttu-id="0a553-103">Pokračuje v provádění po dokončení rutiny zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="0a553-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="0a553-104">Doporučujeme používat strukturované zpracování výjimek ve vašem kódu, kdykoli je to možné, spíš než nestrukturované zpracování výjimek a `On Error` a `Resume` příkazy.</span><span class="sxs-lookup"><span data-stu-id="0a553-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="0a553-105">Další informace najdete v tématu [zkuste... Catch... Příkaz finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0a553-105">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a553-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a553-106">Syntax</span></span>  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="0a553-107">Součásti</span><span class="sxs-lookup"><span data-stu-id="0a553-107">Parts</span></span>  
 `Resume`  
 <span data-ttu-id="0a553-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="0a553-108">Required.</span></span> <span data-ttu-id="0a553-109">Pokud k chybě došlo ve stejné proceduře jako obslužná rutina chyb, provádění pokračuje s příkazem, který způsobil chybu.</span><span class="sxs-lookup"><span data-stu-id="0a553-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="0a553-110">Pokud k chybě došlo ve volané procedury, provádění pokračuje v příkazu, který naposledy provedla volání mimo procedura obsahuje rutiny pro zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="0a553-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="0a553-111">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="0a553-111">Optional.</span></span> <span data-ttu-id="0a553-112">Pokud k chybě došlo ve stejné proceduře jako obslužná rutina chyb, provádění pokračuje s příkazem bezprostředně následující příkaz, který způsobil chybu.</span><span class="sxs-lookup"><span data-stu-id="0a553-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="0a553-113">Pokud k chybě došlo ve volané procedury, provádění pokračuje s příkazem okamžitě po příkazu, který naposledy provedla volání mimo procedura obsahuje rutiny pro zpracování chyb (nebo `On Error Resume Next` příkaz).</span><span class="sxs-lookup"><span data-stu-id="0a553-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="0a553-114">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="0a553-114">Optional.</span></span> <span data-ttu-id="0a553-115">Provádění pokračuje na řádku zadaném v požadovaném `line` argument.</span><span class="sxs-lookup"><span data-stu-id="0a553-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="0a553-116">`line` Argument popisku řádku nebo číslo řádku a musí být ve stejné proceduře jako obslužná rutina chyb.</span><span class="sxs-lookup"><span data-stu-id="0a553-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0a553-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0a553-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0a553-118">Doporučujeme používat strukturované zpracování výjimek ve vašem kódu, kdykoli je to možné, spíš než nestrukturované zpracování výjimek a `On Error` a `Resume` příkazy.</span><span class="sxs-lookup"><span data-stu-id="0a553-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="0a553-119">Další informace najdete v tématu [zkuste... Catch... Příkaz finally](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0a553-119">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="0a553-120">Pokud používáte `Resume` příkaz kdekoli jinak než v rutiny zpracování chyb, dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="0a553-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="0a553-121">`Resume` Příkaz nelze použít v všechny procedury, které obsahuje `Try...Catch...Finally` příkazu.</span><span class="sxs-lookup"><span data-stu-id="0a553-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a553-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a553-122">Example</span></span>  
 <span data-ttu-id="0a553-123">V tomto příkladu `Resume` příkazu k ukončení zpracování chyb v proceduru a poté pokračovat v provádění pomocí příkazu, který způsobil chybu.</span><span class="sxs-lookup"><span data-stu-id="0a553-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="0a553-124">Číslo chyby 55 se vygeneruje pro ilustraci použití `Resume` příkazu.</span><span class="sxs-lookup"><span data-stu-id="0a553-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a><span data-ttu-id="0a553-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0a553-125">Requirements</span></span>  
 <span data-ttu-id="0a553-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="0a553-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="0a553-127">**Sestavení:** Visual Basic Runtime Library (v souboru Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="0a553-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a553-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a553-128">See also</span></span>

- [<span data-ttu-id="0a553-129">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="0a553-129">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="0a553-130">Příkaz Error</span><span class="sxs-lookup"><span data-stu-id="0a553-130">Error Statement</span></span>](../../../visual-basic/language-reference/statements/error-statement.md)
- [<span data-ttu-id="0a553-131">Příkaz On Error</span><span class="sxs-lookup"><span data-stu-id="0a553-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
