---
title: Finalizační metody – Průvodce programováním v C#
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: a266cfd5996aca7b7a6b297b0775526cf38b8f64
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241419"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="ee375-102">Finalizační metody (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="ee375-102">Finalizers (C# Programming Guide)</span></span>
<span data-ttu-id="ee375-103">Finalizační metody (označované také jako **destruktory**) se používají k provedení všech nezbytných finálních vyčištění při shromažďování instance třídy systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ee375-103">Finalizers (which are also called **destructors**) are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee375-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ee375-104">Remarks</span></span>  
  
- <span data-ttu-id="ee375-105">Finalizační metody nelze definovat ve strukturách.</span><span class="sxs-lookup"><span data-stu-id="ee375-105">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="ee375-106">Používají se pouze s třídami.</span><span class="sxs-lookup"><span data-stu-id="ee375-106">They are only used with classes.</span></span>  
  
- <span data-ttu-id="ee375-107">Třída může mít pouze jeden finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="ee375-107">A class can only have one finalizer.</span></span>  
  
- <span data-ttu-id="ee375-108">Finalizační metody nemůžou být zděděné nebo přetížené.</span><span class="sxs-lookup"><span data-stu-id="ee375-108">Finalizers cannot be inherited or overloaded.</span></span>  
  
- <span data-ttu-id="ee375-109">Finalizační metody nelze volat.</span><span class="sxs-lookup"><span data-stu-id="ee375-109">Finalizers cannot be called.</span></span> <span data-ttu-id="ee375-110">Jsou vyvolány automaticky.</span><span class="sxs-lookup"><span data-stu-id="ee375-110">They are invoked automatically.</span></span>  
  
- <span data-ttu-id="ee375-111">Finalizační metoda nepřijímá modifikátory nebo má parametry.</span><span class="sxs-lookup"><span data-stu-id="ee375-111">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="ee375-112">Například následující je deklarace finalizační metody pro `Car` třídu.</span><span class="sxs-lookup"><span data-stu-id="ee375-112">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

<span data-ttu-id="ee375-113">Finalizační metodu lze také implementovat jako definici těla výrazu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="ee375-113">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="ee375-114">Finalizační metoda implicitně volá <xref:System.Object.Finalize%2A> základní třídu objektu.</span><span class="sxs-lookup"><span data-stu-id="ee375-114">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="ee375-115">Proto volání finalizační metody je implicitně přeloženo na následující kód:</span><span class="sxs-lookup"><span data-stu-id="ee375-115">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
```csharp  
protected override void Finalize()  
{  
    try  
    {  
        // Cleanup statements...  
    }  
    finally  
    {  
        base.Finalize();  
    }  
}  
```  
  
 <span data-ttu-id="ee375-116">To znamená, že `Finalize` Metoda je volána rekurzivně pro všechny instance v řetězu dědičnosti, od nejvíce odvozené k nejméně odvozenému.</span><span class="sxs-lookup"><span data-stu-id="ee375-116">This means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee375-117">Nemusíte používat prázdné finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="ee375-117">Empty finalizers should not be used.</span></span> <span data-ttu-id="ee375-118">Pokud třída obsahuje finalizační metodu, je ve `Finalize` frontě vytvořena položka.</span><span class="sxs-lookup"><span data-stu-id="ee375-118">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="ee375-119">Po volání finalizační metody je vyvolán systém uvolňování paměti pro zpracování fronty.</span><span class="sxs-lookup"><span data-stu-id="ee375-119">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="ee375-120">Prázdný finalizační metoda vyvolá jenom nepotřebnou ztrátu výkonu.</span><span class="sxs-lookup"><span data-stu-id="ee375-120">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="ee375-121">Programátor nemá žádné řízení při volání finalizační metody, protože je určen systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="ee375-121">The programmer has no control over when the finalizer is called because this is determined by the garbage collector.</span></span> <span data-ttu-id="ee375-122">Systém uvolňování paměti kontroluje objekty, které již aplikace nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="ee375-122">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="ee375-123">Pokud se považuje za objekt s nárokem na finalizaci, zavolá finalizační metodu (pokud existuje) a uvolní paměť použitou k uložení objektu.</span><span class="sxs-lookup"><span data-stu-id="ee375-123">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span>

 <span data-ttu-id="ee375-124">V .NET Frameworkch aplikacích (ale ne v aplikacích .NET Core), jsou také volány finalizační metody při ukončení programu.</span><span class="sxs-lookup"><span data-stu-id="ee375-124">In .NET Framework applications (but not in .NET Core applications), finalizers are also called when the program exits.</span></span>
  
 <span data-ttu-id="ee375-125">Je možné vynutit uvolňování paměti voláním <xref:System.GC.Collect%2A> , ale většinou by se to mělo vyhnout, protože může způsobit problémy s výkonem.</span><span class="sxs-lookup"><span data-stu-id="ee375-125">It is possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="ee375-126">Použití finalizační metody k uvolnění prostředků</span><span class="sxs-lookup"><span data-stu-id="ee375-126">Using finalizers to release resources</span></span>  
 <span data-ttu-id="ee375-127">Obecně platí, že jazyk C# při vývoji s jazykem, který necílí na modul runtime s uvolňováním paměti, nevyžaduje tolik správy paměti, kolik je potřeba.</span><span class="sxs-lookup"><span data-stu-id="ee375-127">In general, C# does not require as much memory management as is needed when you develop with a language that does not target a runtime with garbage collection.</span></span> <span data-ttu-id="ee375-128">Důvodem je to, že systém uvolňování paměti .NET implicitně spravuje přidělování a uvolňování paměti pro vaše objekty.</span><span class="sxs-lookup"><span data-stu-id="ee375-128">This is because the .NET garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="ee375-129">Pokud však vaše aplikace zapouzdřuje nespravované prostředky, jako jsou například Windows, soubory a síťová připojení, měli byste k uvolnění těchto prostředků použít finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="ee375-129">However, when your application encapsulates unmanaged resources, such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="ee375-130">Pokud je objekt způsobilý pro finalizaci, systém uvolňování paměti spustí `Finalize` metodu objektu.</span><span class="sxs-lookup"><span data-stu-id="ee375-130">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="ee375-131">Explicitní vydání prostředků</span><span class="sxs-lookup"><span data-stu-id="ee375-131">Explicit release of resources</span></span>  
 <span data-ttu-id="ee375-132">Pokud vaše aplikace používá nákladný externí prostředek, doporučujeme vám, abyste poskytli způsob, jak prostředek explicitně uvolnit před tím, než systém uvolňování paměti uvolní objekt.</span><span class="sxs-lookup"><span data-stu-id="ee375-132">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="ee375-133">Provedete to tak `Dispose` , že implementujete metodu z <xref:System.IDisposable> rozhraní, které provádí nezbytné vyčištění objektu.</span><span class="sxs-lookup"><span data-stu-id="ee375-133">You do this by implementing a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="ee375-134">To může výrazně zlepšit výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="ee375-134">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="ee375-135">I s tímto explicitním ovládáním prostředků se finalizační metoda stala ochranou pro vyčištění prostředků v případě, že volání `Dispose` metody se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="ee375-135">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method failed.</span></span>  
  
 <span data-ttu-id="ee375-136">Další podrobnosti o čištění prostředků najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="ee375-136">For more details about cleaning up resources, see the following topics:</span></span>  
  
- [<span data-ttu-id="ee375-137">Vymazání nespravovaných prostředků</span><span class="sxs-lookup"><span data-stu-id="ee375-137">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
- [<span data-ttu-id="ee375-138">Implementace metody Dispose</span><span class="sxs-lookup"><span data-stu-id="ee375-138">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [<span data-ttu-id="ee375-139">using – příkaz</span><span class="sxs-lookup"><span data-stu-id="ee375-139">using Statement</span></span>](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="ee375-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="ee375-140">Example</span></span>  
 <span data-ttu-id="ee375-141">Následující příklad vytvoří tři třídy, které tvoří řetěz dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="ee375-141">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="ee375-142">Třída `First` je základní třídou, `Second` je odvozena z `First` a `Third` je odvozena z `Second` .</span><span class="sxs-lookup"><span data-stu-id="ee375-142">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="ee375-143">Všechny tři mají finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="ee375-143">All three have finalizers.</span></span> <span data-ttu-id="ee375-144">V je `Main` vytvořena instance nejvíce odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="ee375-144">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="ee375-145">Když se program spustí, Všimněte si, že finalizační metody pro tři třídy jsou volány automaticky a v pořadí od nejvíce odvozené k nejmenšímu odvozenému.</span><span class="sxs-lookup"><span data-stu-id="ee375-145">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="ee375-146">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ee375-146">C# language specification</span></span>  

<span data-ttu-id="ee375-147">Další informace naleznete v části [destruktory](~/_csharplang/spec/classes.md#destructors) [specifikace jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="ee375-147">For more information, see the [Destructors](~/_csharplang/spec/classes.md#destructors) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ee375-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee375-148">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="ee375-149">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ee375-149">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ee375-150">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="ee375-150">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="ee375-151">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="ee375-151">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
