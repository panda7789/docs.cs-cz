---
title: Using – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: 6ec0e228b3898f66f27e322b5db2dd7f3bf3d7d6
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352760"
---
# <a name="using-statement-visual-basic"></a><span data-ttu-id="33925-102">Using – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="33925-102">Using Statement (Visual Basic)</span></span>

<span data-ttu-id="33925-103">Deklaruje začátek bloku `Using` a volitelně získá systémové prostředky, které blok ovládá.</span><span class="sxs-lookup"><span data-stu-id="33925-103">Declares the beginning of a `Using` block and optionally acquires the system resources that the block controls.</span></span>

## <a name="syntax"></a><span data-ttu-id="33925-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33925-104">Syntax</span></span>

```vb
Using { resourcelist | resourceexpression }
    [ statements ]
End Using
```

## <a name="parts"></a><span data-ttu-id="33925-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="33925-105">Parts</span></span>

|<span data-ttu-id="33925-106">Termín</span><span class="sxs-lookup"><span data-stu-id="33925-106">Term</span></span>|<span data-ttu-id="33925-107">Definice</span><span class="sxs-lookup"><span data-stu-id="33925-107">Definition</span></span>|  
|---|---|  
|`resourcelist`|<span data-ttu-id="33925-108">Vyžaduje se, pokud neposkytnete `resourceexpression`.</span><span class="sxs-lookup"><span data-stu-id="33925-108">Required if you do not supply `resourceexpression`.</span></span> <span data-ttu-id="33925-109">Seznam jednoho nebo více systémových prostředků, které tento `Using` blokuje ovládací prvky, oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="33925-109">List of one or more system resources that this `Using` block controls, separated by commas.</span></span>|  
|`resourceexpression`|<span data-ttu-id="33925-110">Vyžaduje se, pokud neposkytnete `resourcelist`.</span><span class="sxs-lookup"><span data-stu-id="33925-110">Required if you do not supply `resourcelist`.</span></span> <span data-ttu-id="33925-111">Referenční proměnná nebo výraz odkazující na systémový prostředek, který má být ovládán tímto `Using`m blokem.</span><span class="sxs-lookup"><span data-stu-id="33925-111">Reference variable or expression referring to a system resource to be controlled by this `Using` block.</span></span>|  
|`statements`|<span data-ttu-id="33925-112">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="33925-112">Optional.</span></span> <span data-ttu-id="33925-113">Blok příkazů, které spouští blok `Using`.</span><span class="sxs-lookup"><span data-stu-id="33925-113">Block of statements that the `Using` block runs.</span></span>|  
|`End Using`|<span data-ttu-id="33925-114">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="33925-114">Required.</span></span> <span data-ttu-id="33925-115">Ukončí definici `Using` bloku a uvolní všechny prostředky, které ovládací prvek IT ovládá.</span><span class="sxs-lookup"><span data-stu-id="33925-115">Terminates the definition of the `Using` block and disposes of all the resources that it controls.</span></span>|  

 <span data-ttu-id="33925-116">Každý prostředek v části `resourcelist` má následující syntaxi a části:</span><span class="sxs-lookup"><span data-stu-id="33925-116">Each resource in the `resourcelist` part has the following syntax and parts:</span></span>

 `resourcename As New resourcetype [ ( [ arglist ] ) ]`

 <span data-ttu-id="33925-117">-nebo-</span><span class="sxs-lookup"><span data-stu-id="33925-117">-or-</span></span>

 `resourcename As resourcetype = resourceexpression`

## <a name="resourcelist-parts"></a><span data-ttu-id="33925-118">resourceList části</span><span class="sxs-lookup"><span data-stu-id="33925-118">resourcelist Parts</span></span>

|<span data-ttu-id="33925-119">Termín</span><span class="sxs-lookup"><span data-stu-id="33925-119">Term</span></span>|<span data-ttu-id="33925-120">Definice</span><span class="sxs-lookup"><span data-stu-id="33925-120">Definition</span></span>|  
|---|---|  
|`resourcename`|<span data-ttu-id="33925-121">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="33925-121">Required.</span></span> <span data-ttu-id="33925-122">Referenční proměnná, která odkazuje na systémový prostředek, který ovládací prvky blokování `Using`.</span><span class="sxs-lookup"><span data-stu-id="33925-122">Reference variable that refers to a system resource that the `Using` block controls.</span></span>|  
|`New`|<span data-ttu-id="33925-123">Vyžaduje se, pokud příkaz `Using` získá prostředek.</span><span class="sxs-lookup"><span data-stu-id="33925-123">Required if the `Using` statement acquires the resource.</span></span> <span data-ttu-id="33925-124">Pokud jste už tento prostředek získali, použijte druhou alternativu syntaxe.</span><span class="sxs-lookup"><span data-stu-id="33925-124">If you have already acquired the resource, use the second syntax alternative.</span></span>|  
|`resourcetype`|<span data-ttu-id="33925-125">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="33925-125">Required.</span></span> <span data-ttu-id="33925-126">Třída prostředku</span><span class="sxs-lookup"><span data-stu-id="33925-126">The class of the resource.</span></span> <span data-ttu-id="33925-127">Třída musí implementovat rozhraní <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="33925-127">The class must implement the <xref:System.IDisposable> interface.</span></span>|  
|`arglist`|<span data-ttu-id="33925-128">Volitelná.</span><span class="sxs-lookup"><span data-stu-id="33925-128">Optional.</span></span> <span data-ttu-id="33925-129">Seznam argumentů, které předáváte konstruktoru pro vytvoření instance `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="33925-129">List of arguments you are passing to the constructor to create an instance of `resourcetype`.</span></span> <span data-ttu-id="33925-130">Viz [seznam parametrů](parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="33925-130">See [Parameter List](parameter-list.md).</span></span>|  
|`resourceexpression`|<span data-ttu-id="33925-131">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="33925-131">Required.</span></span> <span data-ttu-id="33925-132">Proměnná nebo výraz odkazující na systémový prostředek splňující požadavky `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="33925-132">Variable or expression referring to a system resource satisfying the requirements of `resourcetype`.</span></span> <span data-ttu-id="33925-133">Použijete-li druhou alternativu syntaxe, je nutné získat prostředek před předáním řízení příkazu `Using`.</span><span class="sxs-lookup"><span data-stu-id="33925-133">If you use the second syntax alternative, you must acquire the resource before passing control to the `Using` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33925-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="33925-134">Remarks</span></span>

 <span data-ttu-id="33925-135">Někdy váš kód vyžaduje nespravovaný prostředek, jako je popisovač souboru, Obálka COM nebo připojení SQL.</span><span class="sxs-lookup"><span data-stu-id="33925-135">Sometimes your code requires an unmanaged resource, such as a file handle, a COM wrapper, or a SQL connection.</span></span> <span data-ttu-id="33925-136">`Using` blok garantuje vyřazení jednoho nebo více takových prostředků, když je kód dokončen.</span><span class="sxs-lookup"><span data-stu-id="33925-136">A `Using` block guarantees the disposal of one or more such resources when your code is finished with them.</span></span> <span data-ttu-id="33925-137">Díky tomu jsou k dispozici pro další kód pro použití.</span><span class="sxs-lookup"><span data-stu-id="33925-137">This makes them available for other code to use.</span></span>

 <span data-ttu-id="33925-138">Spravované prostředky jsou odstraněny nástrojem .NET Framework uvolňování paměti (GC) bez dalšího kódování na vaší straně.</span><span class="sxs-lookup"><span data-stu-id="33925-138">Managed resources are disposed of by the .NET Framework garbage collector (GC) without any extra coding on your part.</span></span> <span data-ttu-id="33925-139">Pro spravované prostředky nepotřebujete `Using` blok.</span><span class="sxs-lookup"><span data-stu-id="33925-139">You do not need a `Using` block for managed resources.</span></span> <span data-ttu-id="33925-140">K vynucení vyřazení spravovaného prostředku místo toho, aby se čekalo na uvolňování paměti, však stále můžete použít blok `Using`.</span><span class="sxs-lookup"><span data-stu-id="33925-140">However, you can still use a `Using` block to force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>

 <span data-ttu-id="33925-141">`Using` blok má tři části: pořízení, využití a vyřazení.</span><span class="sxs-lookup"><span data-stu-id="33925-141">A `Using` block has three parts: acquisition, usage, and disposal.</span></span>

- <span data-ttu-id="33925-142">*Akvizice* znamená vytvoření proměnné a její inicializaci, aby odkazovala na systémový prostředek.</span><span class="sxs-lookup"><span data-stu-id="33925-142">*Acquisition* means creating a variable and initializing it to refer to the system resource.</span></span> <span data-ttu-id="33925-143">Příkaz `Using` může získat jeden nebo více prostředků, nebo můžete získat přesně jeden prostředek před vstupem do bloku a zadat ho do příkazu `Using`.</span><span class="sxs-lookup"><span data-stu-id="33925-143">The `Using` statement can acquire one or more resources, or you can acquire exactly one resource before entering the block and supply it to the `Using` statement.</span></span> <span data-ttu-id="33925-144">Pokud zadáte `resourceexpression`, je nutné získat prostředek před předáním řízení příkazu `Using`.</span><span class="sxs-lookup"><span data-stu-id="33925-144">If you supply `resourceexpression`, you must acquire the resource before passing control to the `Using` statement.</span></span>

- <span data-ttu-id="33925-145">*Použití* znamená přístup k prostředkům a provádění akcí s nimi.</span><span class="sxs-lookup"><span data-stu-id="33925-145">*Usage* means accessing the resources and performing actions with them.</span></span> <span data-ttu-id="33925-146">Příkazy mezi `Using` a `End Using` reprezentují využití prostředků.</span><span class="sxs-lookup"><span data-stu-id="33925-146">The statements between `Using` and `End Using` represent the usage of the resources.</span></span>

- <span data-ttu-id="33925-147">*Odstraňování* znamená volání metody <xref:System.IDisposable.Dispose%2A> u objektu v `resourcename`.</span><span class="sxs-lookup"><span data-stu-id="33925-147">*Disposal* means calling the <xref:System.IDisposable.Dispose%2A> method on the object in `resourcename`.</span></span> <span data-ttu-id="33925-148">Tím umožníte, aby objekt čistě ukončil své prostředky.</span><span class="sxs-lookup"><span data-stu-id="33925-148">This allows the object to cleanly terminate its resources.</span></span> <span data-ttu-id="33925-149">Příkaz `End Using` uvolní prostředky pod ovládacím prvkem bloku `Using`.</span><span class="sxs-lookup"><span data-stu-id="33925-149">The `End Using` statement disposes of the resources under the `Using` block's control.</span></span>

## <a name="behavior"></a><span data-ttu-id="33925-150">Chování</span><span class="sxs-lookup"><span data-stu-id="33925-150">Behavior</span></span>

 <span data-ttu-id="33925-151">`Using` blok se chová jako `Try`...`Finally` konstrukce, ve které `Try` blok používá prostředky a `Finally` blokuje jejich uvolnění.</span><span class="sxs-lookup"><span data-stu-id="33925-151">A `Using` block behaves like a `Try`...`Finally` construction in which the `Try` block uses the resources and the `Finally` block disposes of them.</span></span> <span data-ttu-id="33925-152">Z tohoto důvodu blok `Using` garantuje odstranění prostředků bez ohledu na to, jak tento blok ukončujete.</span><span class="sxs-lookup"><span data-stu-id="33925-152">Because of this, the `Using` block guarantees disposal of the resources, no matter how you exit the block.</span></span> <span data-ttu-id="33925-153">To platí i v případě neošetřené výjimky, s výjimkou <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="33925-153">This is true even in the case of an unhandled exception, except for a <xref:System.StackOverflowException>.</span></span>

 <span data-ttu-id="33925-154">Rozsah všech proměnných prostředků získaných příkazem `Using` je omezen na blok `Using`.</span><span class="sxs-lookup"><span data-stu-id="33925-154">The scope of every resource variable acquired by the `Using` statement is limited to the `Using` block.</span></span>

 <span data-ttu-id="33925-155">Pokud zadáte více než jeden systémový prostředek v příkazu `Using`, efekt je stejný, jako při vnoření `Using` bloků v rámci jiného.</span><span class="sxs-lookup"><span data-stu-id="33925-155">If you specify more than one system resource in the `Using` statement, the effect is the same as if you nested `Using` blocks one within another.</span></span>

 <span data-ttu-id="33925-156">Pokud je `resourcename` `Nothing`, není provedeno žádné volání <xref:System.IDisposable.Dispose%2A> a není vyvolána žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="33925-156">If `resourcename` is `Nothing`, no call to <xref:System.IDisposable.Dispose%2A> is made, and no exception is thrown.</span></span>

## <a name="structured-exception-handling-within-a-using-block"></a><span data-ttu-id="33925-157">Strukturované zpracování výjimek v bloku using</span><span class="sxs-lookup"><span data-stu-id="33925-157">Structured Exception Handling Within a Using Block</span></span>

 <span data-ttu-id="33925-158">Pokud potřebujete zpracovat výjimku, ke které může dojít v rámci bloku `Using`, můžete přidat kompletní `Try`...`Finally` konstrukce.</span><span class="sxs-lookup"><span data-stu-id="33925-158">If you need to handle an exception that might occur within the `Using` block, you can add a complete `Try`...`Finally` construction to it.</span></span> <span data-ttu-id="33925-159">Pokud potřebujete zpracovat případ, kde se příkaz `Using` v získání prostředku nezdařil, můžete otestovat a zjistit, zda `resourcename` `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="33925-159">If you need to handle the case where the `Using` statement is not successful in acquiring a resource, you can test to see if `resourcename` is `Nothing`.</span></span>

## <a name="structured-exception-handling-instead-of-a-using-block"></a><span data-ttu-id="33925-160">Strukturované zpracování výjimek namísto bloku using</span><span class="sxs-lookup"><span data-stu-id="33925-160">Structured Exception Handling Instead of a Using Block</span></span>

 <span data-ttu-id="33925-161">Pokud potřebujete lepší kontrolu nad získáním prostředků nebo potřebujete další kód v bloku `Finally`, můžete `Using` bloku přepsat jako `Try`...`Finally` konstrukce.</span><span class="sxs-lookup"><span data-stu-id="33925-161">If you need finer control over the acquisition of the resources, or you need additional code in the `Finally` block, you can rewrite the `Using` block as a `Try`...`Finally` construction.</span></span> <span data-ttu-id="33925-162">Následující příklad ukazuje kostru `Try` a `Using` konstrukce, které jsou ekvivalentní při získávání a odstraňování `resource`.</span><span class="sxs-lookup"><span data-stu-id="33925-162">The following example shows skeleton `Try` and `Using` constructions that are equivalent in the acquisition and disposal of `resource`.</span></span>

```vb
Using resource As New resourceType
    ' Insert code to work with resource.
End Using

' For the acquisition and disposal of resource, the following  
' Try construction is equivalent to the Using block.
Dim resource As New resourceType
Try
    ' Insert code to work with resource.
Finally
    If resource IsNot Nothing Then
        resource.Dispose()
    End If
End Try
```

> [!NOTE]
> <span data-ttu-id="33925-163">Kód uvnitř bloku `Using` by neměl přiřazovat objekt v `resourcename` jiné proměnné.</span><span class="sxs-lookup"><span data-stu-id="33925-163">The code inside the `Using` block should not assign the object in `resourcename` to another variable.</span></span> <span data-ttu-id="33925-164">Když ukončíte blok `Using`, prostředek je uvolněn a druhá proměnná nemá přístup k prostředku, ke kterému odkazuje.</span><span class="sxs-lookup"><span data-stu-id="33925-164">When you exit the `Using` block, the resource is disposed, and the other variable cannot access the resource to which it points.</span></span>

## <a name="example"></a><span data-ttu-id="33925-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="33925-165">Example</span></span>

 <span data-ttu-id="33925-166">Následující příklad vytvoří soubor s názvem log. txt a zapíše dva řádky textu do souboru.</span><span class="sxs-lookup"><span data-stu-id="33925-166">The following example creates a file that is named log.txt and writes two lines of text to the file.</span></span> <span data-ttu-id="33925-167">Příklad také přečte stejný soubor a zobrazí řádky textu:</span><span class="sxs-lookup"><span data-stu-id="33925-167">The example also reads that same file and displays the lines of text:</span></span>

 <span data-ttu-id="33925-168">Vzhledem k tomu, že třídy <xref:System.IO.TextWriter> a <xref:System.IO.TextReader> implementují rozhraní <xref:System.IDisposable>, může kód použít příkazy `Using`, aby bylo zajištěno, že je soubor správně uzavřen po operacích zápisu a čtení.</span><span class="sxs-lookup"><span data-stu-id="33925-168">Because the <xref:System.IO.TextWriter> and <xref:System.IO.TextReader> classes implement the <xref:System.IDisposable> interface, the code can use `Using` statements to ensure that the file is correctly closed after the write and read operations.</span></span>

 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]

## <a name="see-also"></a><span data-ttu-id="33925-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="33925-169">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="33925-170">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="33925-170">Try...Catch...Finally Statement</span></span>](try-catch-finally-statement.md)
- [<span data-ttu-id="33925-171">Postupy: Odstranění systémového prostředku</span><span class="sxs-lookup"><span data-stu-id="33925-171">How to: Dispose of a System Resource</span></span>](../../programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
