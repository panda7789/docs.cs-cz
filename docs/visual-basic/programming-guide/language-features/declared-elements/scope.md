---
title: Rozsah v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
ms.openlocfilehash: 38dd9d6d40780c25f06a35cf1ffbe4743b7da4a4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537235"
---
# <a name="scope-in-visual-basic"></a><span data-ttu-id="c9dd5-102">Rozsah v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c9dd5-102">Scope in Visual Basic</span></span>
<span data-ttu-id="c9dd5-103">*Oboru* deklarované elementu je sada veškerý kód, který na ni můžete odkazovat bez kvalifikace názvu nebo ji dáte k dispozici prostřednictvím [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="c9dd5-103">The *scope* of a declared element is the set of all code that can refer to it without qualifying its name or making it available through an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="c9dd5-104">Element může mít rozsah na jednu z následujících úrovní:</span><span class="sxs-lookup"><span data-stu-id="c9dd5-104">An element can have scope at one of the following levels:</span></span>  
  
|<span data-ttu-id="c9dd5-105">úroveň</span><span class="sxs-lookup"><span data-stu-id="c9dd5-105">Level</span></span>|<span data-ttu-id="c9dd5-106">Popis</span><span class="sxs-lookup"><span data-stu-id="c9dd5-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c9dd5-107">Rozsah bloku</span><span class="sxs-lookup"><span data-stu-id="c9dd5-107">Block scope</span></span>|<span data-ttu-id="c9dd5-108">K dispozici pouze v rámci kód blok, ve kterém je deklarována</span><span class="sxs-lookup"><span data-stu-id="c9dd5-108">Available only within the code block in which it is declared</span></span>|  
|<span data-ttu-id="c9dd5-109">Rozsah procedury</span><span class="sxs-lookup"><span data-stu-id="c9dd5-109">Procedure scope</span></span>|<span data-ttu-id="c9dd5-110">K dispozici pro všechen kód v rámci procedury, ve kterém je deklarována</span><span class="sxs-lookup"><span data-stu-id="c9dd5-110">Available to all code within the procedure in which it is declared</span></span>|  
|<span data-ttu-id="c9dd5-111">Rozsah modulu</span><span class="sxs-lookup"><span data-stu-id="c9dd5-111">Module scope</span></span>|<span data-ttu-id="c9dd5-112">K dispozici pro všechen kód v rámci modulu, třídy nebo struktury, ve kterém je deklarována</span><span class="sxs-lookup"><span data-stu-id="c9dd5-112">Available to all code within the module, class, or structure in which it is declared</span></span>|  
|<span data-ttu-id="c9dd5-113">Namespace oboru</span><span class="sxs-lookup"><span data-stu-id="c9dd5-113">Namespace scope</span></span>|<span data-ttu-id="c9dd5-114">K dispozici pro všechen kód v oboru názvů, ve kterém je deklarována</span><span class="sxs-lookup"><span data-stu-id="c9dd5-114">Available to all code in the namespace in which it is declared</span></span>|  
  
 <span data-ttu-id="c9dd5-115">Tyto úrovně oboru průběh na základě nejužší (bloku) na nejširší (obor názvů), kde *od nejužšího oboru po* znamená, že nejmenší sadu kód, který může odkazovat na prvek bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-115">These levels of scope progress from the narrowest (block) to the widest (namespace), where *narrowest scope* means the smallest set of code that can refer to the element without qualification.</span></span> <span data-ttu-id="c9dd5-116">Další informace najdete v tématu "Úrovně oboru" na této stránce.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-116">For more information, see "Levels of Scope" on this page.</span></span>  
  
## <a name="specifying-scope-and-defining-variables"></a><span data-ttu-id="c9dd5-117">Určení oboru a definování proměnných</span><span class="sxs-lookup"><span data-stu-id="c9dd5-117">Specifying Scope and Defining Variables</span></span>  
 <span data-ttu-id="c9dd5-118">Můžete určit obor element při jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-118">You specify the scope of an element when you declare it.</span></span> <span data-ttu-id="c9dd5-119">Rozsah může záviset na následujících faktorech:</span><span class="sxs-lookup"><span data-stu-id="c9dd5-119">The scope can depend on the following factors:</span></span>  
  
-   <span data-ttu-id="c9dd5-120">Oblast (blok, postup, modulu, třídy nebo struktury), ve kterém můžete deklarovat element</span><span class="sxs-lookup"><span data-stu-id="c9dd5-120">The region (block, procedure, module, class, or structure) in which you declare the element</span></span>  
  
-   <span data-ttu-id="c9dd5-121">Obor názvů obsahující deklarace prvku</span><span class="sxs-lookup"><span data-stu-id="c9dd5-121">The namespace containing the element's declaration</span></span>  
  
-   <span data-ttu-id="c9dd5-122">Úroveň přístupu, které deklarujete pro element</span><span class="sxs-lookup"><span data-stu-id="c9dd5-122">The access level you declare for the element</span></span>  
  
 <span data-ttu-id="c9dd5-123">Pečlivě při definování proměnné se stejným názvem, ale jiného oboru, protože to může vést k neočekávaným výsledkům.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-123">Use care when you define variables with the same name but different scope, because doing so can lead to unexpected results.</span></span> <span data-ttu-id="c9dd5-124">Další informace najdete v tématu [odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="c9dd5-124">For more information, see [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="levels-of-scope"></a><span data-ttu-id="c9dd5-125">Úrovně rozsahu</span><span class="sxs-lookup"><span data-stu-id="c9dd5-125">Levels of Scope</span></span>  
 <span data-ttu-id="c9dd5-126">Programovací element je k dispozici v rámci oblasti, ve kterém se deklaruje.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-126">A programming element is available throughout the region in which you declare it.</span></span> <span data-ttu-id="c9dd5-127">Veškerý kód ve stejné oblasti můžete odkazovat na prvek bez kvalifikace názvu.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-127">All code in the same region can refer to the element without qualifying its name.</span></span>  
  
### <a name="block-scope"></a><span data-ttu-id="c9dd5-128">Obor bloku</span><span class="sxs-lookup"><span data-stu-id="c9dd5-128">Block Scope</span></span>  
 <span data-ttu-id="c9dd5-129">Blok je sadu příkazů uzavřených v rámci inicializace a ukončování příkazy deklarace, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="c9dd5-129">A block is a set of statements enclosed within initiating and terminating declaration statements, such as the following:</span></span>  
  
-   <span data-ttu-id="c9dd5-130">`Do` a `Loop`</span><span class="sxs-lookup"><span data-stu-id="c9dd5-130">`Do` and `Loop`</span></span>  
  
-   <span data-ttu-id="c9dd5-131">`For` [`Each`] a `Next`</span><span class="sxs-lookup"><span data-stu-id="c9dd5-131">`For` [`Each`] and `Next`</span></span>  
  
-   <span data-ttu-id="c9dd5-132">`If` a `End If`</span><span class="sxs-lookup"><span data-stu-id="c9dd5-132">`If` and `End If`</span></span>  
  
-   <span data-ttu-id="c9dd5-133">`Select` a `End Select`</span><span class="sxs-lookup"><span data-stu-id="c9dd5-133">`Select` and `End Select`</span></span>  
  
-   <span data-ttu-id="c9dd5-134">`SyncLock` a `End SyncLock`</span><span class="sxs-lookup"><span data-stu-id="c9dd5-134">`SyncLock` and `End SyncLock`</span></span>  
  
-   <span data-ttu-id="c9dd5-135">`Try` a `End Try`</span><span class="sxs-lookup"><span data-stu-id="c9dd5-135">`Try` and `End Try`</span></span>  
  
-   <span data-ttu-id="c9dd5-136">`While` a `End While`</span><span class="sxs-lookup"><span data-stu-id="c9dd5-136">`While` and `End While`</span></span>  
  
-   <span data-ttu-id="c9dd5-137">`With` a `End With`</span><span class="sxs-lookup"><span data-stu-id="c9dd5-137">`With` and `End With`</span></span>  
  
 <span data-ttu-id="c9dd5-138">Pokud deklarujete proměnnou v bloku, můžete ji použít pouze v tomto bloku.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-138">If you declare a variable within a block, you can use it only within that block.</span></span> <span data-ttu-id="c9dd5-139">V následujícím příkladu oboru celočíselné proměnné `cube` je blok mezi `If` a `End If`, a už se můžete vrátit k `cube` při provádění předá mimo blok.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-139">In the following example, the scope of the integer variable `cube` is the block between `If` and `End If`, and you can no longer refer to `cube` when execution passes out of the block.</span></span>  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  <span data-ttu-id="c9dd5-140">I v případě, že rozsah proměnné je omezen na blok, dobu života je stále celého procesu.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-140">Even if the scope of a variable is limited to a block, its lifetime is still that of the entire procedure.</span></span> <span data-ttu-id="c9dd5-141">Pokud zadáte během postupu bloku více než jednou, každý blok proměnná zachová svou předchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-141">If you enter the block more than once during the procedure, each block variable retains its previous value.</span></span> <span data-ttu-id="c9dd5-142">Aby se zabránilo neočekávaným výsledkům v takovém případě je z pohledu inicializovat proměnné v bloku na začátku bloku.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-142">To avoid unexpected results in such a case, it is wise to initialize block variables at the beginning of the block.</span></span>  
  
### <a name="procedure-scope"></a><span data-ttu-id="c9dd5-143">Rozsah procedury</span><span class="sxs-lookup"><span data-stu-id="c9dd5-143">Procedure Scope</span></span>  
 <span data-ttu-id="c9dd5-144">Element deklarovaný v rámci procedury není k dispozici mimo tento postup.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-144">An element declared within a procedure is not available outside that procedure.</span></span> <span data-ttu-id="c9dd5-145">Pouze proceduru, která obsahuje deklaraci můžete ho použít.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-145">Only the procedure that contains the declaration can use it.</span></span> <span data-ttu-id="c9dd5-146">Proměnné na této úrovni se také označují jako *lokální proměnné*.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-146">Variables at this level are also known as *local variables*.</span></span> <span data-ttu-id="c9dd5-147">Můžete je deklarovat pomocí [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md), s nebo bez [statické](../../../../visual-basic/language-reference/modifiers/static.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-147">You declare them with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), with or without the [Static](../../../../visual-basic/language-reference/modifiers/static.md) keyword.</span></span>  
  
 <span data-ttu-id="c9dd5-148">Postup a zároveň se zablokují oboru jsou úzce souvisí.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-148">Procedure and block scope are closely related.</span></span> <span data-ttu-id="c9dd5-149">Pokud deklarujete proměnnou uvnitř procedury, ale mimo všechny bloky v rámci tohoto postupu si můžete představit proměnnou jako s rozsahem bloku, pokud blok je celého procesu.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-149">If you declare a variable inside a procedure but outside any block within that procedure, you can think of the variable as having block scope, where the block is the entire procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c9dd5-150">Všechny místní prvky, dokonce i v případě, že jsou `Static` proměnné, jsou privátní pro proceduru, v jakém jsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-150">All local elements, even if they are `Static` variables, are private to the procedure in which they appear.</span></span> <span data-ttu-id="c9dd5-151">Nelze deklarovat element pomocí [veřejné](../../../../visual-basic/language-reference/modifiers/public.md) – klíčové slovo v rámci procedury.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-151">You cannot declare any element using the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword within a procedure.</span></span>  
  
### <a name="module-scope"></a><span data-ttu-id="c9dd5-152">Rozsah modulu</span><span class="sxs-lookup"><span data-stu-id="c9dd5-152">Module Scope</span></span>  
 <span data-ttu-id="c9dd5-153">Pro usnadnění práce, jeden výraz *úroveň modulu* vztahuje stejnou měrou na moduly, třídy a struktury.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-153">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="c9dd5-154">Prvky na této úrovni můžete deklarovat umístěním příkazu deklarace mimo žádné procedury ani bloku, ale v rámci modulu, třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-154">You can declare elements at this level by placing the declaration statement outside of any procedure or block but within the module, class, or structure.</span></span>  
  
 <span data-ttu-id="c9dd5-155">Pokud provedete deklarace na úrovni modulu, zjistí úroveň přístupu, kterou zvolíte rozsah.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-155">When you make a declaration at the module level, the access level you choose determines the scope.</span></span> <span data-ttu-id="c9dd5-156">Obor názvů obsahující modulu, třídy nebo struktury má vliv také na obor.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-156">The namespace that contains the module, class, or structure also affects the scope.</span></span>  
  
 <span data-ttu-id="c9dd5-157">Prvky, pro které deklarujete [privátní](../../../../visual-basic/language-reference/modifiers/private.md) úroveň přístupu jsou k dispozici pro každý postup v tomto modulu, ale ne k libovolnému kódu ve jiný modul.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-157">Elements for which you declare [Private](../../../../visual-basic/language-reference/modifiers/private.md) access level are available to every procedure in that module, but not to any code in a different module.</span></span> <span data-ttu-id="c9dd5-158">`Dim` Výchozí příkaz na úrovni modulu `Private` Pokud nepoužijete klíčová slova úrovně přístupu.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-158">The `Dim` statement at module level defaults to `Private` if you do not use any access level keywords.</span></span> <span data-ttu-id="c9dd5-159">Však můžete provádět oboru a úroveň přístupu jasnější pomocí `Private` – klíčové slovo v `Dim` příkazu.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-159">However, you can make the scope and access level more obvious by using the `Private` keyword in the `Dim` statement.</span></span>  
  
 <span data-ttu-id="c9dd5-160">V následujícím příkladu všechny postupy definované v modulu mohou odkazovat na proměnné řetězce `strMsg`.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-160">In the following example, all procedures defined in the module can refer to the string variable `strMsg`.</span></span> <span data-ttu-id="c9dd5-161">Při volání druhý postup zobrazí obsah proměnné řetězce `strMsg` v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-161">When the second procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
```  
' Put the following declaration at module level (not in any procedure).  
Private strMsg As String  
' Put the following Sub procedure in the same module.  
Sub initializePrivateVariable()  
    strMsg = "This variable cannot be used outside this module."  
End Sub  
' Put the following Sub procedure in the same module.  
Sub usePrivateVariable()  
    MsgBox(strMsg)  
End Sub  
```  
  
### <a name="namespace-scope"></a><span data-ttu-id="c9dd5-162">Namespace oboru</span><span class="sxs-lookup"><span data-stu-id="c9dd5-162">Namespace Scope</span></span>  
 <span data-ttu-id="c9dd5-163">Je-li deklarovat element na úrovni pomocí modulu [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) nebo [veřejné](../../../../visual-basic/language-reference/modifiers/public.md) – klíčové slovo, stane se dostupným pro všechny postupy v rámci oboru názvů, ve kterém je deklarován element.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-163">If you declare an element at module level using the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword, it becomes available to all procedures throughout the namespace in which the element is declared.</span></span> <span data-ttu-id="c9dd5-164">S následující změnou v předchozím příkladu, Řetězcová hodnota `strMsg` lze odkazovat pomocí kódu kdekoli v deklaraci oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-164">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 <span data-ttu-id="c9dd5-165">Namespace obor obsahuje vnořené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-165">Namespace scope includes nested namespaces.</span></span> <span data-ttu-id="c9dd5-166">Element dostupné v rámci oboru názvů je také dostupné v rámci libovolný obor názvů vnořit do daného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-166">An element available from within a namespace is also available from within any namespace nested inside that namespace.</span></span>  
  
 <span data-ttu-id="c9dd5-167">Pokud projekt neobsahuje žádný [příkaz Namespace](../../../../visual-basic/language-reference/statements/namespace-statement.md)všechno, co v projektu jsou ve stejném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-167">If your project does not contain any [Namespace Statement](../../../../visual-basic/language-reference/statements/namespace-statement.md)s, everything in the project is in the same namespace.</span></span> <span data-ttu-id="c9dd5-168">V takovém případě oboru názvů můžete představit jako rozsah projektu.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-168">In this case, namespace scope can be thought of as project scope.</span></span> <span data-ttu-id="c9dd5-169">`Public` prvky v modulu, třídy nebo struktury jsou také k dispozici do jakéhokoli projektu, který odkazuje na projekt.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-169">`Public` elements in a module, class, or structure are also available to any project that references their project.</span></span>  
  
## <a name="choice-of-scope"></a><span data-ttu-id="c9dd5-170">Výběr rozsahu</span><span class="sxs-lookup"><span data-stu-id="c9dd5-170">Choice of Scope</span></span>  
 <span data-ttu-id="c9dd5-171">Při deklarování proměnné můžete by měl vzít v úvahu následující body při výběru svého oboru.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-171">When you declare a variable, you should keep in mind the following points when choosing its scope.</span></span>  
  
### <a name="advantages-of-local-variables"></a><span data-ttu-id="c9dd5-172">Výhody lokální proměnné</span><span class="sxs-lookup"><span data-stu-id="c9dd5-172">Advantages of Local Variables</span></span>  
 <span data-ttu-id="c9dd5-173">Lokální proměnné jsou dobrou volbou pro jakýkoli druh dočasné výpočtu z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="c9dd5-173">Local variables are a good choice for any kind of temporary calculation, for the following reasons:</span></span>  
  
-   <span data-ttu-id="c9dd5-174">**Předcházení název konflikt.**</span><span class="sxs-lookup"><span data-stu-id="c9dd5-174">**Name Conflict Avoidance.**</span></span> <span data-ttu-id="c9dd5-175">Místní názvy proměnných nejsou náchylné k jsou v konfliktu.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-175">Local variable names are not susceptible to conflict.</span></span> <span data-ttu-id="c9dd5-176">Například můžete vytvořit několik různých postupů obsahujícího proměnnou s názvem `intTemp`.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-176">For example, you can create several different procedures containing a variable called `intTemp`.</span></span> <span data-ttu-id="c9dd5-177">Tak dlouho, dokud každý `intTemp` je deklarován jako místní proměnná, každý postup rozpozná pouze svou vlastní verzi z `intTemp`.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-177">As long as each `intTemp` is declared as a local variable, each procedure recognizes only its own version of `intTemp`.</span></span> <span data-ttu-id="c9dd5-178">Jakékoli jedné postupem můžete změnit hodnotu v jeho místní `intTemp` aniž by to ovlivnilo `intTemp` proměnné v dalších postupech.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-178">Any one procedure can alter the value in its local `intTemp` without affecting `intTemp` variables in other procedures.</span></span>  
  
-   <span data-ttu-id="c9dd5-179">**Využití paměti.**</span><span class="sxs-lookup"><span data-stu-id="c9dd5-179">**Memory Consumption.**</span></span> <span data-ttu-id="c9dd5-180">Lokální proměnné využívání paměti pouze při jejich postupu běží.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-180">Local variables consume memory only while their procedure is running.</span></span> <span data-ttu-id="c9dd5-181">Když postup vrátí volajícímu kódu, se uvolní jejich paměť.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-181">Their memory is released when the procedure returns to the calling code.</span></span> <span data-ttu-id="c9dd5-182">Naopak [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) a [statické](../../../../visual-basic/language-reference/modifiers/static.md) proměnné spotřebovávají prostředky paměti, dokud se vaše aplikace se zastaví, proto je pouze v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-182">By contrast, [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) and [Static](../../../../visual-basic/language-reference/modifiers/static.md) variables consume memory resources until your application stops running, so use them only when necessary.</span></span> <span data-ttu-id="c9dd5-183">*Instance proměnné* využívání paměti při jejich instance existuje, i nadále, což je méně efektivní než místní proměnné, ale potenciálně efektivnější než `Shared` nebo `Static` proměnné.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-183">*Instance variables* consume memory while their instance continues to exist, which makes them less efficient than local variables, but potentially more efficient than `Shared` or `Static` variables.</span></span>  
  
### <a name="minimizing-scope"></a><span data-ttu-id="c9dd5-184">Minimalizace oboru</span><span class="sxs-lookup"><span data-stu-id="c9dd5-184">Minimizing Scope</span></span>  
 <span data-ttu-id="c9dd5-185">Obecně platí, při deklarování jakoukoli proměnnou nebo konstantu, je programování je dobrým zvykem aby bylo co nejrovnoměrnější rozsah (obor bloku je nejbližší).</span><span class="sxs-lookup"><span data-stu-id="c9dd5-185">In general, when declaring any variable or constant, it is good programming practice to make the scope as narrow as possible (block scope is the narrowest).</span></span> <span data-ttu-id="c9dd5-186">To pomáhá šetřit paměť a minimalizuje případné chybně odkazující na proměnnou nesprávného kódu.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-186">This helps conserve memory and minimizes the chances of your code erroneously referring to the wrong variable.</span></span> <span data-ttu-id="c9dd5-187">Podobně by měla deklarovat proměnnou [statické](../../../../visual-basic/language-reference/modifiers/static.md) pouze pokud je potřeba zachovat jeho hodnotu mezi volání procedur.</span><span class="sxs-lookup"><span data-stu-id="c9dd5-187">Similarly, you should declare a variable to be [Static](../../../../visual-basic/language-reference/modifiers/static.md) only when it is necessary to preserve its value between procedure calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9dd5-188">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c9dd5-188">See also</span></span>
- [<span data-ttu-id="c9dd5-189">Deklarované charakteristiky elementů</span><span class="sxs-lookup"><span data-stu-id="c9dd5-189">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="c9dd5-190">Postupy: Řízení rozsahu proměnné</span><span class="sxs-lookup"><span data-stu-id="c9dd5-190">How to: Control the Scope of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [<span data-ttu-id="c9dd5-191">Doba platnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c9dd5-191">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [<span data-ttu-id="c9dd5-192">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c9dd5-192">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="c9dd5-193">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="c9dd5-193">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="c9dd5-194">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="c9dd5-194">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
