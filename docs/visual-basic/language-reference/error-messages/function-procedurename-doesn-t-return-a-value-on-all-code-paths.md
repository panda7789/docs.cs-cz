---
title: Ve funkci '<procedurename>' existují cesty kódu, které nevrací žádnou hodnotu.
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: edb2195f4e83c2315aa929936aff8af88ca8556c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374132"
---
# <a name="function-procedurename-doesnt-return-a-value-on-all-code-paths"></a><span data-ttu-id="1c961-102">Ve funkci '\<procedurename>' existují cesty kódu, které nevrací žádnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1c961-102">Function '\<procedurename>' doesn't return a value on all code paths</span></span>
<span data-ttu-id="1c961-103">Funkce \<procedurename> ' ' nevrací hodnotu na všech cestách kódu.</span><span class="sxs-lookup"><span data-stu-id="1c961-103">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="1c961-104">Nechybí příkaz return?</span><span class="sxs-lookup"><span data-stu-id="1c961-104">Are you missing a 'Return' statement?</span></span>  
  
 <span data-ttu-id="1c961-105">`Function`Procedura má k dispozici alespoň jednu možnou cestu prostřednictvím kódu, který nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1c961-105">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="1c961-106">Můžete vrátit hodnotu z `Function` procedury v libovolném z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="1c961-106">You can return a value from a `Function` procedure in any of the following ways:</span></span>  
  
- <span data-ttu-id="1c961-107">Zahrňte hodnotu do [příkazu return](../statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1c961-107">Include the value in a [Return Statement](../statements/return-statement.md).</span></span>  
  
- <span data-ttu-id="1c961-108">Přiřaďte hodnotu k `Function` názvu procedury a pak `Exit Function` příkaz proveďte.</span><span class="sxs-lookup"><span data-stu-id="1c961-108">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>  
  
- <span data-ttu-id="1c961-109">Přiřaďte hodnotu k `Function` názvu procedury a pak `End Function` příkaz proveďte.</span><span class="sxs-lookup"><span data-stu-id="1c961-109">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>  
  
 <span data-ttu-id="1c961-110">Pokud řízení projde `Exit Function` nebo `End Function` a Vy jste k názvu procedury nepřiřadili žádnou hodnotu, procedura vrátí výchozí hodnotu návratového datového typu.</span><span class="sxs-lookup"><span data-stu-id="1c961-110">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="1c961-111">Další informace naleznete v tématu "Behavior" v [příkazu Function](../statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="1c961-111">For more information, see "Behavior" in [Function Statement](../statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="1c961-112">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="1c961-112">By default, this message is a warning.</span></span> <span data-ttu-id="1c961-113">Další informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="1c961-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="1c961-114">**ID chyby:** BC42105</span><span class="sxs-lookup"><span data-stu-id="1c961-114">**Error ID:** BC42105</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1c961-115">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="1c961-115">To correct this error</span></span>  
  
- <span data-ttu-id="1c961-116">Zkontrolujte logiku toku ovládacích prvků a ujistěte se, že přiřadíte hodnotu před všemi příkazy, které způsobují návrat.</span><span class="sxs-lookup"><span data-stu-id="1c961-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="1c961-117">Je snazší zaručit, že při každém návratu z této procedury vrátí hodnotu, pokud vždy použijete `Return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="1c961-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="1c961-118">Pokud to uděláte, poslední příkaz před `End Function` by měl být `Return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="1c961-118">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c961-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c961-119">See also</span></span>

- [<span data-ttu-id="1c961-120">Procedury funkcí</span><span class="sxs-lookup"><span data-stu-id="1c961-120">Function Procedures</span></span>](../../programming-guide/language-features/procedures/function-procedures.md)
- [<span data-ttu-id="1c961-121">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="1c961-121">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="1c961-122">Stránka Kompilovat, návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1c961-122">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
