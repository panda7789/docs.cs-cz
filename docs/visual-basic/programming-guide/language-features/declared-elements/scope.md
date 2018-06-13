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
ms.openlocfilehash: d6692379626d787b728d6e92bd447c4a96e6680e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656292"
---
# <a name="scope-in-visual-basic"></a><span data-ttu-id="a2144-102">Rozsah v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a2144-102">Scope in Visual Basic</span></span>
<span data-ttu-id="a2144-103">*Oboru* deklarované elementu je sada všechen kód, který může na ni odkazuje bez určení názvu nebo ji dáte k dispozici prostřednictvím [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="a2144-103">The *scope* of a declared element is the set of all code that can refer to it without qualifying its name or making it available through an [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="a2144-104">Element může mít rozsah v některém z následujících úrovní:</span><span class="sxs-lookup"><span data-stu-id="a2144-104">An element can have scope at one of the following levels:</span></span>  
  
|<span data-ttu-id="a2144-105">úroveň</span><span class="sxs-lookup"><span data-stu-id="a2144-105">Level</span></span>|<span data-ttu-id="a2144-106">Popis</span><span class="sxs-lookup"><span data-stu-id="a2144-106">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a2144-107">Rozsah bloku</span><span class="sxs-lookup"><span data-stu-id="a2144-107">Block scope</span></span>|<span data-ttu-id="a2144-108">K dispozici pouze v rámci kód blok, ve kterém je deklarovaná</span><span class="sxs-lookup"><span data-stu-id="a2144-108">Available only within the code block in which it is declared</span></span>|  
|<span data-ttu-id="a2144-109">Rozsah procedury</span><span class="sxs-lookup"><span data-stu-id="a2144-109">Procedure scope</span></span>|<span data-ttu-id="a2144-110">K dispozici pro všechny kódu v rámci procesu, ve kterém je deklarovaná</span><span class="sxs-lookup"><span data-stu-id="a2144-110">Available to all code within the procedure in which it is declared</span></span>|  
|<span data-ttu-id="a2144-111">Rozsah modulu</span><span class="sxs-lookup"><span data-stu-id="a2144-111">Module scope</span></span>|<span data-ttu-id="a2144-112">K dispozici pro všechny kódu v rámci modulu, třídu nebo strukturu, ve kterém je deklarovaná</span><span class="sxs-lookup"><span data-stu-id="a2144-112">Available to all code within the module, class, or structure in which it is declared</span></span>|  
|<span data-ttu-id="a2144-113">Namespace oboru</span><span class="sxs-lookup"><span data-stu-id="a2144-113">Namespace scope</span></span>|<span data-ttu-id="a2144-114">K dispozici pro všechny kódu v oboru názvů, ve kterém je deklarovaná</span><span class="sxs-lookup"><span data-stu-id="a2144-114">Available to all code in the namespace in which it is declared</span></span>|  
  
 <span data-ttu-id="a2144-115">Tyto úrovně oboru průběh z nejbližší (bloku) na širokou (obor názvů), kde *zpomalit* znamená nejmenší sadu kód, který může odkazovat na prvek bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="a2144-115">These levels of scope progress from the narrowest (block) to the widest (namespace), where *narrowest scope* means the smallest set of code that can refer to the element without qualification.</span></span> <span data-ttu-id="a2144-116">Další informace najdete v tématu "Úrovně obor" na této stránce.</span><span class="sxs-lookup"><span data-stu-id="a2144-116">For more information, see "Levels of Scope" on this page.</span></span>  
  
## <a name="specifying-scope-and-defining-variables"></a><span data-ttu-id="a2144-117">Určení oboru a definování proměnné</span><span class="sxs-lookup"><span data-stu-id="a2144-117">Specifying Scope and Defining Variables</span></span>  
 <span data-ttu-id="a2144-118">Můžete určit obor element při jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="a2144-118">You specify the scope of an element when you declare it.</span></span> <span data-ttu-id="a2144-119">Obor může záviset na následujících faktorech:</span><span class="sxs-lookup"><span data-stu-id="a2144-119">The scope can depend on the following factors:</span></span>  
  
-   <span data-ttu-id="a2144-120">Region (bloku, postup, modulu, – třída nebo struktura), ve kterém je deklarovat elementu</span><span class="sxs-lookup"><span data-stu-id="a2144-120">The region (block, procedure, module, class, or structure) in which you declare the element</span></span>  
  
-   <span data-ttu-id="a2144-121">Obor názvů obsahující deklaraci elementu</span><span class="sxs-lookup"><span data-stu-id="a2144-121">The namespace containing the element's declaration</span></span>  
  
-   <span data-ttu-id="a2144-122">Úroveň přístupu, které deklarace pro daný element</span><span class="sxs-lookup"><span data-stu-id="a2144-122">The access level you declare for the element</span></span>  
  
 <span data-ttu-id="a2144-123">Použití pozor při definování proměnné se stejným názvem, ale jiný rozsah, protože díky tomu může vést k neočekávaným výsledkům.</span><span class="sxs-lookup"><span data-stu-id="a2144-123">Use care when you define variables with the same name but different scope, because doing so can lead to unexpected results.</span></span> <span data-ttu-id="a2144-124">Další informace najdete v tématu [odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="a2144-124">For more information, see [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>  
  
## <a name="levels-of-scope"></a><span data-ttu-id="a2144-125">Úrovně rozsahu</span><span class="sxs-lookup"><span data-stu-id="a2144-125">Levels of Scope</span></span>  
 <span data-ttu-id="a2144-126">Programovací element je k dispozici v celé oblasti, ve kterém je deklarovat.</span><span class="sxs-lookup"><span data-stu-id="a2144-126">A programming element is available throughout the region in which you declare it.</span></span> <span data-ttu-id="a2144-127">Všechny kódu ve stejné oblasti odkazovat na element bez určení názvu.</span><span class="sxs-lookup"><span data-stu-id="a2144-127">All code in the same region can refer to the element without qualifying its name.</span></span>  
  
### <a name="block-scope"></a><span data-ttu-id="a2144-128">Obor bloku</span><span class="sxs-lookup"><span data-stu-id="a2144-128">Block Scope</span></span>  
 <span data-ttu-id="a2144-129">Blok je sada uzavřené v rámci inicializace a ukončování deklarační příkazy, jako je například následující příkazy:</span><span class="sxs-lookup"><span data-stu-id="a2144-129">A block is a set of statements enclosed within initiating and terminating declaration statements, such as the following:</span></span>  
  
-   <span data-ttu-id="a2144-130">`Do` A `Loop`</span><span class="sxs-lookup"><span data-stu-id="a2144-130">`Do` and `Loop`</span></span>  
  
-   <span data-ttu-id="a2144-131">`For` [`Each`] a `Next`</span><span class="sxs-lookup"><span data-stu-id="a2144-131">`For` [`Each`] and `Next`</span></span>  
  
-   <span data-ttu-id="a2144-132">`If` A `End If`</span><span class="sxs-lookup"><span data-stu-id="a2144-132">`If` and `End If`</span></span>  
  
-   <span data-ttu-id="a2144-133">`Select` A `End Select`</span><span class="sxs-lookup"><span data-stu-id="a2144-133">`Select` and `End Select`</span></span>  
  
-   <span data-ttu-id="a2144-134">`SyncLock` A `End SyncLock`</span><span class="sxs-lookup"><span data-stu-id="a2144-134">`SyncLock` and `End SyncLock`</span></span>  
  
-   <span data-ttu-id="a2144-135">`Try` A `End Try`</span><span class="sxs-lookup"><span data-stu-id="a2144-135">`Try` and `End Try`</span></span>  
  
-   <span data-ttu-id="a2144-136">`While` A `End While`</span><span class="sxs-lookup"><span data-stu-id="a2144-136">`While` and `End While`</span></span>  
  
-   <span data-ttu-id="a2144-137">`With` A `End With`</span><span class="sxs-lookup"><span data-stu-id="a2144-137">`With` and `End With`</span></span>  
  
 <span data-ttu-id="a2144-138">Pokud je deklarovat proměnnou v bloku, můžete ji pouze v tomto bloku.</span><span class="sxs-lookup"><span data-stu-id="a2144-138">If you declare a variable within a block, you can use it only within that block.</span></span> <span data-ttu-id="a2144-139">V následujícím příkladu, rozsah proměnná s celým číslem `cube` je blok mezi `If` a `End If`, a už se může vztahovat na `cube` při provádění předá mimo blok.</span><span class="sxs-lookup"><span data-stu-id="a2144-139">In the following example, the scope of the integer variable `cube` is the block between `If` and `End If`, and you can no longer refer to `cube` when execution passes out of the block.</span></span>  
  
```  
If n < 1291 Then  
    Dim cube As Integer  
    cube = n ^ 3  
End If  
```  
  
> [!NOTE]
>  <span data-ttu-id="a2144-140">I když rozsah proměnné je omezený na blok, celé jeho životnosti je stále u celého procesu.</span><span class="sxs-lookup"><span data-stu-id="a2144-140">Even if the scope of a variable is limited to a block, its lifetime is still that of the entire procedure.</span></span> <span data-ttu-id="a2144-141">Pokud zadáte během postupu bloku více než jednou, každá proměnná bloku ponechá jejich předchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a2144-141">If you enter the block more than once during the procedure, each block variable retains its previous value.</span></span> <span data-ttu-id="a2144-142">Chcete-li se vyhnout neočekávaným výsledkům v tomto případě, je vhodné k chybě při inicializaci bloku proměnné na začátku bloku.</span><span class="sxs-lookup"><span data-stu-id="a2144-142">To avoid unexpected results in such a case, it is wise to initialize block variables at the beginning of the block.</span></span>  
  
### <a name="procedure-scope"></a><span data-ttu-id="a2144-143">Rozsah procedury</span><span class="sxs-lookup"><span data-stu-id="a2144-143">Procedure Scope</span></span>  
 <span data-ttu-id="a2144-144">Element deklarované v rámci procedury není k dispozici mimo tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="a2144-144">An element declared within a procedure is not available outside that procedure.</span></span> <span data-ttu-id="a2144-145">Pouze procedury, která obsahuje deklaraci můžete ji použít.</span><span class="sxs-lookup"><span data-stu-id="a2144-145">Only the procedure that contains the declaration can use it.</span></span> <span data-ttu-id="a2144-146">Proměnné na této úrovni se také označují jako *místní proměnné*.</span><span class="sxs-lookup"><span data-stu-id="a2144-146">Variables at this level are also known as *local variables*.</span></span> <span data-ttu-id="a2144-147">Je deklarovat s [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md), bez ohledu [statické](../../../../visual-basic/language-reference/modifiers/static.md) – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="a2144-147">You declare them with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), with or without the [Static](../../../../visual-basic/language-reference/modifiers/static.md) keyword.</span></span>  
  
 <span data-ttu-id="a2144-148">Postup a bloku oboru jsou úzce související.</span><span class="sxs-lookup"><span data-stu-id="a2144-148">Procedure and block scope are closely related.</span></span> <span data-ttu-id="a2144-149">Pokud je deklarovat proměnnou uvnitř procedury, ale mimo všechny bloky v rámci tohoto postupu si můžete představit proměnné tak, že má rozsah bloku, kde blok je celý postup.</span><span class="sxs-lookup"><span data-stu-id="a2144-149">If you declare a variable inside a procedure but outside any block within that procedure, you can think of the variable as having block scope, where the block is the entire procedure.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a2144-150">Všechny místní elementy, i když jsou `Static` proměnné, jsou privátní procedury, ve kterém se zobrazí.</span><span class="sxs-lookup"><span data-stu-id="a2144-150">All local elements, even if they are `Static` variables, are private to the procedure in which they appear.</span></span> <span data-ttu-id="a2144-151">Nelze deklarovat element pomocí [veřejné](../../../../visual-basic/language-reference/modifiers/public.md) – klíčové slovo v rámci procedury.</span><span class="sxs-lookup"><span data-stu-id="a2144-151">You cannot declare any element using the [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword within a procedure.</span></span>  
  
### <a name="module-scope"></a><span data-ttu-id="a2144-152">Rozsah modulu</span><span class="sxs-lookup"><span data-stu-id="a2144-152">Module Scope</span></span>  
 <span data-ttu-id="a2144-153">Pro usnadnění práce jeden termín *úroveň modulu* vztahuje stejnou měrou na moduly, třídy a struktury.</span><span class="sxs-lookup"><span data-stu-id="a2144-153">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="a2144-154">Prvky na této úrovni můžete tím, že příkaz deklarace mimo žádné procedury ani bloku, ale v rámci modulu, třídu nebo strukturu deklarovat.</span><span class="sxs-lookup"><span data-stu-id="a2144-154">You can declare elements at this level by placing the declaration statement outside of any procedure or block but within the module, class, or structure.</span></span>  
  
 <span data-ttu-id="a2144-155">Pokud provedete deklaraci na úrovni modulu, určuje úroveň přístupu, který zvolíte oboru.</span><span class="sxs-lookup"><span data-stu-id="a2144-155">When you make a declaration at the module level, the access level you choose determines the scope.</span></span> <span data-ttu-id="a2144-156">Obor názvů, který obsahuje modul, třídu nebo strukturu ovlivní také oboru.</span><span class="sxs-lookup"><span data-stu-id="a2144-156">The namespace that contains the module, class, or structure also affects the scope.</span></span>  
  
 <span data-ttu-id="a2144-157">Elementy, pro které je deklarovat [privátní](../../../../visual-basic/language-reference/modifiers/private.md) úroveň přístupu jsou dostupné pro každý postup v tomto modulu, ale nechcete žádný kód v různých modulu.</span><span class="sxs-lookup"><span data-stu-id="a2144-157">Elements for which you declare [Private](../../../../visual-basic/language-reference/modifiers/private.md) access level are available to every procedure in that module, but not to any code in a different module.</span></span> <span data-ttu-id="a2144-158">`Dim` Příkaz na úrovni modulu výchozí `Private` Pokud nepoužijete všechny klíčová slova úrovně přístupu.</span><span class="sxs-lookup"><span data-stu-id="a2144-158">The `Dim` statement at module level defaults to `Private` if you do not use any access level keywords.</span></span> <span data-ttu-id="a2144-159">Však můžete provádět oboru a úroveň přístupu zřejmější pomocí `Private` – klíčové slovo v `Dim` příkaz.</span><span class="sxs-lookup"><span data-stu-id="a2144-159">However, you can make the scope and access level more obvious by using the `Private` keyword in the `Dim` statement.</span></span>  
  
 <span data-ttu-id="a2144-160">V následujícím příkladu, všechny postupy, které jsou definované v modulu mohou odkazovat na proměnnou string `strMsg`.</span><span class="sxs-lookup"><span data-stu-id="a2144-160">In the following example, all procedures defined in the module can refer to the string variable `strMsg`.</span></span> <span data-ttu-id="a2144-161">Pokud je druhý postup je volána, zobrazuje obsah proměnnou řetězce `strMsg` v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="a2144-161">When the second procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>  
  
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
  
### <a name="namespace-scope"></a><span data-ttu-id="a2144-162">Namespace oboru</span><span class="sxs-lookup"><span data-stu-id="a2144-162">Namespace Scope</span></span>  
 <span data-ttu-id="a2144-163">Pokud je deklarovat element na úrovni pomocí modulu [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) nebo [veřejné](../../../../visual-basic/language-reference/modifiers/public.md) – klíčové slovo, je k dispozici pro všechny postupy v rámci oboru názvů, ve kterém je deklarovaný element.</span><span class="sxs-lookup"><span data-stu-id="a2144-163">If you declare an element at module level using the [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) or [Public](../../../../visual-basic/language-reference/modifiers/public.md) keyword, it becomes available to all procedures throughout the namespace in which the element is declared.</span></span> <span data-ttu-id="a2144-164">S následující změnou v předcházejícím příkladu proměnnou řetězce `strMsg` lze odkazovat kódem kdekoli v oboru názvů jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="a2144-164">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>  
  
```  
' Include this declaration at module level (not inside any procedure).  
Public strMsg As String  
```  
  
 <span data-ttu-id="a2144-165">Namespace obor obsahuje vnořené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="a2144-165">Namespace scope includes nested namespaces.</span></span> <span data-ttu-id="a2144-166">Element dostupné v rámci oboru názvů je také k dispozici v rámci všech názvů vnořit do daného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a2144-166">An element available from within a namespace is also available from within any namespace nested inside that namespace.</span></span>  
  
 <span data-ttu-id="a2144-167">Pokud projekt neobsahuje žádné [příkaz Namespace](../../../../visual-basic/language-reference/statements/namespace-statement.md)s, které se nacházejí v projektu je v stejného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a2144-167">If your project does not contain any [Namespace Statement](../../../../visual-basic/language-reference/statements/namespace-statement.md)s, everything in the project is in the same namespace.</span></span> <span data-ttu-id="a2144-168">V takovém případě oboru názvů můžete představit jako rozsah projektu.</span><span class="sxs-lookup"><span data-stu-id="a2144-168">In this case, namespace scope can be thought of as project scope.</span></span> <span data-ttu-id="a2144-169">`Public` elementy v modulu, třídu nebo strukturu jsou také k dispozici žádné projekt, který odkazuje na jejich projekt.</span><span class="sxs-lookup"><span data-stu-id="a2144-169">`Public` elements in a module, class, or structure are also available to any project that references their project.</span></span>  
  
## <a name="choice-of-scope"></a><span data-ttu-id="a2144-170">Výběr rozsahu</span><span class="sxs-lookup"><span data-stu-id="a2144-170">Choice of Scope</span></span>  
 <span data-ttu-id="a2144-171">Po deklarování proměnné, byste měli mít na paměti následující body při výběru její obor.</span><span class="sxs-lookup"><span data-stu-id="a2144-171">When you declare a variable, you should keep in mind the following points when choosing its scope.</span></span>  
  
### <a name="advantages-of-local-variables"></a><span data-ttu-id="a2144-172">Výhody lokální proměnné</span><span class="sxs-lookup"><span data-stu-id="a2144-172">Advantages of Local Variables</span></span>  
 <span data-ttu-id="a2144-173">Lokální proměnné jsou dobrou volbou pro jakýkoli druh dočasné výpočet, z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="a2144-173">Local variables are a good choice for any kind of temporary calculation, for the following reasons:</span></span>  
  
-   <span data-ttu-id="a2144-174">**Předcházení název konflikt.**</span><span class="sxs-lookup"><span data-stu-id="a2144-174">**Name Conflict Avoidance.**</span></span> <span data-ttu-id="a2144-175">Místní názvy proměnných nejsou náchylné k konfliktu.</span><span class="sxs-lookup"><span data-stu-id="a2144-175">Local variable names are not susceptible to conflict.</span></span> <span data-ttu-id="a2144-176">Například můžete vytvořit několik různé postupy obsahující proměnné s názvem `intTemp`.</span><span class="sxs-lookup"><span data-stu-id="a2144-176">For example, you can create several different procedures containing a variable called `intTemp`.</span></span> <span data-ttu-id="a2144-177">Stejně dlouho jako každý `intTemp` je deklarován jako místní proměnné, každý postup rozpozná pouze svou vlastní verzi z `intTemp`.</span><span class="sxs-lookup"><span data-stu-id="a2144-177">As long as each `intTemp` is declared as a local variable, each procedure recognizes only its own version of `intTemp`.</span></span> <span data-ttu-id="a2144-178">Všechny jedním postupem změnit hodnotu v jeho místní `intTemp` bez ovlivnění `intTemp` proměnné v další postupy.</span><span class="sxs-lookup"><span data-stu-id="a2144-178">Any one procedure can alter the value in its local `intTemp` without affecting `intTemp` variables in other procedures.</span></span>  
  
-   <span data-ttu-id="a2144-179">**Využití paměti.**</span><span class="sxs-lookup"><span data-stu-id="a2144-179">**Memory Consumption.**</span></span> <span data-ttu-id="a2144-180">Lokální proměnné spotřebuje paměť pouze tehdy, když jejich postup běží.</span><span class="sxs-lookup"><span data-stu-id="a2144-180">Local variables consume memory only while their procedure is running.</span></span> <span data-ttu-id="a2144-181">Jejich paměti je vydala, když se proces vrátí do volající kód.</span><span class="sxs-lookup"><span data-stu-id="a2144-181">Their memory is released when the procedure returns to the calling code.</span></span> <span data-ttu-id="a2144-182">Naopak [sdílené](../../../../visual-basic/language-reference/modifiers/shared.md) a [statické](../../../../visual-basic/language-reference/modifiers/static.md) proměnné spotřebovávat prostředky paměti, dokud vaše aplikace se zastaví, takže použijte je pouze v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="a2144-182">By contrast, [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) and [Static](../../../../visual-basic/language-reference/modifiers/static.md) variables consume memory resources until your application stops running, so use them only when necessary.</span></span> <span data-ttu-id="a2144-183">*Instance proměnné* využívání paměti při jejich instance i nadále existovat, což zajišťuje jejich méně efektivní než místní proměnné, ale potenciálně efektivnější než `Shared` nebo `Static` proměnné.</span><span class="sxs-lookup"><span data-stu-id="a2144-183">*Instance variables* consume memory while their instance continues to exist, which makes them less efficient than local variables, but potentially more efficient than `Shared` or `Static` variables.</span></span>  
  
### <a name="minimizing-scope"></a><span data-ttu-id="a2144-184">Minimalizace oboru</span><span class="sxs-lookup"><span data-stu-id="a2144-184">Minimizing Scope</span></span>  
 <span data-ttu-id="a2144-185">Obecně platí, pokud deklarace, všechny proměnné nebo konstanta, je vhodné programování postupem zajistit co nejrovnoměrnější oboru (rozsah bloku je nejbližší).</span><span class="sxs-lookup"><span data-stu-id="a2144-185">In general, when declaring any variable or constant, it is good programming practice to make the scope as narrow as possible (block scope is the narrowest).</span></span> <span data-ttu-id="a2144-186">To pomáhá konzervaci paměti a minimalizuje případné chybnou informací odkaz na proměnnou nesprávný kód.</span><span class="sxs-lookup"><span data-stu-id="a2144-186">This helps conserve memory and minimizes the chances of your code erroneously referring to the wrong variable.</span></span> <span data-ttu-id="a2144-187">Podobně platí, by měly deklarovat proměnnou, do které se [statické](../../../../visual-basic/language-reference/modifiers/static.md) pouze když je potřeba zachovat jeho hodnota mezi volání procedur.</span><span class="sxs-lookup"><span data-stu-id="a2144-187">Similarly, you should declare a variable to be [Static](../../../../visual-basic/language-reference/modifiers/static.md) only when it is necessary to preserve its value between procedure calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2144-188">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2144-188">See Also</span></span>  
 [<span data-ttu-id="a2144-189">Deklarované charakteristiky elementů</span><span class="sxs-lookup"><span data-stu-id="a2144-189">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="a2144-190">Postupy: Řízení rozsahu proměnné</span><span class="sxs-lookup"><span data-stu-id="a2144-190">How to: Control the Scope of a Variable</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)  
 [<span data-ttu-id="a2144-191">Doba platnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a2144-191">Lifetime in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [<span data-ttu-id="a2144-192">Úrovně přístupu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a2144-192">Access levels in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [<span data-ttu-id="a2144-193">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="a2144-193">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="a2144-194">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="a2144-194">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
