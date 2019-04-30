---
title: Ve funkci '<procedurename>' existují cesty kódu, které nevrací žádnou hodnotu.
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: badcfea4f24ba3858071e02ba47b8f77ab557f88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802372"
---
# <a name="function-procedurename-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="31b16-102">Funkce "\<název_procedury >' nevrací hodnotu ve všech cestách kódu.</span><span class="sxs-lookup"><span data-stu-id="31b16-102">Function '\<procedurename>' doesn't return a value on all code paths</span></span>
<span data-ttu-id="31b16-103">Funkce "\<název_procedury >' nevrací hodnotu ve všech cestách kódu.</span><span class="sxs-lookup"><span data-stu-id="31b16-103">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="31b16-104">Chybí příkaz 'Return'?</span><span class="sxs-lookup"><span data-stu-id="31b16-104">Are you missing a 'Return' statement?</span></span>  
  
 <span data-ttu-id="31b16-105">A `Function` postup obsahuje alespoň jeden možných cest pomocí jejího kódu, která nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="31b16-105">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="31b16-106">Může vrátit hodnotu z `Function` postup v některém z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="31b16-106">You can return a value from a `Function` procedure in any of the following ways:</span></span>  
  
- <span data-ttu-id="31b16-107">Hodnota v [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="31b16-107">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
- <span data-ttu-id="31b16-108">Přiřadí hodnotu k `Function` postup pojmenujte a pak proveďte `Exit Function` příkazu.</span><span class="sxs-lookup"><span data-stu-id="31b16-108">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>  
  
- <span data-ttu-id="31b16-109">Přiřadí hodnotu k `Function` postup pojmenujte a pak proveďte `End Function` příkazu.</span><span class="sxs-lookup"><span data-stu-id="31b16-109">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>  
  
 <span data-ttu-id="31b16-110">Pokud řízení se předá `Exit Function` nebo `End Function` a jste ještě nepřiřadili žádné hodnoty pro název procedury, postup vrátí návratový typ dat výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="31b16-110">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="31b16-111">Další informace najdete v tématu "Chování" [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="31b16-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="31b16-112">Ve výchozím nastavení tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="31b16-112">By default, this message is a warning.</span></span> <span data-ttu-id="31b16-113">Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="31b16-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="31b16-114">**ID chyby:** BC42105</span><span class="sxs-lookup"><span data-stu-id="31b16-114">**Error ID:** BC42105</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="31b16-115">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="31b16-115">To correct this error</span></span>  
  
- <span data-ttu-id="31b16-116">Zkontrolujte logiku toku řízení a ujistěte se, že přidělíte hodnotu před každý příkaz, který způsobí, že vrácení.</span><span class="sxs-lookup"><span data-stu-id="31b16-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="31b16-117">Je snazší zajistit, že každý návrat z procedury vrací hodnotu, pokud vždy používáte `Return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="31b16-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="31b16-118">Pokud to provedete, poslední příkaz před `End Function` by měl být `Return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="31b16-118">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31b16-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="31b16-119">See also</span></span>

- [<span data-ttu-id="31b16-120">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="31b16-120">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="31b16-121">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="31b16-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="31b16-122">Stránka Kompilovat, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="31b16-122">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
