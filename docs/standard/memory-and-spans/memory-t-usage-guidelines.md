---
title: Pokyny k používání Memory<T> a Span<T>
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
ms.openlocfilehash: 0a614f628faa98be778c627573e4dddc462c9107
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121964"
---
# <a name="memoryt-and-spant-usage-guidelines"></a><span data-ttu-id="7e939-102">\<v paměti > a rozpětí\<T > pokyny pro použití</span><span class="sxs-lookup"><span data-stu-id="7e939-102">Memory\<T> and Span\<T> usage guidelines</span></span>

<span data-ttu-id="7e939-103">.NET Core obsahuje několik typů, které reprezentují libovolnou souvislou oblast paměti.</span><span class="sxs-lookup"><span data-stu-id="7e939-103">.NET Core includes a number of types that represent an arbitrary contiguous region of memory.</span></span> <span data-ttu-id="7e939-104">Rozhraní .NET Core 2,0 zavedlo <xref:System.Span%601> a <xref:System.ReadOnlySpan%601>, což jsou odlehčené vyrovnávací paměti, které mohou být zajištěny spravovanou nebo nespravovanou pamětí.</span><span class="sxs-lookup"><span data-stu-id="7e939-104">.NET Core 2.0 introduced <xref:System.Span%601> and <xref:System.ReadOnlySpan%601>, which are lightweight memory buffers that can be backed by managed or unmanaged memory.</span></span> <span data-ttu-id="7e939-105">Vzhledem k tomu, že tyto typy mohou být uloženy pouze v zásobníku, nejsou vhodné pro různé scénáře, včetně volání asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="7e939-105">Because these types can only be stored on the stack, they are unsuitable for a number of scenarios, including asynchronous method calls.</span></span> <span data-ttu-id="7e939-106">.NET Core 2,1 přidává mnoho dalších typů, včetně <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>a <xref:System.Buffers.MemoryPool%601>.</span><span class="sxs-lookup"><span data-stu-id="7e939-106">.NET Core 2.1 adds a number of additional types, including <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>, and <xref:System.Buffers.MemoryPool%601>.</span></span> <span data-ttu-id="7e939-107">Stejně jako <xref:System.Span%601>, <xref:System.Memory%601> a jeho související typy lze zálohovat pomocí spravované i nespravované paměti.</span><span class="sxs-lookup"><span data-stu-id="7e939-107">Like <xref:System.Span%601>, <xref:System.Memory%601> and its related types can be backed by both managed and unmanaged memory.</span></span> <span data-ttu-id="7e939-108">Na rozdíl od <xref:System.Span%601>mohou být <xref:System.Memory%601> uloženy na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="7e939-108">Unlike <xref:System.Span%601>, <xref:System.Memory%601> can be stored on the managed heap.</span></span>

<span data-ttu-id="7e939-109"><xref:System.Span%601> i <xref:System.Memory%601> jsou vyrovnávací paměti strukturovaných dat, která se dají používat v kanálech.</span><span class="sxs-lookup"><span data-stu-id="7e939-109">Both <xref:System.Span%601> and <xref:System.Memory%601> are buffers of structured data that can be used in pipelines.</span></span> <span data-ttu-id="7e939-110">To znamená, že jsou navržené tak, aby některá nebo všechna data mohla být efektivně předána součástem v kanálu, která je může zpracovávat a případně upravovat vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="7e939-110">That is, they are designed so that some or all of the data can be efficiently passed to components in the pipeline, which can process them and optionally modify the buffer.</span></span> <span data-ttu-id="7e939-111">Vzhledem k tomu, že <xref:System.Memory%601> a ke svým souvisejícím typům lze získat pøístup více komponent nebo více vlákny, je důležité, aby vývojáři při vytváření robustního kódu dodržovali některé standardní pokyny pro použití.</span><span class="sxs-lookup"><span data-stu-id="7e939-111">Because <xref:System.Memory%601> and its related types can be accessed by multiple components or by multiple threads, it's important that developers follow some standard usage guidelines to produce robust code.</span></span>

## <a name="owners-consumers-and-lifetime-management"></a><span data-ttu-id="7e939-112">Vlastníci, spotřebitelé a správa životního cyklu</span><span class="sxs-lookup"><span data-stu-id="7e939-112">Owners, consumers, and lifetime management</span></span>

<span data-ttu-id="7e939-113">Vzhledem k tomu, že vyrovnávací paměti lze předávat mezi rozhraními API a vzhledem k tomu, že vyrovnávací paměti mohou být někdy k dispozici z více vláken, je důležité zvážit správu životnosti.</span><span class="sxs-lookup"><span data-stu-id="7e939-113">Since buffers can be passed around between APIs, and since buffers can sometimes be accessed from multiple threads, it's important to consider lifetime management.</span></span> <span data-ttu-id="7e939-114">Existují tři základní koncepty:</span><span class="sxs-lookup"><span data-stu-id="7e939-114">There are three core concepts:</span></span>

- <span data-ttu-id="7e939-115">**Vlastnictví**.</span><span class="sxs-lookup"><span data-stu-id="7e939-115">**Ownership**.</span></span> <span data-ttu-id="7e939-116">Vlastník instance vyrovnávací paměti je zodpovědný za správu životnosti, včetně zničení vyrovnávací paměti, když se už nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="7e939-116">The owner of a buffer instance is responsible for lifetime management, including destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="7e939-117">Všechny vyrovnávací paměti mají jednoho vlastníka.</span><span class="sxs-lookup"><span data-stu-id="7e939-117">All buffers have a single owner.</span></span> <span data-ttu-id="7e939-118">Obecně je vlastníkem komponenta, která vytvořila vyrovnávací paměť nebo která obdržela vyrovnávací paměť z továrny.</span><span class="sxs-lookup"><span data-stu-id="7e939-118">Generally the owner is the component that created the buffer or that received the buffer from a factory.</span></span> <span data-ttu-id="7e939-119">Vlastnictví lze také přenést; **Součást-a** může opustit řízení vyrovnávací paměti pro **komponentu B**, na které **Komponenta bodu-A** již nesmí používat vyrovnávací paměť, a **Komponenta B** se stane zodpovědností za zničení vyrovnávací paměti, pokud se už nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="7e939-119">Ownership can also be transferred; **Component-A** can relinquish control of the buffer to **Component-B**, at which point **Component-A** may no longer use the buffer, and **Component-B** becomes responsible for destroying the buffer when it's no longer in use.</span></span>

- <span data-ttu-id="7e939-120">**Spotřeba**.</span><span class="sxs-lookup"><span data-stu-id="7e939-120">**Consumption**.</span></span> <span data-ttu-id="7e939-121">Příjemce instance vyrovnávací paměti může použít instanci vyrovnávací paměti čtením z ní a případně do ní zapisovat.</span><span class="sxs-lookup"><span data-stu-id="7e939-121">The consumer of a buffer instance is allowed to use the buffer instance by reading from it and possibly writing to it.</span></span> <span data-ttu-id="7e939-122">Vyrovnávací paměti můžou mít jednoho příjemce v čase, pokud není k dispozici nějaký mechanismus externí synchronizace.</span><span class="sxs-lookup"><span data-stu-id="7e939-122">Buffers can have one consumer at a time unless some external synchronization mechanism is provided.</span></span> <span data-ttu-id="7e939-123">Všimněte si, že aktivní příjemce vyrovnávací paměti nemusí být nutně vlastníkem vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7e939-123">Note that the active consumer of a buffer isn't necessarily the buffer's owner.</span></span>

- <span data-ttu-id="7e939-124">**Zapůjčení**.</span><span class="sxs-lookup"><span data-stu-id="7e939-124">**Lease**.</span></span> <span data-ttu-id="7e939-125">Zapůjčení je doba, po kterou může určitá součást být příjemcem vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7e939-125">The lease is the length of time that a particular component is allowed to be the consumer of the buffer.</span></span>

<span data-ttu-id="7e939-126">Následující příklad pseudo kódu znázorňuje tyto tři koncepty.</span><span class="sxs-lookup"><span data-stu-id="7e939-126">The following pseudo-code example illustrates these three concepts.</span></span> <span data-ttu-id="7e939-127">Obsahuje `Main` metodu, která vytvoří instanci <xref:System.Memory%601> vyrovnávací paměti typu <xref:System.Char>, volá metodu `WriteInt32ToBuffer` pro zápis řetězcové reprezentace celého čísla do vyrovnávací paměti a potom zavolá metodu `DisplayBufferToConsole` pro zobrazení hodnoty vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7e939-127">It includes a `Main` method that instantiates a <xref:System.Memory%601> buffer of type <xref:System.Char>, calls the `WriteInt32ToBuffer` method to write the string representation of an integer to the buffer, and then calls the `DisplayBufferToConsole` method to display the value of the buffer.</span></span>

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

<span data-ttu-id="7e939-128">Metoda `Main` vytvoří vyrovnávací paměť (v tomto případě instance <xref:System.Span%601>) a tedy její vlastníka.</span><span class="sxs-lookup"><span data-stu-id="7e939-128">The `Main` method creates the buffer (in this case an <xref:System.Span%601> instance) and so is its owner.</span></span> <span data-ttu-id="7e939-129">Proto `Main` zodpovídá za zničení vyrovnávací paměti, když se už nepoužívá.</span><span class="sxs-lookup"><span data-stu-id="7e939-129">Therefore, `Main` is responsible for destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="7e939-130">Provede to voláním metody <xref:System.Span%601.Clear?displayProperty=nameWithType> vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7e939-130">It does this by calling the buffer's <xref:System.Span%601.Clear?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="7e939-131">(<xref:System.Span%601.Clear> metoda ve skutečnosti vymaže paměť vyrovnávací paměti; struktura <xref:System.Span%601> ve skutečnosti nemá metodu, která zničí vyrovnávací paměť.)</span><span class="sxs-lookup"><span data-stu-id="7e939-131">(The <xref:System.Span%601.Clear> method here actually clears the buffer's memory; the <xref:System.Span%601> structure doesn't actually have a method that destroys the buffer.)</span></span>

<span data-ttu-id="7e939-132">Vyrovnávací paměť má dva uživatele `WriteInt32ToBuffer` a `DisplayBufferToConsole`.</span><span class="sxs-lookup"><span data-stu-id="7e939-132">The buffer has two consumers, `WriteInt32ToBuffer` and `DisplayBufferToConsole`.</span></span> <span data-ttu-id="7e939-133">V jednom okamžiku je jen jeden příjemce (první `WriteInt32ToBuffer`, potom `DisplayBufferToConsole`) a žádný z uživatelů nevlastní vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="7e939-133">There is only one consumer at a time (first `WriteInt32ToBuffer`, then `DisplayBufferToConsole`), and neither of the consumers owns the buffer.</span></span> <span data-ttu-id="7e939-134">Všimněte si také, že "příjemce" v tomto kontextu neznamená zobrazení vyrovnávací paměti jen pro čtení. Uživatelé můžou upravit obsah vyrovnávací paměti, jak `WriteInt32ToBuffer` v případě, že je pro čtení a zápis vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7e939-134">Note also that "consumer" in this context doesn't imply a read-only view of the buffer; consumers can modify the buffer's contents, as `WriteInt32ToBuffer` does, if given a read/write view of the buffer.</span></span>

<span data-ttu-id="7e939-135">Metoda `WriteInt32ToBuffer` má zapůjčení (může spotřebovávat) vyrovnávací paměť mezi začátkem volání metody a časem, který metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="7e939-135">The `WriteInt32ToBuffer` method has a lease on (can consume) the buffer between the start of the method call and the time the method returns.</span></span> <span data-ttu-id="7e939-136">Podobně `DisplayBufferToConsole` má zapůjčení ve vyrovnávací paměti během jeho provádění a zapůjčení je uvolněno, pokud metoda odvíjí.</span><span class="sxs-lookup"><span data-stu-id="7e939-136">Similarly, `DisplayBufferToConsole` has a lease on the buffer while it's executing, and the lease is released when the method unwinds.</span></span> <span data-ttu-id="7e939-137">(K dispozici není žádné rozhraní API pro správu zapůjčených adres. "zapůjčení" je koncepční záležitost.)</span><span class="sxs-lookup"><span data-stu-id="7e939-137">(There is no API for lease management; a "lease" is a conceptual matter.)</span></span>

## <a name="memoryt-and-the-ownerconsumer-model"></a><span data-ttu-id="7e939-138">Paměť\<> a model vlastník/příjemce</span><span class="sxs-lookup"><span data-stu-id="7e939-138">Memory\<T> and the owner/consumer model</span></span>

<span data-ttu-id="7e939-139">Jako poznámky k oddílům [pro vlastníky, uživatele a správu životního cyklu](#owners-consumers-and-lifetime-management) má vyrovnávací paměť vždy vlastníka.</span><span class="sxs-lookup"><span data-stu-id="7e939-139">As the [Owners, consumers, and lifetime management](#owners-consumers-and-lifetime-management) section notes, a buffer always has an owner.</span></span> <span data-ttu-id="7e939-140">.NET Core podporuje dva modely vlastnictví:</span><span class="sxs-lookup"><span data-stu-id="7e939-140">.NET Core supports two ownership models:</span></span>

- <span data-ttu-id="7e939-141">Model, který podporuje jediné vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="7e939-141">A model that supports single ownership.</span></span> <span data-ttu-id="7e939-142">Vyrovnávací paměť má jednoho vlastníka pro celou dobu života.</span><span class="sxs-lookup"><span data-stu-id="7e939-142">A buffer has a single owner for its entire lifetime.</span></span>

- <span data-ttu-id="7e939-143">Model, který podporuje přenos vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="7e939-143">A model that supports ownership transfer.</span></span> <span data-ttu-id="7e939-144">Vlastnictví vyrovnávací paměti lze přenést od původního vlastníka (jeho tvůrce) do jiné součásti, která pak bude zodpovědná za správu životnosti vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7e939-144">Ownership of a buffer can be transferred from its original owner (its creator) to another component, which then becomes responsible for the buffer's lifetime management.</span></span> <span data-ttu-id="7e939-145">Vlastník může převést vlastnictví na jinou komponentu a tak dále.</span><span class="sxs-lookup"><span data-stu-id="7e939-145">That owner can in turn transfer ownership to another component, and so on.</span></span>

<span data-ttu-id="7e939-146">Rozhraní <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> použijete k explicitní správě vlastnictví vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7e939-146">You use the <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> interface to explicitly manage the ownership of a buffer.</span></span> <span data-ttu-id="7e939-147"><xref:System.Buffers.IMemoryOwner%601> podporuje oba modely vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="7e939-147"><xref:System.Buffers.IMemoryOwner%601> supports both ownership models.</span></span> <span data-ttu-id="7e939-148">Komponenta, která má odkaz <xref:System.Buffers.IMemoryOwner%601> vlastní vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="7e939-148">The component that has an <xref:System.Buffers.IMemoryOwner%601> reference owns the buffer.</span></span> <span data-ttu-id="7e939-149">Následující příklad používá instanci <xref:System.Buffers.IMemoryOwner%601?> pro reflektování vlastnictví <xref:System.Memory%601> vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7e939-149">The following example uses an <xref:System.Buffers.IMemoryOwner%601?> instance to reflect the ownership of an <xref:System.Memory%601> buffer.</span></span>

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

<span data-ttu-id="7e939-150">Tento příklad můžeme také zapsat s [`using`](../../csharp/language-reference/keywords/using-statement.md):</span><span class="sxs-lookup"><span data-stu-id="7e939-150">We can also write this example with the [`using`](../../csharp/language-reference/keywords/using-statement.md):</span></span>

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

<span data-ttu-id="7e939-151">V tomto kódu:</span><span class="sxs-lookup"><span data-stu-id="7e939-151">In this code:</span></span>

- <span data-ttu-id="7e939-152">Metoda `Main` obsahuje odkaz na instanci <xref:System.Buffers.IMemoryOwner%601>, takže metoda `Main` je vlastníkem vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7e939-152">The `Main` method holds the reference to the <xref:System.Buffers.IMemoryOwner%601> instance, so the `Main` method is the owner of the buffer.</span></span>

- <span data-ttu-id="7e939-153">Metody `WriteInt32ToBuffer` a `DisplayBufferToConsole` přijímají <xref:System.Memory%601> jako veřejné rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="7e939-153">The `WriteInt32ToBuffer` and `DisplayBufferToConsole` methods accept <xref:System.Memory%601> as a public API.</span></span> <span data-ttu-id="7e939-154">Proto jsou příjemci vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7e939-154">Therefore, they are consumers of the buffer.</span></span> <span data-ttu-id="7e939-155">A využívají je pouze po jednom.</span><span class="sxs-lookup"><span data-stu-id="7e939-155">And they only consume it one at a time.</span></span>

<span data-ttu-id="7e939-156">I když je metoda `WriteInt32ToBuffer` určena k zápisu hodnoty do vyrovnávací paměti, metoda `DisplayBufferToConsole` není.</span><span class="sxs-lookup"><span data-stu-id="7e939-156">Although the `WriteInt32ToBuffer` method is intended to write a value to the buffer, the `DisplayBufferToConsole` method isn't.</span></span> <span data-ttu-id="7e939-157">V takovém případě by bylo možné akceptovat argument typu <xref:System.ReadOnlyMemory%601>.</span><span class="sxs-lookup"><span data-stu-id="7e939-157">To reflect this, it could have accepted an argument of type <xref:System.ReadOnlyMemory%601>.</span></span> <span data-ttu-id="7e939-158">Další informace o <xref:System.ReadOnlyMemory%601>najdete v tématu [pravidla #2: použijte ReadOnlySpan\<t > nebo ReadOnlyMemory\<t >, pokud by měla být vyrovnávací paměť jen pro čtení](#rule-2).</span><span class="sxs-lookup"><span data-stu-id="7e939-158">For additional information on <xref:System.ReadOnlyMemory%601>, see [Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only](#rule-2).</span></span>

### <a name="ownerless-memoryt-instances"></a><span data-ttu-id="7e939-159">Nevlastní > instance\<paměti pro vlastníka</span><span class="sxs-lookup"><span data-stu-id="7e939-159">"Ownerless" Memory\<T> instances</span></span>

<span data-ttu-id="7e939-160">Instanci <xref:System.Memory%601> můžete vytvořit bez použití <xref:System.Buffers.IMemoryOwner%601>.</span><span class="sxs-lookup"><span data-stu-id="7e939-160">You can create a <xref:System.Memory%601> instance without using <xref:System.Buffers.IMemoryOwner%601>.</span></span> <span data-ttu-id="7e939-161">V takovém případě je vlastnictví vyrovnávací paměti implicitní, nikoli explicitní, a podporuje se jenom model s jedním vlastníkem.</span><span class="sxs-lookup"><span data-stu-id="7e939-161">In this case, ownership of the buffer is implicit rather than explicit, and only the single-owner model is supported.</span></span> <span data-ttu-id="7e939-162">Můžete to udělat takto:</span><span class="sxs-lookup"><span data-stu-id="7e939-162">You can do this by:</span></span>

- <span data-ttu-id="7e939-163">Volání jednoho konstruktoru <xref:System.Memory%601> přímo, předání do `T[]`, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7e939-163">Calling one of the  <xref:System.Memory%601> constructors directly, passing in a `T[]`, as the following example does.</span></span>

- <span data-ttu-id="7e939-164">Voláním metody rozšíření [String. AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) vytvořte instanci `ReadOnlyMemory<char>`.</span><span class="sxs-lookup"><span data-stu-id="7e939-164">Calling the [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) extension method to produce a `ReadOnlyMemory<char>` instance.</span></span>

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

<span data-ttu-id="7e939-165">Metoda, která zpočátku vytvoří instanci <xref:System.Memory%601>, je implicitní vlastník vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7e939-165">The method that initially creates the <xref:System.Memory%601> instance is the implicit owner of the buffer.</span></span> <span data-ttu-id="7e939-166">Vlastnictví nelze přenést do žádné jiné součásti, protože není k dispozici žádná instance <xref:System.Buffers.IMemoryOwner%601> pro usnadnění přenosu.</span><span class="sxs-lookup"><span data-stu-id="7e939-166">Ownership cannot be transferred to any other component because there is no <xref:System.Buffers.IMemoryOwner%601> instance to facilitate the transfer.</span></span> <span data-ttu-id="7e939-167">(Jako alternativu můžete také představovat, že systém uvolňování paměti modulu runtime vlastní vyrovnávací paměť, a všechny metody pouze využívají vyrovnávací paměť.)</span><span class="sxs-lookup"><span data-stu-id="7e939-167">(As an alternative, you can also imagine that the runtime's garbage collector owns the buffer, and all methods just consume the buffer.)</span></span>

## <a name="usage-guidelines"></a><span data-ttu-id="7e939-168">Pokyny k použití</span><span class="sxs-lookup"><span data-stu-id="7e939-168">Usage guidelines</span></span>

<span data-ttu-id="7e939-169">Vzhledem k tomu, že blok paměti je vlastněn, ale má být předán více komponentám, některé z nich mohou fungovat současně na konkrétní blok paměti, je důležité vytvořit pokyny pro použití <xref:System.Memory%601> i <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="7e939-169">Because a memory block is owned but is intended to be passed to multiple components, some of which may operate upon a particular memory block simultaneously, it is important to establish guidelines for using both <xref:System.Memory%601> and <xref:System.Span%601>.</span></span>  <span data-ttu-id="7e939-170">Pokyny jsou nezbytné z těchto důvodů:</span><span class="sxs-lookup"><span data-stu-id="7e939-170">Guidelines are necessary because:</span></span>

- <span data-ttu-id="7e939-171">Je možné, že komponenta uchovává odkaz na blok paměti poté, co ho jeho vlastník uvolnil.</span><span class="sxs-lookup"><span data-stu-id="7e939-171">It is possible for a component to retain a reference to a memory block after its owner has released it.</span></span>

- <span data-ttu-id="7e939-172">Je možné, že komponenta pracuje na vyrovnávací paměti současně s tím, že na ní jiná komponenta pracuje, v procesu poškození dat ve vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7e939-172">It is possible for a component to operate on a buffer at the same time that another component is operating on it, in the process corrupting the data in the buffer.</span></span>

- <span data-ttu-id="7e939-173">I když povaha přidělená do zásobníku <xref:System.Span%601> optimalizuje výkon a dává <xref:System.Span%601> upřednostňovaný typ pro provoz na bloku paměti, také subjekty <xref:System.Span%601> na některá hlavní omezení.</span><span class="sxs-lookup"><span data-stu-id="7e939-173">While the stack-allocated nature of <xref:System.Span%601> optimizes performance and makes <xref:System.Span%601> the preferred type for operating on a memory block, it also subjects <xref:System.Span%601> to some major restrictions.</span></span> <span data-ttu-id="7e939-174">Je důležité znát, kdy použít <xref:System.Span%601> a kdy použít <xref:System.Memory%601>.</span><span class="sxs-lookup"><span data-stu-id="7e939-174">It is important to know when to use a <xref:System.Span%601> and when to use <xref:System.Memory%601>.</span></span>

<span data-ttu-id="7e939-175">Níže jsou naše doporučení pro úspěšné použití <xref:System.Memory%601> a souvisejících typů.</span><span class="sxs-lookup"><span data-stu-id="7e939-175">The following are our recommendations for successfully using <xref:System.Memory%601> and its related types.</span></span> <span data-ttu-id="7e939-176">Všimněte si, že pokyny, které se vztahují na <xref:System.Memory%601> a <xref:System.Span%601>, platí i pro <xref:System.ReadOnlyMemory%601> a <xref:System.ReadOnlySpan%601>, pokud výslovně nepovažujeme za jinak.</span><span class="sxs-lookup"><span data-stu-id="7e939-176">Note that guidance that applies to <xref:System.Memory%601> and <xref:System.Span%601> also applies to <xref:System.ReadOnlyMemory%601> and <xref:System.ReadOnlySpan%601> unless we explicitly note otherwise.</span></span>

<span data-ttu-id="7e939-177">**#1 pravidla: u synchronního rozhraní API použijte >\<T místo paměti\<T > jako parametr, pokud je to možné.**</span><span class="sxs-lookup"><span data-stu-id="7e939-177">**Rule #1: For a synchronous API, use Span\<T> instead of Memory\<T> as a parameter if possible.**</span></span>

<span data-ttu-id="7e939-178"><xref:System.Span%601> je všestrannější než <xref:System.Memory%601> a může představovat širší škálu souvislých vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="7e939-178"><xref:System.Span%601> is more versatile than <xref:System.Memory%601> and can represent a wider variety of contiguous memory buffers.</span></span> <span data-ttu-id="7e939-179"><xref:System.Span%601> také nabízí lepší výkon než <xref:System.Memory%601>.</span><span class="sxs-lookup"><span data-stu-id="7e939-179"><xref:System.Span%601> also offers better performance than <xref:System.Memory%601>.</span></span> <span data-ttu-id="7e939-180">Nakonec můžete použít vlastnost <xref:System.Memory%601.Span?displayProperty=nameWithType> k převedení instance <xref:System.Memory%601> na <xref:System.Span%601>, i když je\<T > převod na paměť\<T > převod není možný.</span><span class="sxs-lookup"><span data-stu-id="7e939-180">Finally, you can use the <xref:System.Memory%601.Span?displayProperty=nameWithType> property to convert a <xref:System.Memory%601> instance to a <xref:System.Span%601>, although Span\<T>-to-Memory\<T> conversion isn't possible.</span></span> <span data-ttu-id="7e939-181">Takže v případě, že se volající mají instanci <xref:System.Memory%601>, budou moci volat vaše metody s parametry <xref:System.Span%601> přesto.</span><span class="sxs-lookup"><span data-stu-id="7e939-181">So if your callers happen to have a <xref:System.Memory%601> instance, they'll be able to call your methods with <xref:System.Span%601> parameters anyway.</span></span>

<span data-ttu-id="7e939-182">Použití parametru typu <xref:System.Span%601> místo typu <xref:System.Memory%601> také pomůže napsat správnou implementaci metody.</span><span class="sxs-lookup"><span data-stu-id="7e939-182">Using a parameter of type <xref:System.Span%601> instead of type <xref:System.Memory%601> also helps you write a correct consuming method implementation.</span></span> <span data-ttu-id="7e939-183">Automaticky získáte kontroly za běhu, abyste se ujistili, že se nepokoušíte o přístup k vyrovnávací paměti nad zapůjčením vaší metody (Další informace najdete později).</span><span class="sxs-lookup"><span data-stu-id="7e939-183">You'll automatically get compile-time checks to ensure that you're not attempting to access the buffer beyond your method's lease (more on this later).</span></span>

<span data-ttu-id="7e939-184">V některých případech budete muset místo parametru <xref:System.Span%601> použít parametr <xref:System.Memory%601>, a to i v případě, že jste plně synchronně.</span><span class="sxs-lookup"><span data-stu-id="7e939-184">Sometimes, you'll have to use a <xref:System.Memory%601> parameter instead of a <xref:System.Span%601> parameter, even if you're fully synchronous.</span></span> <span data-ttu-id="7e939-185">Možná rozhraní API, které závisí, přijímá pouze <xref:System.Memory%601> argumentů.</span><span class="sxs-lookup"><span data-stu-id="7e939-185">Perhaps an API that you depend accepts only <xref:System.Memory%601> arguments.</span></span> <span data-ttu-id="7e939-186">Je to v pořádku, ale mějte na paměti, že při použití <xref:System.Memory%601> synchronně se jedná o kompromisy.</span><span class="sxs-lookup"><span data-stu-id="7e939-186">This is fine, but be aware of the tradeoffs involved when using <xref:System.Memory%601> synchronously.</span></span>

<a name="rule-2" />

<span data-ttu-id="7e939-187">**#2 pravidla: použijte ReadOnlySpan\<T > nebo ReadOnlyMemory\<T >, pokud by měla být vyrovnávací paměť jen pro čtení.**</span><span class="sxs-lookup"><span data-stu-id="7e939-187">**Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only.**</span></span>

<span data-ttu-id="7e939-188">V předchozích příkladech metoda `DisplayBufferToConsole` čte pouze z vyrovnávací paměti; neupravuje obsah vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7e939-188">In the earlier examples, the `DisplayBufferToConsole` method only reads from the buffer; it doesn't modify the contents of the buffer.</span></span> <span data-ttu-id="7e939-189">Signatura metody by se měla změnit na následující.</span><span class="sxs-lookup"><span data-stu-id="7e939-189">The method signature should be changed to the following.</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

<span data-ttu-id="7e939-190">V případě, že toto pravidlo a pravidlo kombinujeme #1, můžeme ještě lepší a přepsat signaturu metody následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="7e939-190">In fact, if we combine this rule and Rule #1, we can do even better and rewrite the method signature as follows:</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

<span data-ttu-id="7e939-191">Metoda `DisplayBufferToConsole` nyní funguje s prakticky všemi typy vyrovnávací paměti, které lze předcházet: `T[]`, úložiště přidělené [stackalloc](../../csharp/language-reference/operators/stackalloc.md)a tak dále.</span><span class="sxs-lookup"><span data-stu-id="7e939-191">The `DisplayBufferToConsole` method now works with virtually every buffer type imaginable: `T[]`, storage allocated with [stackalloc](../../csharp/language-reference/operators/stackalloc.md), and so on.</span></span> <span data-ttu-id="7e939-192">Můžete dokonce předat <xref:System.String> přímo na to!</span><span class="sxs-lookup"><span data-stu-id="7e939-192">You can even pass a <xref:System.String> directly into it!</span></span>

<span data-ttu-id="7e939-193">**#3 pravidla: Pokud vaše metoda přijímá paměť\<T > a vrátí `void`, nemusíte po návratu metody použít instanci paměti\<T >.**</span><span class="sxs-lookup"><span data-stu-id="7e939-193">**Rule #3: If your method accepts Memory\<T> and returns `void`, you must not use the Memory\<T> instance after your method returns.**</span></span>

<span data-ttu-id="7e939-194">To se týká konceptu zapůjčení uvedeného výše.</span><span class="sxs-lookup"><span data-stu-id="7e939-194">This relates to the "lease" concept mentioned earlier.</span></span> <span data-ttu-id="7e939-195">Zapůjčení metody vracející hodnotu void u <xref:System.Memory%601> instance začíná při zadání metody a končí při ukončení metody.</span><span class="sxs-lookup"><span data-stu-id="7e939-195">A void-returning method's lease on the <xref:System.Memory%601> instance begins when the method is entered, and it ends when the method exits.</span></span> <span data-ttu-id="7e939-196">Vezměte v úvahu následující příklad, který volá `Log` ve smyčce na základě vstupu z konzoly.</span><span class="sxs-lookup"><span data-stu-id="7e939-196">Consider the following example, which calls `Log` in a loop based on input from the console.</span></span>

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

<span data-ttu-id="7e939-197">Pokud je `Log` plně synchronní metodou, bude tento kód fungovat podle očekávání, protože v daném okamžiku existuje pouze jeden aktivní spotřebitel instance paměti.</span><span class="sxs-lookup"><span data-stu-id="7e939-197">If `Log` is a fully synchronous method, this code will behave as expected because there is only one active consumer of the memory instance at any given time.</span></span>
<span data-ttu-id="7e939-198">Ale představte si, že `Log` má tuto implementaci.</span><span class="sxs-lookup"><span data-stu-id="7e939-198">But imagine instead that `Log` has this implementation.</span></span>

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

<span data-ttu-id="7e939-199">V této implementaci `Log` porušuje své zapůjčení, protože se stále pokouší použít instanci <xref:System.Memory%601> na pozadí po vrácení původní metody.</span><span class="sxs-lookup"><span data-stu-id="7e939-199">In this implementation, `Log` violates its lease because it still attempts to use the <xref:System.Memory%601> instance in the background after the original method has returned.</span></span> <span data-ttu-id="7e939-200">Metoda `Main` by mohla způsobit vyrovnávací paměť, zatímco `Log` se z ní pokusí číst, což by mohlo vést k poškození dat.</span><span class="sxs-lookup"><span data-stu-id="7e939-200">The `Main` method could mutate the buffer while `Log` attempts to read from it, which could result in data corruption.</span></span>

<span data-ttu-id="7e939-201">Tuto chybu lze vyřešit několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="7e939-201">There are several ways to resolve this:</span></span>

- <span data-ttu-id="7e939-202">Metoda `Log` může vracet <xref:System.Threading.Tasks.Task> namísto `void`, jako následující implementace metody `Log`.</span><span class="sxs-lookup"><span data-stu-id="7e939-202">The `Log` method can return a <xref:System.Threading.Tasks.Task> instead of `void`, as the following implementation of the `Log` method does.</span></span>

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- <span data-ttu-id="7e939-203">místo toho `Log` možné implementovat následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="7e939-203">`Log` can instead be implemented as follows:</span></span>

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

<span data-ttu-id="7e939-204">**#4 pravidla: Pokud vaše metoda přijímá paměť\<T > a vrátí úlohu, po přechodu úlohy do stavu terminálu nemusíte používat instanci paměti\<T >.**</span><span class="sxs-lookup"><span data-stu-id="7e939-204">**Rule #4: If your method accepts a Memory\<T> and returns a Task, you must not use the Memory\<T> instance after the Task transitions to a terminal state.**</span></span>

<span data-ttu-id="7e939-205">Toto je pouze asynchronní varianta pravidla #3.</span><span class="sxs-lookup"><span data-stu-id="7e939-205">This is just the async variant of Rule #3.</span></span> <span data-ttu-id="7e939-206">Metodu `Log` z předchozího příkladu můžete zapsat takto, aby splňovala toto pravidlo:</span><span class="sxs-lookup"><span data-stu-id="7e939-206">The `Log` method from the earlier example can be written as follows to comply with this rule:</span></span>

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

<span data-ttu-id="7e939-207">V tomto případě "stav terminálu" znamená, že se úloha přechází do stavu dokončeno, chyba nebo zrušeno.</span><span class="sxs-lookup"><span data-stu-id="7e939-207">Here, "terminal state" means that the task transitions to a completed, faulted, or canceled state.</span></span> <span data-ttu-id="7e939-208">Jinými slovy "Terminal State" znamená "cokoli, co by způsobilo, že se očekává, že se má vyvolávat nebo pokračovat v provádění."</span><span class="sxs-lookup"><span data-stu-id="7e939-208">In other words, "terminal state" means "anything that would cause await to throw or to continue execution."</span></span>

<span data-ttu-id="7e939-209">Tento návod se vztahuje na metody, které vracejí <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>nebo jakýkoli podobný typ.</span><span class="sxs-lookup"><span data-stu-id="7e939-209">This guidance applies to methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>, or any similar type.</span></span>

<span data-ttu-id="7e939-210">**#5 pravidla: Pokud váš konstruktor přijímá paměť\<T > jako parametr, předpokládá se, že metody instance na vytvořeném objektu budou spotřebiteli instance paměti\<T >.**</span><span class="sxs-lookup"><span data-stu-id="7e939-210">**Rule #5: If your constructor accepts Memory\<T> as a parameter, instance methods on the constructed object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="7e939-211">Vezměte v úvahu následující příklad:</span><span class="sxs-lookup"><span data-stu-id="7e939-211">Consider the following example:</span></span>

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

<span data-ttu-id="7e939-212">V tomto případě konstruktor `OddValueExtractor` přijímá `ReadOnlyMemory<int>` jako parametr konstruktoru, takže samotný konstruktor je příjemcem instance `ReadOnlyMemory<int>` a všechny metody instance vrácené hodnoty jsou také příjemci původní instance `ReadOnlyMemory<int>`.</span><span class="sxs-lookup"><span data-stu-id="7e939-212">Here, the `OddValueExtractor` constructor accepts a `ReadOnlyMemory<int>` as a constructor parameter, so the constructor itself is a consumer of the `ReadOnlyMemory<int>` instance, and all instance methods on the returned value are also consumers of the original `ReadOnlyMemory<int>` instance.</span></span> <span data-ttu-id="7e939-213">To znamená, že `TryReadNextOddValue` spotřebovává `ReadOnlyMemory<int>` instanci, i když instance není předána přímo metodě `TryReadNextOddValue`.</span><span class="sxs-lookup"><span data-stu-id="7e939-213">This means that `TryReadNextOddValue` consumes the `ReadOnlyMemory<int>` instance, even though the instance isn't passed directly to the `TryReadNextOddValue` method.</span></span>

<span data-ttu-id="7e939-214">**#6 pravidla: Pokud máte ve svém typu nastavitelnou vlastnost\<T >-Type (nebo ekvivalentní metodu instance), předpokládá se, že metody instance tohoto objektu budou spotřebiteli instance paměti\<T >.**</span><span class="sxs-lookup"><span data-stu-id="7e939-214">**Rule #6: If you have a settable Memory\<T>-typed property (or an equivalent instance method) on your type, instance methods on that object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="7e939-215">Toto je opravdu pouze varianta pravidla #5.</span><span class="sxs-lookup"><span data-stu-id="7e939-215">This is really just a variant of Rule #5.</span></span> <span data-ttu-id="7e939-216">Toto pravidlo existuje, protože metody setter nebo ekvivalentní metody jsou považovány za zachycení a uchování jejich vstupů, takže metody instance u stejného objektu mohou využívat zachycený stav.</span><span class="sxs-lookup"><span data-stu-id="7e939-216">This rule exists because property setters or equivalent methods are assumed to capture and persist their inputs, so instance methods on the same object may utilize the captured state.</span></span>

<span data-ttu-id="7e939-217">Toto pravidlo se spustí v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="7e939-217">The following example triggers this rule:</span></span>

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

<span data-ttu-id="7e939-218">**#7 pravidla: Pokud máte > odkazem na\<IMemoryOwner, je potřeba, abyste ho odstranili nebo přenesli jeho vlastnictví (ale ne obojí).**</span><span class="sxs-lookup"><span data-stu-id="7e939-218">**Rule #7: If you have an IMemoryOwner\<T> reference, you must at some point dispose of it or transfer its ownership (but not both).**</span></span>

<span data-ttu-id="7e939-219">Vzhledem k tomu, že instance <xref:System.Memory%601> může být zajištěna buď spravovanou, nebo nespravovanou pamětí, musí vlastník volat <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>, pokud je dokončená práce na instanci <xref:System.Memory%601>.</span><span class="sxs-lookup"><span data-stu-id="7e939-219">Since a <xref:System.Memory%601> instance may be backed by either managed or unmanaged memory, the owner must call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> when work performed on the <xref:System.Memory%601> instance is complete.</span></span> <span data-ttu-id="7e939-220">Alternativně může vlastník přenést vlastnictví instance <xref:System.Buffers.IMemoryOwner%601> do jiné komponenty. v takovém případě se komponenta pro získání bude zodpovědná za volání <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> v příslušné době (Další informace najdete později).</span><span class="sxs-lookup"><span data-stu-id="7e939-220">Alternatively, the owner may transfer ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component, at which point the acquiring component becomes responsible for calling <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> at the appropriate time (more on this later).</span></span>

<span data-ttu-id="7e939-221">Selhání volání metody <xref:System.Buffers.MemoryPool%601.Dispose%2A> může vést k nevrácení nespravované paměti nebo jinému snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="7e939-221">Failure to call the <xref:System.Buffers.MemoryPool%601.Dispose%2A> method may lead to unmanaged memory leaks or other performance degradation.</span></span>

<span data-ttu-id="7e939-222">Toto pravidlo platí také pro kód, který volá metody objektu pro vytváření, jako je <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7e939-222">This rule also applies to code that calls factory methods like <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7e939-223">Volající se stane vlastníkem vráceného <xref:System.Buffers.IMemoryOwner%601> a zodpovídá za likvidaci instance po dokončení.</span><span class="sxs-lookup"><span data-stu-id="7e939-223">The caller becomes the owner of the returned <xref:System.Buffers.IMemoryOwner%601> and is responsible for disposing of the instance when finished.</span></span>

<span data-ttu-id="7e939-224">**#8 pravidla: Pokud máte na ploše rozhraní API parametr IMemoryOwner\<T >, přijímáte vlastnictví této instance.**</span><span class="sxs-lookup"><span data-stu-id="7e939-224">**Rule #8: If you have an IMemoryOwner\<T> parameter in your API surface, you are accepting ownership of that instance.**</span></span>

<span data-ttu-id="7e939-225">Přijetí instance tohoto typu signalizuje, že vaše komponenta zamýšlí převzít vlastnictví této instance.</span><span class="sxs-lookup"><span data-stu-id="7e939-225">Accepting an instance of this type signals that your component intends to take ownership of this instance.</span></span> <span data-ttu-id="7e939-226">Vaše komponenta se bude zodpovědná za řádné vyřazení podle pravidla #7.</span><span class="sxs-lookup"><span data-stu-id="7e939-226">Your component becomes responsible for proper disposal according to Rule #7.</span></span>

<span data-ttu-id="7e939-227">Jakákoli komponenta, která přenáší vlastnictví instance <xref:System.Buffers.IMemoryOwner%601> na jinou komponentu, by již neměla používat tuto instanci po dokončení volání metody.</span><span class="sxs-lookup"><span data-stu-id="7e939-227">Any component that transfers ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component should no longer use that instance after the method call completes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7e939-228">Pokud konstruktor přijímá <xref:System.Buffers.IMemoryOwner%601> jako parametr, jeho typ by měl implementovat <xref:System.IDisposable>a metoda <xref:System.IDisposable.Dispose%2A> by měla volat <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7e939-228">If your constructor accepts <xref:System.Buffers.IMemoryOwner%601> as a parameter, its type should implement <xref:System.IDisposable>, and your <xref:System.IDisposable.Dispose%2A> method should call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="7e939-229">**#9 pravidla: Pokud zabalíte synchronní metodu volání nespravovaného volání, rozhraní API by mělo jako parametr přijmout\<T >.**</span><span class="sxs-lookup"><span data-stu-id="7e939-229">**Rule #9: If you're wrapping a synchronous p/invoke method, your API should accept Span\<T> as a parameter.**</span></span>

<span data-ttu-id="7e939-230">V souladu s pravidly #1 je <xref:System.Span%601> správného typu, který se má použít pro synchronní rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="7e939-230">According to Rule #1, <xref:System.Span%601> is generally the correct type to use for synchronous APIs.</span></span> <span data-ttu-id="7e939-231">Instance <xref:System.Span%601> můžete připnout pomocí klíčového slova [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) , jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7e939-231">You can pin <xref:System.Span%601> instances via the [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) keyword, as in the following example.</span></span>

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

<span data-ttu-id="7e939-232">V předchozím příkladu může `pbData` mít hodnotu null, pokud je například vstupní rozpětí prázdné.</span><span class="sxs-lookup"><span data-stu-id="7e939-232">In the previous example, `pbData` can be null if, for example, the input span is empty.</span></span> <span data-ttu-id="7e939-233">Pokud exportovaná metoda naprosto vyžaduje, aby `pbData` být nenulové, i když je `cbData` 0, může být metoda implementována takto:</span><span class="sxs-lookup"><span data-stu-id="7e939-233">If the exported method absolutely requires that `pbData` be non-null, even if `cbData` is 0, the method can be implemented as follows:</span></span>

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

<span data-ttu-id="7e939-234">**#10 pravidla: Pokud zabalíte asynchronní metodu volání nespravovaného volání, rozhraní API by mělo jako parametr přijímat paměť\<T >.**</span><span class="sxs-lookup"><span data-stu-id="7e939-234">**Rule #10: If you're wrapping an asynchronous p/invoke method, your API should accept Memory\<T> as a parameter.**</span></span>

<span data-ttu-id="7e939-235">Vzhledem k tomu, že nemůžete použít klíčové slovo [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) napříč asynchronními operacemi, použijte metodu <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> k připnutí instancí <xref:System.Memory%601>, bez ohledu na druh souvislé paměti, kterou instance představuje.</span><span class="sxs-lookup"><span data-stu-id="7e939-235">Since you cannot use the [`fixed`](../../csharp/language-reference/keywords/fixed-statement.md) keyword across asynchronous operations, you use the <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> method to pin <xref:System.Memory%601> instances, regardless of the kind of contiguous memory the instance represents.</span></span> <span data-ttu-id="7e939-236">Následující příklad ukazuje, jak použít toto rozhraní API k provedení asynchronního volání volání nespravovaného volání.</span><span class="sxs-lookup"><span data-stu-id="7e939-236">The following example shows how to use this API to perform an asynchronous p/invoke call.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7e939-237">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e939-237">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
