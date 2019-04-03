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
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58824829"
---
# <a name="function-procedurename-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="3006d-102">Funkce "\<název_procedury >' nevrací hodnotu ve všech cestách kódu.</span><span class="sxs-lookup"><span data-stu-id="3006d-102">Function '\<procedurename>' doesn't return a value on all code paths</span></span>
<span data-ttu-id="3006d-103">Funkce "\<název_procedury >' nevrací hodnotu ve všech cestách kódu.</span><span class="sxs-lookup"><span data-stu-id="3006d-103">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="3006d-104">Chybí příkaz 'Return'?</span><span class="sxs-lookup"><span data-stu-id="3006d-104">Are you missing a 'Return' statement?</span></span>  
  
 <span data-ttu-id="3006d-105">A `Function` postup obsahuje alespoň jeden možných cest pomocí jejího kódu, která nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3006d-105">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="3006d-106">Může vrátit hodnotu z `Function` postup v některém z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="3006d-106">You can return a value from a `Function` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="3006d-107">Hodnota v [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3006d-107">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
-   <span data-ttu-id="3006d-108">Přiřadí hodnotu k `Function` postup pojmenujte a pak proveďte `Exit Function` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3006d-108">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>  
  
-   <span data-ttu-id="3006d-109">Přiřadí hodnotu k `Function` postup pojmenujte a pak proveďte `End Function` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3006d-109">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>  
  
 <span data-ttu-id="3006d-110">Pokud řízení se předá `Exit Function` nebo `End Function` a jste ještě nepřiřadili žádné hodnoty pro název procedury, postup vrátí návratový typ dat výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3006d-110">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="3006d-111">Další informace najdete v tématu "Chování" [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="3006d-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="3006d-112">Ve výchozím nastavení tato zpráva je upozornění.</span><span class="sxs-lookup"><span data-stu-id="3006d-112">By default, this message is a warning.</span></span> <span data-ttu-id="3006d-113">Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="3006d-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="3006d-114">**ID chyby:** BC42105</span><span class="sxs-lookup"><span data-stu-id="3006d-114">**Error ID:** BC42105</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="3006d-115">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="3006d-115">To correct this error</span></span>  
  
-   <span data-ttu-id="3006d-116">Zkontrolujte logiku toku řízení a ujistěte se, že přidělíte hodnotu před každý příkaz, který způsobí, že vrácení.</span><span class="sxs-lookup"><span data-stu-id="3006d-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="3006d-117">Je snazší zajistit, že každý návrat z procedury vrací hodnotu, pokud vždy používáte `Return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3006d-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="3006d-118">Pokud to provedete, poslední příkaz před `End Function` by měl být `Return` příkazu.</span><span class="sxs-lookup"><span data-stu-id="3006d-118">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3006d-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3006d-119">See also</span></span>

- [<span data-ttu-id="3006d-120">Procedury funkce</span><span class="sxs-lookup"><span data-stu-id="3006d-120">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="3006d-121">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="3006d-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)
- [<span data-ttu-id="3006d-122">Stránka Kompilovat, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3006d-122">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
