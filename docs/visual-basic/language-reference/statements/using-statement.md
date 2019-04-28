---
title: Using – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
ms.openlocfilehash: fe53ea58dc98a4de793fe9dad1c3ceeac71622fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698652"
---
# <a name="using-statement-visual-basic"></a><span data-ttu-id="c19a4-102">Using – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c19a4-102">Using Statement (Visual Basic)</span></span>
<span data-ttu-id="c19a4-103">Deklaruje začátku `Using` blokovat a volitelně získá systémové prostředky, které řídí bloku.</span><span class="sxs-lookup"><span data-stu-id="c19a4-103">Declares the beginning of a `Using` block and optionally acquires the system resources that the block controls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c19a4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c19a4-104">Syntax</span></span>  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a><span data-ttu-id="c19a4-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="c19a4-105">Parts</span></span>  
  
|<span data-ttu-id="c19a4-106">Termín</span><span class="sxs-lookup"><span data-stu-id="c19a4-106">Term</span></span>|<span data-ttu-id="c19a4-107">Definice</span><span class="sxs-lookup"><span data-stu-id="c19a4-107">Definition</span></span>|  
|---|---|  
|`resourcelist`|<span data-ttu-id="c19a4-108">Povinné, pokud nezadáte `resourceexpression`.</span><span class="sxs-lookup"><span data-stu-id="c19a4-108">Required if you do not supply `resourceexpression`.</span></span> <span data-ttu-id="c19a4-109">Seznam jedné nebo více systémových prostředků, který tato `Using` blokovat ovládací prvky, oddělené čárkami.</span><span class="sxs-lookup"><span data-stu-id="c19a4-109">List of one or more system resources that this `Using` block controls, separated by commas.</span></span>|  
|`resourceexpression`|<span data-ttu-id="c19a4-110">Povinné, pokud nezadáte `resourcelist`.</span><span class="sxs-lookup"><span data-stu-id="c19a4-110">Required if you do not supply `resourcelist`.</span></span> <span data-ttu-id="c19a4-111">Odkaz na proměnnou nebo výraz odkazuje na systémový prostředek pro řízení situace `Using` bloku.</span><span class="sxs-lookup"><span data-stu-id="c19a4-111">Reference variable or expression referring to a system resource to be controlled by this `Using` block.</span></span>|  
|`statements`|<span data-ttu-id="c19a4-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="c19a4-112">Optional.</span></span> <span data-ttu-id="c19a4-113">Blok příkazů, který `Using` blok.</span><span class="sxs-lookup"><span data-stu-id="c19a4-113">Block of statements that the `Using` block runs.</span></span>|  
|`End Using`|<span data-ttu-id="c19a4-114">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="c19a4-114">Required.</span></span> <span data-ttu-id="c19a4-115">Ukončí definici `Using` bloku a spravované všechny prostředky, které ji řídí.</span><span class="sxs-lookup"><span data-stu-id="c19a4-115">Terminates the definition of the `Using` block and disposes of all the resources that it controls.</span></span>|  
  
 <span data-ttu-id="c19a4-116">Každý prostředek v `resourcelist` část má následující syntaxi a části:</span><span class="sxs-lookup"><span data-stu-id="c19a4-116">Each resource in the `resourcelist` part has the following syntax and parts:</span></span>  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 <span data-ttu-id="c19a4-117">-nebo-</span><span class="sxs-lookup"><span data-stu-id="c19a4-117">-or-</span></span>  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a><span data-ttu-id="c19a4-118">resourcelist částí</span><span class="sxs-lookup"><span data-stu-id="c19a4-118">resourcelist Parts</span></span>  
  
|<span data-ttu-id="c19a4-119">Termín</span><span class="sxs-lookup"><span data-stu-id="c19a4-119">Term</span></span>|<span data-ttu-id="c19a4-120">Definice</span><span class="sxs-lookup"><span data-stu-id="c19a4-120">Definition</span></span>|  
|---|---|  
|`resourcename`|<span data-ttu-id="c19a4-121">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="c19a4-121">Required.</span></span> <span data-ttu-id="c19a4-122">Odkaz na proměnnou, která odkazuje na systémový prostředek, který `Using` blokovat ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="c19a4-122">Reference variable that refers to a system resource that the `Using` block controls.</span></span>|  
|`New`|<span data-ttu-id="c19a4-123">Požadováno pokud `Using` příkaz získá prostředek.</span><span class="sxs-lookup"><span data-stu-id="c19a4-123">Required if the `Using` statement acquires the resource.</span></span> <span data-ttu-id="c19a4-124">Pokud jste už zakoupili prostředku, použijte druhý alternativní syntaxi.</span><span class="sxs-lookup"><span data-stu-id="c19a4-124">If you have already acquired the resource, use the second syntax alternative.</span></span>|  
|`resourcetype`|<span data-ttu-id="c19a4-125">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="c19a4-125">Required.</span></span> <span data-ttu-id="c19a4-126">Třída prostředku.</span><span class="sxs-lookup"><span data-stu-id="c19a4-126">The class of the resource.</span></span> <span data-ttu-id="c19a4-127">Třída musí implementovat <xref:System.IDisposable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c19a4-127">The class must implement the <xref:System.IDisposable> interface.</span></span>|  
|`arglist`|<span data-ttu-id="c19a4-128">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="c19a4-128">Optional.</span></span> <span data-ttu-id="c19a4-129">Seznam argumentů, které předáváte konstruktor pro vytvoření instance `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="c19a4-129">List of arguments you are passing to the constructor to create an instance of `resourcetype`.</span></span> <span data-ttu-id="c19a4-130">Zobrazit [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="c19a4-130">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`resourceexpression`|<span data-ttu-id="c19a4-131">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="c19a4-131">Required.</span></span> <span data-ttu-id="c19a4-132">Proměnné nebo výraz odkazuje na systémový prostředek splňující požadavky `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="c19a4-132">Variable or expression referring to a system resource satisfying the requirements of `resourcetype`.</span></span> <span data-ttu-id="c19a4-133">Pokud použijete druhý alternativní syntaxi, musíte získat zdroje před předáním řízení `Using` příkazu.</span><span class="sxs-lookup"><span data-stu-id="c19a4-133">If you use the second syntax alternative, you must acquire the resource before passing control to the `Using` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c19a4-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c19a4-134">Remarks</span></span>  
 <span data-ttu-id="c19a4-135">Váš kód vyžaduje někdy nespravovaný prostředek, jako je například popisovač souboru, obálky COM nebo připojení SQL.</span><span class="sxs-lookup"><span data-stu-id="c19a4-135">Sometimes your code requires an unmanaged resource, such as a file handle, a COM wrapper, or a SQL connection.</span></span> <span data-ttu-id="c19a4-136">A `Using` bloku zaručuje k dispozici jeden nebo více těchto prostředků po dokončení se váš kód s nimi.</span><span class="sxs-lookup"><span data-stu-id="c19a4-136">A `Using` block guarantees the disposal of one or more such resources when your code is finished with them.</span></span> <span data-ttu-id="c19a4-137">Adaptéry tak budou k dispozici pro další kód používat.</span><span class="sxs-lookup"><span data-stu-id="c19a4-137">This makes them available for other code to use.</span></span>  
  
 <span data-ttu-id="c19a4-138">Spravované prostředky jsou odstraněny ze systému uvolňování paměti rozhraní .NET Framework (GC) bez dalších kódování z vaší strany.</span><span class="sxs-lookup"><span data-stu-id="c19a4-138">Managed resources are disposed of by the .NET Framework garbage collector (GC) without any extra coding on your part.</span></span> <span data-ttu-id="c19a4-139">Není nutné `Using` blok pro spravované prostředky.</span><span class="sxs-lookup"><span data-stu-id="c19a4-139">You do not need a `Using` block for managed resources.</span></span> <span data-ttu-id="c19a4-140">Ale můžete pořád použít `Using` bloku k vynucení uvolnění spravovaného prostředku, místo abyste čekali, systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="c19a4-140">However, you can still use a `Using` block to force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="c19a4-141">A `Using` blok má tři části: získání, využití a vyřazení.</span><span class="sxs-lookup"><span data-stu-id="c19a4-141">A `Using` block has three parts: acquisition, usage, and disposal.</span></span>  
  
- <span data-ttu-id="c19a4-142">*Získání* znamená, že vytváření proměnných a inicializuje ji k odkazování na systémový prostředek.</span><span class="sxs-lookup"><span data-stu-id="c19a4-142">*Acquisition* means creating a variable and initializing it to refer to the system resource.</span></span> <span data-ttu-id="c19a4-143">`Using` Příkazu můžete získat jednu nebo více prostředků, nebo můžete získat přesně jeden prostředek před vstupem bloku a bude `Using` příkazu.</span><span class="sxs-lookup"><span data-stu-id="c19a4-143">The `Using` statement can acquire one or more resources, or you can acquire exactly one resource before entering the block and supply it to the `Using` statement.</span></span> <span data-ttu-id="c19a4-144">Pokud zadáte `resourceexpression`, musíte získat zdroje před předáním řízení `Using` příkazu.</span><span class="sxs-lookup"><span data-stu-id="c19a4-144">If you supply `resourceexpression`, you must acquire the resource before passing control to the `Using` statement.</span></span>  
  
- <span data-ttu-id="c19a4-145">*Využití* znamená, že přístup k prostředkům a provádění akcí s nimi.</span><span class="sxs-lookup"><span data-stu-id="c19a4-145">*Usage* means accessing the resources and performing actions with them.</span></span> <span data-ttu-id="c19a4-146">Příkazy mezi `Using` a `End Using` představují využití prostředků.</span><span class="sxs-lookup"><span data-stu-id="c19a4-146">The statements between `Using` and `End Using` represent the usage of the resources.</span></span>  
  
- <span data-ttu-id="c19a4-147">*Vyřazení* znamená, že volání <xref:System.IDisposable.Dispose%2A> metodu na objekt v `resourcename`.</span><span class="sxs-lookup"><span data-stu-id="c19a4-147">*Disposal* means calling the <xref:System.IDisposable.Dispose%2A> method on the object in `resourcename`.</span></span> <span data-ttu-id="c19a4-148">To umožňuje objektu čistě ukončit jeho prostředky.</span><span class="sxs-lookup"><span data-stu-id="c19a4-148">This allows the object to cleanly terminate its resources.</span></span> <span data-ttu-id="c19a4-149">`End Using` Příkaz uvolní prostředky v rámci `Using` bloku ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c19a4-149">The `End Using` statement disposes of the resources under the `Using` block's control.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="c19a4-150">Chování</span><span class="sxs-lookup"><span data-stu-id="c19a4-150">Behavior</span></span>  
 <span data-ttu-id="c19a4-151">A `Using` bloku se chová stejně jako `Try`... `Finally` konstrukce, ve kterém `Try` blok používá prostředky a `Finally` uvolní blok z nich.</span><span class="sxs-lookup"><span data-stu-id="c19a4-151">A `Using` block behaves like a `Try`...`Finally` construction in which the `Try` block uses the resources and the `Finally` block disposes of them.</span></span> <span data-ttu-id="c19a4-152">Z toho důvodu `Using` bloku zaručuje zacházení s prostředky, bez ohledu na to, jak ukončení bloku.</span><span class="sxs-lookup"><span data-stu-id="c19a4-152">Because of this, the `Using` block guarantees disposal of the resources, no matter how you exit the block.</span></span> <span data-ttu-id="c19a4-153">To platí i v případě neošetřené výjimky, s výjimkou <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="c19a4-153">This is true even in the case of an unhandled exception, except for a <xref:System.StackOverflowException>.</span></span>  
  
 <span data-ttu-id="c19a4-154">Obor proměnné každý prostředek získala `Using` příkaz je omezená na `Using` bloku.</span><span class="sxs-lookup"><span data-stu-id="c19a4-154">The scope of every resource variable acquired by the `Using` statement is limited to the `Using` block.</span></span>  
  
 <span data-ttu-id="c19a4-155">Pokud zadáte více než jeden systémový prostředek v `Using` příkaz efekt je stejný, jako kdyby jste vnořené `Using` blokuje jednoho do jiného.</span><span class="sxs-lookup"><span data-stu-id="c19a4-155">If you specify more than one system resource in the `Using` statement, the effect is the same as if you nested `Using` blocks one within another.</span></span>  
  
 <span data-ttu-id="c19a4-156">Pokud `resourcename` je `Nothing`, bez volání <xref:System.IDisposable.Dispose%2A> se provádí, a není vyvolána žádná výjimka.</span><span class="sxs-lookup"><span data-stu-id="c19a4-156">If `resourcename` is `Nothing`, no call to <xref:System.IDisposable.Dispose%2A> is made, and no exception is thrown.</span></span>  
  
## <a name="structured-exception-handling-within-a-using-block"></a><span data-ttu-id="c19a4-157">Strukturované zpracování výjimek v rámci bloku pomocí</span><span class="sxs-lookup"><span data-stu-id="c19a4-157">Structured Exception Handling Within a Using Block</span></span>  
 <span data-ttu-id="c19a4-158">Pokud potřebujete ke zpracování výjimky, ke kterému může dojít v rámci `Using` blok, můžete přidat kompletní `Try`... `Finally` konstrukce k němu.</span><span class="sxs-lookup"><span data-stu-id="c19a4-158">If you need to handle an exception that might occur within the `Using` block, you can add a complete `Try`...`Finally` construction to it.</span></span> <span data-ttu-id="c19a4-159">Pokud budete potřebovat pro zpracování případu, kdy `Using` příkaz se nepovedlo úspěšně dokončit při získávání prostředku, můžete otestovat a zjistěte, jestli `resourcename` je `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="c19a4-159">If you need to handle the case where the `Using` statement is not successful in acquiring a resource, you can test to see if `resourcename` is `Nothing`.</span></span>  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a><span data-ttu-id="c19a4-160">Namísto použití bloku zpracování strukturovaných výjimek</span><span class="sxs-lookup"><span data-stu-id="c19a4-160">Structured Exception Handling Instead of a Using Block</span></span>  
 <span data-ttu-id="c19a4-161">Pokud potřebujete lepší kontrolu nad pořízení prostředků, nebo potřebujete další kód v `Finally` blok, je možné přepsat `Using` blokovat, jako `Try`... `Finally` konstrukce.</span><span class="sxs-lookup"><span data-stu-id="c19a4-161">If you need finer control over the acquisition of the resources, or you need additional code in the `Finally` block, you can rewrite the `Using` block as a `Try`...`Finally` construction.</span></span> <span data-ttu-id="c19a4-162">Následující příklad ukazuje osnovu `Try` a `Using` konstrukce, které jsou ekvivalentní v získávání a odstraňování `resource`.</span><span class="sxs-lookup"><span data-stu-id="c19a4-162">The following example shows skeleton `Try` and `Using` constructions that are equivalent in the acquisition and disposal of `resource`.</span></span>  
  
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
>  <span data-ttu-id="c19a4-163">Kód uvnitř `Using` bloku by neměl přiřazení objektu v `resourcename` do jiné proměnné.</span><span class="sxs-lookup"><span data-stu-id="c19a4-163">The code inside the `Using` block should not assign the object in `resourcename` to another variable.</span></span> <span data-ttu-id="c19a4-164">Po ukončení `Using` bloku, prostředek je uvolněn a jiné proměnné nemůže přistupovat k prostředku, na kterou odkazuje.</span><span class="sxs-lookup"><span data-stu-id="c19a4-164">When you exit the `Using` block, the resource is disposed, and the other variable cannot access the resource to which it points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c19a4-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="c19a4-165">Example</span></span>  
 <span data-ttu-id="c19a4-166">Následující příklad vytvoří soubor, který má název log.txt a zapíše dva řádky textu do souboru.</span><span class="sxs-lookup"><span data-stu-id="c19a4-166">The following example creates a file that is named log.txt and writes two lines of text to the file.</span></span> <span data-ttu-id="c19a4-167">V příkladu také přečte Tento stejný soubor a zobrazí řádky textu.</span><span class="sxs-lookup"><span data-stu-id="c19a4-167">The example also reads that same file and displays the lines of text.</span></span>  
  
 <span data-ttu-id="c19a4-168">Protože <xref:System.IO.TextWriter> a <xref:System.IO.TextReader> implementace třídy <xref:System.IDisposable> rozhraní, můžete použít kód `Using` příkazy k zajištění, že soubor je správně uzavřen po zápisu a operace čtení.</span><span class="sxs-lookup"><span data-stu-id="c19a4-168">Because the <xref:System.IO.TextWriter> and <xref:System.IO.TextReader> classes implement the <xref:System.IDisposable> interface, the code can use `Using` statements to ensure that the file is correctly closed after the write and read operations.</span></span>  
  
 [!code-vb[VbVbalrStatements#50](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#50)]  
  
## <a name="see-also"></a><span data-ttu-id="c19a4-169">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c19a4-169">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="c19a4-170">Příkaz Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="c19a4-170">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="c19a4-171">Postupy: Odstranění systémového prostředku</span><span class="sxs-lookup"><span data-stu-id="c19a4-171">How to: Dispose of a System Resource</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
