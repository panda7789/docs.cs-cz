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
ms.openlocfilehash: 884bdaa0c19508b5a6bf6377568a53acc6880518
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957680"
---
# <a name="resume-statement"></a><span data-ttu-id="ea64e-102">Resume – příkaz</span><span class="sxs-lookup"><span data-stu-id="ea64e-102">Resume Statement</span></span>
<span data-ttu-id="ea64e-103">Po dokončení rutiny zpracování chyb pokračuje v provádění.</span><span class="sxs-lookup"><span data-stu-id="ea64e-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="ea64e-104">Doporučujeme, abyste ve svém kódu používali strukturované zpracování výjimek, kdykoli je to možné, místo použití nestrukturovaných zpracování výjimek `On Error` a `Resume` příkazů a.</span><span class="sxs-lookup"><span data-stu-id="ea64e-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="ea64e-105">Další informace najdete v tématu [Try... Zachytit... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ea64e-105">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea64e-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea64e-106">Syntax</span></span>  
  
```  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="ea64e-107">Součásti</span><span class="sxs-lookup"><span data-stu-id="ea64e-107">Parts</span></span>  
 `Resume`  
 <span data-ttu-id="ea64e-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="ea64e-108">Required.</span></span> <span data-ttu-id="ea64e-109">Pokud k chybě došlo ve stejné proceduře jako obslužná rutina chyby, spuštění pokračuje s příkazem, který způsobil chybu.</span><span class="sxs-lookup"><span data-stu-id="ea64e-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="ea64e-110">Pokud k chybě došlo v volané proceduře, spuštění pokračuje na příkazu, který naposledy volal proceduru, která obsahuje rutinu zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="ea64e-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="ea64e-111">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="ea64e-111">Optional.</span></span> <span data-ttu-id="ea64e-112">Pokud k chybě došlo ve stejné proceduře jako obslužná rutina chyby, provádění pokračuje příkazem hned po příkazu, který způsobil chybu.</span><span class="sxs-lookup"><span data-stu-id="ea64e-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="ea64e-113">Pokud k chybě došlo v volané proceduře, provádění pokračuje příkazem ihned po příkazu, který byl naposledy volán z procedury obsahující rutinu zpracování chyb (nebo `On Error Resume Next` příkazu).</span><span class="sxs-lookup"><span data-stu-id="ea64e-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="ea64e-114">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="ea64e-114">Optional.</span></span> <span data-ttu-id="ea64e-115">Spuštění pokračuje na řádku zadaném v požadovaném `line` argumentu.</span><span class="sxs-lookup"><span data-stu-id="ea64e-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="ea64e-116">`line` Argument je popisek řádku nebo číslo řádku a musí být ve stejném postupu jako obslužná rutina chyby.</span><span class="sxs-lookup"><span data-stu-id="ea64e-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ea64e-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ea64e-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ea64e-118">Doporučujeme používat strukturované zpracování výjimek v kódu, kdykoli je to možné, místo použití nestrukturovaného zpracování výjimek a `On Error` příkazů a. `Resume`</span><span class="sxs-lookup"><span data-stu-id="ea64e-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="ea64e-119">Další informace najdete v tématu [Try... Zachytit... Finally – příkaz](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ea64e-119">For more information, see [Try...Catch...Finally Statement](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="ea64e-120">Použijete- `Resume` li příkaz kdekoli jinde než v rutině zpracování chyb, dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="ea64e-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="ea64e-121">Příkaz nelze použít v žádné proceduře, která `Try...Catch...Finally` obsahuje příkaz. `Resume`</span><span class="sxs-lookup"><span data-stu-id="ea64e-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea64e-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="ea64e-122">Example</span></span>  
 <span data-ttu-id="ea64e-123">V tomto příkladu se `Resume` používá příkaz k ukončení zpracování chyb v proceduře a následné pokračování v provádění s příkazem, který způsobil chybu.</span><span class="sxs-lookup"><span data-stu-id="ea64e-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="ea64e-124">K ilustraci použití `Resume` příkazu se generuje číslo chyby 55.</span><span class="sxs-lookup"><span data-stu-id="ea64e-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a><span data-ttu-id="ea64e-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ea64e-125">Requirements</span></span>  
 <span data-ttu-id="ea64e-126">**Hosting** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="ea64e-126">**Namespace:** [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="ea64e-127">**Shromážděním** Visual Basic Runtime Library (v souboru Microsoft.VisualBasic.dll)</span><span class="sxs-lookup"><span data-stu-id="ea64e-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea64e-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea64e-128">See also</span></span>

- [<span data-ttu-id="ea64e-129">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="ea64e-129">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="ea64e-130">Příkaz Error</span><span class="sxs-lookup"><span data-stu-id="ea64e-130">Error Statement</span></span>](../../../visual-basic/language-reference/statements/error-statement.md)
- [<span data-ttu-id="ea64e-131">Příkaz On Error</span><span class="sxs-lookup"><span data-stu-id="ea64e-131">On Error Statement</span></span>](../../../visual-basic/language-reference/statements/on-error-statement.md)
