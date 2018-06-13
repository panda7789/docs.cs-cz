---
title: Finalizační metody (C# Průvodce programováním)
ms.date: 05/10/2017
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: fc15818883736015419f8599d482185bbab5120a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313963"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="7e601-102">Finalizační metody (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="7e601-102">Finalizers (C# Programming Guide)</span></span>
<span data-ttu-id="7e601-103">Finalizační metody se používají k destruct instance tříd.</span><span class="sxs-lookup"><span data-stu-id="7e601-103">Finalizers are used to destruct instances of classes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e601-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e601-104">Remarks</span></span>  
  
-   <span data-ttu-id="7e601-105">Finalizační metody nemůže být definovaný ve struktury.</span><span class="sxs-lookup"><span data-stu-id="7e601-105">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="7e601-106">Použijí se jenom s třídami.</span><span class="sxs-lookup"><span data-stu-id="7e601-106">They are only used with classes.</span></span>  
  
-   <span data-ttu-id="7e601-107">Třída může mít pouze jeden finalizační metodu.</span><span class="sxs-lookup"><span data-stu-id="7e601-107">A class can only have one finalizer.</span></span>  
  
-   <span data-ttu-id="7e601-108">Finalizační metody nelze zděděná nebo přetížený.</span><span class="sxs-lookup"><span data-stu-id="7e601-108">Finalizers cannot be inherited or overloaded.</span></span>  
  
-   <span data-ttu-id="7e601-109">Nelze volat finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="7e601-109">Finalizers cannot be called.</span></span> <span data-ttu-id="7e601-110">Jsou vyvolány automaticky.</span><span class="sxs-lookup"><span data-stu-id="7e601-110">They are invoked automatically.</span></span>  
  
-   <span data-ttu-id="7e601-111">Finalizační metody nemá trvat modifikátory nebo mít parametry.</span><span class="sxs-lookup"><span data-stu-id="7e601-111">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="7e601-112">Například následující je deklaraci finalizační metodu pro `Car` třídy.</span><span class="sxs-lookup"><span data-stu-id="7e601-112">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_1.cs)]  

<span data-ttu-id="7e601-113">Finalizační metody lze také implementovat jako definici textu výrazu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="7e601-113">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="7e601-114">Implicitně volá finalizační metodu <xref:System.Object.Finalize%2A> na základní třídu objektu.</span><span class="sxs-lookup"><span data-stu-id="7e601-114">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="7e601-115">Proto volání finalizační metody implicitně převést na následující kód:</span><span class="sxs-lookup"><span data-stu-id="7e601-115">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
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
  
 <span data-ttu-id="7e601-116">To znamená, že `Finalize` metoda je volána rekurzivně pro všechny instance v řetězu dědičnosti z většinou odvozených pro odvozené nejmenší.</span><span class="sxs-lookup"><span data-stu-id="7e601-116">This means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e601-117">Prázdné finalizační metody by nemělo být použito.</span><span class="sxs-lookup"><span data-stu-id="7e601-117">Empty finalizers should not be used.</span></span> <span data-ttu-id="7e601-118">Pokud třída obsahuje finalizační metody, vytvoří se záznam v `Finalize` fronty.</span><span class="sxs-lookup"><span data-stu-id="7e601-118">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="7e601-119">Při volání finalizační metodu volá se ke zpracování fronty uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7e601-119">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="7e601-120">Prázdné finalizační metodu právě způsobí, že zbytečně snížením výkonu.</span><span class="sxs-lookup"><span data-stu-id="7e601-120">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="7e601-121">Programátorů nemá žádnou kontrolu nad při volání finalizační metodu, protože to je dáno uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7e601-121">The programmer has no control over when the finalizer is called because this is determined by the garbage collector.</span></span> <span data-ttu-id="7e601-122">Uvolňování paměti kontroluje pro objekty, které jsou již používá aplikace.</span><span class="sxs-lookup"><span data-stu-id="7e601-122">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="7e601-123">Pokud objekt považuje vhodné pro dokončení, zavolá finalizační metodu (pokud existuje) a uvolní paměť použitá k uložení objektu.</span><span class="sxs-lookup"><span data-stu-id="7e601-123">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span> <span data-ttu-id="7e601-124">Finalizační metody se také nazývají při ukončení programu.</span><span class="sxs-lookup"><span data-stu-id="7e601-124">Finalizers are also called when the program exits.</span></span>  
  
 <span data-ttu-id="7e601-125">Je možné vynutit uvolňování voláním <xref:System.GC.Collect%2A>, ale ve většině případů, to je nutno vzhledem k tomu může způsobit problémy s výkonem.</span><span class="sxs-lookup"><span data-stu-id="7e601-125">It is possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="7e601-126">Pomocí finalizační metody k prostředkům verze</span><span class="sxs-lookup"><span data-stu-id="7e601-126">Using Finalizers to Release Resources</span></span>  
 <span data-ttu-id="7e601-127">Obecně platí jazyka C# nevyžaduje, aby Správa tolik paměti, jako je potřeba při vývoji v jazyce, který není zaměřen modulu runtime s uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="7e601-127">In general, C# does not require as much memory management as is needed when you develop with a language that does not target a runtime with garbage collection.</span></span> <span data-ttu-id="7e601-128">To je proto garbage collector v rozhraní .NET Framework implicitně spravuje přidělování a uvolňování paměti pro objektů.</span><span class="sxs-lookup"><span data-stu-id="7e601-128">This is because the .NET Framework garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="7e601-129">Ale při aplikaci zapouzdří nespravovaných prostředků, jako jsou windows, soubory a připojení k síti, byste měli použít finalizační metody k uvolnění těchto prostředků.</span><span class="sxs-lookup"><span data-stu-id="7e601-129">However, when your application encapsulates unmanaged resources such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="7e601-130">Pokud je objekt vhodné pro dokončení, bude systém uvolňování běží `Finalize` metodu objektu.</span><span class="sxs-lookup"><span data-stu-id="7e601-130">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>  
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="7e601-131">Explicitní uvolnění prostředků</span><span class="sxs-lookup"><span data-stu-id="7e601-131">Explicit Release of Resources</span></span>  
 <span data-ttu-id="7e601-132">Pokud vaše aplikace používá nákladné externí prostředek, doporučujeme také zadat způsob, jak explicitně verzi prostředku před uvolňování uvolní objekt.</span><span class="sxs-lookup"><span data-stu-id="7e601-132">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="7e601-133">To provedete tím, že implementujete `Dispose` metoda z <xref:System.IDisposable> rozhraní, které provádí nezbytné vyčištění pro objekt.</span><span class="sxs-lookup"><span data-stu-id="7e601-133">You do this by implementing a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="7e601-134">To může výrazně zlepšit výkon aplikace.</span><span class="sxs-lookup"><span data-stu-id="7e601-134">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="7e601-135">I přes tato explicitní kontrolu nad prostředky finalizační metodu bude chránit vyčištění prostředků, pokud volání `Dispose` metoda se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="7e601-135">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method failed.</span></span>  
  
 <span data-ttu-id="7e601-136">Další podrobnosti o vymazání prostředků najdete v následujících tématech:</span><span class="sxs-lookup"><span data-stu-id="7e601-136">For more details about cleaning up resources, see the following topics:</span></span>  
  
-   [<span data-ttu-id="7e601-137">Vymazání nespravovaných prostředků</span><span class="sxs-lookup"><span data-stu-id="7e601-137">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
-   [<span data-ttu-id="7e601-138">Implementace metody Dispose</span><span class="sxs-lookup"><span data-stu-id="7e601-138">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
-   [<span data-ttu-id="7e601-139">using – příkaz</span><span class="sxs-lookup"><span data-stu-id="7e601-139">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="7e601-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e601-140">Example</span></span>  
 <span data-ttu-id="7e601-141">Následující příklad vytvoří tři třídy, které Ujistěte se, řetězce dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="7e601-141">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="7e601-142">Třída `First` je základní třídou `Second` je odvozený od `First`, a `Third` je odvozený od `Second`.</span><span class="sxs-lookup"><span data-stu-id="7e601-142">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="7e601-143">Všechny tři mít finalizační metody.</span><span class="sxs-lookup"><span data-stu-id="7e601-143">All three have finalizers.</span></span> <span data-ttu-id="7e601-144">V `Main`, je vytvořena instance většinou odvozených tříd.</span><span class="sxs-lookup"><span data-stu-id="7e601-144">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="7e601-145">Když se program spouští, Všimněte si, že finalizační metody pro tři třídy jsou volány automaticky a v pořadí, z většinou odvozených pro odvozené nejmenší.</span><span class="sxs-lookup"><span data-stu-id="7e601-145">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="7e601-146">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7e601-146">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7e601-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e601-147">See Also</span></span>  
 <xref:System.IDisposable>  
 [<span data-ttu-id="7e601-148">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7e601-148">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="7e601-149">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="7e601-149">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="7e601-150">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="7e601-150">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
