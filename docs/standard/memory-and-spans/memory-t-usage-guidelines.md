---
title: Pokyny k používání Memory<T> a Span<T>
description: Tento článek popisuje paměť <T> a rozsah <T> , což jsou vyrovnávací paměti strukturovaných dat v .NET Core, které je možné použít v kanálech.
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
ms.openlocfilehash: cb9075a12bb8d842cd8e937e74f8869c910fc0ab
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201942"
---
# <a name="memoryt-and-spant-usage-guidelines"></a><span data-ttu-id="e726a-103">Pokyny k používání Memory\<T> a Span\<T></span><span class="sxs-lookup"><span data-stu-id="e726a-103">Memory\<T> and Span\<T> usage guidelines</span></span>

<span data-ttu-id="e726a-104">.NET Core obsahuje několik typů, které reprezentují libovolnou souvislou oblast paměti.</span><span class="sxs-lookup"><span data-stu-id="e726a-104">.NET Core includes a number of types that represent an arbitrary contiguous region of memory.</span></span> <span data-ttu-id="e726a-105">.NET Core 2,0 zavádí <xref:System.Span%601> a <xref:System.ReadOnlySpan%601> , což jsou odlehčené vyrovnávací paměti, které mohou být zajištěny spravovanou nebo nespravovanou pamětí.</span><span class="sxs-lookup"><span data-stu-id="e726a-105">.NET Core 2.0 introduced <xref:System.Span%601> and <xref:System.ReadOnlySpan%601>, which are lightweight memory buffers that can be backed by managed or unmanaged memory.</span></span> <span data-ttu-id="e726a-106">Vzhledem k tomu, že tyto typy mohou být uloženy pouze v zásobníku, nejsou vhodné pro různé scénáře, včetně volání asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="e726a-106">Because these types can only be stored on the stack, they are unsuitable for a number of scenarios, including asynchronous method calls.</span></span> <span data-ttu-id="e726a-107">.NET Core 2,1 přidává mnoho dalších typů, včetně <xref:System.Memory%601> , <xref:System.ReadOnlyMemory%601> , <xref:System.Buffers.IMemoryOwner%601> a <xref:System.Buffers.MemoryPool%601> .</span><span class="sxs-lookup"><span data-stu-id="e726a-107">.NET Core 2.1 adds a number of additional types, including <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>, and <xref:System.Buffers.MemoryPool%601>.</span></span> <span data-ttu-id="e726a-108">Podobně <xref:System.Span%601> jako <xref:System.Memory%601> a jeho související typy lze zálohovat pomocí spravované i nespravované paměti.</span><span class="sxs-lookup"><span data-stu-id="e726a-108">Like <xref:System.Span%601>, <xref:System.Memory%601> and its related types can be backed by both managed and unmanaged memory.</span></span> <span data-ttu-id="e726a-109">Na rozdíl od <xref:System.Span%601> , <xref:System.Memory%601> může být uloženo na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="e726a-109">Unlike <xref:System.Span%601>, <xref:System.Memory%601> can be stored on the managed heap.</span></span>

<span data-ttu-id="e726a-110">Obojí <xref:System.Span%601> i <xref:System.Memory%601> jsou vyrovnávací paměti strukturovaných dat, která lze použít v kanálech.</span><span class="sxs-lookup"><span data-stu-id="e726a-110">Both <xref:System.Span%601> and <xref:System.Memory%601> are buffers of structured data that can be used in pipelines.</span></span> <span data-ttu-id="e726a-111">To znamená, že jsou navržené tak, aby některá nebo všechna data mohla být efektivně předána součástem v kanálu, která je může zpracovávat a případně upravovat vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="e726a-111">That is, they are designed so that some or all of the data can be efficiently passed to components in the pipeline, which can process them and optionally modify the buffer.</span></span> <span data-ttu-id="e726a-112">Vzhledem <xref:System.Memory%601> k tomu, že a ke kterým souvisejícímu typu lze získat pøístup více komponent nebo více vlákny, je důležité, aby vývojáři při vytváření robustního kódu dodržovali některé standardní pokyny pro použití.</span><span class="sxs-lookup"><span data-stu-id="e726a-112">Because <xref:System.Memory%601> and its related types can be accessed by multiple components or by multiple threads, it's important that developers follow some standard usage guidelines to produce robust code.</span></span>

## <a name="owners-consumers-and-lifetime-management"></a><span data-ttu-id="e726a-113">Vlastníci, spotřebitelé a správa životního cyklu</span><span class="sxs-lookup"><span data-stu-id="e726a-113">Owners, consumers, and lifetime management</span></span>

<span data-ttu-id="e726a-114">Vzhledem k tomu, že vyrovnávací paměti lze předávat mezi rozhraními API a vzhledem k tomu, že vyrovnávací paměti mohou být někdy k dispozici z více vláken, je důležité zvážit správu životnosti.</span><span class="sxs-lookup"><span data-stu-id="e726a-114">Since buffers can be passed around between APIs, and since buffers can sometimes be accessed from multiple threads, it's important to consider lifetime management.</span></span> <span data-ttu-id="e726a-115">Existují tři základní koncepty:</span><span class="sxs-lookup"><span data-stu-id="e726a-115">There are three core concepts:</span></span>

- <span data-ttu-id="e726a-116">**Vlastnictví**.</span><span class="sxs-lookup"><span data-stu-id="e726a-116">**Ownership**.</span></span> <span data-ttu-id="e726a-117">Vlastník instance vyrovnávací paměti je zodpovědný za správu životnosti, včetně zničení vyrovnávací paměti, když se už nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="e726a-117">The owner of a buffer instance is responsible for lifetime management, including destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="e726a-118">Všechny vyrovnávací paměti mají jednoho vlastníka.</span><span class="sxs-lookup"><span data-stu-id="e726a-118">All buffers have a single owner.</span></span> <span data-ttu-id="e726a-119">Obecně je vlastníkem komponenta, která vytvořila vyrovnávací paměť nebo která obdržela vyrovnávací paměť z továrny.</span><span class="sxs-lookup"><span data-stu-id="e726a-119">Generally the owner is the component that created the buffer or that received the buffer from a factory.</span></span> <span data-ttu-id="e726a-120">Vlastnictví lze také přenést; **Součást-a** může opustit řízení vyrovnávací paměti pro **komponentu B**, na které **Komponenta bodu-A** již nesmí používat vyrovnávací paměť, a **Komponenta B** se stane zodpovědností za zničení vyrovnávací paměti, pokud se už nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="e726a-120">Ownership can also be transferred; **Component-A** can relinquish control of the buffer to **Component-B**, at which point **Component-A** may no longer use the buffer, and **Component-B** becomes responsible for destroying the buffer when it's no longer in use.</span></span>

- <span data-ttu-id="e726a-121">**Spotřeba**.</span><span class="sxs-lookup"><span data-stu-id="e726a-121">**Consumption**.</span></span> <span data-ttu-id="e726a-122">Příjemce instance vyrovnávací paměti může použít instanci vyrovnávací paměti čtením z ní a případně do ní zapisovat.</span><span class="sxs-lookup"><span data-stu-id="e726a-122">The consumer of a buffer instance is allowed to use the buffer instance by reading from it and possibly writing to it.</span></span> <span data-ttu-id="e726a-123">Vyrovnávací paměti můžou mít jednoho příjemce v čase, pokud není k dispozici nějaký mechanismus externí synchronizace.</span><span class="sxs-lookup"><span data-stu-id="e726a-123">Buffers can have one consumer at a time unless some external synchronization mechanism is provided.</span></span> <span data-ttu-id="e726a-124">Aktivní příjemce vyrovnávací paměti nemusí být nutně vlastníkem vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e726a-124">The active consumer of a buffer isn't necessarily the buffer's owner.</span></span>

- <span data-ttu-id="e726a-125">**Zapůjčení**.</span><span class="sxs-lookup"><span data-stu-id="e726a-125">**Lease**.</span></span> <span data-ttu-id="e726a-126">Zapůjčení je doba, po kterou může určitá součást být příjemcem vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e726a-126">The lease is the length of time that a particular component is allowed to be the consumer of the buffer.</span></span>

<span data-ttu-id="e726a-127">Následující příklad pseudo kódu znázorňuje tyto tři koncepty.</span><span class="sxs-lookup"><span data-stu-id="e726a-127">The following pseudo-code example illustrates these three concepts.</span></span> <span data-ttu-id="e726a-128">Obsahuje `Main` metodu, která vytváří instanci <xref:System.Memory%601> vyrovnávací paměti typu <xref:System.Char> , volá `WriteInt32ToBuffer` metodu pro zápis řetězcové reprezentace celého čísla do vyrovnávací paměti a poté volá `DisplayBufferToConsole` metodu pro zobrazení hodnoty vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e726a-128">It includes a `Main` method that instantiates a <xref:System.Memory%601> buffer of type <xref:System.Char>, calls the `WriteInt32ToBuffer` method to write the string representation of an integer to the buffer, and then calls the `DisplayBufferToConsole` method to display the value of the buffer.</span></span>

```csharp
using System;

class Program
{
    // Write 'value' as a human-readable string to the output buffer.
    void WriteInt32ToBuffer(int value, Buffer buffer);

    // Display the contents of the buffer to the console.
    void DisplayBufferToConsole(Buffer buffer);

    // Application code
    static void Main()
    {
        var buffer = CreateBuffer();
        try
        {
            int value = Int32.Parse(Console.ReadLine());
            WriteInt32ToBuffer(value, buffer);
            DisplayBufferToConsole(buffer);
        }
        finally
        {
            buffer.Destroy();
        }
    }
}
```

<span data-ttu-id="e726a-129">`Main`Metoda vytvoří vyrovnávací paměť (v tomto případě <xref:System.Span%601> instance) a tedy její vlastníka.</span><span class="sxs-lookup"><span data-stu-id="e726a-129">The `Main` method creates the buffer (in this case an <xref:System.Span%601> instance) and so is its owner.</span></span> <span data-ttu-id="e726a-130">Proto `Main` zodpovídá za zničení vyrovnávací paměti, když se už nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="e726a-130">Therefore, `Main` is responsible for destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="e726a-131">Provede to voláním metody vyrovnávací paměti <xref:System.Span%601.Clear?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e726a-131">It does this by calling the buffer's <xref:System.Span%601.Clear?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="e726a-132">(Tato <xref:System.Span%601.Clear> Metoda ve skutečnosti vymaže paměť vyrovnávací paměti; <xref:System.Span%601> Struktura ve skutečnosti nemá metodu, která zničí vyrovnávací paměť.)</span><span class="sxs-lookup"><span data-stu-id="e726a-132">(The <xref:System.Span%601.Clear> method here actually clears the buffer's memory; the <xref:System.Span%601> structure doesn't actually have a method that destroys the buffer.)</span></span>

<span data-ttu-id="e726a-133">Vyrovnávací paměť má dva uživatele `WriteInt32ToBuffer` a `DisplayBufferToConsole` .</span><span class="sxs-lookup"><span data-stu-id="e726a-133">The buffer has two consumers, `WriteInt32ToBuffer` and `DisplayBufferToConsole`.</span></span> <span data-ttu-id="e726a-134">V jednom okamžiku je k dispozici pouze jeden příjemce (první `WriteInt32ToBuffer` , potom `DisplayBufferToConsole` ) a žádný z uživatelů vlastní vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="e726a-134">There is only one consumer at a time (first `WriteInt32ToBuffer`, then `DisplayBufferToConsole`), and neither of the consumers owns the buffer.</span></span> <span data-ttu-id="e726a-135">Všimněte si také, že "příjemce" v tomto kontextu neznamená zobrazení vyrovnávací paměti jen pro čtení. Uživatelé můžou upravovat obsah vyrovnávací paměti, jak to `WriteInt32ToBuffer` dělá, pokud je k dispozici zobrazení pro čtení a zápis vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e726a-135">Note also that "consumer" in this context doesn't imply a read-only view of the buffer; consumers can modify the buffer's contents, as `WriteInt32ToBuffer` does, if given a read/write view of the buffer.</span></span>

<span data-ttu-id="e726a-136">`WriteInt32ToBuffer`Metoda má zapůjčení (může spotřebovat) vyrovnávací paměť mezi začátkem volání metody a časem, který metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="e726a-136">The `WriteInt32ToBuffer` method has a lease on (can consume) the buffer between the start of the method call and the time the method returns.</span></span> <span data-ttu-id="e726a-137">Podobně `DisplayBufferToConsole` má zapůjčení ve vyrovnávací paměti během jeho provádění a zapůjčení je uvolněno při zrušení metody.</span><span class="sxs-lookup"><span data-stu-id="e726a-137">Similarly, `DisplayBufferToConsole` has a lease on the buffer while it's executing, and the lease is released when the method unwinds.</span></span> <span data-ttu-id="e726a-138">(K dispozici není žádné rozhraní API pro správu zapůjčených adres. "zapůjčení" je koncepční záležitost.)</span><span class="sxs-lookup"><span data-stu-id="e726a-138">(There is no API for lease management; a "lease" is a conceptual matter.)</span></span>

## <a name="memoryt-and-the-ownerconsumer-model"></a><span data-ttu-id="e726a-139">Paměť \<T> a model vlastník/příjemce</span><span class="sxs-lookup"><span data-stu-id="e726a-139">Memory\<T> and the owner/consumer model</span></span>

<span data-ttu-id="e726a-140">Jako poznámky k oddílům [pro vlastníky, uživatele a správu životního cyklu](#owners-consumers-and-lifetime-management) má vyrovnávací paměť vždy vlastníka.</span><span class="sxs-lookup"><span data-stu-id="e726a-140">As the [Owners, consumers, and lifetime management](#owners-consumers-and-lifetime-management) section notes, a buffer always has an owner.</span></span> <span data-ttu-id="e726a-141">.NET Core podporuje dva modely vlastnictví:</span><span class="sxs-lookup"><span data-stu-id="e726a-141">.NET Core supports two ownership models:</span></span>

- <span data-ttu-id="e726a-142">Model, který podporuje jediné vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="e726a-142">A model that supports single ownership.</span></span> <span data-ttu-id="e726a-143">Vyrovnávací paměť má jednoho vlastníka pro celou dobu života.</span><span class="sxs-lookup"><span data-stu-id="e726a-143">A buffer has a single owner for its entire lifetime.</span></span>

- <span data-ttu-id="e726a-144">Model, který podporuje přenos vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="e726a-144">A model that supports ownership transfer.</span></span> <span data-ttu-id="e726a-145">Vlastnictví vyrovnávací paměti lze přenést od původního vlastníka (jeho tvůrce) do jiné součásti, která pak bude zodpovědná za správu životnosti vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e726a-145">Ownership of a buffer can be transferred from its original owner (its creator) to another component, which then becomes responsible for the buffer's lifetime management.</span></span> <span data-ttu-id="e726a-146">Vlastník může převést vlastnictví na jinou komponentu a tak dále.</span><span class="sxs-lookup"><span data-stu-id="e726a-146">That owner can in turn transfer ownership to another component, and so on.</span></span>

<span data-ttu-id="e726a-147">Rozhraní použijete <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> k explicitní správě vlastnictví vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e726a-147">You use the <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> interface to explicitly manage the ownership of a buffer.</span></span> <span data-ttu-id="e726a-148"><xref:System.Buffers.IMemoryOwner%601>podporuje oba modely vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="e726a-148"><xref:System.Buffers.IMemoryOwner%601> supports both ownership models.</span></span> <span data-ttu-id="e726a-149">Komponenta, která má <xref:System.Buffers.IMemoryOwner%601> odkaz na vlastní vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="e726a-149">The component that has an <xref:System.Buffers.IMemoryOwner%601> reference owns the buffer.</span></span> <span data-ttu-id="e726a-150">Následující příklad používá <xref:System.Buffers.IMemoryOwner%601?> instanci pro reflektování vlastnictví <xref:System.Memory%601> vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e726a-150">The following example uses an <xref:System.Buffers.IMemoryOwner%601?> instance to reflect the ownership of a <xref:System.Memory%601> buffer.</span></span>

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

<span data-ttu-id="e726a-151">Tento příklad můžeme také zapsat pomocí [`using`](../../csharp/language-reference/keywords/using-statement.md) :</span><span class="sxs-lookup"><span data-stu-id="e726a-151">We can also write this example with the [`using`](../../csharp/language-reference/keywords/using-statement.md):</span></span>

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

<span data-ttu-id="e726a-152">V tomto kódu:</span><span class="sxs-lookup"><span data-stu-id="e726a-152">In this code:</span></span>

- <span data-ttu-id="e726a-153">`Main`Metoda obsahuje odkaz na <xref:System.Buffers.IMemoryOwner%601> instanci, takže `Main` Metoda je vlastníkem vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e726a-153">The `Main` method holds the reference to the <xref:System.Buffers.IMemoryOwner%601> instance, so the `Main` method is the owner of the buffer.</span></span>

- <span data-ttu-id="e726a-154">`WriteInt32ToBuffer`Metody a `DisplayBufferToConsole` akceptují <xref:System.Memory%601> jako veřejné rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="e726a-154">The `WriteInt32ToBuffer` and `DisplayBufferToConsole` methods accept <xref:System.Memory%601> as a public API.</span></span> <span data-ttu-id="e726a-155">Proto jsou příjemci vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e726a-155">Therefore, they are consumers of the buffer.</span></span> <span data-ttu-id="e726a-156">A využívají je pouze po jednom.</span><span class="sxs-lookup"><span data-stu-id="e726a-156">And they only consume it one at a time.</span></span>

<span data-ttu-id="e726a-157">I když `WriteInt32ToBuffer` je metoda určena pro zápis hodnoty do vyrovnávací paměti, `DisplayBufferToConsole` metoda není.</span><span class="sxs-lookup"><span data-stu-id="e726a-157">Although the `WriteInt32ToBuffer` method is intended to write a value to the buffer, the `DisplayBufferToConsole` method isn't.</span></span> <span data-ttu-id="e726a-158">Aby se to odráželo, mohl by být přijatý argument typu <xref:System.ReadOnlyMemory%601> .</span><span class="sxs-lookup"><span data-stu-id="e726a-158">To reflect this, it could have accepted an argument of type <xref:System.ReadOnlyMemory%601>.</span></span> <span data-ttu-id="e726a-159">Další informace o naleznete v <xref:System.ReadOnlyMemory%601> tématu [Rule #2: použijte ReadOnlySpan \<T> nebo ReadOnlyMemory, \<T> Pokud by měla být vyrovnávací paměť jen pro čtení](#rule-2).</span><span class="sxs-lookup"><span data-stu-id="e726a-159">For more information on <xref:System.ReadOnlyMemory%601>, see [Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only](#rule-2).</span></span>

### <a name="ownerless-memoryt-instances"></a><span data-ttu-id="e726a-160">Instance paměti "nevlastní" \<T></span><span class="sxs-lookup"><span data-stu-id="e726a-160">"Ownerless" Memory\<T> instances</span></span>

<span data-ttu-id="e726a-161">Můžete vytvořit <xref:System.Memory%601> instanci bez použití <xref:System.Buffers.IMemoryOwner%601> .</span><span class="sxs-lookup"><span data-stu-id="e726a-161">You can create a <xref:System.Memory%601> instance without using <xref:System.Buffers.IMemoryOwner%601>.</span></span> <span data-ttu-id="e726a-162">V takovém případě je vlastnictví vyrovnávací paměti implicitní, nikoli explicitní, a podporuje se jenom model s jedním vlastníkem.</span><span class="sxs-lookup"><span data-stu-id="e726a-162">In this case, ownership of the buffer is implicit rather than explicit, and only the single-owner model is supported.</span></span> <span data-ttu-id="e726a-163">Můžete to udělat takto:</span><span class="sxs-lookup"><span data-stu-id="e726a-163">You can do this by:</span></span>

- <span data-ttu-id="e726a-164">Volání jednoho z <xref:System.Memory%601> konstruktorů přímo, předání v `T[]` , jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e726a-164">Calling one of the  <xref:System.Memory%601> constructors directly, passing in a `T[]`, as the following example does.</span></span>

- <span data-ttu-id="e726a-165">Voláním metody rozšíření [String. AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) pro vytvoření `ReadOnlyMemory<char>` instance.</span><span class="sxs-lookup"><span data-stu-id="e726a-165">Calling the [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) extension method to produce a `ReadOnlyMemory<char>` instance.</span></span>

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

<span data-ttu-id="e726a-166">Metoda, která zpočátku vytvoří <xref:System.Memory%601> instanci, je implicitní vlastník vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e726a-166">The method that initially creates the <xref:System.Memory%601> instance is the implicit owner of the buffer.</span></span> <span data-ttu-id="e726a-167">Vlastnictví nelze přenést do žádné jiné součásti, protože není k dispozici žádná <xref:System.Buffers.IMemoryOwner%601> instance pro usnadnění přenosu.</span><span class="sxs-lookup"><span data-stu-id="e726a-167">Ownership cannot be transferred to any other component because there is no <xref:System.Buffers.IMemoryOwner%601> instance to facilitate the transfer.</span></span> <span data-ttu-id="e726a-168">(Jako alternativu můžete také představovat, že systém uvolňování paměti modulu runtime vlastní vyrovnávací paměť, a všechny metody pouze využívají vyrovnávací paměť.)</span><span class="sxs-lookup"><span data-stu-id="e726a-168">(As an alternative, you can also imagine that the runtime's garbage collector owns the buffer, and all methods just consume the buffer.)</span></span>

## <a name="usage-guidelines"></a><span data-ttu-id="e726a-169">Pokyny k používání</span><span class="sxs-lookup"><span data-stu-id="e726a-169">Usage guidelines</span></span>

<span data-ttu-id="e726a-170">Vzhledem k tomu, že blok paměti je vlastněn, ale má být předán více komponentám, některé z nich mohou fungovat současně na konkrétní blok paměti, je důležité vytvořit pokyny pro použití obou <xref:System.Memory%601> i <xref:System.Span%601> .</span><span class="sxs-lookup"><span data-stu-id="e726a-170">Because a memory block is owned but is intended to be passed to multiple components, some of which may operate upon a particular memory block simultaneously, it is important to establish guidelines for using both <xref:System.Memory%601> and <xref:System.Span%601>.</span></span>  <span data-ttu-id="e726a-171">Pokyny jsou nezbytné z těchto důvodů:</span><span class="sxs-lookup"><span data-stu-id="e726a-171">Guidelines are necessary because:</span></span>

- <span data-ttu-id="e726a-172">Je možné, že komponenta uchovává odkaz na blok paměti poté, co ho jeho vlastník uvolnil.</span><span class="sxs-lookup"><span data-stu-id="e726a-172">It is possible for a component to retain a reference to a memory block after its owner has released it.</span></span>

- <span data-ttu-id="e726a-173">Je možné, že komponenta pracuje na vyrovnávací paměti současně s tím, že na ní jiná komponenta pracuje, v procesu poškození dat ve vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e726a-173">It is possible for a component to operate on a buffer at the same time that another component is operating on it, in the process corrupting the data in the buffer.</span></span>

- <span data-ttu-id="e726a-174">I když je vyhrazená sada <xref:System.Span%601> pro optimalizaci výkonu a dává <xref:System.Span%601> preferovaný typ pro provoz na bloku paměti, je také předmětům <xref:System.Span%601> některých hlavních omezení.</span><span class="sxs-lookup"><span data-stu-id="e726a-174">While the stack-allocated nature of <xref:System.Span%601> optimizes performance and makes <xref:System.Span%601> the preferred type for operating on a memory block, it also subjects <xref:System.Span%601> to some major restrictions.</span></span> <span data-ttu-id="e726a-175">Je důležité znát, kdy použít <xref:System.Span%601> a kdy použít <xref:System.Memory%601> .</span><span class="sxs-lookup"><span data-stu-id="e726a-175">It is important to know when to use a <xref:System.Span%601> and when to use <xref:System.Memory%601>.</span></span>

<span data-ttu-id="e726a-176">Níže jsou naše doporučení pro úspěšné používání <xref:System.Memory%601> a související typy.</span><span class="sxs-lookup"><span data-stu-id="e726a-176">The following are our recommendations for successfully using <xref:System.Memory%601> and its related types.</span></span> <span data-ttu-id="e726a-177">Doprovodné materiály, které se vztahují na <xref:System.Memory%601> a <xref:System.Span%601> platí i <xref:System.ReadOnlyMemory%601> <xref:System.ReadOnlySpan%601> v případě, že výslovně nebereme jinak.</span><span class="sxs-lookup"><span data-stu-id="e726a-177">Guidance that applies to <xref:System.Memory%601> and <xref:System.Span%601> also applies to <xref:System.ReadOnlyMemory%601> and <xref:System.ReadOnlySpan%601> unless we explicitly note otherwise.</span></span>

<span data-ttu-id="e726a-178">**#1 pravidla: pro synchronní rozhraní API použijte \<T> místo toho možnost span namísto paměti \<T> jako parametru, pokud je to možné.**</span><span class="sxs-lookup"><span data-stu-id="e726a-178">**Rule #1: For a synchronous API, use Span\<T> instead of Memory\<T> as a parameter if possible.**</span></span>

<span data-ttu-id="e726a-179"><xref:System.Span%601>je všestrannější než <xref:System.Memory%601> a může představovat širší škálu souvislých vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="e726a-179"><xref:System.Span%601> is more versatile than <xref:System.Memory%601> and can represent a wider variety of contiguous memory buffers.</span></span> <span data-ttu-id="e726a-180"><xref:System.Span%601>nabízí také lepší výkon než <xref:System.Memory%601> .</span><span class="sxs-lookup"><span data-stu-id="e726a-180"><xref:System.Span%601> also offers better performance than <xref:System.Memory%601>.</span></span> <span data-ttu-id="e726a-181">Nakonec můžete použít <xref:System.Memory%601.Span?displayProperty=nameWithType> vlastnost k převedení <xref:System.Memory%601> instance na <xref:System.Span%601> , i když převod z rozsahu \<T> na paměť \<T> není možný.</span><span class="sxs-lookup"><span data-stu-id="e726a-181">Finally, you can use the <xref:System.Memory%601.Span?displayProperty=nameWithType> property to convert a <xref:System.Memory%601> instance to a <xref:System.Span%601>, although Span\<T>-to-Memory\<T> conversion isn't possible.</span></span> <span data-ttu-id="e726a-182">Takže v případě, že se volající mají <xref:System.Memory%601> instance, budou moci volat metody s <xref:System.Span%601> parametry přesto.</span><span class="sxs-lookup"><span data-stu-id="e726a-182">So if your callers happen to have a <xref:System.Memory%601> instance, they'll be able to call your methods with <xref:System.Span%601> parameters anyway.</span></span>

<span data-ttu-id="e726a-183">Použití parametru typu <xref:System.Span%601> místo typu <xref:System.Memory%601> také vám pomůže napsat správnou implementaci využívající metodu.</span><span class="sxs-lookup"><span data-stu-id="e726a-183">Using a parameter of type <xref:System.Span%601> instead of type <xref:System.Memory%601> also helps you write a correct consuming method implementation.</span></span> <span data-ttu-id="e726a-184">Automaticky získáte kontroly za běhu, abyste se ujistili, že se nepokoušíte o přístup k vyrovnávací paměti nad zapůjčením vaší metody (Další informace najdete později).</span><span class="sxs-lookup"><span data-stu-id="e726a-184">You'll automatically get compile-time checks to ensure that you're not attempting to access the buffer beyond your method's lease (more on this later).</span></span>

<span data-ttu-id="e726a-185">V některých případech budete muset <xref:System.Memory%601> místo parametru použít parametr <xref:System.Span%601> , a to i v případě, že jste plně synchronně.</span><span class="sxs-lookup"><span data-stu-id="e726a-185">Sometimes, you'll have to use a <xref:System.Memory%601> parameter instead of a <xref:System.Span%601> parameter, even if you're fully synchronous.</span></span> <span data-ttu-id="e726a-186">Možná rozhraní API, které zabíráte, přijímá jenom <xref:System.Memory%601> argumenty.</span><span class="sxs-lookup"><span data-stu-id="e726a-186">Perhaps an API that you depend accepts only <xref:System.Memory%601> arguments.</span></span> <span data-ttu-id="e726a-187">Je to v pořádku, ale mějte na paměti, že při použití synchronně dochází k kompromisům <xref:System.Memory%601> .</span><span class="sxs-lookup"><span data-stu-id="e726a-187">This is fine, but be aware of the tradeoffs involved when using <xref:System.Memory%601> synchronously.</span></span>

<a name="rule-2" />

<span data-ttu-id="e726a-188">**#2 pravidla: použijte ReadOnlySpan \<T> nebo ReadOnlyMemory, \<T> Pokud by vyrovnávací paměť měla být jen pro čtení.**</span><span class="sxs-lookup"><span data-stu-id="e726a-188">**Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only.**</span></span>

<span data-ttu-id="e726a-189">V předchozích příkladech `DisplayBufferToConsole` Metoda načítá jenom z vyrovnávací paměti. neupravuje obsah vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e726a-189">In the earlier examples, the `DisplayBufferToConsole` method only reads from the buffer; it doesn't modify the contents of the buffer.</span></span> <span data-ttu-id="e726a-190">Signatura metody by se měla změnit na následující.</span><span class="sxs-lookup"><span data-stu-id="e726a-190">The method signature should be changed to the following.</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

<span data-ttu-id="e726a-191">V případě, že toto pravidlo a pravidlo kombinujeme #1, můžeme ještě lepší a přepsat signaturu metody následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e726a-191">In fact, if we combine this rule and Rule #1, we can do even better and rewrite the method signature as follows:</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

<span data-ttu-id="e726a-192">`DisplayBufferToConsole`Metoda teď funguje s prakticky všemi typy vyrovnávací paměti, které lze `T[]` předcházet:, úložiště přidělené [stackalloc](../../csharp/language-reference/operators/stackalloc.md)a tak dále.</span><span class="sxs-lookup"><span data-stu-id="e726a-192">The `DisplayBufferToConsole` method now works with virtually every buffer type imaginable: `T[]`, storage allocated with [stackalloc](../../csharp/language-reference/operators/stackalloc.md), and so on.</span></span> <span data-ttu-id="e726a-193">Můžete dokonce předat <xref:System.String> přímo na!</span><span class="sxs-lookup"><span data-stu-id="e726a-193">You can even pass a <xref:System.String> directly into it!</span></span>

<span data-ttu-id="e726a-194">**#3 pravidla: Pokud vaše metoda přijímá paměť \<T> a vrací `void` , nemusíte \<T> po návratu metody použít instanci paměti.**</span><span class="sxs-lookup"><span data-stu-id="e726a-194">**Rule #3: If your method accepts Memory\<T> and returns `void`, you must not use the Memory\<T> instance after your method returns.**</span></span>

<span data-ttu-id="e726a-195">To se týká konceptu zapůjčení uvedeného výše.</span><span class="sxs-lookup"><span data-stu-id="e726a-195">This relates to the "lease" concept mentioned earlier.</span></span> <span data-ttu-id="e726a-196">Zapůjčení metody vracející anulování <xref:System.Memory%601> instance začíná při zadání metody a končí při ukončení metody.</span><span class="sxs-lookup"><span data-stu-id="e726a-196">A void-returning method's lease on the <xref:System.Memory%601> instance begins when the method is entered, and it ends when the method exits.</span></span> <span data-ttu-id="e726a-197">Vezměte v úvahu následující příklad, který volá `Log` smyčku na základě vstupu z konzoly.</span><span class="sxs-lookup"><span data-stu-id="e726a-197">Consider the following example, which calls `Log` in a loop based on input from the console.</span></span>

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

<span data-ttu-id="e726a-198">Pokud `Log` je plně synchronní metodou, bude tento kód fungovat podle očekávání, protože v daném okamžiku existuje pouze jeden aktivní spotřebitel instance paměti.</span><span class="sxs-lookup"><span data-stu-id="e726a-198">If `Log` is a fully synchronous method, this code will behave as expected because there is only one active consumer of the memory instance at any given time.</span></span>
<span data-ttu-id="e726a-199">Ale představte si, že `Log` Tato implementace má tuto implementaci.</span><span class="sxs-lookup"><span data-stu-id="e726a-199">But imagine instead that `Log` has this implementation.</span></span>

```csharp
// !!! INCORRECT IMPLEMENTATION !!!
static void Log(ReadOnlyMemory<char> message)
{
    // Run in background so that we don't block the main thread while performing IO.
    Task.Run(() =>
    {
        StreamWriter sw = File.AppendText(@".\input-numbers.dat");
        sw.WriteLine(message);
    });
}
```

<span data-ttu-id="e726a-200">V této implementaci `Log` porušuje své zapůjčení, protože se stále pokouší použít <xref:System.Memory%601> instanci na pozadí po vrácení původní metody.</span><span class="sxs-lookup"><span data-stu-id="e726a-200">In this implementation, `Log` violates its lease because it still attempts to use the <xref:System.Memory%601> instance in the background after the original method has returned.</span></span> <span data-ttu-id="e726a-201">`Main`Metoda by mohla při `Log` pokusech o čtení z ní načítat vyrovnávací paměť, což by mohlo vést k poškození dat.</span><span class="sxs-lookup"><span data-stu-id="e726a-201">The `Main` method could mutate the buffer while `Log` attempts to read from it, which could result in data corruption.</span></span>

<span data-ttu-id="e726a-202">Tuto chybu lze vyřešit několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="e726a-202">There are several ways to resolve this:</span></span>

- <span data-ttu-id="e726a-203">`Log`Metoda může vracet <xref:System.Threading.Tasks.Task> namísto `void` , jako následující implementace `Log` metody.</span><span class="sxs-lookup"><span data-stu-id="e726a-203">The `Log` method can return a <xref:System.Threading.Tasks.Task> instead of `void`, as the following implementation of the `Log` method does.</span></span>

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- <span data-ttu-id="e726a-204">`Log`místo toho je možné implementovat následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e726a-204">`Log` can instead be implemented as follows:</span></span>

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

<span data-ttu-id="e726a-205">**#4 pravidla: Pokud vaše metoda přijímá paměť \<T> a vrátí úlohu, \<T> po přechodu úlohy do stavu terminálu nemusíte instanci paměti používat.**</span><span class="sxs-lookup"><span data-stu-id="e726a-205">**Rule #4: If your method accepts a Memory\<T> and returns a Task, you must not use the Memory\<T> instance after the Task transitions to a terminal state.**</span></span>

<span data-ttu-id="e726a-206">Toto je pouze asynchronní varianta pravidla #3.</span><span class="sxs-lookup"><span data-stu-id="e726a-206">This is just the async variant of Rule #3.</span></span> <span data-ttu-id="e726a-207">`Log`Metodu z předchozího příkladu můžete zapsat takto, aby splňovala toto pravidlo:</span><span class="sxs-lookup"><span data-stu-id="e726a-207">The `Log` method from the earlier example can be written as follows to comply with this rule:</span></span>

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

<span data-ttu-id="e726a-208">V tomto případě "stav terminálu" znamená, že se úloha přechází do stavu dokončeno, chyba nebo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="e726a-208">Here, "terminal state" means that the task transitions to a completed, faulted, or canceled state.</span></span> <span data-ttu-id="e726a-209">Jinými slovy "Terminal State" znamená "cokoli, co by způsobilo, že se očekává, že se má vyvolávat nebo pokračovat v provádění."</span><span class="sxs-lookup"><span data-stu-id="e726a-209">In other words, "terminal state" means "anything that would cause await to throw or to continue execution."</span></span>

<span data-ttu-id="e726a-210">Tento návod se vztahuje na metody, které vracejí <xref:System.Threading.Tasks.Task> , <xref:System.Threading.Tasks.Task%601> , <xref:System.Threading.Tasks.ValueTask%601> nebo podobného typu.</span><span class="sxs-lookup"><span data-stu-id="e726a-210">This guidance applies to methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>, or any similar type.</span></span>

<span data-ttu-id="e726a-211">**#5 pravidla: Pokud váš konstruktor přijímá paměť \<T> jako parametr, předpokládá se, že metody instance u vytvořeného objektu budou spotřebiteli instance paměti \<T> .**</span><span class="sxs-lookup"><span data-stu-id="e726a-211">**Rule #5: If your constructor accepts Memory\<T> as a parameter, instance methods on the constructed object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="e726a-212">Uvažujte následující příklad:</span><span class="sxs-lookup"><span data-stu-id="e726a-212">Consider the following example:</span></span>

```csharp
class OddValueExtractor
{
    public OddValueExtractor(ReadOnlyMemory<int> input);
    public bool TryReadNextOddValue(out int value);
}

void PrintAllOddValues(ReadOnlyMemory<int> input)
{
    var extractor = new OddValueExtractor(input);
    while (extractor.TryReadNextOddValue(out int value))
    {
      Console.WriteLine(value);
    }
}
```

<span data-ttu-id="e726a-213">V tomto případě `OddValueExtractor` konstruktor přijímá `ReadOnlyMemory<int>` jako parametr konstruktoru, takže samotný konstruktor je příjemcem `ReadOnlyMemory<int>` instance a všechny metody instance vrácené hodnoty jsou také příjemci původní `ReadOnlyMemory<int>` instance.</span><span class="sxs-lookup"><span data-stu-id="e726a-213">Here, the `OddValueExtractor` constructor accepts a `ReadOnlyMemory<int>` as a constructor parameter, so the constructor itself is a consumer of the `ReadOnlyMemory<int>` instance, and all instance methods on the returned value are also consumers of the original `ReadOnlyMemory<int>` instance.</span></span> <span data-ttu-id="e726a-214">To znamená, že `TryReadNextOddValue` instance spotřebovává `ReadOnlyMemory<int>` , i když instance není předána přímo `TryReadNextOddValue` metodě.</span><span class="sxs-lookup"><span data-stu-id="e726a-214">This means that `TryReadNextOddValue` consumes the `ReadOnlyMemory<int>` instance, even though the instance isn't passed directly to the `TryReadNextOddValue` method.</span></span>

<span data-ttu-id="e726a-215">**#6 pravidla: Pokud máte na svém typu nastavitelnou vlastnost typu paměti \<T> (nebo ekvivalentní metodu instance), předpokládá se, že metody instance tohoto objektu budou spotřebiteli \<T> instance paměti.**</span><span class="sxs-lookup"><span data-stu-id="e726a-215">**Rule #6: If you have a settable Memory\<T>-typed property (or an equivalent instance method) on your type, instance methods on that object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="e726a-216">Toto je opravdu pouze varianta pravidla #5.</span><span class="sxs-lookup"><span data-stu-id="e726a-216">This is really just a variant of Rule #5.</span></span> <span data-ttu-id="e726a-217">Toto pravidlo existuje, protože metody setter nebo ekvivalentní metody jsou považovány za zachycení a uchování jejich vstupů, takže metody instance u stejného objektu mohou využívat zachycený stav.</span><span class="sxs-lookup"><span data-stu-id="e726a-217">This rule exists because property setters or equivalent methods are assumed to capture and persist their inputs, so instance methods on the same object may utilize the captured state.</span></span>

<span data-ttu-id="e726a-218">Toto pravidlo se spustí v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e726a-218">The following example triggers this rule:</span></span>

```csharp
class Person
{
    // Settable property.
    public Memory<char> FirstName { get; set; }

    // alternatively, equivalent "setter" method
    public SetFirstName(Memory<char> value);

    // alternatively, a public settable field
    public Memory<char> FirstName;
}
```

<span data-ttu-id="e726a-219">**#7 pravidla: Pokud máte \<T> odkaz IMemoryOwner, je potřeba, abyste ho odstranili nebo přenesli jeho vlastnictví (ale ne obojí).**</span><span class="sxs-lookup"><span data-stu-id="e726a-219">**Rule #7: If you have an IMemoryOwner\<T> reference, you must at some point dispose of it or transfer its ownership (but not both).**</span></span>

<span data-ttu-id="e726a-220">Vzhledem k <xref:System.Memory%601> tomu, že instance může být zajištěna buď spravovanou, nebo nespravovanou pamětí, musí vlastník zavolat, <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> až bude dokončena práce na <xref:System.Memory%601> instanci.</span><span class="sxs-lookup"><span data-stu-id="e726a-220">Since a <xref:System.Memory%601> instance may be backed by either managed or unmanaged memory, the owner must call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> when work performed on the <xref:System.Memory%601> instance is complete.</span></span> <span data-ttu-id="e726a-221">Alternativně může vlastník přenést vlastnictví <xref:System.Buffers.IMemoryOwner%601> instance na jinou komponentu. v takovém případě se součást získání bude zodpovědná za volání <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> v příslušné době (Další informace najdete později).</span><span class="sxs-lookup"><span data-stu-id="e726a-221">Alternatively, the owner may transfer ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component, at which point the acquiring component becomes responsible for calling <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> at the appropriate time (more on this later).</span></span>

<span data-ttu-id="e726a-222">Nepodaří-li se zavolat <xref:System.Buffers.MemoryPool%601.Dispose%2A> metodu, může dojít k nevrácení nespravované paměti nebo jinému snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="e726a-222">Failure to call the <xref:System.Buffers.MemoryPool%601.Dispose%2A> method may lead to unmanaged memory leaks or other performance degradation.</span></span>

<span data-ttu-id="e726a-223">Toto pravidlo platí také pro kód, který volá metody objektu pro vytváření, jako je <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e726a-223">This rule also applies to code that calls factory methods like <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="e726a-224">Volající se stane vlastníkem vráceného <xref:System.Buffers.IMemoryOwner%601> a zodpovídá za odstranění instance po dokončení.</span><span class="sxs-lookup"><span data-stu-id="e726a-224">The caller becomes the owner of the returned <xref:System.Buffers.IMemoryOwner%601> and is responsible for disposing of the instance when finished.</span></span>

<span data-ttu-id="e726a-225">**#8 pravidla: Pokud máte \<T> na ploše rozhraní API parametr IMemoryOwner, přijímáte vlastnictví této instance.**</span><span class="sxs-lookup"><span data-stu-id="e726a-225">**Rule #8: If you have an IMemoryOwner\<T> parameter in your API surface, you are accepting ownership of that instance.**</span></span>

<span data-ttu-id="e726a-226">Přijetí instance tohoto typu signalizuje, že vaše komponenta zamýšlí převzít vlastnictví této instance.</span><span class="sxs-lookup"><span data-stu-id="e726a-226">Accepting an instance of this type signals that your component intends to take ownership of this instance.</span></span> <span data-ttu-id="e726a-227">Vaše komponenta se bude zodpovědná za řádné vyřazení podle pravidla #7.</span><span class="sxs-lookup"><span data-stu-id="e726a-227">Your component becomes responsible for proper disposal according to Rule #7.</span></span>

<span data-ttu-id="e726a-228">Jakákoli komponenta, která přenáší vlastnictví <xref:System.Buffers.IMemoryOwner%601> instance do jiné komponenty, by již neměla používat tuto instanci po dokončení volání metody.</span><span class="sxs-lookup"><span data-stu-id="e726a-228">Any component that transfers ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component should no longer use that instance after the method call completes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e726a-229">Pokud váš konstruktor přijímá <xref:System.Buffers.IMemoryOwner%601> jako parametr, jeho typ by měl implementovat <xref:System.IDisposable> a vaše <xref:System.IDisposable.Dispose%2A> Metoda by měla volat <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="e726a-229">If your constructor accepts <xref:System.Buffers.IMemoryOwner%601> as a parameter, its type should implement <xref:System.IDisposable>, and your <xref:System.IDisposable.Dispose%2A> method should call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="e726a-230">**#9 pravidla: Pokud zabalíte synchronní metodu volání nespravovaného volání, rozhraní API by mělo přijmout \<T> jako parametr.**</span><span class="sxs-lookup"><span data-stu-id="e726a-230">**Rule #9: If you're wrapping a synchronous p/invoke method, your API should accept Span\<T> as a parameter.**</span></span>

<span data-ttu-id="e726a-231">V souladu s pravidly #1 <xref:System.Span%601> je všeobecně správný typ, který se má použít pro synchronní rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="e726a-231">According to Rule #1, <xref:System.Span%601> is generally the correct type to use for synchronous APIs.</span></span> <span data-ttu-id="e726a-232">Instance můžete připnout <xref:System.Span%601> prostřednictvím [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) klíčového slova, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e726a-232">You can pin <xref:System.Span%601> instances via the [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) keyword, as in the following example.</span></span>

```csharp
using System.Runtime.InteropServices;

[DllImport(...)]
private static extern unsafe int ExportedMethod(byte* pbData, int cbData);

public unsafe int ManagedWrapper(Span<byte> data)
{
    fixed (byte* pbData = &MemoryMarshal.GetReference(data))
    {
        int retVal = ExportedMethod(pbData, data.Length);

        /* error checking retVal goes here */

        return retVal;
    }
}
```

<span data-ttu-id="e726a-233">V předchozím příkladu `pbData` může mít hodnotu null, pokud je například vstupní rozpětí prázdné.</span><span class="sxs-lookup"><span data-stu-id="e726a-233">In the previous example, `pbData` can be null if, for example, the input span is empty.</span></span> <span data-ttu-id="e726a-234">Pokud exportovaná metoda naprosto vyžaduje, aby `pbData` byla nenulová, i když `cbData` je hodnota 0, metoda může být implementována takto:</span><span class="sxs-lookup"><span data-stu-id="e726a-234">If the exported method absolutely requires that `pbData` be non-null, even if `cbData` is 0, the method can be implemented as follows:</span></span>

```csharp
public unsafe int ManagedWrapper(Span<byte> data)
{
    fixed (byte* pbData = &MemoryMarshal.GetReference(data))
    {
        byte dummy = 0;
        int retVal = ExportedMethod((pbData != null) ? pbData : &dummy, data.Length);

        /* error checking retVal goes here */

        return retVal;
    }
}
```

<span data-ttu-id="e726a-235">**#10 pravidla: Pokud zabalíte asynchronní metodu volání metody p/Invoke, rozhraní API by mělo přijmout paměť \<T> jako parametr.**</span><span class="sxs-lookup"><span data-stu-id="e726a-235">**Rule #10: If you're wrapping an asynchronous p/invoke method, your API should accept Memory\<T> as a parameter.**</span></span>

<span data-ttu-id="e726a-236">Vzhledem k tomu, že nelze použít [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) klíčové slovo v rámci asynchronních operací, použijte <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> metodu pro připnutí <xref:System.Memory%601> instancí bez ohledu na druh souvislé paměti, kterou instance představuje.</span><span class="sxs-lookup"><span data-stu-id="e726a-236">Since you cannot use the [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) keyword across asynchronous operations, you use the <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> method to pin <xref:System.Memory%601> instances, regardless of the kind of contiguous memory the instance represents.</span></span> <span data-ttu-id="e726a-237">Následující příklad ukazuje, jak použít toto rozhraní API k provedení asynchronního volání volání nespravovaného volání.</span><span class="sxs-lookup"><span data-stu-id="e726a-237">The following example shows how to use this API to perform an asynchronous p/invoke call.</span></span>

```csharp
using System.Runtime.InteropServices;

[UnmanagedFunctionPointer(...)]
private delegate void OnCompletedCallback(IntPtr state, int result);

[DllImport(...)]
private static extern unsafe int ExportedAsyncMethod(byte* pbData, int cbData, IntPtr pState, IntPtr lpfnOnCompletedCallback);

private static readonly IntPtr _callbackPtr = GetCompletionCallbackPointer();

public unsafe Task<int> ManagedWrapperAsync(Memory<byte> data)
{
    // setup
    var tcs = new TaskCompletionSource<int>();
    var state = new MyCompletedCallbackState
    {
        Tcs = tcs
    };
    var pState = (IntPtr)GCHandle.Alloc(state);

    var memoryHandle = data.Pin();
    state.MemoryHandle = memoryHandle;

    // make the call
    int result;
    try
    {
        result = ExportedAsyncMethod((byte*)memoryHandle.Pointer, data.Length, pState, _callbackPtr);
    }
    catch
    {
        ((GCHandle)pState).Free(); // cleanup since callback won't be invoked
        memoryHandle.Dispose();
        throw;
    }

    if (result != PENDING)
    {
        // Operation completed synchronously; invoke callback manually
        // for result processing and cleanup.
        MyCompletedCallbackImplementation(pState, result);
    }

    return tcs.Task;
}

private static void MyCompletedCallbackImplementation(IntPtr state, int result)
{
    GCHandle handle = (GCHandle)state;
    var actualState = (MyCompletedCallbackState)(handle.Target);
    handle.Free();
    actualState.MemoryHandle.Dispose();

    /* error checking result goes here */

    if (error)
    {
        actualState.Tcs.SetException(...);
    }
    else
    {
        actualState.Tcs.SetResult(result);
    }
}

private static IntPtr GetCompletionCallbackPointer()
{
    OnCompletedCallback callback = MyCompletedCallbackImplementation;
    GCHandle.Alloc(callback); // keep alive for lifetime of application
    return Marshal.GetFunctionPointerForDelegate(callback);
}

private class MyCompletedCallbackState
{
    public TaskCompletionSource<int> Tcs;
    public MemoryHandle MemoryHandle;
}
```

## <a name="see-also"></a><span data-ttu-id="e726a-238">Viz také</span><span class="sxs-lookup"><span data-stu-id="e726a-238">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
