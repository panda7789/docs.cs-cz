---
title: Rozsah
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
ms.openlocfilehash: 1bee904996257474b7457b2aefb1f17d250933cb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410731"
---
# <a name="scope-in-visual-basic"></a><span data-ttu-id="7d944-102">Rozsah v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7d944-102">Scope in Visual Basic</span></span>

<span data-ttu-id="7d944-103">*Obor* deklarovaného prvku je sada veškerého kódu, který se na něj může odkazovat bez kvalifikovaného názvu nebo jeho zpřístupnění prostřednictvím [příkazu Imports (obor názvů a typ .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="7d944-103">The *scope* of a declared element is the set of all code that can refer to it without qualifying its name or making it available through an [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span> <span data-ttu-id="7d944-104">Element může mít obor na jedné z následujících úrovní:</span><span class="sxs-lookup"><span data-stu-id="7d944-104">An element can have scope at one of the following levels:</span></span>

|<span data-ttu-id="7d944-105">Úroveň</span><span class="sxs-lookup"><span data-stu-id="7d944-105">Level</span></span>|<span data-ttu-id="7d944-106">Description</span><span class="sxs-lookup"><span data-stu-id="7d944-106">Description</span></span>|
|-----------|-----------------|
|<span data-ttu-id="7d944-107">Rozsah bloku</span><span class="sxs-lookup"><span data-stu-id="7d944-107">Block scope</span></span>|<span data-ttu-id="7d944-108">K dispozici pouze v bloku kódu, ve kterém je deklarována</span><span class="sxs-lookup"><span data-stu-id="7d944-108">Available only within the code block in which it is declared</span></span>|
|<span data-ttu-id="7d944-109">Rozsah procedury</span><span class="sxs-lookup"><span data-stu-id="7d944-109">Procedure scope</span></span>|<span data-ttu-id="7d944-110">K dispozici pro veškerý kód v rámci postupu, ve kterém je deklarována</span><span class="sxs-lookup"><span data-stu-id="7d944-110">Available to all code within the procedure in which it is declared</span></span>|
|<span data-ttu-id="7d944-111">Rozsah modulu</span><span class="sxs-lookup"><span data-stu-id="7d944-111">Module scope</span></span>|<span data-ttu-id="7d944-112">K dispozici pro veškerý kód v rámci modulu, třídy nebo struktury, ve které je deklarována</span><span class="sxs-lookup"><span data-stu-id="7d944-112">Available to all code within the module, class, or structure in which it is declared</span></span>|
|<span data-ttu-id="7d944-113">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="7d944-113">Namespace scope</span></span>|<span data-ttu-id="7d944-114">K dispozici pro veškerý kód v oboru názvů, ve kterém je deklarována</span><span class="sxs-lookup"><span data-stu-id="7d944-114">Available to all code in the namespace in which it is declared</span></span>|

<span data-ttu-id="7d944-115">Tyto úrovně postupu rozsahu od nejužšího (bloku) po nejširší (obor názvů), kde *nejužší rozsah* znamená nejmenší sadu kódu, který může odkazovat na prvek bez kvalifikace.</span><span class="sxs-lookup"><span data-stu-id="7d944-115">These levels of scope progress from the narrowest (block) to the widest (namespace), where *narrowest scope* means the smallest set of code that can refer to the element without qualification.</span></span> <span data-ttu-id="7d944-116">Další informace najdete v části "úrovně oboru" na této stránce.</span><span class="sxs-lookup"><span data-stu-id="7d944-116">For more information, see "Levels of Scope" on this page.</span></span>

## <a name="specifying-scope-and-defining-variables"></a><span data-ttu-id="7d944-117">Určení rozsahu a definování proměnných</span><span class="sxs-lookup"><span data-stu-id="7d944-117">Specifying Scope and Defining Variables</span></span>

<span data-ttu-id="7d944-118">Rozsah prvku určíte při jeho deklaraci.</span><span class="sxs-lookup"><span data-stu-id="7d944-118">You specify the scope of an element when you declare it.</span></span> <span data-ttu-id="7d944-119">Rozsah může záviset na následujících faktorech:</span><span class="sxs-lookup"><span data-stu-id="7d944-119">The scope can depend on the following factors:</span></span>

- <span data-ttu-id="7d944-120">Oblast (blok, procedura, modul, třída nebo struktura), ve které deklarujete element</span><span class="sxs-lookup"><span data-stu-id="7d944-120">The region (block, procedure, module, class, or structure) in which you declare the element</span></span>

- <span data-ttu-id="7d944-121">Obor názvů obsahující deklaraci elementu</span><span class="sxs-lookup"><span data-stu-id="7d944-121">The namespace containing the element's declaration</span></span>

- <span data-ttu-id="7d944-122">Úroveň přístupu, kterou deklarujete pro element</span><span class="sxs-lookup"><span data-stu-id="7d944-122">The access level you declare for the element</span></span>

<span data-ttu-id="7d944-123">Pokud definujete proměnné se stejným názvem, ale s jiným rozsahem, postupujte opatrně, protože by to mohlo vést k neočekávaným výsledkům.</span><span class="sxs-lookup"><span data-stu-id="7d944-123">Use care when you define variables with the same name but different scope, because doing so can lead to unexpected results.</span></span> <span data-ttu-id="7d944-124">Další informace naleznete v tématu [odkazy na deklarované elementy](references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="7d944-124">For more information, see [References to Declared Elements](references-to-declared-elements.md).</span></span>

## <a name="levels-of-scope"></a><span data-ttu-id="7d944-125">Úrovně rozsahu</span><span class="sxs-lookup"><span data-stu-id="7d944-125">Levels of Scope</span></span>

<span data-ttu-id="7d944-126">Programový prvek je k dispozici v celé oblasti, ve které jej deklarujete.</span><span class="sxs-lookup"><span data-stu-id="7d944-126">A programming element is available throughout the region in which you declare it.</span></span> <span data-ttu-id="7d944-127">Veškerý kód ve stejné oblasti může odkazovat na prvek bez kvalifikovaného názvu.</span><span class="sxs-lookup"><span data-stu-id="7d944-127">All code in the same region can refer to the element without qualifying its name.</span></span>

### <a name="block-scope"></a><span data-ttu-id="7d944-128">Rozsah bloku</span><span class="sxs-lookup"><span data-stu-id="7d944-128">Block Scope</span></span>

<span data-ttu-id="7d944-129">Blok je sada příkazů, které jsou uzavřeny v rámci inicializační a ukončovací příkazy deklarace, například následující:</span><span class="sxs-lookup"><span data-stu-id="7d944-129">A block is a set of statements enclosed within initiating and terminating declaration statements, such as the following:</span></span>

- <span data-ttu-id="7d944-130">`Do` a `Loop`</span><span class="sxs-lookup"><span data-stu-id="7d944-130">`Do` and `Loop`</span></span>

- <span data-ttu-id="7d944-131">`For`[ `Each` ] a`Next`</span><span class="sxs-lookup"><span data-stu-id="7d944-131">`For` [`Each`] and `Next`</span></span>

- <span data-ttu-id="7d944-132">`If` a `End If`</span><span class="sxs-lookup"><span data-stu-id="7d944-132">`If` and `End If`</span></span>

- <span data-ttu-id="7d944-133">`Select` a `End Select`</span><span class="sxs-lookup"><span data-stu-id="7d944-133">`Select` and `End Select`</span></span>

- <span data-ttu-id="7d944-134">`SyncLock` a `End SyncLock`</span><span class="sxs-lookup"><span data-stu-id="7d944-134">`SyncLock` and `End SyncLock`</span></span>

- <span data-ttu-id="7d944-135">`Try` a `End Try`</span><span class="sxs-lookup"><span data-stu-id="7d944-135">`Try` and `End Try`</span></span>

- <span data-ttu-id="7d944-136">`While` a `End While`</span><span class="sxs-lookup"><span data-stu-id="7d944-136">`While` and `End While`</span></span>

- <span data-ttu-id="7d944-137">`With` a `End With`</span><span class="sxs-lookup"><span data-stu-id="7d944-137">`With` and `End With`</span></span>

<span data-ttu-id="7d944-138">Pokud deklarujete proměnnou v rámci bloku, můžete ji použít pouze v rámci tohoto bloku.</span><span class="sxs-lookup"><span data-stu-id="7d944-138">If you declare a variable within a block, you can use it only within that block.</span></span> <span data-ttu-id="7d944-139">V následujícím příkladu je rozsah proměnné celého čísla `cube` blok mezi `If` a `End If` a nemůžete již odkazovat na, `cube` Pokud provádění projde z bloku.</span><span class="sxs-lookup"><span data-stu-id="7d944-139">In the following example, the scope of the integer variable `cube` is the block between `If` and `End If`, and you can no longer refer to `cube` when execution passes out of the block.</span></span>

```vb
If n < 1291 Then
    Dim cube As Integer
    cube = n ^ 3
End If
```

> [!NOTE]
> <span data-ttu-id="7d944-140">I v případě, že rozsah proměnné je omezen na blok, je jeho životnost stále i u celého postupu.</span><span class="sxs-lookup"><span data-stu-id="7d944-140">Even if the scope of a variable is limited to a block, its lifetime is still that of the entire procedure.</span></span> <span data-ttu-id="7d944-141">Pokud zadáte blok více než jednou během postupu, každá proměnná bloku uchová svou předchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7d944-141">If you enter the block more than once during the procedure, each block variable retains its previous value.</span></span> <span data-ttu-id="7d944-142">Chcete-li se vyhnout neočekávaným výsledkům v takovém případě, je vhodné inicializovat blokové proměnné na začátku bloku.</span><span class="sxs-lookup"><span data-stu-id="7d944-142">To avoid unexpected results in such a case, it is wise to initialize block variables at the beginning of the block.</span></span>

### <a name="procedure-scope"></a><span data-ttu-id="7d944-143">Rozsah procedury</span><span class="sxs-lookup"><span data-stu-id="7d944-143">Procedure Scope</span></span>

<span data-ttu-id="7d944-144">Element deklarovaný v proceduře není k dispozici mimo tento postup.</span><span class="sxs-lookup"><span data-stu-id="7d944-144">An element declared within a procedure is not available outside that procedure.</span></span> <span data-ttu-id="7d944-145">Může použít pouze postup, který obsahuje deklaraci.</span><span class="sxs-lookup"><span data-stu-id="7d944-145">Only the procedure that contains the declaration can use it.</span></span> <span data-ttu-id="7d944-146">Proměnné na této úrovni se označují také jako *místní proměnné*.</span><span class="sxs-lookup"><span data-stu-id="7d944-146">Variables at this level are also known as *local variables*.</span></span> <span data-ttu-id="7d944-147">Deklarujete je pomocí [příkazu Dim](../../../language-reference/statements/dim-statement.md)s klíčovým slovem [static](../../../language-reference/modifiers/static.md) nebo bez něj.</span><span class="sxs-lookup"><span data-stu-id="7d944-147">You declare them with the [Dim Statement](../../../language-reference/statements/dim-statement.md), with or without the [Static](../../../language-reference/modifiers/static.md) keyword.</span></span>

<span data-ttu-id="7d944-148">Postup a rozsah bloku úzce souvisejí.</span><span class="sxs-lookup"><span data-stu-id="7d944-148">Procedure and block scope are closely related.</span></span> <span data-ttu-id="7d944-149">Pokud deklarujete proměnnou uvnitř procedury, ale mimo libovolný blok v rámci této procedury, můžete si považovat proměnnou jako s rozsahem bloku, kde blok je celý postup.</span><span class="sxs-lookup"><span data-stu-id="7d944-149">If you declare a variable inside a procedure but outside any block within that procedure, you can think of the variable as having block scope, where the block is the entire procedure.</span></span>

> [!NOTE]
> <span data-ttu-id="7d944-150">Všechny místní prvky, i když jsou `Static` proměnné, jsou soukromé pro proceduru, ve které se vyskytují.</span><span class="sxs-lookup"><span data-stu-id="7d944-150">All local elements, even if they are `Static` variables, are private to the procedure in which they appear.</span></span> <span data-ttu-id="7d944-151">V proceduře nelze deklarovat žádný element pomocí klíčového slova [Public](../../../language-reference/modifiers/public.md) .</span><span class="sxs-lookup"><span data-stu-id="7d944-151">You cannot declare any element using the [Public](../../../language-reference/modifiers/public.md) keyword within a procedure.</span></span>

### <a name="module-scope"></a><span data-ttu-id="7d944-152">Rozsah modulu</span><span class="sxs-lookup"><span data-stu-id="7d944-152">Module Scope</span></span>

<span data-ttu-id="7d944-153">Pro usnadnění práce se *úroveň modulu* s jedním termínem aplikuje rovnoměrně na moduly, třídy a struktury.</span><span class="sxs-lookup"><span data-stu-id="7d944-153">For convenience, the single term *module level* applies equally to modules, classes, and structures.</span></span> <span data-ttu-id="7d944-154">Můžete deklarovat prvky na této úrovni tím, že umístíte příkaz deklarace mimo jakýkoli postup nebo blok, ale v rámci modulu, třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="7d944-154">You can declare elements at this level by placing the declaration statement outside of any procedure or block but within the module, class, or structure.</span></span>

<span data-ttu-id="7d944-155">Při vytváření deklarace na úrovni modulu určuje úroveň přístupu, kterou zvolíte, obor.</span><span class="sxs-lookup"><span data-stu-id="7d944-155">When you make a declaration at the module level, the access level you choose determines the scope.</span></span> <span data-ttu-id="7d944-156">Obor názvů, který obsahuje modul, třídu nebo strukturu, má vliv také na obor.</span><span class="sxs-lookup"><span data-stu-id="7d944-156">The namespace that contains the module, class, or structure also affects the scope.</span></span>

<span data-ttu-id="7d944-157">Prvky, pro které deklarujete úroveň [privátního](../../../language-reference/modifiers/private.md) přístupu, jsou k dispozici pro každý postup v daném modulu, ale nikoli pro jakýkoliv kód v jiném modulu.</span><span class="sxs-lookup"><span data-stu-id="7d944-157">Elements for which you declare [Private](../../../language-reference/modifiers/private.md) access level are available to every procedure in that module, but not to any code in a different module.</span></span> <span data-ttu-id="7d944-158">`Dim` `Private` Pokud nepoužíváte žádná klíčová slova úrovně přístupu, příkaz na úrovni modulu se nastaví na výchozí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7d944-158">The `Dim` statement at module level defaults to `Private` if you do not use any access level keywords.</span></span> <span data-ttu-id="7d944-159">Pomocí `Private` klíčového slova v příkazu však můžete nastavit rozsah a úroveň přístupu `Dim` .</span><span class="sxs-lookup"><span data-stu-id="7d944-159">However, you can make the scope and access level more obvious by using the `Private` keyword in the `Dim` statement.</span></span>

<span data-ttu-id="7d944-160">V následujícím příkladu mohou všechny procedury definované v modulu odkazovat na řetězcovou proměnnou `strMsg` .</span><span class="sxs-lookup"><span data-stu-id="7d944-160">In the following example, all procedures defined in the module can refer to the string variable `strMsg`.</span></span> <span data-ttu-id="7d944-161">Při volání druhého postupu se v dialogovém okně zobrazí obsah řetězcové proměnné `strMsg` .</span><span class="sxs-lookup"><span data-stu-id="7d944-161">When the second procedure is called, it displays the contents of the string variable `strMsg` in a dialog box.</span></span>

```vb
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

### <a name="namespace-scope"></a><span data-ttu-id="7d944-162">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="7d944-162">Namespace Scope</span></span>

<span data-ttu-id="7d944-163">Pokud deklarujete element na úrovni modulu pomocí klíčového slova [Friend](../../../language-reference/modifiers/friend.md) nebo [Public](../../../language-reference/modifiers/public.md) , bude zpřístupněn všem procedurám v rámci oboru názvů, ve kterém je element deklarován.</span><span class="sxs-lookup"><span data-stu-id="7d944-163">If you declare an element at module level using the [Friend](../../../language-reference/modifiers/friend.md) or [Public](../../../language-reference/modifiers/public.md) keyword, it becomes available to all procedures throughout the namespace in which the element is declared.</span></span> <span data-ttu-id="7d944-164">S následující změnou v předchozím příkladu může být řetězcová proměnná `strMsg` odkazována pomocí kódu kdekoli v oboru názvů své deklarace.</span><span class="sxs-lookup"><span data-stu-id="7d944-164">With the following alteration to the preceding example, the string variable `strMsg` can be referred to by code anywhere in the namespace of its declaration.</span></span>

```vb
' Include this declaration at module level (not inside any procedure).
Public strMsg As String
```

<span data-ttu-id="7d944-165">Obor názvů zahrnuje vnořené obory názvů.</span><span class="sxs-lookup"><span data-stu-id="7d944-165">Namespace scope includes nested namespaces.</span></span> <span data-ttu-id="7d944-166">Element dostupný v rámci oboru názvů je také k dispozici v rámci jakéhokoli oboru názvů vnořeného uvnitř daného oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7d944-166">An element available from within a namespace is also available from within any namespace nested inside that namespace.</span></span>

<span data-ttu-id="7d944-167">Pokud projekt neobsahuje žádné [Příkazy oboru názvů](../../../language-reference/statements/namespace-statement.md), je vše v projektu ve stejném oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="7d944-167">If your project does not contain any [Namespace Statement](../../../language-reference/statements/namespace-statement.md)s, everything in the project is in the same namespace.</span></span> <span data-ttu-id="7d944-168">V tomto případě lze obor názvů představit jako rozsah projektu.</span><span class="sxs-lookup"><span data-stu-id="7d944-168">In this case, namespace scope can be thought of as project scope.</span></span> <span data-ttu-id="7d944-169">`Public`prvky v modulu, třídě nebo struktuře jsou také k dispozici pro každý projekt, který odkazuje na svůj projekt.</span><span class="sxs-lookup"><span data-stu-id="7d944-169">`Public` elements in a module, class, or structure are also available to any project that references their project.</span></span>

## <a name="choice-of-scope"></a><span data-ttu-id="7d944-170">Volba rozsahu</span><span class="sxs-lookup"><span data-stu-id="7d944-170">Choice of Scope</span></span>

<span data-ttu-id="7d944-171">Při deklaraci proměnné byste měli při výběru jejího rozsahu brát v úvahu následující body.</span><span class="sxs-lookup"><span data-stu-id="7d944-171">When you declare a variable, you should keep in mind the following points when choosing its scope.</span></span>

### <a name="advantages-of-local-variables"></a><span data-ttu-id="7d944-172">Výhody místních proměnných</span><span class="sxs-lookup"><span data-stu-id="7d944-172">Advantages of Local Variables</span></span>

<span data-ttu-id="7d944-173">Místní proměnné jsou dobrou volbou pro jakýkoliv druh dočasného výpočtu, a to z následujících důvodů:</span><span class="sxs-lookup"><span data-stu-id="7d944-173">Local variables are a good choice for any kind of temporary calculation, for the following reasons:</span></span>

- <span data-ttu-id="7d944-174">**Vyhnout se konfliktu názvů.**</span><span class="sxs-lookup"><span data-stu-id="7d944-174">**Name Conflict Avoidance.**</span></span> <span data-ttu-id="7d944-175">Názvy místních proměnných nejsou náchylné ke konfliktu.</span><span class="sxs-lookup"><span data-stu-id="7d944-175">Local variable names are not susceptible to conflict.</span></span> <span data-ttu-id="7d944-176">Můžete například vytvořit několik různých postupů obsahujících proměnnou s názvem `intTemp` .</span><span class="sxs-lookup"><span data-stu-id="7d944-176">For example, you can create several different procedures containing a variable called `intTemp`.</span></span> <span data-ttu-id="7d944-177">Pokud `intTemp` je každý deklarován jako místní proměnná, každý postup rozpoznává pouze svou vlastní verzi `intTemp` .</span><span class="sxs-lookup"><span data-stu-id="7d944-177">As long as each `intTemp` is declared as a local variable, each procedure recognizes only its own version of `intTemp`.</span></span> <span data-ttu-id="7d944-178">Kterýkoli z těchto postupů může změnit hodnotu v místním prostředí, `intTemp` aniž by to ovlivnilo `intTemp` proměnné v jiných postupech.</span><span class="sxs-lookup"><span data-stu-id="7d944-178">Any one procedure can alter the value in its local `intTemp` without affecting `intTemp` variables in other procedures.</span></span>

- <span data-ttu-id="7d944-179">**Spotřeba paměti.**</span><span class="sxs-lookup"><span data-stu-id="7d944-179">**Memory Consumption.**</span></span> <span data-ttu-id="7d944-180">Místní proměnné spotřebovávají paměť pouze v době, kdy je spuštěn jejich postup.</span><span class="sxs-lookup"><span data-stu-id="7d944-180">Local variables consume memory only while their procedure is running.</span></span> <span data-ttu-id="7d944-181">Jejich paměť je uvolněna v případě, že se procedura vrátí na volající kód.</span><span class="sxs-lookup"><span data-stu-id="7d944-181">Their memory is released when the procedure returns to the calling code.</span></span> <span data-ttu-id="7d944-182">Naproti tomu [sdílené](../../../language-reference/modifiers/shared.md) a [statické](../../../language-reference/modifiers/static.md) proměnné využívají paměťové prostředky, dokud se vaše aplikace neukončí, takže je používejte, jenom když je to potřeba.</span><span class="sxs-lookup"><span data-stu-id="7d944-182">By contrast, [Shared](../../../language-reference/modifiers/shared.md) and [Static](../../../language-reference/modifiers/static.md) variables consume memory resources until your application stops running, so use them only when necessary.</span></span> <span data-ttu-id="7d944-183">*Proměnné instance* spotřebovávají paměť, zatímco jejich instance stále existují, což snižuje efektivitu než lokální proměnné, ale potenciálně účinnější než `Shared` nebo `Static` proměnných.</span><span class="sxs-lookup"><span data-stu-id="7d944-183">*Instance variables* consume memory while their instance continues to exist, which makes them less efficient than local variables, but potentially more efficient than `Shared` or `Static` variables.</span></span>

### <a name="minimizing-scope"></a><span data-ttu-id="7d944-184">Minimalizace rozsahu</span><span class="sxs-lookup"><span data-stu-id="7d944-184">Minimizing Scope</span></span>

<span data-ttu-id="7d944-185">Obecně platí, že při deklaraci jakékoli proměnné nebo konstanty je dobrým postupem způsob, jak rozsah co nejblíže omezit (rozsah bloku je nejužší).</span><span class="sxs-lookup"><span data-stu-id="7d944-185">In general, when declaring any variable or constant, it is good programming practice to make the scope as narrow as possible (block scope is the narrowest).</span></span> <span data-ttu-id="7d944-186">To pomáhá šetřit paměť a minimalizovat šance na to, že váš kód chybně odkazuje na nesprávnou proměnnou.</span><span class="sxs-lookup"><span data-stu-id="7d944-186">This helps conserve memory and minimizes the chances of your code erroneously referring to the wrong variable.</span></span> <span data-ttu-id="7d944-187">Podobně byste měli deklarovat proměnnou, která bude [statická](../../../language-reference/modifiers/static.md) pouze v případě, že je nutné zachovat hodnotu mezi voláními procedur.</span><span class="sxs-lookup"><span data-stu-id="7d944-187">Similarly, you should declare a variable to be [Static](../../../language-reference/modifiers/static.md) only when it is necessary to preserve its value between procedure calls.</span></span>

## <a name="see-also"></a><span data-ttu-id="7d944-188">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d944-188">See also</span></span>

- [<span data-ttu-id="7d944-189">Deklarované charakteristiky elementů</span><span class="sxs-lookup"><span data-stu-id="7d944-189">Declared Element Characteristics</span></span>](declared-element-characteristics.md)
- [<span data-ttu-id="7d944-190">Postupy: Řízení rozsahu proměnné</span><span class="sxs-lookup"><span data-stu-id="7d944-190">How to: Control the Scope of a Variable</span></span>](how-to-control-the-scope-of-a-variable.md)
- [<span data-ttu-id="7d944-191">Doba platnosti v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7d944-191">Lifetime in Visual Basic</span></span>](lifetime.md)
- [<span data-ttu-id="7d944-192">Úrovně přístupu v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7d944-192">Access levels in Visual Basic</span></span>](access-levels.md)
- [<span data-ttu-id="7d944-193">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="7d944-193">References to Declared Elements</span></span>](references-to-declared-elements.md)
- [<span data-ttu-id="7d944-194">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="7d944-194">Variable Declaration</span></span>](../variables/variable-declaration.md)
