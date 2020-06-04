---
title: Resume – příkaz
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
ms.openlocfilehash: 3f49f05f1deb2027b03bbf3443ca44f30c44344e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404210"
---
# <a name="resume-statement"></a><span data-ttu-id="01541-102">Resume – příkaz</span><span class="sxs-lookup"><span data-stu-id="01541-102">Resume Statement</span></span>
<span data-ttu-id="01541-103">Po dokončení rutiny zpracování chyb pokračuje v provádění.</span><span class="sxs-lookup"><span data-stu-id="01541-103">Resumes execution after an error-handling routine is finished.</span></span>  
  
 <span data-ttu-id="01541-104">Doporučujeme, abyste ve svém kódu používali strukturované zpracování výjimek, kdykoli je to možné, místo použití nestrukturovaných zpracování výjimek `On Error` a `Resume` příkazů a.</span><span class="sxs-lookup"><span data-stu-id="01541-104">We suggest that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="01541-105">Další informace najdete v tématu [Try... Zachytit... Finally – příkaz](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="01541-105">For more information, see [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01541-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01541-106">Syntax</span></span>  
  
```vb  
Resume [ Next | line ]  
```  
  
## <a name="parts"></a><span data-ttu-id="01541-107">Součásti</span><span class="sxs-lookup"><span data-stu-id="01541-107">Parts</span></span>  
 `Resume`  
 <span data-ttu-id="01541-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="01541-108">Required.</span></span> <span data-ttu-id="01541-109">Pokud k chybě došlo ve stejné proceduře jako obslužná rutina chyby, spuštění pokračuje s příkazem, který způsobil chybu.</span><span class="sxs-lookup"><span data-stu-id="01541-109">If the error occurred in the same procedure as the error handler, execution resumes with the statement that caused the error.</span></span> <span data-ttu-id="01541-110">Pokud k chybě došlo v volané proceduře, spuštění pokračuje na příkazu, který naposledy volal proceduru, která obsahuje rutinu zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="01541-110">If the error occurred in a called procedure, execution resumes at the statement that last called out of the procedure containing the error-handling routine.</span></span>  
  
 `Next`  
 <span data-ttu-id="01541-111">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="01541-111">Optional.</span></span> <span data-ttu-id="01541-112">Pokud k chybě došlo ve stejné proceduře jako obslužná rutina chyby, provádění pokračuje příkazem hned po příkazu, který způsobil chybu.</span><span class="sxs-lookup"><span data-stu-id="01541-112">If the error occurred in the same procedure as the error handler, execution resumes with the statement immediately following the statement that caused the error.</span></span> <span data-ttu-id="01541-113">Pokud k chybě došlo v volané proceduře, provádění pokračuje příkazem ihned po příkazu, který byl naposledy volán z procedury obsahující rutinu zpracování chyb (nebo `On Error Resume Next` příkazu).</span><span class="sxs-lookup"><span data-stu-id="01541-113">If the error occurred in a called procedure, execution resumes with the statement immediately following the statement that last called out of the procedure containing the error-handling routine (or `On Error Resume Next` statement).</span></span>  
  
 `line`  
 <span data-ttu-id="01541-114">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="01541-114">Optional.</span></span> <span data-ttu-id="01541-115">Spuštění pokračuje na řádku zadaném v požadovaném `line` argumentu.</span><span class="sxs-lookup"><span data-stu-id="01541-115">Execution resumes at the line specified in the required `line` argument.</span></span> <span data-ttu-id="01541-116">`line`Argument je popisek řádku nebo číslo řádku a musí být ve stejném postupu jako obslužná rutina chyby.</span><span class="sxs-lookup"><span data-stu-id="01541-116">The `line` argument is a line label or line number and must be in the same procedure as the error handler.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01541-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01541-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01541-118">Doporučujeme používat strukturované zpracování výjimek v kódu, kdykoli je to možné, místo použití nestrukturovaného zpracování výjimek a `On Error` `Resume` příkazů a.</span><span class="sxs-lookup"><span data-stu-id="01541-118">We recommend that you use structured exception handling in your code whenever possible, rather than using unstructured exception handling and the `On Error` and `Resume` statements.</span></span> <span data-ttu-id="01541-119">Další informace najdete v tématu [Try... Zachytit... Finally – příkaz](try-catch-finally-statement.md).</span><span class="sxs-lookup"><span data-stu-id="01541-119">For more information, see [Try...Catch...Finally Statement](try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="01541-120">Použijete-li `Resume` příkaz kdekoli jinde než v rutině zpracování chyb, dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="01541-120">If you use a `Resume` statement anywhere other than in an error-handling routine, an error occurs.</span></span>  
  
 <span data-ttu-id="01541-121">`Resume`Příkaz nelze použít v žádné proceduře, která obsahuje `Try...Catch...Finally` příkaz.</span><span class="sxs-lookup"><span data-stu-id="01541-121">The `Resume` statement cannot be used in any procedure that contains a `Try...Catch...Finally` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="01541-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="01541-122">Example</span></span>  
 <span data-ttu-id="01541-123">V tomto příkladu se používá `Resume` příkaz k ukončení zpracování chyb v proceduře a následné pokračování v provádění s příkazem, který způsobil chybu.</span><span class="sxs-lookup"><span data-stu-id="01541-123">This example uses the `Resume` statement to end error handling in a procedure and then resume execution with the statement that caused the error.</span></span> <span data-ttu-id="01541-124">K ilustraci použití příkazu se generuje číslo chyby 55 `Resume` .</span><span class="sxs-lookup"><span data-stu-id="01541-124">Error number 55 is generated to illustrate use of the `Resume` statement.</span></span>  
  
 [!code-vb[VbVbalrErrorHandling#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrErrorHandling/VB/Class1.vb#16)]  
  
## <a name="requirements"></a><span data-ttu-id="01541-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="01541-125">Requirements</span></span>  
 <span data-ttu-id="01541-126">**Obor názvů:** [Microsoft. VisualBasic](../runtime-library-members.md)</span><span class="sxs-lookup"><span data-stu-id="01541-126">**Namespace:** [Microsoft.VisualBasic](../runtime-library-members.md)</span></span>  
  
 <span data-ttu-id="01541-127">**Sestavení:** Knihovna Visual Basic runtime (v souboru Microsoft. VisualBasic. dll)</span><span class="sxs-lookup"><span data-stu-id="01541-127">**Assembly:** Visual Basic Runtime Library (in Microsoft.VisualBasic.dll)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01541-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="01541-128">See also</span></span>

- [<span data-ttu-id="01541-129">Try...Catch....Finally – příkaz</span><span class="sxs-lookup"><span data-stu-id="01541-129">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="01541-130">Error – příkaz</span><span class="sxs-lookup"><span data-stu-id="01541-130">Error Statement</span></span>](error-statement.md)
- [<span data-ttu-id="01541-131">On Error – příkaz</span><span class="sxs-lookup"><span data-stu-id="01541-131">On Error Statement</span></span>](on-error-statement.md)
