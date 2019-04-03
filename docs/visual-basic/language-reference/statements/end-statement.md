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
ms.openlocfilehash: 4fc4fd36fb6b057195e9d8a79eb0a5b3ac9ff95c
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58832018"
---
# <a name="end-statement"></a><span data-ttu-id="788dd-102">End – příkaz</span><span class="sxs-lookup"><span data-stu-id="788dd-102">End Statement</span></span>
<span data-ttu-id="788dd-103">Ukončí provádění okamžitě.</span><span class="sxs-lookup"><span data-stu-id="788dd-103">Terminates execution immediately.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="788dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="788dd-104">Syntax</span></span>  
  
```  
End  
```  
  
## <a name="remarks"></a><span data-ttu-id="788dd-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="788dd-105">Remarks</span></span>  
 <span data-ttu-id="788dd-106">Můžete umístit `End` příkaz kdekoli v proceduře přinutit celé aplikace ukončené.</span><span class="sxs-lookup"><span data-stu-id="788dd-106">You can place the `End` statement anywhere in a procedure to force the entire application to stop running.</span></span> <span data-ttu-id="788dd-107">`End` Zavře všechny soubory otevřené se `Open` příkazu a vymaže všechny aplikace proměnné.</span><span class="sxs-lookup"><span data-stu-id="788dd-107">`End` closes any files opened with an `Open` statement and clears all the application's variables.</span></span> <span data-ttu-id="788dd-108">Aplikace se zavře, jakmile nejsou žádné jiné programy obsahující odkazy na objekty a žádný z jeho kód běží.</span><span class="sxs-lookup"><span data-stu-id="788dd-108">The application closes as soon as there are no other programs holding references to its objects and none of its code is running.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="788dd-109">`End` Příkaz náhle zastaví provádění kódu a se nevyvolá `Dispose` nebo `Finalize` metody nebo jakýkoli jiný kód jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="788dd-109">The `End` statement stops code execution abruptly, and does not invoke the `Dispose` or `Finalize` method, or any other Visual Basic code.</span></span> <span data-ttu-id="788dd-110">Odkazy na objekty uchovávat jinými programy nejsou zneplatněny.</span><span class="sxs-lookup"><span data-stu-id="788dd-110">Object references held by other programs are invalidated.</span></span> <span data-ttu-id="788dd-111">Pokud `End` příkaz dochází v rámci `Try` nebo `Catch` bloku, ovládací prvek nepředává odpovídající `Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="788dd-111">If an `End` statement is encountered within a `Try` or `Catch` block, control does not pass to the corresponding `Finally` block.</span></span>  
  
 <span data-ttu-id="788dd-112">`Stop` Příkaz pozastaví provádění, ale na rozdíl od `End`, ne zavřít všechny soubory, nebo zrušte všechny proměnné, pokud není nalezen v souboru zkompilovaného spustitelného souboru (.exe).</span><span class="sxs-lookup"><span data-stu-id="788dd-112">The `Stop` statement suspends execution, but unlike `End`, it does not close any files or clear any variables, unless it is encountered in a compiled executable (.exe) file.</span></span>  
  
 <span data-ttu-id="788dd-113">Protože `End` ukončí vaše aplikace bez vaši účast na všechny prostředky, které může být otevřený, snažte se zavřít čistě před jeho použitím.</span><span class="sxs-lookup"><span data-stu-id="788dd-113">Because `End` terminates your application without attending to any resources that might be open, you should try to close down cleanly before using it.</span></span> <span data-ttu-id="788dd-114">Například pokud má vaše aplikace formulářů otevřete, zavřete je před ovládací prvek dosáhne `End` příkazu.</span><span class="sxs-lookup"><span data-stu-id="788dd-114">For example, if your application has any forms open, you should close them before control reaches the `End` statement.</span></span>  
  
 <span data-ttu-id="788dd-115">Měli byste použít `End` opatrně a pouze pokud je potřeba zastavit okamžitě.</span><span class="sxs-lookup"><span data-stu-id="788dd-115">You should use `End` sparingly, and only when you need to stop immediately.</span></span> <span data-ttu-id="788dd-116">Běžné způsoby ukončí proceduru ([příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md) a [příkaz Exit](../../../visual-basic/language-reference/statements/exit-statement.md)) nejen ukončete proces čistě, ale také poskytují možnost Zavřít čistě volajícímu kódu.</span><span class="sxs-lookup"><span data-stu-id="788dd-116">The normal ways to terminate a procedure ([Return Statement](../../../visual-basic/language-reference/statements/return-statement.md) and [Exit Statement](../../../visual-basic/language-reference/statements/exit-statement.md)) not only close down the procedure cleanly but also give the calling code the opportunity to close down cleanly.</span></span> <span data-ttu-id="788dd-117">Konzolová aplikace, například můžete jednoduše `Return` z `Main` postup.</span><span class="sxs-lookup"><span data-stu-id="788dd-117">A console application, for example, can simply `Return` from the `Main` procedure.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="788dd-118">`End` Příkaz volá <xref:System.Environment.Exit%2A> metodu <xref:System.Environment> třídy v <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="788dd-118">The `End` statement calls the <xref:System.Environment.Exit%2A> method of the <xref:System.Environment> class in the <xref:System> namespace.</span></span> <span data-ttu-id="788dd-119"><xref:System.Environment.Exit%2A> vyžaduje, abyste měli `UnmanagedCode` oprávnění.</span><span class="sxs-lookup"><span data-stu-id="788dd-119"><xref:System.Environment.Exit%2A> requires that you have `UnmanagedCode` permission.</span></span> <span data-ttu-id="788dd-120">Pokud tak neučiníte, <xref:System.Security.SecurityException> dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="788dd-120">If you do not, a <xref:System.Security.SecurityException> error occurs.</span></span>  
  
 <span data-ttu-id="788dd-121">Pokud následuje další klíčové slovo, [End \<– klíčové slovo > příkaz](../../../visual-basic/language-reference/statements/end-keyword-statement.md) kolem Konec definice vhodný postup uvedený nebo bloku.</span><span class="sxs-lookup"><span data-stu-id="788dd-121">When followed by an additional keyword, [End \<keyword> Statement](../../../visual-basic/language-reference/statements/end-keyword-statement.md) delineates the end of the definition of the appropriate procedure or block.</span></span> <span data-ttu-id="788dd-122">Například `End Function` ukončí definici `Function` postup.</span><span class="sxs-lookup"><span data-stu-id="788dd-122">For example, `End Function` terminates the definition of a `Function` procedure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="788dd-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="788dd-123">Example</span></span>  
 <span data-ttu-id="788dd-124">V následujícím příkladu `End` příkaz k ukončení provádění kódu, pokud uživatel požaduje.</span><span class="sxs-lookup"><span data-stu-id="788dd-124">The following example uses the `End` statement to terminate code execution if the user requests it.</span></span>  
  
 [!code-vb[VbVersHelp60Controls#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVersHelp60Controls/VB/Form1.vb#64)]  
  
## <a name="smart-device-developer-notes"></a><span data-ttu-id="788dd-125">Poznámky pro vývojáře inteligentního zařízení</span><span class="sxs-lookup"><span data-stu-id="788dd-125">Smart Device Developer Notes</span></span>  
 <span data-ttu-id="788dd-126">Tento příkaz není podporován.</span><span class="sxs-lookup"><span data-stu-id="788dd-126">This statement is not supported.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="788dd-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="788dd-127">See also</span></span>

- <xref:System.Security.Permissions.SecurityPermissionFlag>
- [<span data-ttu-id="788dd-128">Příkaz Stop</span><span class="sxs-lookup"><span data-stu-id="788dd-128">Stop Statement</span></span>](../../../visual-basic/language-reference/statements/stop-statement.md)
- [<span data-ttu-id="788dd-129">End \<– klíčové slovo > – příkaz</span><span class="sxs-lookup"><span data-stu-id="788dd-129">End \<keyword> Statement</span></span>](../../../visual-basic/language-reference/statements/end-keyword-statement.md)
