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
ms.openlocfilehash: 864ac5ef1713f8ffa93c18accede8ecd5b3b7a8c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604422"
---
# <a name="end-statement"></a><span data-ttu-id="72be3-102">End – příkaz</span><span class="sxs-lookup"><span data-stu-id="72be3-102">End Statement</span></span>
<span data-ttu-id="72be3-103">Ukončí provádění okamžitě.</span><span class="sxs-lookup"><span data-stu-id="72be3-103">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72be3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72be3-104">Syntax</span></span>  
  
```  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="72be3-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="72be3-105">Remarks</span></span>  
 <span data-ttu-id="72be3-106">Můžete umístit `End` příkaz kdekoli v proceduře vynutit bude celá aplikace zastavení.</span><span class="sxs-lookup"><span data-stu-id="72be3-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="72be3-107">`End` Zavře všechny soubory otevřené se `Open` prohlášení a vymaže všechny aplikace proměnné.</span><span class="sxs-lookup"><span data-stu-id="72be3-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="72be3-108">Aplikace se zavře, jakmile nejsou žádné další programy, která uchovává odkazy na jeho objekty a žádný z jeho kód běží.</span><span class="sxs-lookup"><span data-stu-id="72be3-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72be3-109">`End` Příkaz náhle zastaví spuštění kódu a nevyvolá `Dispose` nebo `Finalize` metoda nebo jakýkoli jiný kód jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="72be3-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="72be3-110">Odkazy na objekty ukládaná jinými programy jsou zneplatněny.</span><span class="sxs-lookup"><span data-stu-id="72be3-110">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="72be3-111">Pokud `End` je příkaz zjistil v rámci `Try` nebo `Catch` bloku řízení nepředává do odpovídajících `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="72be3-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="72be3-112">`Stop` Příkaz pozastaví spuštění, ale na rozdíl od `End`, nemá zavřete všechny soubory, nebo zrušte všechny proměnné, pokud se vyskytuje v kompilovaném spustitelný soubor (.exe) soubor.</span><span class="sxs-lookup"><span data-stu-id="72be3-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="72be3-113">Protože `End` ukončí aplikaci bez vaši účast na všechny prostředky, které může být otevřený, že byste měli zkusit zavřete dolů ještě jednou před jeho použitím.</span><span class="sxs-lookup"><span data-stu-id="72be3-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="72be3-114">Například pokud vaše aplikace nemá žádné formuláře otevřete, zavřete je před dosáhnou ovládacího prvku `End` příkaz.</span><span class="sxs-lookup"><span data-stu-id="72be3-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="72be3-115">Měli byste použít `End` pouze a pouze pokud je třeba ukončit okamžitě.</span><span class="sxs-lookup"><span data-stu-id="72be3-115">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="72be3-116">Běžné způsoby ukončit procedury ([příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md) a [ukončení příkazu](../../../visual-basic/language-reference/statements/exit-statement.md)) nejen zavřít řízení, které ještě jednou, ale také poskytnout kód volání možnost Zavřít ještě jednou.</span><span class="sxs-lookup"><span data-stu-id="72be3-116">The normal ways to terminate a procedure ([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) and [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="72be3-117">Konzolové aplikace, například můžete jednoduše `Return` z `Main` postupu.</span><span class="sxs-lookup"><span data-stu-id="72be3-117">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="72be3-118">`End` Příkaz volání <xref:System.Environment.Exit%2A> metodu <xref:System.Environment> třídy v <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="72be3-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="72be3-119"><xref:System.Environment.Exit%2A> vyžaduje, abyste měli `UnmanagedCode` oprávnění.</span><span class="sxs-lookup"><span data-stu-id="72be3-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="72be3-120">Pokud ho použít nechcete, <xref:System.Security.SecurityException> dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="72be3-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="72be3-121">Když následuje další klíčové slovo, [End \<– klíčové slovo > příkaz](../../../visual-basic/language-reference/statements/end-keyword-statement.md) určí konec definici vhodný postup uvedený nebo bloku.</span><span class="sxs-lookup"><span data-stu-id="72be3-121">When followed by an additional keyword, [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="72be3-122">Například `End Function` ukončí definice `Function` postupu.</span><span class="sxs-lookup"><span data-stu-id="72be3-122">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72be3-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="72be3-123">Example</span></span>  
 <span data-ttu-id="72be3-124">Následující příklad používá `End` příkaz k ukončení provádění kódu, pokud uživatel požaduje.</span><span class="sxs-lookup"><span data-stu-id="72be3-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 [!code-vb[VbVersHelp60Controls#64](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/end-statement_1.vb)]  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="72be3-125">Poznámky pro vývojáře inteligentního zařízení</span><span class="sxs-lookup"><span data-stu-id="72be3-125">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="72be3-126">Tento příkaz není podporován.</span><span class="sxs-lookup"><span data-stu-id="72be3-126">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72be3-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="72be3-127">See Also</span></span>  
 <xref:System.Security.Permissions.SecurityPermissionFlag>  
 [<span data-ttu-id="72be3-128">Příkaz Stop</span><span class="sxs-lookup"><span data-stu-id="72be3-128">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)  
 [<span data-ttu-id="72be3-129">End \<– klíčové slovo > – příkaz</span><span class="sxs-lookup"><span data-stu-id="72be3-129">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
