---
title: Finalizační metody – programovací příručka Jazyka C#
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: c8ad738baa3ff76cf9ae8367f2fd2a1fb44a79d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170296"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="88f8a-102">Finalizační metody (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="88f8a-102">Finalizers (C# Programming Guide)</span></span>
<span data-ttu-id="88f8a-103">Finalizační metody (které se také nazývají **destruktory)** se používají k provedení všech nezbytných konečných vyčištění při shromažďování instance třídy systémem uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="88f8a-103">Finalizers (which are also called **destructors**) are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88f8a-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="88f8a-104">Remarks</span></span>  
  
- <span data-ttu-id="88f8a-105">Finalizační metody nelze definovat ve strukturách.</span><span class="sxs-lookup"><span data-stu-id="88f8a-105">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="88f8a-106">Používají se pouze s třídami.</span><span class="sxs-lookup"><span data-stu-id="88f8a-106">They are only used with classes.</span></span>  
  
- <span data-ttu-id="88f8a-107">Třída může mít pouze jednu finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="88f8a-107">A class can only have one finalizer.</span></span>  
  
- <span data-ttu-id="88f8a-108">Finalizační metody nelze zdědit nebo přetížené.</span><span class="sxs-lookup"><span data-stu-id="88f8a-108">Finalizers cannot be inherited or overloaded.</span></span>  
  
- <span data-ttu-id="88f8a-109">Finalizační metody nelze volat.</span><span class="sxs-lookup"><span data-stu-id="88f8a-109">Finalizers cannot be called.</span></span> <span data-ttu-id="88f8a-110">Jsou vyvolány automaticky.</span><span class="sxs-lookup"><span data-stu-id="88f8a-110">They are invoked automatically.</span></span>  
  
- <span data-ttu-id="88f8a-111">Finalizační metoda nepřijímá modifikátory nebo má parametry.</span><span class="sxs-lookup"><span data-stu-id="88f8a-111">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="88f8a-112">Například následující je deklarace finalizační metody `Car` pro třídu.</span><span class="sxs-lookup"><span data-stu-id="88f8a-112">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

<span data-ttu-id="88f8a-113">Finalizační metodu lze také implementovat jako definici těla výrazu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="88f8a-113">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="88f8a-114">Finalizační metoda implicitně volá <xref:System.Object.Finalize%2A> základní třídu objektu.</span><span class="sxs-lookup"><span data-stu-id="88f8a-114">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="88f8a-115">Proto volání finalizační metody je implicitně přeloženo do následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="88f8a-115">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
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
  
 <span data-ttu-id="88f8a-116">To znamená, `Finalize` že metoda se nazývá rekurzivně pro všechny instance v řetězci dědičnosti, od nejvíce odvozených po nejméně odvozené.</span><span class="sxs-lookup"><span data-stu-id="88f8a-116">This means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="88f8a-117">Prázdné finalizační metody by neměly být používány.</span><span class="sxs-lookup"><span data-stu-id="88f8a-117">Empty finalizers should not be used.</span></span> <span data-ttu-id="88f8a-118">Pokud třída obsahuje finalizační metodu, je `Finalize` ve frontě vytvořena položka.</span><span class="sxs-lookup"><span data-stu-id="88f8a-118">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="88f8a-119">Při volání finalizační metody je vyvolána systém uvolňování paměti ke zpracování fronty.</span><span class="sxs-lookup"><span data-stu-id="88f8a-119">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="88f8a-120">Prázdná finalizační metoda způsobí zbytečnou ztrátu výkonu.</span><span class="sxs-lookup"><span data-stu-id="88f8a-120">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="88f8a-121">Programátor nemá žádnou kontrolu nad při finalizační metody je volána, protože to je určeno uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="88f8a-121">The programmer has no control over when the finalizer is called because this is determined by the garbage collector.</span></span> <span data-ttu-id="88f8a-122">Systém uvolňování paměti kontroluje objekty, které již nejsou používány aplikací.</span><span class="sxs-lookup"><span data-stu-id="88f8a-122">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="88f8a-123">Pokud považuje objekt způsobilý pro dokončení, volá finalizační metodu (pokud existuje) a uvolní paměť použitou k uložení objektu.</span><span class="sxs-lookup"><span data-stu-id="88f8a-123">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span>

 <span data-ttu-id="88f8a-124">V aplikacích rozhraní .NET Framework (ale ne v aplikacích .NET Core) jsou při ukončení programu také volány finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="88f8a-124">In .NET Framework applications (but not in .NET Core applications), finalizers are also called when the program exits.</span></span>
  
 <span data-ttu-id="88f8a-125">Je možné vynutit uvolňování <xref:System.GC.Collect%2A>paměti voláním , ale většinu času, je třeba se tomu vyhnout, protože může způsobit problémy s výkonem.</span><span class="sxs-lookup"><span data-stu-id="88f8a-125">It is possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="88f8a-126">Použití finalizačních metod k uvolnění prostředků</span><span class="sxs-lookup"><span data-stu-id="88f8a-126">Using finalizers to release resources</span></span>  
 <span data-ttu-id="88f8a-127">Obecně c# nevyžaduje tolik správy paměti, jak je potřeba při vývoji s jazykem, který necílí na runtime s uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="88f8a-127">In general, C# does not require as much memory management as is needed when you develop with a language that does not target a runtime with garbage collection.</span></span> <span data-ttu-id="88f8a-128">Důvodem je, že systém uvolňování paměti rozhraní .NET Framework implicitně spravuje přidělení a uvolnění paměti pro vaše objekty.</span><span class="sxs-lookup"><span data-stu-id="88f8a-128">This is because the .NET Framework garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="88f8a-129">Pokud však aplikace zapouzdřuje nespravované prostředky, jako jsou okna, soubory a síťová připojení, měli byste tyto prostředky uvolnit pomocí finalizačních metod.</span><span class="sxs-lookup"><span data-stu-id="88f8a-129">However, when your application encapsulates unmanaged resources such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="88f8a-130">Pokud je objekt způsobilý pro dokončení, systém `Finalize` uvolňování paměti spustí metodu objektu.</span><span class="sxs-lookup"><span data-stu-id="88f8a-130">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>  
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="88f8a-131">Explicitní uvolnění zdrojů</span><span class="sxs-lookup"><span data-stu-id="88f8a-131">Explicit release of resources</span></span>  
 <span data-ttu-id="88f8a-132">Pokud vaše aplikace používá nákladné externí prostředek, doporučujeme také poskytnout způsob, jak explicitně uvolnit prostředek před uvolňování uvolní objekt.</span><span class="sxs-lookup"><span data-stu-id="88f8a-132">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="88f8a-133">Provedete to implementací `Dispose` metody <xref:System.IDisposable> z rozhraní, které provádí nezbytné vyčištění objektu.</span><span class="sxs-lookup"><span data-stu-id="88f8a-133">You do this by implementing a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="88f8a-134">To může výrazně zlepšit výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="88f8a-134">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="88f8a-135">I s touto explicitní kontrolu nad prostředky finalizační metody se stane `Dispose` ochrannou pro vyčištění prostředků, pokud volání metody se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="88f8a-135">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method failed.</span></span>  
  
 <span data-ttu-id="88f8a-136">Další podrobnosti o čištění prostředků naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="88f8a-136">For more details about cleaning up resources, see the following topics:</span></span>  
  
- [<span data-ttu-id="88f8a-137">Vymazání nespravovaných prostředků</span><span class="sxs-lookup"><span data-stu-id="88f8a-137">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
- [<span data-ttu-id="88f8a-138">Implementace metody Dispose</span><span class="sxs-lookup"><span data-stu-id="88f8a-138">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [<span data-ttu-id="88f8a-139">using – příkaz</span><span class="sxs-lookup"><span data-stu-id="88f8a-139">using Statement</span></span>](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="88f8a-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="88f8a-140">Example</span></span>  
 <span data-ttu-id="88f8a-141">Následující příklad vytvoří tři třídy, které vytvářejí řetězec dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="88f8a-141">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="88f8a-142">Třída `First` `Second` je základní třída, je `First`odvozena `Third` od , `Second`a je odvozen a .</span><span class="sxs-lookup"><span data-stu-id="88f8a-142">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="88f8a-143">Všechny tři mají finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="88f8a-143">All three have finalizers.</span></span> <span data-ttu-id="88f8a-144">V `Main`aplikaci je vytvořena instance nejvíce odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="88f8a-144">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="88f8a-145">Při spuštění programu všimněte si, že finalizační metody pro tři třídy jsou volány automaticky a v pořadí od nejvíce odvozené k nejméně odvozené.</span><span class="sxs-lookup"><span data-stu-id="88f8a-145">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="88f8a-146">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="88f8a-146">C# language specification</span></span>  

<span data-ttu-id="88f8a-147">Další informace naleznete v části [Destruktory](~/_csharplang/spec/classes.md#destructors) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="88f8a-147">For more information, see the [Destructors](~/_csharplang/spec/classes.md#destructors) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="88f8a-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="88f8a-148">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="88f8a-149">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="88f8a-149">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="88f8a-150">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="88f8a-150">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="88f8a-151">Kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="88f8a-151">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
