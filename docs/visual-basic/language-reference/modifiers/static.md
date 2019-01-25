---
title: Static (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Static
helpviewer_keywords:
- static modifier
- Static keyword [Visual Basic]
ms.assetid: 19013910-4658-47b6-a22e-1744b527979e
ms.openlocfilehash: 1205d620fb5b6ec6af14cdeb7c6d78439f9e6b97
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54627626"
---
# <a name="static-visual-basic"></a><span data-ttu-id="7d969-102">Static (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7d969-102">Static (Visual Basic)</span></span>
<span data-ttu-id="7d969-103">Určuje, že nejmíň jeden z deklarovaných lokálních proměnných jsou dál existovat a zachovat svou poslední hodnotu po ukončení procesu, ve kterém jsou deklarovány.</span><span class="sxs-lookup"><span data-stu-id="7d969-103">Specifies that one or more declared local variables are to continue to exist and retain their latest values after termination of the procedure in which they are declared.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d969-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d969-104">Remarks</span></span>  
 <span data-ttu-id="7d969-105">Za normálních okolností místní proměnné v postupu zaniká ihned poté, co proces se zastaví.</span><span class="sxs-lookup"><span data-stu-id="7d969-105">Normally, a local variable in a procedure ceases to exist as soon as the procedure stops.</span></span> <span data-ttu-id="7d969-106">Statická proměnná existuje i nadále a zachová svou poslední hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7d969-106">A static variable continues to exist and retains its most recent value.</span></span> <span data-ttu-id="7d969-107">Při příštím kódu volá proceduru, proměnná není opakování inicializace odběrů a dál obsahuje nejnovější hodnotu, který jste přiřadili.</span><span class="sxs-lookup"><span data-stu-id="7d969-107">The next time your code calls the procedure, the variable is not reinitialized, and it still holds the latest value that you assigned to it.</span></span> <span data-ttu-id="7d969-108">Statická proměnná nebude existuje po dobu životnosti třídu nebo modul, který je definován v i nadále.</span><span class="sxs-lookup"><span data-stu-id="7d969-108">A static variable continues to exist for the lifetime of the class or module that it is defined in.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="7d969-109">pravidla</span><span class="sxs-lookup"><span data-stu-id="7d969-109">Rules</span></span>  
  
-   <span data-ttu-id="7d969-110">**Místní deklarace.**</span><span class="sxs-lookup"><span data-stu-id="7d969-110">**Declaration Context.**</span></span> <span data-ttu-id="7d969-111">Můžete použít `Static` pouze pro místní proměnné.</span><span class="sxs-lookup"><span data-stu-id="7d969-111">You can use `Static` only on local variables.</span></span> <span data-ttu-id="7d969-112">To znamená, že deklarace kontext `Static` proměnná musí být procedura nebo blok v postupu, a nemůže být zdrojový soubor, obor názvů, třídy, struktury nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="7d969-112">This means the declaration context for a `Static` variable must be a procedure or a block in a procedure, and it cannot be a source file, namespace, class, structure, or module.</span></span>  
  
     <span data-ttu-id="7d969-113">Nemůžete použít `Static` uvnitř procedury struktury.</span><span class="sxs-lookup"><span data-stu-id="7d969-113">You cannot use `Static` inside a structure procedure.</span></span>  
  
-   <span data-ttu-id="7d969-114">Datové typy `Static` lokální proměnné nelze odvodit.</span><span class="sxs-lookup"><span data-stu-id="7d969-114">The data types of `Static` local variables cannot be inferred.</span></span> <span data-ttu-id="7d969-115">Další informace najdete v tématu [odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span><span class="sxs-lookup"><span data-stu-id="7d969-115">For more information, see [Local Type Inference](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).</span></span>  
  
-   <span data-ttu-id="7d969-116">**Kombinované modifikátory.**</span><span class="sxs-lookup"><span data-stu-id="7d969-116">**Combined Modifiers.**</span></span> <span data-ttu-id="7d969-117">Nelze zadat `Static` spolu s `ReadOnly`, `Shadows`, nebo `Shared` ve stejné deklaraci.</span><span class="sxs-lookup"><span data-stu-id="7d969-117">You cannot specify `Static` together with `ReadOnly`, `Shadows`, or `Shared` in the same declaration.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="7d969-118">Chování</span><span class="sxs-lookup"><span data-stu-id="7d969-118">Behavior</span></span>  
 <span data-ttu-id="7d969-119">Pokud deklarujete statickou proměnnou `Shared` postupu jenom jednu kopii statická proměnná je k dispozici pro celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7d969-119">When you declare a static variable in a `Shared` procedure, only one copy of the static variable is available for the whole application.</span></span> <span data-ttu-id="7d969-120">Volání `Shared` název postupu pomocí třídy, není proměnná, která odkazuje na instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="7d969-120">You call a `Shared` procedure by using the class name, not a variable that points to an instance of the class.</span></span>  
  
 <span data-ttu-id="7d969-121">Pokud deklarujete statická proměnná v postupu, který není `Shared`pouze jednu kopii proměnné je k dispozici pro každou instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="7d969-121">When you declare a static variable in a procedure that isn't `Shared`, only one copy of the variable is available for each instance of the class.</span></span> <span data-ttu-id="7d969-122">Volání procedury nesdílené pomocí proměnné, která odkazuje na konkrétní instanci třídy.</span><span class="sxs-lookup"><span data-stu-id="7d969-122">You call a non-shared procedure by using a variable that points to a specific instance of the class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d969-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d969-123">Example</span></span>  
 <span data-ttu-id="7d969-124">Následující příklad ukazuje použití `Static`.</span><span class="sxs-lookup"><span data-stu-id="7d969-124">The following example demonstrates the use of `Static`.</span></span>  
  
 [!code-vb[VbVbalrKeywords#5](../../../visual-basic/language-reference/codesnippet/VisualBasic/static_1.vb)]  
  
 <span data-ttu-id="7d969-125">`Static` Proměnnou `totalSales` je inicializován na hodnotu 0 pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="7d969-125">The `Static` variable `totalSales` is initialized to 0 only one time.</span></span> <span data-ttu-id="7d969-126">Pokaždé, když zadáte `updateSales`, `totalSales` stále obsahuje nejnovější hodnotu, kterou jste vypočítali pro něj.</span><span class="sxs-lookup"><span data-stu-id="7d969-126">Each time that you enter `updateSales`, `totalSales` still has the most recent value that you calculated for it.</span></span>  
  
 <span data-ttu-id="7d969-127">`Static` Modifikátor lze použít v tomto kontextu:</span><span class="sxs-lookup"><span data-stu-id="7d969-127">The `Static` modifier can be used in this context:</span></span>  
  
 [<span data-ttu-id="7d969-128">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="7d969-128">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="7d969-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d969-129">See also</span></span>
- [<span data-ttu-id="7d969-130">Shadows</span><span class="sxs-lookup"><span data-stu-id="7d969-130">Shadows</span></span>](../../../visual-basic/language-reference/modifiers/shadows.md)
- [<span data-ttu-id="7d969-131">Shared</span><span class="sxs-lookup"><span data-stu-id="7d969-131">Shared</span></span>](../../../visual-basic/language-reference/modifiers/shared.md)
- [<span data-ttu-id="7d969-132">Doba platnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7d969-132">Lifetime in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="7d969-133">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="7d969-133">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="7d969-134">Struktury</span><span class="sxs-lookup"><span data-stu-id="7d969-134">Structures</span></span>](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="7d969-135">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="7d969-135">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="7d969-136">Objekty a třídy</span><span class="sxs-lookup"><span data-stu-id="7d969-136">Objects and Classes</span></span>](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
