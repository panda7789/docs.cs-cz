---
title: "Funkce & č. 39; &lt;procedurename&gt;& č. 39; nemá & č. 39; t vrátit hodnotu na všechny cesty kódu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5244d97a79f2450f44fe05f63510369914375912
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="function-39ltprocedurenamegt39-doesn39t-return-a-value-on-all-code-paths"></a><span data-ttu-id="0a021-102">Funkce & č. 39; &lt;procedurename&gt;& č. 39; nemá & č. 39; t vrátit hodnotu na všechny cesty kódu</span><span class="sxs-lookup"><span data-stu-id="0a021-102">Function &#39;&lt;procedurename&gt;&#39; doesn&#39;t return a value on all code paths</span></span>
<span data-ttu-id="0a021-103">Funkce '\<procedurename >' nevrací hodnotu na všechny cesty kódu.</span><span class="sxs-lookup"><span data-stu-id="0a021-103">Function '\<procedurename>' doesn't return a value on all code paths.</span></span> <span data-ttu-id="0a021-104">Chybějící příkaz 'Return'?</span><span class="sxs-lookup"><span data-stu-id="0a021-104">Are you missing a 'Return' statement?</span></span>  
  
 <span data-ttu-id="0a021-105">A `Function` procedura nemá alespoň jednu cestu možný prostřednictvím jeho kód, který nevrací hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0a021-105">A `Function` procedure has at least one possible path through its code that does not return a value.</span></span>  
  
 <span data-ttu-id="0a021-106">Můžete vrátit hodnotu z `Function` postup v některém z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="0a021-106">You can return a value from a `Function` procedure in any of the following ways:</span></span>  
  
-   <span data-ttu-id="0a021-107">Zahrnout hodnotu v [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0a021-107">Include the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
-   <span data-ttu-id="0a021-108">Přiřazení hodnoty k `Function` postup název a potom proveďte `Exit Function` příkaz.</span><span class="sxs-lookup"><span data-stu-id="0a021-108">Assign the value to the `Function` procedure name and then perform an `Exit Function` statement.</span></span>  
  
-   <span data-ttu-id="0a021-109">Přiřazení hodnoty k `Function` postup název a poté proveďte `End Function` příkaz.</span><span class="sxs-lookup"><span data-stu-id="0a021-109">Assign the value to the `Function` procedure name and then perform the `End Function` statement.</span></span>  
  
 <span data-ttu-id="0a021-110">Pokud ovládací prvek předává do `Exit Function` nebo `End Function` a hodnotou nebyly přiřazovány název procedury, postup vrátí výchozí hodnotu návratový datový typ.</span><span class="sxs-lookup"><span data-stu-id="0a021-110">If control passes to `Exit Function` or `End Function` and you have not assigned any value to the procedure name, the procedure returns the default value of the return data type.</span></span> <span data-ttu-id="0a021-111">Další informace najdete v tématu "Chování" v [funkce příkaz](../../../visual-basic/language-reference/statements/function-statement.md).</span><span class="sxs-lookup"><span data-stu-id="0a021-111">For more information, see "Behavior" in [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md).</span></span>  
  
 <span data-ttu-id="0a021-112">Ve výchozím nastavení je tato zpráva upozornění.</span><span class="sxs-lookup"><span data-stu-id="0a021-112">By default, this message is a warning.</span></span> <span data-ttu-id="0a021-113">Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="0a021-113">For more information on hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="0a021-114">**ID chyby:** BC42105</span><span class="sxs-lookup"><span data-stu-id="0a021-114">**Error ID:** BC42105</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="0a021-115">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="0a021-115">To correct this error</span></span>  
  
-   <span data-ttu-id="0a021-116">Zkontrolujte logika toku řízení a ujistěte se, že přiřadit hodnotu před každý příkaz, který způsobí, že vrátit.</span><span class="sxs-lookup"><span data-stu-id="0a021-116">Check your control flow logic and make sure you assign a value before every statement that causes a return.</span></span>  
  
     <span data-ttu-id="0a021-117">Je snazší zaručit, že každý vrátit v postupu vrací hodnotu, pokud je vždy použít `Return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="0a021-117">It is easier to guarantee that every return from the procedure returns a value if you always use the `Return` statement.</span></span> <span data-ttu-id="0a021-118">Pokud použijete tento, poslední příkaz před `End Function` by měla být `Return` příkaz.</span><span class="sxs-lookup"><span data-stu-id="0a021-118">If you do this, the last statement before `End Function` should be a `Return` statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a021-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="0a021-119">See Also</span></span>  
 [<span data-ttu-id="0a021-120">Function – procedury</span><span class="sxs-lookup"><span data-stu-id="0a021-120">Function Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [<span data-ttu-id="0a021-121">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="0a021-121">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
 [<span data-ttu-id="0a021-122">Stránka kompilovat, Návrhář projektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a021-122">Compile Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
