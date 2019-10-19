---
title: End – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.End
- End
helpviewer_keywords:
- execution [Visual Basic], ending
- files [Visual Basic], closing
- End keyword [Visual Basic], End statements
- programs [Visual Basic], quitting
- code, exiting
- program termination
- End statement [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 0e64467c-0f34-4aab-9ddd-43f8b9d55d90
ms.openlocfilehash: 66dba1df125a08b8ae05519a0c66edb6da15ceaa
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583416"
---
# <a name="end-statement"></a><span data-ttu-id="f6bb8-102">End – příkaz</span><span class="sxs-lookup"><span data-stu-id="f6bb8-102">End Statement</span></span>
<span data-ttu-id="f6bb8-103">Okamžitě ukončí provádění.</span><span class="sxs-lookup"><span data-stu-id="f6bb8-103">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6bb8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6bb8-104">Syntax</span></span>  
  
```vb  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="f6bb8-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f6bb8-105">Remarks</span></span>  
 <span data-ttu-id="f6bb8-106">Příkaz `End` můžete umístit kamkoli do postupu pro vynucení, že se celá aplikace přestane spouštět.</span><span class="sxs-lookup"><span data-stu-id="f6bb8-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="f6bb8-107">`End` zavře všechny soubory otevřené pomocí příkazu `Open` a vymaže všechny proměnné aplikace.</span><span class="sxs-lookup"><span data-stu-id="f6bb8-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="f6bb8-108">Aplikace se zavře, jakmile neexistují žádné další programy, které by podržely odkazy na své objekty a žádný z jeho kódu není spuštěn.</span><span class="sxs-lookup"><span data-stu-id="f6bb8-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6bb8-109">Příkaz `End` zastaví provádění kódu náhlém způsobem a nevyvolává metodu `Dispose` nebo `Finalize` ani jiný kód Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f6bb8-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="f6bb8-110">Odkazy na objekty držené jinými programy jsou neověřené.</span><span class="sxs-lookup"><span data-stu-id="f6bb8-110">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="f6bb8-111">Pokud byl v rámci `Try` nebo `Catch` bloku nalezen příkaz `End`, ovládací prvek neprojde odpovídajícím `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="f6bb8-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="f6bb8-112">Příkaz `Stop` pozastaví provádění, ale na rozdíl od `End` nezavře žádné soubory ani nevymaže žádné proměnné, pokud se nevyskytly v kompilovaném spustitelném souboru (. exe).</span><span class="sxs-lookup"><span data-stu-id="f6bb8-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="f6bb8-113">Vzhledem k tomu, že `End` ukončí vaši aplikaci, aniž by se účastnila jakýchkoli prostředků, které by mohly být otevřené, měli byste se před použitím pokusit ukončit činnost.</span><span class="sxs-lookup"><span data-stu-id="f6bb8-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="f6bb8-114">Například pokud má vaše aplikace otevřené nějaké formuláře, měli byste je zavřít před tím, než ovládací prvek dosáhne příkazu `End`.</span><span class="sxs-lookup"><span data-stu-id="f6bb8-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="f6bb8-115">Měli byste použít `End` bez jakýchkoli potřeb, a to pouze v případě, že potřebujete okamžitě ukončit činnost.</span><span class="sxs-lookup"><span data-stu-id="f6bb8-115">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="f6bb8-116">Normální způsoby ukončení procedury ([příkaz return](../../../visual-basic/language-reference/statements/return-statement.md) a [příkaz exit](../../../visual-basic/language-reference/statements/exit-statement.md)) nezavřou pouze postup, ale také volajícímu kódu, aby příležitost uzavřela čistou činnost.</span><span class="sxs-lookup"><span data-stu-id="f6bb8-116">The normal ways to terminate a procedure ([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) and [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="f6bb8-117">Konzolová aplikace může například jednoduše `Return` z `Main`ho postupu.</span><span class="sxs-lookup"><span data-stu-id="f6bb8-117">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f6bb8-118">Příkaz `End` volá metodu <xref:System.Environment.Exit%2A> třídy <xref:System.Environment> v oboru názvů <xref:System>.</span><span class="sxs-lookup"><span data-stu-id="f6bb8-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="f6bb8-119"><xref:System.Environment.Exit%2A> vyžaduje, abyste měli `UnmanagedCode` oprávnění.</span><span class="sxs-lookup"><span data-stu-id="f6bb8-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="f6bb8-120">Pokud to neuděláte, dojde k chybě <xref:System.Security.SecurityException>.</span><span class="sxs-lookup"><span data-stu-id="f6bb8-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="f6bb8-121">Po následování dalšího klíčového slova [příkaz End \<keyword >](../../../visual-basic/language-reference/statements/end-keyword-statement.md) rozděluje konec definice příslušného postupu nebo bloku.</span><span class="sxs-lookup"><span data-stu-id="f6bb8-121">When followed by an additional keyword, [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="f6bb8-122">Například `End Function` ukončí definici `Function` postupu.</span><span class="sxs-lookup"><span data-stu-id="f6bb8-122">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f6bb8-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6bb8-123">Example</span></span>  
 <span data-ttu-id="f6bb8-124">Následující příklad používá příkaz `End` k ukončení provádění kódu, pokud si ho uživatel požádá.</span><span class="sxs-lookup"><span data-stu-id="f6bb8-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="f6bb8-125">Poznámky pro vývojáře inteligentního zařízení</span><span class="sxs-lookup"><span data-stu-id="f6bb8-125">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="f6bb8-126">Tento příkaz není podporován.</span><span class="sxs-lookup"><span data-stu-id="f6bb8-126">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6bb8-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6bb8-127">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [<span data-ttu-id="f6bb8-128">Příkaz Stop</span><span class="sxs-lookup"><span data-stu-id="f6bb8-128">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)
- [<span data-ttu-id="f6bb8-129">Příkaz end \<keyword ></span><span class="sxs-lookup"><span data-stu-id="f6bb8-129">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
