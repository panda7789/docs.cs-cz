---
title: Static (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e08f46076281e766a5bc0b99cd61fee9cd41ece5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="static-visual-basic"></a><span data-ttu-id="8f27c-102">Static (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8f27c-102">Static (Visual Basic)</span></span>
<span data-ttu-id="8f27c-103">Určuje, že jeden nebo více deklarované lokální proměnné jsou nadále existovat a po ukončení procesu, ve které jsou deklarovány zachovat jejich nejnovější hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8f27c-103">Specifies that one or more declared local variables are to continue to exist and retain their latest values after termination of the procedure in which they are declared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f27c-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8f27c-104">Remarks</span></span>  
 <span data-ttu-id="8f27c-105">Za normálních okolností místní proměnné v postupu přestane existovat také zastaví proces.</span><span class="sxs-lookup"><span data-stu-id="8f27c-105">Normally, a local variable in a procedure ceases to exist as soon as the procedure stops.</span></span> <span data-ttu-id="8f27c-106">Statické proměnné nadále existovat a jeho nejnovější hodnotu zachová.</span><span class="sxs-lookup"><span data-stu-id="8f27c-106">A static variable continues to exist and retains its most recent value.</span></span> <span data-ttu-id="8f27c-107">Při příštím kódu volá proceduru, není inicializace proměnné a že dál obsahuje nejpozdější hodnotu, který jste přiřadili k němu.</span><span class="sxs-lookup"><span data-stu-id="8f27c-107">The next time your code calls the procedure, the variable is not reinitialized, and it still holds the latest value that you assigned to it.</span></span> <span data-ttu-id="8f27c-108">Statické proměnné i nadále existovat pro životnost třídu nebo modul, který je definován v.</span><span class="sxs-lookup"><span data-stu-id="8f27c-108">A static variable continues to exist for the lifetime of the class or module that it is defined in.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="8f27c-109">Pravidla</span><span class="sxs-lookup"><span data-stu-id="8f27c-109">Rules</span></span>  
  
-   <span data-ttu-id="8f27c-110">**Kontext deklarace.**</span><span class="sxs-lookup"><span data-stu-id="8f27c-110">**Declaration Context.**</span></span> <span data-ttu-id="8f27c-111">Můžete použít `Static` pouze na místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="8f27c-111">You can use `Static` only on local variables.</span></span> <span data-ttu-id="8f27c-112">To znamená kontext deklarace `Static` proměnná musí být procedury nebo blok v postupu, a nelze ji zdrojový soubor, obor názvů, třídy, struktury nebo modul.</span><span class="sxs-lookup"><span data-stu-id="8f27c-112">This means the declaration context for a `Static` variable must be a procedure or a block in a procedure, and it cannot be a source file, namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="8f27c-113">Nemůžete použít `Static` uvnitř procedury struktura.</span><span class="sxs-lookup"><span data-stu-id="8f27c-113">You cannot use `Static` inside a structure procedure.</span></span>  
  
-   <span data-ttu-id="8f27c-114">Datové typy `Static` místní proměnné nelze odvodit.</span><span class="sxs-lookup"><span data-stu-id="8f27c-114">The data types of `Static` local variables cannot be inferred.</span></span> <span data-ttu-id="8f27c-115">Další informace najdete v tématu [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="8f27c-115">For more information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
-   <span data-ttu-id="8f27c-116">**Kombinovaná parametrů.**</span><span class="sxs-lookup"><span data-stu-id="8f27c-116">**Combined Modifiers.**</span></span> <span data-ttu-id="8f27c-117">Nelze zadat `Static` společně s `ReadOnly`, `Shadows`, nebo `Shared` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="8f27c-117">You cannot specify `Static` together with `ReadOnly`, `Shadows`, or `Shared` in the same declaration.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="8f27c-118">Chování</span><span class="sxs-lookup"><span data-stu-id="8f27c-118">Behavior</span></span>  
 <span data-ttu-id="8f27c-119">Když je deklarovat statickou proměnnou v `Shared` postup, pouze jedna kopie statické proměnné je k dispozici pro celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8f27c-119">When you declare a static variable in a `Shared` procedure, only one copy of the static variable is available for the whole application.</span></span> <span data-ttu-id="8f27c-120">Volání `Shared` název postupu pomocí třídy, ne proměnné, která odkazuje na instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="8f27c-120">You call a `Shared` procedure by using the class name, not a variable that points to an instance of the class.</span></span>  
  
 <span data-ttu-id="8f27c-121">Když je deklarovat statické proměnné v postupu, který není `Shared`, pouze jedna kopie proměnné je k dispozici pro každou instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="8f27c-121">When you declare a static variable in a procedure that isn't `Shared`, only one copy of the variable is available for each instance of the class.</span></span> <span data-ttu-id="8f27c-122">Volání procedury, nesdílené pomocí proměnné, která odkazuje na konkrétní instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="8f27c-122">You call a non-shared procedure by using a variable that points to a specific instance of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f27c-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="8f27c-123">Example</span></span>  
 <span data-ttu-id="8f27c-124">Následující příklad ukazuje použití `Static`.</span><span class="sxs-lookup"><span data-stu-id="8f27c-124">The following example demonstrates the use of `Static`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#5](../../../visual-basic/language-reference/codesnippet/VisualBasic/static_1.vb)]  
  
 <span data-ttu-id="8f27c-125">`Static` Proměnná `totalSales` je inicializováno 0 pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="8f27c-125">The `Static` variable `totalSales` is initialized to 0 only one time.</span></span> <span data-ttu-id="8f27c-126">Pokaždé, když zadáte `updateSales`, `totalSales` má stále nejnovější hodnotu, kterou jste vypočítali pro něj.</span><span class="sxs-lookup"><span data-stu-id="8f27c-126">Each time that you enter `updateSales`, `totalSales` still has the most recent value that you calculated for it.</span></span>  
  
 <span data-ttu-id="8f27c-127">`Static` Modifikátor můžete v tomto kontextu použít:</span><span class="sxs-lookup"><span data-stu-id="8f27c-127">The `Static` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="8f27c-128">Dim – příkaz</span><span class="sxs-lookup"><span data-stu-id="8f27c-128">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="8f27c-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f27c-129">See Also</span></span>  
 [<span data-ttu-id="8f27c-130">Stínů</span><span class="sxs-lookup"><span data-stu-id="8f27c-130">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [<span data-ttu-id="8f27c-131">Sdílené</span><span class="sxs-lookup"><span data-stu-id="8f27c-131">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)  
 [<span data-ttu-id="8f27c-132">Doba platnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8f27c-132">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [<span data-ttu-id="8f27c-133">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="8f27c-133">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="8f27c-134">Struktury</span><span class="sxs-lookup"><span data-stu-id="8f27c-134">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [<span data-ttu-id="8f27c-135">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="8f27c-135">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="8f27c-136">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="8f27c-136">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
