---
title: End – příkaz
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
ms.openlocfilehash: fe17a82662c4014069c77f2da76723a051ab9084
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404703"
---
# <a name="end-statement"></a><span data-ttu-id="25ae6-102">End – příkaz</span><span class="sxs-lookup"><span data-stu-id="25ae6-102">End Statement</span></span>
<span data-ttu-id="25ae6-103">Okamžitě ukončí provádění.</span><span class="sxs-lookup"><span data-stu-id="25ae6-103">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25ae6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25ae6-104">Syntax</span></span>  
  
```vb  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="25ae6-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25ae6-105">Remarks</span></span>  
 <span data-ttu-id="25ae6-106">Příkaz lze umístit `End` kdekoli v proceduře pro vynucení zastavení celé aplikace.</span><span class="sxs-lookup"><span data-stu-id="25ae6-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="25ae6-107">`End`zavře všechny soubory otevřené `Open` příkazem a vymaže všechny proměnné aplikace.</span><span class="sxs-lookup"><span data-stu-id="25ae6-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="25ae6-108">Aplikace se zavře, jakmile neexistují žádné další programy, které by podržely odkazy na své objekty a žádný z jeho kódu není spuštěn.</span><span class="sxs-lookup"><span data-stu-id="25ae6-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25ae6-109">`End`Příkaz zastaví provádění kódu náhlé a nevyvolává `Dispose` metodu or ani `Finalize` žádný jiný kód Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="25ae6-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="25ae6-110">Odkazy na objekty držené jinými programy jsou neověřené.</span><span class="sxs-lookup"><span data-stu-id="25ae6-110">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="25ae6-111">Pokud `End` se v rámci bloku nebo vyskytne příkaz `Try` `Catch` , ovládací prvek neprojde odpovídajícím `Finally` blokem.</span><span class="sxs-lookup"><span data-stu-id="25ae6-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="25ae6-112">`Stop`Příkaz pozastaví provádění, ale na rozdíl od `End` , neuzavře žádné soubory ani nevymaže žádné proměnné, pokud se nevyskytly v kompilovaném spustitelném souboru (. exe).</span><span class="sxs-lookup"><span data-stu-id="25ae6-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="25ae6-113">Vzhledem k tomu, že `End` aplikace ukončí aplikaci bez účasti na jakýchkoli prostředcích, které mohou být otevřeny, měli byste se před použitím pokusit ukončit činnost.</span><span class="sxs-lookup"><span data-stu-id="25ae6-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="25ae6-114">Například pokud má vaše aplikace otevřené nějaké formuláře, měli byste je před tím, než ovládací prvek dosáhne `End` příkazu, zavřít.</span><span class="sxs-lookup"><span data-stu-id="25ae6-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="25ae6-115">Měli byste používat `End` jenom zřídka a jenom v případě, že potřebujete okamžitě skončit.</span><span class="sxs-lookup"><span data-stu-id="25ae6-115">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="25ae6-116">Normální způsoby ukončení procedury ([příkaz return](return-statement.md) a [příkaz exit](exit-statement.md)) nezavřou pouze postup, ale také volajícímu kódu, aby příležitost uzavřela čistou činnost.</span><span class="sxs-lookup"><span data-stu-id="25ae6-116">The normal ways to terminate a procedure ([Return Statement](return-statement.md) and [Exit Statement](exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="25ae6-117">Konzolová aplikace může být například jednoduše `Return` z `Main` procedury.</span><span class="sxs-lookup"><span data-stu-id="25ae6-117">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="25ae6-118">`End`Příkaz volá <xref:System.Environment.Exit%2A> metodu <xref:System.Environment> třídy v <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="25ae6-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="25ae6-119"><xref:System.Environment.Exit%2A>vyžaduje, abyste měli `UnmanagedCode` oprávnění.</span><span class="sxs-lookup"><span data-stu-id="25ae6-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="25ae6-120">Pokud to neuděláte, <xref:System.Security.SecurityException> dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="25ae6-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="25ae6-121">Když následuje klíčové slovo Next, [ \<keyword> příkaz end](end-keyword-statement.md) rozděluje konec definice příslušného postupu nebo bloku.</span><span class="sxs-lookup"><span data-stu-id="25ae6-121">When followed by an additional keyword, [End \<keyword> Statement](end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="25ae6-122">Například `End Function` ukončí definici `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="25ae6-122">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25ae6-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="25ae6-123">Example</span></span>  
 <span data-ttu-id="25ae6-124">Následující příklad používá `End` příkaz k ukončení provádění kódu, pokud si ho uživatel požádá.</span><span class="sxs-lookup"><span data-stu-id="25ae6-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="25ae6-125">Poznámky pro vývojáře inteligentního zařízení</span><span class="sxs-lookup"><span data-stu-id="25ae6-125">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="25ae6-126">Tento příkaz není podporován.</span><span class="sxs-lookup"><span data-stu-id="25ae6-126">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25ae6-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="25ae6-127">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [<span data-ttu-id="25ae6-128">Stop – příkaz</span><span class="sxs-lookup"><span data-stu-id="25ae6-128">Stop Statement</span></span>](stop-statement.md)
- [<span data-ttu-id="25ae6-129">\<keyword>Příkaz end</span><span class="sxs-lookup"><span data-stu-id="25ae6-129">End \<keyword> Statement</span></span>](end-keyword-statement.md)
