---
title: Using – příkaz (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.using
helpviewer_keywords:
- resource disposal
- Try...Catch...Finally statements, equivalent to Using statement
- resources [Visual Basic], disposing
- Using statement [Visual Basic]
ms.assetid: 665d1580-dd54-4e96-a9a9-6be2a68948f1
caps.latest.revision: 36
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ed9cc0d04c89eac1fe342a0924dd89bb1e258a11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-statement-visual-basic"></a><span data-ttu-id="2cb48-102">Using – příkaz (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2cb48-102">Using Statement (Visual Basic)</span></span>
<span data-ttu-id="2cb48-103">Deklaruje začátku `Using` blokovat a volitelně získá systémové prostředky, které se řídí bloku.</span><span class="sxs-lookup"><span data-stu-id="2cb48-103">Declares the beginning of a `Using` block and optionally acquires the system resources that the block controls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cb48-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2cb48-104">Syntax</span></span>  
  
```  
Using { resourcelist | resourceexpression }  
    [ statements ]  
End Using  
```  
  
## <a name="parts"></a><span data-ttu-id="2cb48-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="2cb48-105">Parts</span></span>  
  
|<span data-ttu-id="2cb48-106">Termín</span><span class="sxs-lookup"><span data-stu-id="2cb48-106">Term</span></span>|<span data-ttu-id="2cb48-107">Definice</span><span class="sxs-lookup"><span data-stu-id="2cb48-107">Definition</span></span>|  
|---|---|  
|`resourcelist`|<span data-ttu-id="2cb48-108">Vyžaduje, pokud nezadáte `resourceexpression`.</span><span class="sxs-lookup"><span data-stu-id="2cb48-108">Required if you do not supply `resourceexpression`.</span></span> <span data-ttu-id="2cb48-109">Seznam jedné nebo více systémových prostředků, které tento `Using` blokovat ovládací prvky, oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="2cb48-109">List of one or more system resources that this `Using` block controls, separated by commas.</span></span>|  
|`resourceexpression`|<span data-ttu-id="2cb48-110">Vyžaduje, pokud nezadáte `resourcelist`.</span><span class="sxs-lookup"><span data-stu-id="2cb48-110">Required if you do not supply `resourcelist`.</span></span> <span data-ttu-id="2cb48-111">Odkaz na proměnnou nebo výraz odkazující na systémový prostředek kontrolován to `Using` bloku.</span><span class="sxs-lookup"><span data-stu-id="2cb48-111">Reference variable or expression referring to a system resource to be controlled by this `Using` block.</span></span>|  
|`statements`|<span data-ttu-id="2cb48-112">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2cb48-112">Optional.</span></span> <span data-ttu-id="2cb48-113">Blok příkazů, `Using` blokovat spuštění.</span><span class="sxs-lookup"><span data-stu-id="2cb48-113">Block of statements that the `Using` block runs.</span></span>|  
|`End Using`|<span data-ttu-id="2cb48-114">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="2cb48-114">Required.</span></span> <span data-ttu-id="2cb48-115">Ukončí definice `Using` bloku a spravované všechny prostředky, které se jimi řídí.</span><span class="sxs-lookup"><span data-stu-id="2cb48-115">Terminates the definition of the `Using` block and disposes of all the resources that it controls.</span></span>|  
  
 <span data-ttu-id="2cb48-116">Všechny prostředky v `resourcelist` část má následující syntaxe a částí:</span><span class="sxs-lookup"><span data-stu-id="2cb48-116">Each resource in the `resourcelist` part has the following syntax and parts:</span></span>  
  
 `resourcename As New resourcetype [ ( [ arglist ] ) ]`  
  
 <span data-ttu-id="2cb48-117">-nebo-</span><span class="sxs-lookup"><span data-stu-id="2cb48-117">-or-</span></span>  
  
 `resourcename As resourcetype = resourceexpression`  
  
## <a name="resourcelist-parts"></a><span data-ttu-id="2cb48-118">resourcelist částí</span><span class="sxs-lookup"><span data-stu-id="2cb48-118">resourcelist Parts</span></span>  
  
|<span data-ttu-id="2cb48-119">Termín</span><span class="sxs-lookup"><span data-stu-id="2cb48-119">Term</span></span>|<span data-ttu-id="2cb48-120">Definice</span><span class="sxs-lookup"><span data-stu-id="2cb48-120">Definition</span></span>|  
|---|---|  
|`resourcename`|<span data-ttu-id="2cb48-121">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="2cb48-121">Required.</span></span> <span data-ttu-id="2cb48-122">Odkaz na proměnnou, která odkazuje na systémový prostředek, `Using` blokovat ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="2cb48-122">Reference variable that refers to a system resource that the `Using` block controls.</span></span>|  
|`New`|<span data-ttu-id="2cb48-123">Požadováno pokud `Using` příkaz získá prostředek.</span><span class="sxs-lookup"><span data-stu-id="2cb48-123">Required if the `Using` statement acquires the resource.</span></span> <span data-ttu-id="2cb48-124">Pokud jste už získali prostředku, použijte druhý alternativní syntaxe.</span><span class="sxs-lookup"><span data-stu-id="2cb48-124">If you have already acquired the resource, use the second syntax alternative.</span></span>|  
|`resourcetype`|<span data-ttu-id="2cb48-125">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="2cb48-125">Required.</span></span> <span data-ttu-id="2cb48-126">Třída prostředku.</span><span class="sxs-lookup"><span data-stu-id="2cb48-126">The class of the resource.</span></span> <span data-ttu-id="2cb48-127">Musí implementovat třídu <xref:System.IDisposable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2cb48-127">The class must implement the <xref:System.IDisposable> interface.</span></span>|  
|`arglist`|<span data-ttu-id="2cb48-128">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2cb48-128">Optional.</span></span> <span data-ttu-id="2cb48-129">Seznam argumentů, které jste předali do konstruktor k vytvoření instance `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="2cb48-129">List of arguments you are passing to the constructor to create an instance of `resourcetype`.</span></span> <span data-ttu-id="2cb48-130">V tématu [seznam parametrů](../../../visual-basic/language-reference/statements/parameter-list.md).</span><span class="sxs-lookup"><span data-stu-id="2cb48-130">See [Parameter List](../../../visual-basic/language-reference/statements/parameter-list.md).</span></span>|  
|`resourceexpression`|<span data-ttu-id="2cb48-131">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="2cb48-131">Required.</span></span> <span data-ttu-id="2cb48-132">Proměnná nebo výraz, která odkazuje na systémový prostředek, které splňují požadavky na `resourcetype`.</span><span class="sxs-lookup"><span data-stu-id="2cb48-132">Variable or expression referring to a system resource satisfying the requirements of `resourcetype`.</span></span> <span data-ttu-id="2cb48-133">Pokud použijete druhý alternativní syntaxe, musíte získat prostředek před předáním řízení k `Using` příkaz.</span><span class="sxs-lookup"><span data-stu-id="2cb48-133">If you use the second syntax alternative, you must acquire the resource before passing control to the `Using` statement.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cb48-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2cb48-134">Remarks</span></span>  
 <span data-ttu-id="2cb48-135">Někdy kódu vyžaduje nespravovaný prostředek, například popisovač souboru, obálky COM nebo připojení SQL.</span><span class="sxs-lookup"><span data-stu-id="2cb48-135">Sometimes your code requires an unmanaged resource, such as a file handle, a COM wrapper, or a SQL connection.</span></span> <span data-ttu-id="2cb48-136">A `Using` bloku zaručuje k dispozici jeden nebo více těchto zdrojů až po dokončení kódu s nimi.</span><span class="sxs-lookup"><span data-stu-id="2cb48-136">A `Using` block guarantees the disposal of one or more such resources when your code is finished with them.</span></span> <span data-ttu-id="2cb48-137">Díky je k dispozici pro ostatní kódu pro použití.</span><span class="sxs-lookup"><span data-stu-id="2cb48-137">This makes them available for other code to use.</span></span>  
  
 <span data-ttu-id="2cb48-138">Spravované prostředky modulem garbage collector v rozhraní .NET Framework (GC) se odstraní bez další kódování z vaší strany.</span><span class="sxs-lookup"><span data-stu-id="2cb48-138">Managed resources are disposed of by the .NET Framework garbage collector (GC) without any extra coding on your part.</span></span> <span data-ttu-id="2cb48-139">Není nutné `Using` blok pro spravované prostředky.</span><span class="sxs-lookup"><span data-stu-id="2cb48-139">You do not need a `Using` block for managed resources.</span></span> <span data-ttu-id="2cb48-140">Ale když můžete nadále používat `Using` bloku přinutit k dispozici prostředek spravované místo abyste čekali, bude systém uvolňování.</span><span class="sxs-lookup"><span data-stu-id="2cb48-140">However, you can still use a `Using` block to force the disposal of a managed resource instead of waiting for the garbage collector.</span></span>  
  
 <span data-ttu-id="2cb48-141">A `Using` bloku má tři části: akvizice, použití a uvolnění.</span><span class="sxs-lookup"><span data-stu-id="2cb48-141">A `Using` block has three parts: acquisition, usage, and disposal.</span></span>  
  
-   <span data-ttu-id="2cb48-142">*Získávání* znamená vytvoření proměnné a inicializací odkazovat na systémový prostředek.</span><span class="sxs-lookup"><span data-stu-id="2cb48-142">*Acquisition* means creating a variable and initializing it to refer to the system resource.</span></span> <span data-ttu-id="2cb48-143">`Using` Příkaz můžete získat jeden nebo více prostředků, nebo můžete získat přesně jeden prostředek před vstupem bloku a zadejte jej do `Using` příkaz.</span><span class="sxs-lookup"><span data-stu-id="2cb48-143">The `Using` statement can acquire one or more resources, or you can acquire exactly one resource before entering the block and supply it to the `Using` statement.</span></span> <span data-ttu-id="2cb48-144">Pokud zadáte `resourceexpression`, musíte získat prostředek před předáním řízení k `Using` příkaz.</span><span class="sxs-lookup"><span data-stu-id="2cb48-144">If you supply `resourceexpression`, you must acquire the resource before passing control to the `Using` statement.</span></span>  
  
-   <span data-ttu-id="2cb48-145">*Využití* znamená přístupu k prostředkům a provádění akcí s nimi.</span><span class="sxs-lookup"><span data-stu-id="2cb48-145">*Usage* means accessing the resources and performing actions with them.</span></span> <span data-ttu-id="2cb48-146">Příkazy mezi `Using` a `End Using` představují využití prostředků.</span><span class="sxs-lookup"><span data-stu-id="2cb48-146">The statements between `Using` and `End Using` represent the usage of the resources.</span></span>  
  
-   <span data-ttu-id="2cb48-147">*Uvolnění* znamená volání <xref:System.IDisposable.Dispose%2A> metoda objektu ve `resourcename`.</span><span class="sxs-lookup"><span data-stu-id="2cb48-147">*Disposal* means calling the <xref:System.IDisposable.Dispose%2A> method on the object in `resourcename`.</span></span> <span data-ttu-id="2cb48-148">To umožňuje objekt řádně ukončit jeho prostředky.</span><span class="sxs-lookup"><span data-stu-id="2cb48-148">This allows the object to cleanly terminate its resources.</span></span> <span data-ttu-id="2cb48-149">`End Using` Příkaz uvolní prostředky v rámci `Using` řízení bloku.</span><span class="sxs-lookup"><span data-stu-id="2cb48-149">The `End Using` statement disposes of the resources under the `Using` block's control.</span></span>  
  
## <a name="behavior"></a><span data-ttu-id="2cb48-150">Chování</span><span class="sxs-lookup"><span data-stu-id="2cb48-150">Behavior</span></span>  
 <span data-ttu-id="2cb48-151">A `Using` bloku se chová stejně jako `Try`... `Finally` konstrukce, ve kterém `Try` bloku používá prostředky a `Finally` bloku uvolní z nich.</span><span class="sxs-lookup"><span data-stu-id="2cb48-151">A `Using` block behaves like a `Try`...`Finally` construction in which the `Try` block uses the resources and the `Finally` block disposes of them.</span></span> <span data-ttu-id="2cb48-152">Z toho důvodu `Using` bloku zaručuje uvolnění prostředků, bez ohledu na to, jak byl ukončen blok.</span><span class="sxs-lookup"><span data-stu-id="2cb48-152">Because of this, the `Using` block guarantees disposal of the resources, no matter how you exit the block.</span></span> <span data-ttu-id="2cb48-153">To platí i v případě neošetřené výjimky, s výjimkou <xref:System.StackOverflowException>.</span><span class="sxs-lookup"><span data-stu-id="2cb48-153">This is true even in the case of an unhandled exception, except for a <xref:System.StackOverflowException>.</span></span>  
  
 <span data-ttu-id="2cb48-154">Obor proměnné každých prostředků se získávají pomocí `Using` příkaz je omezený na `Using` bloku.</span><span class="sxs-lookup"><span data-stu-id="2cb48-154">The scope of every resource variable acquired by the `Using` statement is limited to the `Using` block.</span></span>  
  
 <span data-ttu-id="2cb48-155">Pokud zadáte více než jeden systémový prostředek v `Using` příkaz účinek je stejný jako v případě, že jste vnořené `Using` blokuje jednu v rámci jiného.</span><span class="sxs-lookup"><span data-stu-id="2cb48-155">If you specify more than one system resource in the `Using` statement, the effect is the same as if you nested `Using` blocks one within another.</span></span>  
  
 <span data-ttu-id="2cb48-156">Pokud `resourcename` je `Nothing`, bez volání <xref:System.IDisposable.Dispose%2A> přišla a nedojde k výjimce.</span><span class="sxs-lookup"><span data-stu-id="2cb48-156">If `resourcename` is `Nothing`, no call to <xref:System.IDisposable.Dispose%2A> is made, and no exception is thrown.</span></span>  
  
## <a name="structured-exception-handling-within-a-using-block"></a><span data-ttu-id="2cb48-157">Strukturované zpracování výjimek v rámci bloku pomocí</span><span class="sxs-lookup"><span data-stu-id="2cb48-157">Structured Exception Handling Within a Using Block</span></span>  
 <span data-ttu-id="2cb48-158">Pokud potřebujete ke zpracování výjimky, které může dojít v rámci `Using` blok, můžete přidat úplná `Try`... `Finally` konstrukce k němu.</span><span class="sxs-lookup"><span data-stu-id="2cb48-158">If you need to handle an exception that might occur within the `Using` block, you can add a complete `Try`...`Finally` construction to it.</span></span> <span data-ttu-id="2cb48-159">Pokud potřebujete zpracování případu, kdy `Using` příkaz není úspěšné při získávání prostředek, můžete otestovat a zjistěte, zda `resourcename` je `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="2cb48-159">If you need to handle the case where the `Using` statement is not successful in acquiring a resource, you can test to see if `resourcename` is `Nothing`.</span></span>  
  
## <a name="structured-exception-handling-instead-of-a-using-block"></a><span data-ttu-id="2cb48-160">Strukturované zpracování namísto použití bloku výjimek</span><span class="sxs-lookup"><span data-stu-id="2cb48-160">Structured Exception Handling Instead of a Using Block</span></span>  
 <span data-ttu-id="2cb48-161">Pokud potřebujete lepší kontrolu nad získávání prostředků, nebo budete potřebovat další kód v `Finally` bloku, je možné přepsat `Using` blokovat jako `Try`... `Finally` konstrukce.</span><span class="sxs-lookup"><span data-stu-id="2cb48-161">If you need finer control over the acquisition of the resources, or you need additional code in the `Finally` block, you can rewrite the `Using` block as a `Try`...`Finally` construction.</span></span> <span data-ttu-id="2cb48-162">Následující příklad ukazuje kostru `Try` a `Using` konstrukce, která odpovídají v získávání a odstraňování `resource`.</span><span class="sxs-lookup"><span data-stu-id="2cb48-162">The following example shows skeleton `Try` and `Using` constructions that are equivalent in the acquisition and disposal of `resource`.</span></span>  
  
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
>  <span data-ttu-id="2cb48-163">Kód uvnitř `Using` bloku nesmí přiřaďte objekt v `resourcename` jiné proměnné.</span><span class="sxs-lookup"><span data-stu-id="2cb48-163">The code inside the `Using` block should not assign the object in `resourcename` to another variable.</span></span> <span data-ttu-id="2cb48-164">Po ukončení `Using` bloku, prostředek je zveřejněn a další proměnná nemá přístup k prostředku, na kterou odkazuje.</span><span class="sxs-lookup"><span data-stu-id="2cb48-164">When you exit the `Using` block, the resource is disposed, and the other variable cannot access the resource to which it points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cb48-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="2cb48-165">Example</span></span>  
 <span data-ttu-id="2cb48-166">Následující příklad vytvoří soubor s názvem log.txt a zapíše dva řádky textu do souboru.</span><span class="sxs-lookup"><span data-stu-id="2cb48-166">The following example creates a file that is named log.txt and writes two lines of text to the file.</span></span> <span data-ttu-id="2cb48-167">Tento příklad také přečte Tento stejný soubor a zobrazí řádky textu.</span><span class="sxs-lookup"><span data-stu-id="2cb48-167">The example also reads that same file and displays the lines of text.</span></span>  
  
 <span data-ttu-id="2cb48-168">Protože <xref:System.IO.TextWriter> a <xref:System.IO.TextReader> implementace třídy <xref:System.IDisposable> rozhraní, můžete použít kód `Using` příkazy, čímž zkontrolujte, zda je soubor správně uzavřený po zápisu a operace čtení.</span><span class="sxs-lookup"><span data-stu-id="2cb48-168">Because the <xref:System.IO.TextWriter> and <xref:System.IO.TextReader> classes implement the <xref:System.IDisposable> interface, the code can use `Using` statements to ensure that the file is correctly closed after the write and read operations.</span></span>  
  
 [!code-vb[VbVbalrStatements#50](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/using-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="2cb48-169">Viz také</span><span class="sxs-lookup"><span data-stu-id="2cb48-169">See Also</span></span>  
 <xref:System.IDisposable>  
 [<span data-ttu-id="2cb48-170">Try... Catch... Finally – příkaz</span><span class="sxs-lookup"><span data-stu-id="2cb48-170">Try...Catch...Finally Statement</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="2cb48-171">Postupy: odstranění systémového prostředku</span><span class="sxs-lookup"><span data-stu-id="2cb48-171">How to: Dispose of a System Resource</span></span>](../../../visual-basic/programming-guide/language-features/control-flow/how-to-dispose-of-a-system-resource.md)
