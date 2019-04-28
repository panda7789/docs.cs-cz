---
title: Finalizační metody - C# Průvodce programováním
ms.custom: seodec18
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 19c1f754aaef66197b033a68bc215255511cd618
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646524"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="137a2-102">Finalizační metody (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="137a2-102">Finalizers (C# Programming Guide)</span></span>
<span data-ttu-id="137a2-103">Finalizační metody (také nazývané **destruktory**) jsou používány k provádění všechny nezbytné konečné vyčištění při instanci třídy se shromažďují pomocí systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="137a2-103">Finalizers (which are also called **destructors**) are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="137a2-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="137a2-104">Remarks</span></span>  
  
- <span data-ttu-id="137a2-105">Finalizační metody nelze definovat ve strukturách.</span><span class="sxs-lookup"><span data-stu-id="137a2-105">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="137a2-106">Používají se jenom s třídami.</span><span class="sxs-lookup"><span data-stu-id="137a2-106">They are only used with classes.</span></span>  
  
- <span data-ttu-id="137a2-107">Třída může mít pouze jeden finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="137a2-107">A class can only have one finalizer.</span></span>  
  
- <span data-ttu-id="137a2-108">Finalizační metody nemůže zděděné nebo přetížené.</span><span class="sxs-lookup"><span data-stu-id="137a2-108">Finalizers cannot be inherited or overloaded.</span></span>  
  
- <span data-ttu-id="137a2-109">Nelze volat finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="137a2-109">Finalizers cannot be called.</span></span> <span data-ttu-id="137a2-110">Jsou vyvolány automaticky.</span><span class="sxs-lookup"><span data-stu-id="137a2-110">They are invoked automatically.</span></span>  
  
- <span data-ttu-id="137a2-111">Finalizační metoda nepodporuje trvat modifikátory ani mít parametry.</span><span class="sxs-lookup"><span data-stu-id="137a2-111">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="137a2-112">Například tady je deklarace finalizační metodu pro `Car` třídy.</span><span class="sxs-lookup"><span data-stu-id="137a2-112">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

<span data-ttu-id="137a2-113">Finalizační metoda je také možné implementovat jako definici tělo výrazu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="137a2-113">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="137a2-114">Implicitně volá finalizační metodu <xref:System.Object.Finalize%2A> v základní třídě objektu.</span><span class="sxs-lookup"><span data-stu-id="137a2-114">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="137a2-115">Proto volání finalizační metoda implicitně převádějí na následující kód:</span><span class="sxs-lookup"><span data-stu-id="137a2-115">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
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
  
 <span data-ttu-id="137a2-116">To znamená, že `Finalize` metoda se volá rekurzivně pro všechny instance v řetězu dědičnosti z nejvíce odvozenému pro nejméně odvozené.</span><span class="sxs-lookup"><span data-stu-id="137a2-116">This means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="137a2-117">Prázdné finalizační metody se nesmí používat.</span><span class="sxs-lookup"><span data-stu-id="137a2-117">Empty finalizers should not be used.</span></span> <span data-ttu-id="137a2-118">Pokud třída obsahuje finalizační metodu, je vytvořena položka v `Finalize` fronty.</span><span class="sxs-lookup"><span data-stu-id="137a2-118">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="137a2-119">Když je zavolána finalizační metodu, je vyvolána systému uvolňování paměti ke zpracování fronty.</span><span class="sxs-lookup"><span data-stu-id="137a2-119">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="137a2-120">Prázdná finalizační metoda způsobí pouze zbytečně ke ztrátě výkonu.</span><span class="sxs-lookup"><span data-stu-id="137a2-120">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="137a2-121">Programátor nemá žádnou kontrolu nad při finalizační metoda je volána, protože ta se určují podle systému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="137a2-121">The programmer has no control over when the finalizer is called because this is determined by the garbage collector.</span></span> <span data-ttu-id="137a2-122">Kontroluje, systému uvolňování paměti pro objekty, které jsou již nejsou déle používány aplikací.</span><span class="sxs-lookup"><span data-stu-id="137a2-122">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="137a2-123">Pokud bude objekt oprávnění k dokončení, volá finalizační metody (pokud existuje) a uvolňování paměti pro ukládání objektu.</span><span class="sxs-lookup"><span data-stu-id="137a2-123">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span> 
 
 <span data-ttu-id="137a2-124">V aplikacích .NET Framework (ale ne v aplikacích .NET Core) finalizační metody se také označují jako při ukončení programu.</span><span class="sxs-lookup"><span data-stu-id="137a2-124">In .NET Framework applications (but not in .NET Core applications), finalizers are also called when the program exits.</span></span> 
  
 <span data-ttu-id="137a2-125">Je možné vynutit uvolnění voláním <xref:System.GC.Collect%2A>, ale ve většině případů, toto by měl být vyhnout, protože může způsobit problémy s výkonem.</span><span class="sxs-lookup"><span data-stu-id="137a2-125">It is possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="137a2-126">Pomocí finalizační metody k uvolnění prostředků</span><span class="sxs-lookup"><span data-stu-id="137a2-126">Using finalizers to release resources</span></span>  
 <span data-ttu-id="137a2-127">Obecně platí C# nevyžaduje, aby Správa tolik paměti, jak je zapotřebí při vývoji v jazyce, který sdělení nebudete cílit na modul runtime s uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="137a2-127">In general, C# does not require as much memory management as is needed when you develop with a language that does not target a runtime with garbage collection.</span></span> <span data-ttu-id="137a2-128">Je to proto, že uvolňování paměti rozhraní .NET Framework implicitně spravuje přidělování a uvolňování paměti pro objekty.</span><span class="sxs-lookup"><span data-stu-id="137a2-128">This is because the .NET Framework garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="137a2-129">Ale když vaše aplikace zapouzdřuje nespravované prostředky, jako jsou windows, soubory a připojení k síti, by měl použít finalizační metody k uvolnění těchto prostředků.</span><span class="sxs-lookup"><span data-stu-id="137a2-129">However, when your application encapsulates unmanaged resources such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="137a2-130">Pokud je objekt oprávnění k dokončení, uvolňování paměti běží `Finalize` metodu objektu.</span><span class="sxs-lookup"><span data-stu-id="137a2-130">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>  
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="137a2-131">Explicitní uvolnění prostředků</span><span class="sxs-lookup"><span data-stu-id="137a2-131">Explicit release of resources</span></span>  
 <span data-ttu-id="137a2-132">Pokud vaše aplikace používá nákladné externí prostředek, doporučujeme také, že poskytují způsob, jak explicitně uvolnění prostředku před systému uvolňování paměti uvolní objekt.</span><span class="sxs-lookup"><span data-stu-id="137a2-132">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="137a2-133">Můžete to provést pomocí implementace `Dispose` metodu z <xref:System.IDisposable> rozhraní, které provádí potřebné vyčištění objektu.</span><span class="sxs-lookup"><span data-stu-id="137a2-133">You do this by implementing a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="137a2-134">To může výrazně zlepšit výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="137a2-134">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="137a2-135">I při tomto explicitní kontrolu nad prostředky, finalizační metodu, stane se ochrana pro vyčištění prostředků, pokud volání `Dispose` metody se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="137a2-135">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method failed.</span></span>  
  
 <span data-ttu-id="137a2-136">Podrobné informace o vymazání prostředků naleznete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="137a2-136">For more details about cleaning up resources, see the following topics:</span></span>  
  
- [<span data-ttu-id="137a2-137">Vymazání nespravovaných prostředků</span><span class="sxs-lookup"><span data-stu-id="137a2-137">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
- [<span data-ttu-id="137a2-138">Implementace metody Dispose</span><span class="sxs-lookup"><span data-stu-id="137a2-138">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [<span data-ttu-id="137a2-139">using – příkaz</span><span class="sxs-lookup"><span data-stu-id="137a2-139">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="137a2-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="137a2-140">Example</span></span>  
 <span data-ttu-id="137a2-141">Následující příklad vytvoří tři třídy, které usnadňují řetězu dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="137a2-141">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="137a2-142">Třída `First` je základní třídou `Second` je odvozen z `First`, a `Third` je odvozen z `Second`.</span><span class="sxs-lookup"><span data-stu-id="137a2-142">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="137a2-143">Všechny tři mají finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="137a2-143">All three have finalizers.</span></span> <span data-ttu-id="137a2-144">V `Main`, je vytvořena instance třídy odvozený.</span><span class="sxs-lookup"><span data-stu-id="137a2-144">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="137a2-145">Když se program spouští, Všimněte si, že finalizační metody pro tři třídy jsou volaní automaticky a v pořadí, nejvíce odvozenému na typ derived nejméně.</span><span class="sxs-lookup"><span data-stu-id="137a2-145">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="137a2-146">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="137a2-146">C# language specification</span></span>  

<span data-ttu-id="137a2-147">Další informace najdete v tématu [destruktory](~/_csharplang/spec/classes.md#destructors) část [ C# specifikace jazyka](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="137a2-147">For more information, see the [Destructors](~/_csharplang/spec/classes.md#destructors) section of the [C# language specification](../../language-reference/language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="137a2-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="137a2-148">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="137a2-149">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="137a2-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="137a2-150">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="137a2-150">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)
- [<span data-ttu-id="137a2-151">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="137a2-151">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
