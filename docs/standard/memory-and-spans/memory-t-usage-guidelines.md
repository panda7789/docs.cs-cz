---
title: Pokyny k používání Memory<T> a Span<T>
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
ms.openlocfilehash: 0a614f628faa98be778c627573e4dddc462c9107
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73121964"
---
# <a name="memoryt-and-spant-usage-guidelines"></a><span data-ttu-id="d2449-102">Pokyny k používání Memory\<T> a Span\<T></span><span class="sxs-lookup"><span data-stu-id="d2449-102">Memory\<T> and Span\<T> usage guidelines</span></span>

<span data-ttu-id="d2449-103">Jádro .NET obsahuje řadu typů, které představují libovolnou souvislou oblast paměti.</span><span class="sxs-lookup"><span data-stu-id="d2449-103">.NET Core includes a number of types that represent an arbitrary contiguous region of memory.</span></span> <span data-ttu-id="d2449-104">.NET Core 2.0 <xref:System.Span%601> <xref:System.ReadOnlySpan%601>zavedena a , které jsou zjednodušené vyrovnávací paměti, které mohou být zálohovány spravované nebo nespravované paměti.</span><span class="sxs-lookup"><span data-stu-id="d2449-104">.NET Core 2.0 introduced <xref:System.Span%601> and <xref:System.ReadOnlySpan%601>, which are lightweight memory buffers that can be backed by managed or unmanaged memory.</span></span> <span data-ttu-id="d2449-105">Vzhledem k tomu, že tyto typy mohou být uloženy pouze v zásobníku, jsou nevhodné pro řadu scénářů, včetně volání asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="d2449-105">Because these types can only be stored on the stack, they are unsuitable for a number of scenarios, including asynchronous method calls.</span></span> <span data-ttu-id="d2449-106">.NET Core 2.1 přidává řadu dalších <xref:System.ReadOnlyMemory%601> <xref:System.Buffers.IMemoryOwner%601>typů, <xref:System.Buffers.MemoryPool%601>včetně <xref:System.Memory%601>, , a .</span><span class="sxs-lookup"><span data-stu-id="d2449-106">.NET Core 2.1 adds a number of additional types, including <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>, and <xref:System.Buffers.MemoryPool%601>.</span></span> <span data-ttu-id="d2449-107">Stejně jako <xref:System.Span%601>a <xref:System.Memory%601> jeho související typy mohou být zálohovány spravovanou i nespravovanou pamětí.</span><span class="sxs-lookup"><span data-stu-id="d2449-107">Like <xref:System.Span%601>, <xref:System.Memory%601> and its related types can be backed by both managed and unmanaged memory.</span></span> <span data-ttu-id="d2449-108">Na <xref:System.Span%601> <xref:System.Memory%601> rozdíl od , mohou být uloženy na spravované haldy.</span><span class="sxs-lookup"><span data-stu-id="d2449-108">Unlike <xref:System.Span%601>, <xref:System.Memory%601> can be stored on the managed heap.</span></span>

<span data-ttu-id="d2449-109">Obě <xref:System.Span%601> <xref:System.Memory%601> a jsou vyrovnávací paměti strukturovaných dat, které lze použít v kanálech.</span><span class="sxs-lookup"><span data-stu-id="d2449-109">Both <xref:System.Span%601> and <xref:System.Memory%601> are buffers of structured data that can be used in pipelines.</span></span> <span data-ttu-id="d2449-110">To znamená, že jsou navrženy tak, aby některá nebo všechna data mohla být efektivně předána součástem v kanálu, které je mohou zpracovat a volitelně upravit vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="d2449-110">That is, they are designed so that some or all of the data can be efficiently passed to components in the pipeline, which can process them and optionally modify the buffer.</span></span> <span data-ttu-id="d2449-111">Vzhledem k tomu, <xref:System.Memory%601> že a jeho související typy jsou přístupné více komponent nebo více vláken, je důležité, aby vývojáři dodržovat některé standardní pokyny pro použití k výrobě robustní kód.</span><span class="sxs-lookup"><span data-stu-id="d2449-111">Because <xref:System.Memory%601> and its related types can be accessed by multiple components or by multiple threads, it's important that developers follow some standard usage guidelines to produce robust code.</span></span>

## <a name="owners-consumers-and-lifetime-management"></a><span data-ttu-id="d2449-112">Vlastníci, spotřebitelé a celoživotní správa</span><span class="sxs-lookup"><span data-stu-id="d2449-112">Owners, consumers, and lifetime management</span></span>

<span data-ttu-id="d2449-113">Vzhledem k tomu, že vyrovnávací paměti mohou být předány mezi rozhraními API a protože vyrovnávací paměti lze někdy přistupovat z více vláken, je důležité zvážit správu životnosti.</span><span class="sxs-lookup"><span data-stu-id="d2449-113">Since buffers can be passed around between APIs, and since buffers can sometimes be accessed from multiple threads, it's important to consider lifetime management.</span></span> <span data-ttu-id="d2449-114">Existují tři základní pojmy:</span><span class="sxs-lookup"><span data-stu-id="d2449-114">There are three core concepts:</span></span>

- <span data-ttu-id="d2449-115">**Vlastnictví**.</span><span class="sxs-lookup"><span data-stu-id="d2449-115">**Ownership**.</span></span> <span data-ttu-id="d2449-116">Vlastník instance vyrovnávací paměti je zodpovědný za správu životnosti, včetně zničení vyrovnávací paměti, když se již nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="d2449-116">The owner of a buffer instance is responsible for lifetime management, including destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="d2449-117">Všechny vyrovnávací paměti mají jednoho vlastníka.</span><span class="sxs-lookup"><span data-stu-id="d2449-117">All buffers have a single owner.</span></span> <span data-ttu-id="d2449-118">Obecně vlastník je součást, která vytvořila vyrovnávací paměť nebo která obdržela vyrovnávací paměť z továrny.</span><span class="sxs-lookup"><span data-stu-id="d2449-118">Generally the owner is the component that created the buffer or that received the buffer from a factory.</span></span> <span data-ttu-id="d2449-119">Vlastnictví může být také převedeno; **Komponenta A** můžete vzdát řízení vyrovnávací paměti **komponenty B**, na kterém místě **Component-A** již nemusí používat vyrovnávací paměť a **Component-B** se stane zodpovědný za zničení vyrovnávací paměti, když je již používán.</span><span class="sxs-lookup"><span data-stu-id="d2449-119">Ownership can also be transferred; **Component-A** can relinquish control of the buffer to **Component-B**, at which point **Component-A** may no longer use the buffer, and **Component-B** becomes responsible for destroying the buffer when it's no longer in use.</span></span>

- <span data-ttu-id="d2449-120">**Spotřeba**.</span><span class="sxs-lookup"><span data-stu-id="d2449-120">**Consumption**.</span></span> <span data-ttu-id="d2449-121">Příjemce instance vyrovnávací paměti je povoleno použít instanci vyrovnávací paměti čtením z ní a případně zápis do něj.</span><span class="sxs-lookup"><span data-stu-id="d2449-121">The consumer of a buffer instance is allowed to use the buffer instance by reading from it and possibly writing to it.</span></span> <span data-ttu-id="d2449-122">Vyrovnávací paměti mohou mít jednoho příjemce najednou, pokud není k dispozici nějaký mechanismus externí synchronizace.</span><span class="sxs-lookup"><span data-stu-id="d2449-122">Buffers can have one consumer at a time unless some external synchronization mechanism is provided.</span></span> <span data-ttu-id="d2449-123">Všimněte si, že aktivní příjemce vyrovnávací paměti není nutně vlastníkem vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d2449-123">Note that the active consumer of a buffer isn't necessarily the buffer's owner.</span></span>

- <span data-ttu-id="d2449-124">**Pronájem**.</span><span class="sxs-lookup"><span data-stu-id="d2449-124">**Lease**.</span></span> <span data-ttu-id="d2449-125">Zapůjčení je doba, po kterou může být určitá součást příjemcem vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d2449-125">The lease is the length of time that a particular component is allowed to be the consumer of the buffer.</span></span>

<span data-ttu-id="d2449-126">Následující příklad pseudokódu ilustruje tyto tři koncepty.</span><span class="sxs-lookup"><span data-stu-id="d2449-126">The following pseudo-code example illustrates these three concepts.</span></span> <span data-ttu-id="d2449-127">Obsahuje metodu, `Main` která inkonaluje <xref:System.Memory%601> vyrovnávací paměť typu <xref:System.Char>, volá metodu `WriteInt32ToBuffer` pro zápis řetězcové `DisplayBufferToConsole` reprezentace celého čísla do vyrovnávací paměti a pak volá metodu k zobrazení hodnoty vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d2449-127">It includes a `Main` method that instantiates a <xref:System.Memory%601> buffer of type <xref:System.Char>, calls the `WriteInt32ToBuffer` method to write the string representation of an integer to the buffer, and then calls the `DisplayBufferToConsole` method to display the value of the buffer.</span></span>

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

<span data-ttu-id="d2449-128">Metoda `Main` vytvoří vyrovnávací paměť (v <xref:System.Span%601> tomto případě instanci) a tak je jeho vlastníkem.</span><span class="sxs-lookup"><span data-stu-id="d2449-128">The `Main` method creates the buffer (in this case an <xref:System.Span%601> instance) and so is its owner.</span></span> <span data-ttu-id="d2449-129">Proto `Main` je zodpovědný za zničení vyrovnávací paměti, když již není používán.</span><span class="sxs-lookup"><span data-stu-id="d2449-129">Therefore, `Main` is responsible for destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="d2449-130">To provádí voláním <xref:System.Span%601.Clear?displayProperty=nameWithType> metody vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d2449-130">It does this by calling the buffer's <xref:System.Span%601.Clear?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="d2449-131">(Metoda <xref:System.Span%601.Clear> zde ve skutečnosti vymaže <xref:System.Span%601> vyrovnávací paměti; struktura ve skutečnosti nemá metodu, která ničí vyrovnávací paměť.)</span><span class="sxs-lookup"><span data-stu-id="d2449-131">(The <xref:System.Span%601.Clear> method here actually clears the buffer's memory; the <xref:System.Span%601> structure doesn't actually have a method that destroys the buffer.)</span></span>

<span data-ttu-id="d2449-132">Vyrovnávací paměť má `WriteInt32ToBuffer` dva `DisplayBufferToConsole`spotřebitele a .</span><span class="sxs-lookup"><span data-stu-id="d2449-132">The buffer has two consumers, `WriteInt32ToBuffer` and `DisplayBufferToConsole`.</span></span> <span data-ttu-id="d2449-133">Existuje pouze jeden spotřebitel najednou `WriteInt32ToBuffer`(první `DisplayBufferToConsole`, pak ) a ani jeden ze spotřebitelů vlastní vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="d2449-133">There is only one consumer at a time (first `WriteInt32ToBuffer`, then `DisplayBufferToConsole`), and neither of the consumers owns the buffer.</span></span> <span data-ttu-id="d2449-134">Všimněte si také, že "spotřebitel" v tomto kontextu neznamená zobrazení vyrovnávací paměti jen pro čtení; spotřebitelé můžete upravit obsah vyrovnávací `WriteInt32ToBuffer` paměti, stejně jako, pokud dané čtení a zápis zobrazení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d2449-134">Note also that "consumer" in this context doesn't imply a read-only view of the buffer; consumers can modify the buffer's contents, as `WriteInt32ToBuffer` does, if given a read/write view of the buffer.</span></span>

<span data-ttu-id="d2449-135">Metoda `WriteInt32ToBuffer` má zapůjčení (může spotřebovat) vyrovnávací paměť mezi začátkem volání metody a časem, kdy metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="d2449-135">The `WriteInt32ToBuffer` method has a lease on (can consume) the buffer between the start of the method call and the time the method returns.</span></span> <span data-ttu-id="d2449-136">Podobně `DisplayBufferToConsole` má zapůjčení na vyrovnávací paměti při provádění a zapůjčení je uvolněna při uvolnění metody.</span><span class="sxs-lookup"><span data-stu-id="d2449-136">Similarly, `DisplayBufferToConsole` has a lease on the buffer while it's executing, and the lease is released when the method unwinds.</span></span> <span data-ttu-id="d2449-137">(Neexistuje žádné rozhraní API pro správu zapůjčení; "zapůjčení" je koncepční záležitost.)</span><span class="sxs-lookup"><span data-stu-id="d2449-137">(There is no API for lease management; a "lease" is a conceptual matter.)</span></span>

## <a name="memoryt-and-the-ownerconsumer-model"></a><span data-ttu-id="d2449-138">Paměť\<T> a model vlastníka/spotřebitele</span><span class="sxs-lookup"><span data-stu-id="d2449-138">Memory\<T> and the owner/consumer model</span></span>

<span data-ttu-id="d2449-139">Jako [vlastníci, spotřebitelé a část správy životnosti](#owners-consumers-and-lifetime-management) poznámky, vyrovnávací paměť má vždy vlastníka.</span><span class="sxs-lookup"><span data-stu-id="d2449-139">As the [Owners, consumers, and lifetime management](#owners-consumers-and-lifetime-management) section notes, a buffer always has an owner.</span></span> <span data-ttu-id="d2449-140">.NET Core podporuje dva modely vlastnictví:</span><span class="sxs-lookup"><span data-stu-id="d2449-140">.NET Core supports two ownership models:</span></span>

- <span data-ttu-id="d2449-141">Model, který podporuje jedno vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="d2449-141">A model that supports single ownership.</span></span> <span data-ttu-id="d2449-142">Vyrovnávací paměť má jednoho vlastníka po celou dobu jeho životnosti.</span><span class="sxs-lookup"><span data-stu-id="d2449-142">A buffer has a single owner for its entire lifetime.</span></span>

- <span data-ttu-id="d2449-143">Model, který podporuje převod vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="d2449-143">A model that supports ownership transfer.</span></span> <span data-ttu-id="d2449-144">Vlastnictví vyrovnávací paměti lze převést z původního vlastníka (jeho tvůrce) do jiné součásti, která se pak stane zodpovědností za správu životnosti vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d2449-144">Ownership of a buffer can be transferred from its original owner (its creator) to another component, which then becomes responsible for the buffer's lifetime management.</span></span> <span data-ttu-id="d2449-145">Tento vlastník může zase převést vlastnictví na jinou součást a tak dále.</span><span class="sxs-lookup"><span data-stu-id="d2449-145">That owner can in turn transfer ownership to another component, and so on.</span></span>

<span data-ttu-id="d2449-146">Rozhraní slouží <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> k explicitní správě vlastnictví vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d2449-146">You use the <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> interface to explicitly manage the ownership of a buffer.</span></span> <span data-ttu-id="d2449-147"><xref:System.Buffers.IMemoryOwner%601>podporuje oba modely vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="d2449-147"><xref:System.Buffers.IMemoryOwner%601> supports both ownership models.</span></span> <span data-ttu-id="d2449-148">Součást, která <xref:System.Buffers.IMemoryOwner%601> má odkaz vlastní vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="d2449-148">The component that has an <xref:System.Buffers.IMemoryOwner%601> reference owns the buffer.</span></span> <span data-ttu-id="d2449-149">Následující příklad používá <xref:System.Buffers.IMemoryOwner%601?> instanci tak, <xref:System.Memory%601> aby odrážela vlastnictví vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d2449-149">The following example uses an <xref:System.Buffers.IMemoryOwner%601?> instance to reflect the ownership of an <xref:System.Memory%601> buffer.</span></span>

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

<span data-ttu-id="d2449-150">Můžeme také napsat tento [`using`](../../csharp/language-reference/keywords/using-statement.md)příklad s :</span><span class="sxs-lookup"><span data-stu-id="d2449-150">We can also write this example with the [`using`](../../csharp/language-reference/keywords/using-statement.md):</span></span>

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

<span data-ttu-id="d2449-151">V tomto kódu:</span><span class="sxs-lookup"><span data-stu-id="d2449-151">In this code:</span></span>

- <span data-ttu-id="d2449-152">Metoda `Main` obsahuje odkaz na <xref:System.Buffers.IMemoryOwner%601> instanci, takže `Main` metoda je vlastníkem vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d2449-152">The `Main` method holds the reference to the <xref:System.Buffers.IMemoryOwner%601> instance, so the `Main` method is the owner of the buffer.</span></span>

- <span data-ttu-id="d2449-153">Metody `WriteInt32ToBuffer` `DisplayBufferToConsole` a <xref:System.Memory%601> přijmout jako veřejné rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="d2449-153">The `WriteInt32ToBuffer` and `DisplayBufferToConsole` methods accept <xref:System.Memory%601> as a public API.</span></span> <span data-ttu-id="d2449-154">Proto jsou příjemci vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d2449-154">Therefore, they are consumers of the buffer.</span></span> <span data-ttu-id="d2449-155">A konzumují ho jen jednoho po druhém.</span><span class="sxs-lookup"><span data-stu-id="d2449-155">And they only consume it one at a time.</span></span>

<span data-ttu-id="d2449-156">Přestože `WriteInt32ToBuffer` metoda je určena k zápisu `DisplayBufferToConsole` hodnoty do vyrovnávací paměti, metoda není.</span><span class="sxs-lookup"><span data-stu-id="d2449-156">Although the `WriteInt32ToBuffer` method is intended to write a value to the buffer, the `DisplayBufferToConsole` method isn't.</span></span> <span data-ttu-id="d2449-157">Aby to toto bylo možné, <xref:System.ReadOnlyMemory%601>mohla přijmout argument typu .</span><span class="sxs-lookup"><span data-stu-id="d2449-157">To reflect this, it could have accepted an argument of type <xref:System.ReadOnlyMemory%601>.</span></span> <span data-ttu-id="d2449-158">Další informace <xref:System.ReadOnlyMemory%601>o tématu [naleznete v tématu rule #2: Use ReadOnlySpan\<T> nebo ReadOnlyMemory\<T> pokud by vyrovnávací paměť měla být jen pro čtení](#rule-2).</span><span class="sxs-lookup"><span data-stu-id="d2449-158">For additional information on <xref:System.ReadOnlyMemory%601>, see [Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only](#rule-2).</span></span>

### <a name="ownerless-memoryt-instances"></a><span data-ttu-id="d2449-159">"Ownerless"\<Memory T> instance</span><span class="sxs-lookup"><span data-stu-id="d2449-159">"Ownerless" Memory\<T> instances</span></span>

<span data-ttu-id="d2449-160">Instanci <xref:System.Memory%601> můžete vytvořit <xref:System.Buffers.IMemoryOwner%601>bez použití aplikace .</span><span class="sxs-lookup"><span data-stu-id="d2449-160">You can create a <xref:System.Memory%601> instance without using <xref:System.Buffers.IMemoryOwner%601>.</span></span> <span data-ttu-id="d2449-161">V tomto případě vlastnictví vyrovnávací paměti je implicitní spíše než explicitní a je podporován pouze model jednoho vlastníka.</span><span class="sxs-lookup"><span data-stu-id="d2449-161">In this case, ownership of the buffer is implicit rather than explicit, and only the single-owner model is supported.</span></span> <span data-ttu-id="d2449-162">Můžete to udělat takto:</span><span class="sxs-lookup"><span data-stu-id="d2449-162">You can do this by:</span></span>

- <span data-ttu-id="d2449-163">Volání jednoho <xref:System.Memory%601> z konstruktorů přímo, `T[]`předávání v , jako následující příklad.</span><span class="sxs-lookup"><span data-stu-id="d2449-163">Calling one of the  <xref:System.Memory%601> constructors directly, passing in a `T[]`, as the following example does.</span></span>

- <span data-ttu-id="d2449-164">Volání [string.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) metoda rozšíření `ReadOnlyMemory<char>` k vytvoření instance.</span><span class="sxs-lookup"><span data-stu-id="d2449-164">Calling the [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) extension method to produce a `ReadOnlyMemory<char>` instance.</span></span>

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

<span data-ttu-id="d2449-165">Metoda, která zpočátku vytvoří <xref:System.Memory%601> instanci je implicitní vlastník vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d2449-165">The method that initially creates the <xref:System.Memory%601> instance is the implicit owner of the buffer.</span></span> <span data-ttu-id="d2449-166">Vlastnictví nelze převést na jinou součást, protože neexistuje žádná <xref:System.Buffers.IMemoryOwner%601> instance, která by převod usnadnila.</span><span class="sxs-lookup"><span data-stu-id="d2449-166">Ownership cannot be transferred to any other component because there is no <xref:System.Buffers.IMemoryOwner%601> instance to facilitate the transfer.</span></span> <span data-ttu-id="d2449-167">(Jako alternativu si můžete také představit, že uvolňování času runtime vlastní vyrovnávací paměť a všechny metody právě spotřebovávají vyrovnávací paměť.)</span><span class="sxs-lookup"><span data-stu-id="d2449-167">(As an alternative, you can also imagine that the runtime's garbage collector owns the buffer, and all methods just consume the buffer.)</span></span>

## <a name="usage-guidelines"></a><span data-ttu-id="d2449-168">Pokyny k použití</span><span class="sxs-lookup"><span data-stu-id="d2449-168">Usage guidelines</span></span>

<span data-ttu-id="d2449-169">Vzhledem k tomu, že blok paměti je vlastněn, ale má být předán více součástem, z nichž některé <xref:System.Memory%601> <xref:System.Span%601>mohou pracovat na určitém bloku paměti současně, je důležité stanovit pokyny pro použití obou a .</span><span class="sxs-lookup"><span data-stu-id="d2449-169">Because a memory block is owned but is intended to be passed to multiple components, some of which may operate upon a particular memory block simultaneously, it is important to establish guidelines for using both <xref:System.Memory%601> and <xref:System.Span%601>.</span></span>  <span data-ttu-id="d2449-170">Pokyny jsou nezbytné, protože:</span><span class="sxs-lookup"><span data-stu-id="d2449-170">Guidelines are necessary because:</span></span>

- <span data-ttu-id="d2449-171">Je možné, že součást zachovat odkaz na blok paměti po jeho vlastník a vydal.</span><span class="sxs-lookup"><span data-stu-id="d2449-171">It is possible for a component to retain a reference to a memory block after its owner has released it.</span></span>

- <span data-ttu-id="d2449-172">Je možné, že součást pracovat na vyrovnávací paměti ve stejnou dobu, že jiná součást pracuje na něm, v procesu poškození dat ve vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d2449-172">It is possible for a component to operate on a buffer at the same time that another component is operating on it, in the process corrupting the data in the buffer.</span></span>

- <span data-ttu-id="d2449-173">Zatímco charakter přidělené zásobníku <xref:System.Span%601> optimalizuje <xref:System.Span%601> výkon a umožňuje upřednostňovaný typ pro <xref:System.Span%601> provoz na bloku paměti, také podrobí některé hlavní omezení.</span><span class="sxs-lookup"><span data-stu-id="d2449-173">While the stack-allocated nature of <xref:System.Span%601> optimizes performance and makes <xref:System.Span%601> the preferred type for operating on a memory block, it also subjects <xref:System.Span%601> to some major restrictions.</span></span> <span data-ttu-id="d2449-174">Je důležité vědět, kdy <xref:System.Span%601> a a <xref:System.Memory%601>kdy použít .</span><span class="sxs-lookup"><span data-stu-id="d2449-174">It is important to know when to use a <xref:System.Span%601> and when to use <xref:System.Memory%601>.</span></span>

<span data-ttu-id="d2449-175">Níže jsou uvedeny naše <xref:System.Memory%601> doporučení pro úspěšné použití a související typy.</span><span class="sxs-lookup"><span data-stu-id="d2449-175">The following are our recommendations for successfully using <xref:System.Memory%601> and its related types.</span></span> <span data-ttu-id="d2449-176">Všimněte si, že <xref:System.Memory%601> <xref:System.Span%601> pokyny, které <xref:System.ReadOnlyMemory%601> <xref:System.ReadOnlySpan%601> se vztahují a také se vztahuje na a pokud jsme výslovně na vědomí jinak.</span><span class="sxs-lookup"><span data-stu-id="d2449-176">Note that guidance that applies to <xref:System.Memory%601> and <xref:System.Span%601> also applies to <xref:System.ReadOnlyMemory%601> and <xref:System.ReadOnlySpan%601> unless we explicitly note otherwise.</span></span>

<span data-ttu-id="d2449-177">**Pravidlo #1: Pro synchronní rozhraní API\<použijte span\<t> místo paměti T> jako parametr, pokud je to možné.**</span><span class="sxs-lookup"><span data-stu-id="d2449-177">**Rule #1: For a synchronous API, use Span\<T> instead of Memory\<T> as a parameter if possible.**</span></span>

<span data-ttu-id="d2449-178"><xref:System.Span%601>je univerzálnější než <xref:System.Memory%601> a může představovat širší škálu souvislých vyrovnávacích pamětí paměti.</span><span class="sxs-lookup"><span data-stu-id="d2449-178"><xref:System.Span%601> is more versatile than <xref:System.Memory%601> and can represent a wider variety of contiguous memory buffers.</span></span> <span data-ttu-id="d2449-179"><xref:System.Span%601>nabízí také lepší <xref:System.Memory%601>výkon než .</span><span class="sxs-lookup"><span data-stu-id="d2449-179"><xref:System.Span%601> also offers better performance than <xref:System.Memory%601>.</span></span> <span data-ttu-id="d2449-180">Nakonec můžete <xref:System.Memory%601.Span?displayProperty=nameWithType> vlastnost převést <xref:System.Memory%601> instanci <xref:System.Span%601>na ,\<i když Span\<T>-to-Memory T> převod není možný.</span><span class="sxs-lookup"><span data-stu-id="d2449-180">Finally, you can use the <xref:System.Memory%601.Span?displayProperty=nameWithType> property to convert a <xref:System.Memory%601> instance to a <xref:System.Span%601>, although Span\<T>-to-Memory\<T> conversion isn't possible.</span></span> <span data-ttu-id="d2449-181">Takže pokud vaši volající náhodou <xref:System.Memory%601> mají instanci, budou moci <xref:System.Span%601> volat vaše metody s parametry stejně.</span><span class="sxs-lookup"><span data-stu-id="d2449-181">So if your callers happen to have a <xref:System.Memory%601> instance, they'll be able to call your methods with <xref:System.Span%601> parameters anyway.</span></span>

<span data-ttu-id="d2449-182">Použití parametru <xref:System.Span%601> typu namísto typu <xref:System.Memory%601> také pomáhá napsat správnou implementaci metody spotřeby.</span><span class="sxs-lookup"><span data-stu-id="d2449-182">Using a parameter of type <xref:System.Span%601> instead of type <xref:System.Memory%601> also helps you write a correct consuming method implementation.</span></span> <span data-ttu-id="d2449-183">Budete automaticky získat kontroly v době kompilace, abyste zajistili, že se nepokoušíte o přístup k vyrovnávací paměti nad rámec zapůjčení metody (více o tom později).</span><span class="sxs-lookup"><span data-stu-id="d2449-183">You'll automatically get compile-time checks to ensure that you're not attempting to access the buffer beyond your method's lease (more on this later).</span></span>

<span data-ttu-id="d2449-184">Někdy budete muset použít <xref:System.Memory%601> parametr namísto <xref:System.Span%601> parametru, i když jste plně synchronní.</span><span class="sxs-lookup"><span data-stu-id="d2449-184">Sometimes, you'll have to use a <xref:System.Memory%601> parameter instead of a <xref:System.Span%601> parameter, even if you're fully synchronous.</span></span> <span data-ttu-id="d2449-185">Rozhraní API, které jste <xref:System.Memory%601> závislí přijímá pouze argumenty.</span><span class="sxs-lookup"><span data-stu-id="d2449-185">Perhaps an API that you depend accepts only <xref:System.Memory%601> arguments.</span></span> <span data-ttu-id="d2449-186">To je v pořádku, ale být vědomi <xref:System.Memory%601> kompromisy zapojeny při použití synchronně.</span><span class="sxs-lookup"><span data-stu-id="d2449-186">This is fine, but be aware of the tradeoffs involved when using <xref:System.Memory%601> synchronously.</span></span>

<a name="rule-2" />

<span data-ttu-id="d2449-187">**Pravidlo #2: Použijte ReadOnlySpan\<T\<> nebo ReadOnlyMemory T> pokud vyrovnávací paměť by měla být jen pro čtení.**</span><span class="sxs-lookup"><span data-stu-id="d2449-187">**Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only.**</span></span>

<span data-ttu-id="d2449-188">V předchozích příkladech `DisplayBufferToConsole` metoda čte pouze z vyrovnávací paměti; nemění obsah vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d2449-188">In the earlier examples, the `DisplayBufferToConsole` method only reads from the buffer; it doesn't modify the contents of the buffer.</span></span> <span data-ttu-id="d2449-189">Podpis metody by měl být změněn na následující.</span><span class="sxs-lookup"><span data-stu-id="d2449-189">The method signature should be changed to the following.</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

<span data-ttu-id="d2449-190">Ve skutečnosti, pokud zkombinujeme toto pravidlo a pravidlo #1, můžeme udělat ještě lépe a přepsat podpis metody takto:</span><span class="sxs-lookup"><span data-stu-id="d2449-190">In fact, if we combine this rule and Rule #1, we can do even better and rewrite the method signature as follows:</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

<span data-ttu-id="d2449-191">Metoda `DisplayBufferToConsole` nyní pracuje prakticky s každým typu `T[]`vyrovnávací paměti, který si lze představit: , úložiště přidělené [s stackalloc](../../csharp/language-reference/operators/stackalloc.md)a tak dále.</span><span class="sxs-lookup"><span data-stu-id="d2449-191">The `DisplayBufferToConsole` method now works with virtually every buffer type imaginable: `T[]`, storage allocated with [stackalloc](../../csharp/language-reference/operators/stackalloc.md), and so on.</span></span> <span data-ttu-id="d2449-192">Můžete dokonce předat <xref:System.String> přímo do něj!</span><span class="sxs-lookup"><span data-stu-id="d2449-192">You can even pass a <xref:System.String> directly into it!</span></span>

<span data-ttu-id="d2449-193">**Pravidlo #3: Pokud vaše\<metoda přijme `void`memory t> a\<vrátí , nesmíte použít Memory T> instance po vrátí metodu.**</span><span class="sxs-lookup"><span data-stu-id="d2449-193">**Rule #3: If your method accepts Memory\<T> and returns `void`, you must not use the Memory\<T> instance after your method returns.**</span></span>

<span data-ttu-id="d2449-194">To se týká již zmíněného "nájemního" konceptu.</span><span class="sxs-lookup"><span data-stu-id="d2449-194">This relates to the "lease" concept mentioned earlier.</span></span> <span data-ttu-id="d2449-195">Zapůjčení metody vrácení prázdnoty na <xref:System.Memory%601> instanci začíná, když je metoda zadána, a končí při ukončení metody.</span><span class="sxs-lookup"><span data-stu-id="d2449-195">A void-returning method's lease on the <xref:System.Memory%601> instance begins when the method is entered, and it ends when the method exits.</span></span> <span data-ttu-id="d2449-196">Zvažte následující příklad, `Log` který volá ve smyčce na základě vstupu z konzoly.</span><span class="sxs-lookup"><span data-stu-id="d2449-196">Consider the following example, which calls `Log` in a loop based on input from the console.</span></span>

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

<span data-ttu-id="d2449-197">Pokud `Log` je plně synchronní metoda, tento kód se bude chovat podle očekávání, protože je pouze jeden aktivní příjemce instance paměti v daném okamžiku.</span><span class="sxs-lookup"><span data-stu-id="d2449-197">If `Log` is a fully synchronous method, this code will behave as expected because there is only one active consumer of the memory instance at any given time.</span></span>
<span data-ttu-id="d2449-198">Ale představte `Log` si, že místo toho, že má tuto realizaci.</span><span class="sxs-lookup"><span data-stu-id="d2449-198">But imagine instead that `Log` has this implementation.</span></span>

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

<span data-ttu-id="d2449-199">V této `Log` implementaci porušuje jeho zapůjčení, protože <xref:System.Memory%601> se stále pokouší použít instanci na pozadí po původní metoda byla vrácena.</span><span class="sxs-lookup"><span data-stu-id="d2449-199">In this implementation, `Log` violates its lease because it still attempts to use the <xref:System.Memory%601> instance in the background after the original method has returned.</span></span> <span data-ttu-id="d2449-200">Metoda `Main` může zmutovat `Log` vyrovnávací paměti při pokusech o čtení z ní, což může mít za následek poškození dat.</span><span class="sxs-lookup"><span data-stu-id="d2449-200">The `Main` method could mutate the buffer while `Log` attempts to read from it, which could result in data corruption.</span></span>

<span data-ttu-id="d2449-201">Existuje několik způsobů, jak tento problém vyřešit:</span><span class="sxs-lookup"><span data-stu-id="d2449-201">There are several ways to resolve this:</span></span>

- <span data-ttu-id="d2449-202">Metoda `Log` může vrátit <xref:System.Threading.Tasks.Task> místo `void`, jako následující `Log` implementace metody.</span><span class="sxs-lookup"><span data-stu-id="d2449-202">The `Log` method can return a <xref:System.Threading.Tasks.Task> instead of `void`, as the following implementation of the `Log` method does.</span></span>

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- <span data-ttu-id="d2449-203">`Log`místo toho mohou být implementovány takto:</span><span class="sxs-lookup"><span data-stu-id="d2449-203">`Log` can instead be implemented as follows:</span></span>

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

<span data-ttu-id="d2449-204">**Pravidlo #4: Pokud vaše metoda\<přijímá paměť T> a vrátí\<Task, nesmíte použít memory t> instance po Task přechody do terminálového stavu.**</span><span class="sxs-lookup"><span data-stu-id="d2449-204">**Rule #4: If your method accepts a Memory\<T> and returns a Task, you must not use the Memory\<T> instance after the Task transitions to a terminal state.**</span></span>

<span data-ttu-id="d2449-205">Toto je pouze asynchronní varianta pravidla #3.</span><span class="sxs-lookup"><span data-stu-id="d2449-205">This is just the async variant of Rule #3.</span></span> <span data-ttu-id="d2449-206">Metoda `Log` z předchozího příkladu může být zapsána takto, aby byla v souladu s tímto pravidlem:</span><span class="sxs-lookup"><span data-stu-id="d2449-206">The `Log` method from the earlier example can be written as follows to comply with this rule:</span></span>

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

<span data-ttu-id="d2449-207">Zde "terminálový stav" znamená, že úloha přechází do dokončeného, chybově nebo zrušeného stavu.</span><span class="sxs-lookup"><span data-stu-id="d2449-207">Here, "terminal state" means that the task transitions to a completed, faulted, or canceled state.</span></span> <span data-ttu-id="d2449-208">Jinými slovy, "terminálový stav" znamená "vše, co by způsobilo čekání na vyvolání nebo pokračování v provádění".</span><span class="sxs-lookup"><span data-stu-id="d2449-208">In other words, "terminal state" means "anything that would cause await to throw or to continue execution."</span></span>

<span data-ttu-id="d2449-209">Tyto pokyny platí pro <xref:System.Threading.Tasks.Task>metody, které vracejí , <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>nebo podobný typ.</span><span class="sxs-lookup"><span data-stu-id="d2449-209">This guidance applies to methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>, or any similar type.</span></span>

<span data-ttu-id="d2449-210">**Pravidlo #5: Pokud konstruktor\<přijímá paměť T> jako parametr, instance metody na konstruované\<objektu jsou považovány za spotřebitele memory t> instance.**</span><span class="sxs-lookup"><span data-stu-id="d2449-210">**Rule #5: If your constructor accepts Memory\<T> as a parameter, instance methods on the constructed object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="d2449-211">Uvažujte následující příklad:</span><span class="sxs-lookup"><span data-stu-id="d2449-211">Consider the following example:</span></span>

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

<span data-ttu-id="d2449-212">Zde `OddValueExtractor` konstruktor přijímá `ReadOnlyMemory<int>` jako parametr konstruktoru, takže samotný konstruktor je `ReadOnlyMemory<int>` příjemcem instance a všechny metody instance na `ReadOnlyMemory<int>` vrácené hodnotě jsou také příjemci původní instance.</span><span class="sxs-lookup"><span data-stu-id="d2449-212">Here, the `OddValueExtractor` constructor accepts a `ReadOnlyMemory<int>` as a constructor parameter, so the constructor itself is a consumer of the `ReadOnlyMemory<int>` instance, and all instance methods on the returned value are also consumers of the original `ReadOnlyMemory<int>` instance.</span></span> <span data-ttu-id="d2449-213">To znamená, `TryReadNextOddValue` že `ReadOnlyMemory<int>` spotřebovává instanci, i když instance `TryReadNextOddValue` není předána přímo metodě.</span><span class="sxs-lookup"><span data-stu-id="d2449-213">This means that `TryReadNextOddValue` consumes the `ReadOnlyMemory<int>` instance, even though the instance isn't passed directly to the `TryReadNextOddValue` method.</span></span>

<span data-ttu-id="d2449-214">**Pravidlo #6: Pokud máte nastavenou paměť\<T> typem vlastnosti (nebo ekvivalentní instance metody) na váš typ,\<instance metody na tento objekt se předpokládá, že jsou příjemci memory t> instance.**</span><span class="sxs-lookup"><span data-stu-id="d2449-214">**Rule #6: If you have a settable Memory\<T>-typed property (or an equivalent instance method) on your type, instance methods on that object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="d2449-215">To je opravdu jen varianta pravidla #5.</span><span class="sxs-lookup"><span data-stu-id="d2449-215">This is really just a variant of Rule #5.</span></span> <span data-ttu-id="d2449-216">Toto pravidlo existuje, protože settery vlastností nebo ekvivalentní metody se předpokládá, že zachytit a zachovat jejich vstupy, takže instance metody na stejný objekt může využít zachyceného stavu.</span><span class="sxs-lookup"><span data-stu-id="d2449-216">This rule exists because property setters or equivalent methods are assumed to capture and persist their inputs, so instance methods on the same object may utilize the captured state.</span></span>

<span data-ttu-id="d2449-217">Následující příklad aktivuje toto pravidlo:</span><span class="sxs-lookup"><span data-stu-id="d2449-217">The following example triggers this rule:</span></span>

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

<span data-ttu-id="d2449-218">**Pravidlo #7: Pokud máte Odkaz\<na IMemoryOwner T>, musíte jej v určitém okamžiku nakládat nebo převést jeho vlastnictví (ale ne obojí).**</span><span class="sxs-lookup"><span data-stu-id="d2449-218">**Rule #7: If you have an IMemoryOwner\<T> reference, you must at some point dispose of it or transfer its ownership (but not both).**</span></span>

<span data-ttu-id="d2449-219">Vzhledem <xref:System.Memory%601> k tomu, že instance může být zálohována <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> spravovanou <xref:System.Memory%601> nebo nespravovanou pamětí, vlastník musí volat po dokončení práce provedené na instanci.</span><span class="sxs-lookup"><span data-stu-id="d2449-219">Since a <xref:System.Memory%601> instance may be backed by either managed or unmanaged memory, the owner must call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> when work performed on the <xref:System.Memory%601> instance is complete.</span></span> <span data-ttu-id="d2449-220">Případně vlastník může převést vlastnictví <xref:System.Buffers.IMemoryOwner%601> instance na jinou součást, v tomto okamžiku <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> se nabývající komponenta stane odpovědnou za volání ve vhodnou dobu (více o tom později).</span><span class="sxs-lookup"><span data-stu-id="d2449-220">Alternatively, the owner may transfer ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component, at which point the acquiring component becomes responsible for calling <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> at the appropriate time (more on this later).</span></span>

<span data-ttu-id="d2449-221">Selhání volání <xref:System.Buffers.MemoryPool%601.Dispose%2A> metody může vést k nevracení nespravované paměti nebo jiné snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="d2449-221">Failure to call the <xref:System.Buffers.MemoryPool%601.Dispose%2A> method may lead to unmanaged memory leaks or other performance degradation.</span></span>

<span data-ttu-id="d2449-222">Toto pravidlo platí také pro kód, který volá metody factory jako <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d2449-222">This rule also applies to code that calls factory methods like <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d2449-223">Volající se stane vlastníkem <xref:System.Buffers.IMemoryOwner%601> vrácené a je zodpovědný za likvidaci instance po dokončení.</span><span class="sxs-lookup"><span data-stu-id="d2449-223">The caller becomes the owner of the returned <xref:System.Buffers.IMemoryOwner%601> and is responsible for disposing of the instance when finished.</span></span>

<span data-ttu-id="d2449-224">**Pravidlo #8: Pokud máte v\<povrchu rozhraní API parametr IMemoryOwner T>, přijímáte vlastnictví této instance.**</span><span class="sxs-lookup"><span data-stu-id="d2449-224">**Rule #8: If you have an IMemoryOwner\<T> parameter in your API surface, you are accepting ownership of that instance.**</span></span>

<span data-ttu-id="d2449-225">Přijetí instance tohoto typu signalizuje, že vaše komponenta má v úmyslu převzít vlastnictví této instance.</span><span class="sxs-lookup"><span data-stu-id="d2449-225">Accepting an instance of this type signals that your component intends to take ownership of this instance.</span></span> <span data-ttu-id="d2449-226">Vaše součást k tomu se stává zodpovědní za správnou likvidaci podle pravidla #7.</span><span class="sxs-lookup"><span data-stu-id="d2449-226">Your component becomes responsible for proper disposal according to Rule #7.</span></span>

<span data-ttu-id="d2449-227">Jakákoli součást, která <xref:System.Buffers.IMemoryOwner%601> převádí vlastnictví instance na jinou součást, by již neměla tuto instanci používat po dokončení volání metody.</span><span class="sxs-lookup"><span data-stu-id="d2449-227">Any component that transfers ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component should no longer use that instance after the method call completes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d2449-228">Pokud konstruktor přijímá <xref:System.Buffers.IMemoryOwner%601> jako parametr, jeho <xref:System.IDisposable>typ by <xref:System.IDisposable.Dispose%2A> měl <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>implementovat a vaše metoda by měla volat .</span><span class="sxs-lookup"><span data-stu-id="d2449-228">If your constructor accepts <xref:System.Buffers.IMemoryOwner%601> as a parameter, its type should implement <xref:System.IDisposable>, and your <xref:System.IDisposable.Dispose%2A> method should call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="d2449-229">**Pravidlo #9: Pokud balíte synchronní metodu p/invoke, vaše\<rozhraní API by mělo jako parametr přijmout> Span T.**</span><span class="sxs-lookup"><span data-stu-id="d2449-229">**Rule #9: If you're wrapping a synchronous p/invoke method, your API should accept Span\<T> as a parameter.**</span></span>

<span data-ttu-id="d2449-230">Podle pravidla #1 <xref:System.Span%601> je obecně správný typ pro synchronní api.</span><span class="sxs-lookup"><span data-stu-id="d2449-230">According to Rule #1, <xref:System.Span%601> is generally the correct type to use for synchronous APIs.</span></span> <span data-ttu-id="d2449-231">Instance můžete <xref:System.Span%601> připnout pomocí klíčového [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) slova, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d2449-231">You can pin <xref:System.Span%601> instances via the [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) keyword, as in the following example.</span></span>

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

<span data-ttu-id="d2449-232">V předchozím příkladu `pbData` může být null, pokud je například vstupní rozsah prázdný.</span><span class="sxs-lookup"><span data-stu-id="d2449-232">In the previous example, `pbData` can be null if, for example, the input span is empty.</span></span> <span data-ttu-id="d2449-233">Pokud exportovaná metoda absolutně `pbData` vyžaduje, aby byla `cbData` nenulová, i když je 0, může být metoda implementována následovně:</span><span class="sxs-lookup"><span data-stu-id="d2449-233">If the exported method absolutely requires that `pbData` be non-null, even if `cbData` is 0, the method can be implemented as follows:</span></span>

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

<span data-ttu-id="d2449-234">**Pravidlo #10: Pokud balíte asynchronní metodu p/invoke,\<vaše rozhraní API by mělo jako parametr přijmout paměť T>.**</span><span class="sxs-lookup"><span data-stu-id="d2449-234">**Rule #10: If you're wrapping an asynchronous p/invoke method, your API should accept Memory\<T> as a parameter.**</span></span>

<span data-ttu-id="d2449-235">Vzhledem k [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) tomu, že nelze použít klíčové <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> slovo napříč asynchronními operacemi, použijete metodu k připnutí <xref:System.Memory%601> instancí bez ohledu na druh souvislé paměti, kterou instance představuje.</span><span class="sxs-lookup"><span data-stu-id="d2449-235">Since you cannot use the [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) keyword across asynchronous operations, you use the <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> method to pin <xref:System.Memory%601> instances, regardless of the kind of contiguous memory the instance represents.</span></span> <span data-ttu-id="d2449-236">Následující příklad ukazuje, jak používat toto rozhraní API k provedení asynchronního volání p/invoke.</span><span class="sxs-lookup"><span data-stu-id="d2449-236">The following example shows how to use this API to perform an asynchronous p/invoke call.</span></span>

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
    var actualState = (MyCompletedCallbackState)state;
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

## <a name="see-also"></a><span data-ttu-id="d2449-237">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2449-237">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
