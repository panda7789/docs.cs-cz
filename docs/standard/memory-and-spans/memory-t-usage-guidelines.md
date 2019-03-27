---
title: Paměť<T> a rozpětí<T> pokyny k používání
ms.date: 10/01/2018
helpviewer_keywords:
- Memory&lt;T&gt; and Span&lt;T&gt; best practices
- using Memory&lt;T&gt; and Span&lt;T&gt;
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e942b3f6f6572c05d42a0267f98e6c876a113616
ms.sourcegitcommit: 8258515adc6c37ab6278e5a3d102d593246f8672
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2019
ms.locfileid: "58504337"
---
# <a name="memoryt-and-spant-usage-guidelines"></a><span data-ttu-id="9d801-102">Paměť\<T > a rozpětí\<T > Pokyny k používání</span><span class="sxs-lookup"><span data-stu-id="9d801-102">Memory\<T> and Span\<T> usage guidelines</span></span>

<span data-ttu-id="9d801-103">.NET core obsahuje několik typů, které představují libovolné souvislých oblasti paměti.</span><span class="sxs-lookup"><span data-stu-id="9d801-103">.NET Core includes a number of types that represent an arbitrary contiguous region of memory.</span></span> <span data-ttu-id="9d801-104">.NET core 2.0 zavedené <xref:System.Span%601> a <xref:System.ReadOnlySpan%601>, které jsou zjednodušené paměti vyrovnávacích pamětí, které mohou být se opírá o spravované nebo nespravované paměti.</span><span class="sxs-lookup"><span data-stu-id="9d801-104">.NET Core 2.0 introduced <xref:System.Span%601> and <xref:System.ReadOnlySpan%601>, which are lightweight memory buffers that can be backed by managed or unmanaged memory.</span></span> <span data-ttu-id="9d801-105">Protože tyto typy mohou být uloženy do zásobníku, jsou vhodná pro řadu scénářů, včetně volání asynchronní metody.</span><span class="sxs-lookup"><span data-stu-id="9d801-105">Because these types can be stored on the stack, they are unsuitable for a number of scenarios, including asynchronous method calls.</span></span> <span data-ttu-id="9d801-106">.NET core 2.1 přidává několik dalších typů, včetně <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>, a <xref:System.Buffers.MemoryPool%601>.</span><span class="sxs-lookup"><span data-stu-id="9d801-106">.NET Core 2.1 adds a number of additional types, including <xref:System.Memory%601>, <xref:System.ReadOnlyMemory%601>, <xref:System.Buffers.IMemoryOwner%601>, and <xref:System.Buffers.MemoryPool%601>.</span></span> <span data-ttu-id="9d801-107">Stejně jako <xref:System.Span%601>, <xref:System.Memory%601> a jeho souvisejících typů může být zálohovaný pamětí spravovaných i nespravovaných.</span><span class="sxs-lookup"><span data-stu-id="9d801-107">Like <xref:System.Span%601>, <xref:System.Memory%601> and its related types can be backed by both managed and unmanaged memory.</span></span> <span data-ttu-id="9d801-108">Na rozdíl od <xref:System.Span%601>, <xref:System.Memory%601> se dají ukládat jenom na spravované haldě.</span><span class="sxs-lookup"><span data-stu-id="9d801-108">Unlike <xref:System.Span%601>, <xref:System.Memory%601> can only be stored on the managed heap.</span></span>

<span data-ttu-id="9d801-109">Obě <xref:System.Span%601> a <xref:System.Memory%601> vyrovnávací paměti strukturovaných dat, který lze použít v kanálech.</span><span class="sxs-lookup"><span data-stu-id="9d801-109">Both <xref:System.Span%601> and <xref:System.Memory%601> are buffers of structured data that can be used in pipelines.</span></span> <span data-ttu-id="9d801-110">To znamená, že jsou navržené tak, že některá nebo všechna data lze efektivněji předat komponenty v kanálu, které mohl zpracovat a volitelně změňte vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9d801-110">That is, they are designed so that some or all of the data can be efficiently passed to components in the pipeline, which can process them and optionally modify the buffer.</span></span> <span data-ttu-id="9d801-111">Protože <xref:System.Memory%601> a jeho souvisejících typů je přístupný podle více komponent nebo ve víc vláknech je důležité, že vývojáři postupovali podle některé standardní použití pokyny pro vytvoření robustního kódu.</span><span class="sxs-lookup"><span data-stu-id="9d801-111">Because <xref:System.Memory%601> and its related types can be accessed by multiple components or by multiple threads, it's important that developers follow some standard usage guidelines to produce robust code.</span></span>

## <a name="owners-consumers-and-lifetime-management"></a><span data-ttu-id="9d801-112">Vlastníci, uživatele a správa životního cyklu</span><span class="sxs-lookup"><span data-stu-id="9d801-112">Owners, consumers, and lifetime management</span></span>

<span data-ttu-id="9d801-113">Protože vyrovnávací paměti mohou být předány kolem mezi rozhraním API, a protože vyrovnávací paměti v některých případech je přístupný z více vláken, je důležité vzít v úvahu Správa životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="9d801-113">Since buffers can be passed around between APIs, and since buffers can sometimes be accessed from multiple threads, it's important to consider lifetime management.</span></span> <span data-ttu-id="9d801-114">Existují tři základní koncepty:</span><span class="sxs-lookup"><span data-stu-id="9d801-114">There are three core concepts:</span></span>

- <span data-ttu-id="9d801-115">**Vlastnictví**.</span><span class="sxs-lookup"><span data-stu-id="9d801-115">**Ownership**.</span></span> <span data-ttu-id="9d801-116">Vlastník instance vyrovnávací paměti je zodpovědný za správu životního cyklu, včetně zničení vyrovnávací paměti, když se už používá.</span><span class="sxs-lookup"><span data-stu-id="9d801-116">The owner of a buffer instance is responsible for lifetime management, including destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="9d801-117">Všechny vyrovnávací paměti mají jednoho vlastníka.</span><span class="sxs-lookup"><span data-stu-id="9d801-117">All buffers have a single owner.</span></span> <span data-ttu-id="9d801-118">Obecně vlastníka je komponenta, která vytvoří vyrovnávací paměti nebo vyrovnávací paměti, který přijal od objektu factory.</span><span class="sxs-lookup"><span data-stu-id="9d801-118">Generally the owner is the component that created the buffer or that received the buffer from a factory.</span></span> <span data-ttu-id="9d801-119">Lze také převést vlastnictví; **Komponenty A** můžete opustit ovládacího prvku vyrovnávací paměti pro **součást B**, v tomto okamžiku **komponenty A** může již nebudete používat vyrovnávací paměť, a **součást B**  zodpovědná za zničení vyrovnávací paměti, když se už používá.</span><span class="sxs-lookup"><span data-stu-id="9d801-119">Ownership can also be transferred; **Component-A** can relinquish control of the buffer to **Component-B**, at which point **Component-A** may no longer use the buffer, and **Component-B** becomes responsible for destroying the buffer when it's no longer in use.</span></span>

- <span data-ttu-id="9d801-120">**Spotřeba**.</span><span class="sxs-lookup"><span data-stu-id="9d801-120">**Consumption**.</span></span> <span data-ttu-id="9d801-121">Příjemce instanci vyrovnávací paměti může používat instanci vyrovnávací paměti čtení z něj a může být zápis do něj.</span><span class="sxs-lookup"><span data-stu-id="9d801-121">The consumer of a buffer instance is allowed to use the buffer instance by reading from it and possibly writing to it.</span></span> <span data-ttu-id="9d801-122">Vyrovnávací paměti může mít jednoho příjemce současně, pokud je k dispozici některé externí synchronizační mechanismus.</span><span class="sxs-lookup"><span data-stu-id="9d801-122">Buffers can have one consumer at a time unless some external synchronization mechanism is provided.</span></span> <span data-ttu-id="9d801-123">Upozorňujeme, že aktivní příjemce vyrovnávací paměť není nutně vlastníka přípravné vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9d801-123">Note that the active consumer of a buffer isn't necessarily the buffer's owner.</span></span>

- <span data-ttu-id="9d801-124">**Zapůjčení**.</span><span class="sxs-lookup"><span data-stu-id="9d801-124">**Lease**.</span></span> <span data-ttu-id="9d801-125">Zapůjčení je doba, kterou může být příjemce vyrovnávací paměti jednotlivých součástí.</span><span class="sxs-lookup"><span data-stu-id="9d801-125">The lease is the length of time that a particular component is allowed to be the consumer of the buffer.</span></span>

<span data-ttu-id="9d801-126">Následující příklad kódu pseudo znázorňuje tyto tři pojmy.</span><span class="sxs-lookup"><span data-stu-id="9d801-126">The following pseudo-code example illustrates these three concepts.</span></span> <span data-ttu-id="9d801-127">Zahrnuje `Main` metodu, která vytvoří instanci <xref:System.Memory%601> vyrovnávací paměti typu <xref:System.Char>, volání `WriteInt32ToBuffer` metody zapsat do vyrovnávací paměti a pak volá řetězcové vyjádření celého čísla `DisplayBufferToConsole` metodu pro zobrazení hodnoty vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="9d801-127">It includes a `Main` method that instantiates a <xref:System.Memory%601> buffer of type <xref:System.Char>, calls the `WriteInt32ToBuffer` method to write the string representation of an integer to the buffer, and then calls the `DisplayBufferToConsole` method to display the value of the buffer.</span></span>

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

<span data-ttu-id="9d801-128">`Main` Metoda vytvoří vyrovnávací paměti (v tomto případě <xref:System.Span%601> instance) a proto je jeho vlastníkem.</span><span class="sxs-lookup"><span data-stu-id="9d801-128">The `Main` method creates the buffer (in this case an <xref:System.Span%601> instance) and so is its owner.</span></span> <span data-ttu-id="9d801-129">Proto `Main` zodpovídá za zničení vyrovnávací paměti, když se už používá.</span><span class="sxs-lookup"><span data-stu-id="9d801-129">Therefore, `Main` is responsible for destroying the buffer when it's no longer in use.</span></span> <span data-ttu-id="9d801-130">Dělá to pomocí volání do vyrovnávací paměti <xref:System.Span%601.Clear?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="9d801-130">It does this by calling the buffer's <xref:System.Span%601.Clear?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="9d801-131">( <xref:System.Span%601.Clear> Metoda tady ve skutečnosti Vymaže vyrovnávací paměti; <xref:System.Span%601> struktury ve skutečnosti nemá metodu, která odstraní vyrovnávací paměti.)</span><span class="sxs-lookup"><span data-stu-id="9d801-131">(The <xref:System.Span%601.Clear> method here actually clears the buffer's memory; the <xref:System.Span%601> structure doesn't actually have a method that destroys the buffer.)</span></span>

<span data-ttu-id="9d801-132">Vyrovnávací paměť obsahuje dva zákazníky `WriteInt32ToBuffer` a `DisplayBufferToConsole`.</span><span class="sxs-lookup"><span data-stu-id="9d801-132">The buffer has two consumers, `WriteInt32ToBuffer` and `DisplayBufferToConsole`.</span></span> <span data-ttu-id="9d801-133">Existuje pouze jeden příjemce najednou (první `WriteInt32ToBuffer`, pak `DisplayBufferToConsole`), a ani spotřebitelů vlastní vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9d801-133">There is only one consumer at a time (first `WriteInt32ToBuffer`, then `DisplayBufferToConsole`), and neither of the consumers owns the buffer.</span></span> <span data-ttu-id="9d801-134">Všimněte si také, zda "příjemce" v tomto kontextu není implikují zobrazení jen pro čtení vyrovnávací paměti; příjemci přípravné vyrovnávací paměti obsah, upravit jako `WriteInt32ToBuffer` nedojde, pokud tento parametr zadaný zobrazení pro čtení a zápis vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9d801-134">Note also that "consumer" in this context doesn't imply a read-only view of the buffer; consumers can modify the buffer's contents, as `WriteInt32ToBuffer` does, if given a read/write view of the buffer.</span></span>

<span data-ttu-id="9d801-135">`WriteInt32ToBuffer` Metoda má zapůjčený (může spotřebovat) vyrovnávací paměť mezi začátkem volání metody a čas, metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="9d801-135">The `WriteInt32ToBuffer` method has a lease on (can consume) the buffer between the start of the method call and the time the method returns.</span></span> <span data-ttu-id="9d801-136">Obdobně `DisplayBufferToConsole` má zapůjčený vyrovnávací paměti, zatímco je prováděna a zapůjčení se uvolní, když metoda unwinds.</span><span class="sxs-lookup"><span data-stu-id="9d801-136">Similarly, `DisplayBufferToConsole` has a lease on the buffer while it's executing, and the lease is released when the method unwinds.</span></span> <span data-ttu-id="9d801-137">(Neexistuje žádné rozhraní API pro správu zapůjčení; "pronájmu" což je koncepční.)</span><span class="sxs-lookup"><span data-stu-id="9d801-137">(There is no API for lease management; a "lease" is a conceptual matter.)</span></span>

## <a name="memoryt-and-the-ownerconsumer-model"></a><span data-ttu-id="9d801-138">Paměť\<T > a model vlastníka/konzumenta najdete</span><span class="sxs-lookup"><span data-stu-id="9d801-138">Memory\<T> and the owner/consumer model</span></span>

<span data-ttu-id="9d801-139">Jako [vlastníky, uživatele a správa životního cyklu](#owners-consumers-and-lifetime-management) část poznámky, vyrovnávací paměti má vždy vlastníka.</span><span class="sxs-lookup"><span data-stu-id="9d801-139">As the [Owners, consumers, and lifetime management](#owners-consumers-and-lifetime-management) section notes, a buffer always has an owner.</span></span> <span data-ttu-id="9d801-140">.NET core podporuje dva modely vlastnictví:</span><span class="sxs-lookup"><span data-stu-id="9d801-140">.NET Core supports two ownership models:</span></span>

- <span data-ttu-id="9d801-141">Model, který podporuje jeden vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="9d801-141">A model that supports single ownership.</span></span> <span data-ttu-id="9d801-142">Vyrovnávací paměť nemá jednoho vlastníka pro celou dobu života.</span><span class="sxs-lookup"><span data-stu-id="9d801-142">A buffer has a single owner for its entire lifetime.</span></span>

- <span data-ttu-id="9d801-143">Model, který podporuje převod vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="9d801-143">A model that supports ownership transfer.</span></span> <span data-ttu-id="9d801-144">Vlastnictví vyrovnávací paměti lze přenést z jeho původní vlastníkovi (autorovi) do jiné součásti, která se pak stane zodpovědný za správu životního cyklu přípravné vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9d801-144">Ownership of a buffer can be transferred from its original owner (its creator) to another component, which then becomes responsible for the buffer's lifetime management.</span></span> <span data-ttu-id="9d801-145">Tento vlastník zase můžete převést vlastnictví na jiné součásti a tak dále.</span><span class="sxs-lookup"><span data-stu-id="9d801-145">That owner can in turn transfer ownership to another component, and so on.</span></span>

<span data-ttu-id="9d801-146">Můžete použít <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> rozhraní explicitně spravovat vlastnictví vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9d801-146">You use the <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType> interface to explicitly manage the ownership of a buffer.</span></span> <span data-ttu-id="9d801-147"><xref:System.Buffers.IMemoryOwner%601> podporuje oba modely vlastnictví.</span><span class="sxs-lookup"><span data-stu-id="9d801-147"><xref:System.Buffers.IMemoryOwner%601> supports both ownership models.</span></span> <span data-ttu-id="9d801-148">Komponenta, která má <xref:System.Buffers.IMemoryOwner%601> odkaz na vlastní vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9d801-148">The component that has an <xref:System.Buffers.IMemoryOwner%601> reference owns the buffer.</span></span> <span data-ttu-id="9d801-149">Následující příklad používá <xref:System.Buffers.IMemoryOwner%601?> instance tak, aby odrážely vlastnictví <xref:System.Memory%601> vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9d801-149">The following example uses an <xref:System.Buffers.IMemoryOwner%601?> instance to reflect the ownership of an <xref:System.Memory%601> buffer.</span></span>

[!code-csharp[ownership](~/samples/snippets/standard/buffers/memory-t/owner/owner.cs)]

<span data-ttu-id="9d801-150">Můžeme také napsat v tomto příkladu se [ `using` ](~/docs/csharp/language-reference/keywords/using-statement.md):</span><span class="sxs-lookup"><span data-stu-id="9d801-150">We can also write this example with the [`using`](~/docs/csharp/language-reference/keywords/using-statement.md):</span></span>

[!code-csharp[ownership-using](~/samples/snippets/standard/buffers/memory-t/owner-using/owner-using.cs)]

<span data-ttu-id="9d801-151">V tomto kódu:</span><span class="sxs-lookup"><span data-stu-id="9d801-151">In this code:</span></span>

- <span data-ttu-id="9d801-152">`Main` Metoda obsahuje odkaz na <xref:System.Buffers.IMemoryOwner%601> instance, takže `Main` metoda je vlastníkem vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9d801-152">The `Main` method holds the reference to the <xref:System.Buffers.IMemoryOwner%601> instance, so the `Main` method is the owner of the buffer.</span></span>

- <span data-ttu-id="9d801-153">`WriteInt32ToBuffer` a `DisplayBufferToConsole` metody přijímají xref:System.Memory%601 > jako veřejné rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="9d801-153">The `WriteInt32ToBuffer` and `DisplayBufferToConsole` methods accept xref:System.Memory%601> as a public API.</span></span> <span data-ttu-id="9d801-154">Proto jsou příjemci vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9d801-154">Therefore, they are consumers of the buffer.</span></span> <span data-ttu-id="9d801-155">A jsou pouze použít jeden po druhém.</span><span class="sxs-lookup"><span data-stu-id="9d801-155">And they only consume it one at a time.</span></span>

<span data-ttu-id="9d801-156">I když `WriteInt32ToBuffer` metoda se má zapsat hodnotu do vyrovnávací paměti, `DisplayBufferToConsole` není metoda.</span><span class="sxs-lookup"><span data-stu-id="9d801-156">Although the `WriteInt32ToBuffer` method is intended to write a value to the buffer, the `DisplayBufferToConsole` method isn't.</span></span> <span data-ttu-id="9d801-157">Tyto změny projeví na ho může přijali argument typu <xref:System.ReadOnlyMemory%601>.</span><span class="sxs-lookup"><span data-stu-id="9d801-157">To reflect this, it could have accepted an argument of type <xref:System.ReadOnlyMemory%601>.</span></span> <span data-ttu-id="9d801-158">Další informace o <xref:System.ReadOnlyMemory%601>, naleznete v tématu [pravidlo č. 2: Použít ReadOnlySpan\<T > nebo ReadOnlyMemory\<T > Pokud vyrovnávací paměť by měl být jen pro čtení](#rule-2).</span><span class="sxs-lookup"><span data-stu-id="9d801-158">For additional information on <xref:System.ReadOnlyMemory%601>, see [Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only](#rule-2).</span></span>

### <a name="ownerless-memoryt-instances"></a><span data-ttu-id="9d801-159">"Ownerless" paměti\<T > instancí</span><span class="sxs-lookup"><span data-stu-id="9d801-159">"Ownerless" Memory\<T> instances</span></span>

<span data-ttu-id="9d801-160">Můžete vytvořit <xref:System.Memory%601> instance bez použití <xref:System.Buffers.IMemoryOwner%601>.</span><span class="sxs-lookup"><span data-stu-id="9d801-160">You can create a <xref:System.Memory%601> instance without using <xref:System.Buffers.IMemoryOwner%601>.</span></span> <span data-ttu-id="9d801-161">V takovém případě vlastnictví vyrovnávací paměti je implicitní namísto explicitního a pouze jednoho vlastníka model se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="9d801-161">In this case, ownership of the buffer is implicit rather than explicit, and only the single-owner model is supported.</span></span> <span data-ttu-id="9d801-162">Uděláte to tak:</span><span class="sxs-lookup"><span data-stu-id="9d801-162">You can do this by:</span></span>

- <span data-ttu-id="9d801-163">Volání jedné z <xref:System.Memory%601> konstruktory přímo, předejte `T[]`, stejně jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9d801-163">Calling one of the  <xref:System.Memory%601> constructors directly, passing in a `T[]`, as the following example does.</span></span>

- <span data-ttu-id="9d801-164">Volání [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) metodu rozšíření k vytvoření `ReadOnlyMemory<char>` instance.</span><span class="sxs-lookup"><span data-stu-id="9d801-164">Calling the [String.AsMemory](xref:System.MemoryExtensions.AsMemory(System.String)) extension method to produce a `ReadOnlyMemory<char>` instance.</span></span>

[!code-csharp[ownerless-memory](~/samples/snippets/standard/buffers/memory-t/ownerless/ownerless.cs)]

<span data-ttu-id="9d801-165">Metoda, která původně vytvoří <xref:System.Memory%601> instance je vlastníkem implicitní vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9d801-165">The method that initially creates the <xref:System.Memory%601> instance is the implicit owner of the buffer.</span></span> <span data-ttu-id="9d801-166">Vlastnictví nelze přenést na jakoukoli jinou součástí, protože neexistuje žádný <xref:System.Buffers.IMemoryOwner%601> instance pro usnadnění převodu.</span><span class="sxs-lookup"><span data-stu-id="9d801-166">Ownership cannot be transferred to any other component because there is no <xref:System.Buffers.IMemoryOwner%601> instance to facilitate the transfer.</span></span> <span data-ttu-id="9d801-167">(Alternativně si můžete také představit, že modul runtime systému uvolňování paměti vlastní vyrovnávací paměti a všechny metody právě využití vyrovnávací paměti.)</span><span class="sxs-lookup"><span data-stu-id="9d801-167">(As an alternative, you can also imagine that the runtime's garbage collector owns the buffer, and all methods just consume the buffer.)</span></span>

## <a name="usage-guidelines"></a><span data-ttu-id="9d801-168">Pokyny k používání</span><span class="sxs-lookup"><span data-stu-id="9d801-168">Usage guidelines</span></span>

<span data-ttu-id="9d801-169">Protože bloku paměti vlastní, ale má být předán více komponent, některé z nich může pracovat současně na blok paměti konkrétní, je důležité stanovit pokyny k používání obou <xref:System.Memory%601> a <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="9d801-169">Because a memory block is owned but is intended to be passed to multiple components, some of which may operate upon a particular memory block simultaneously, it is important to establish guidelines for using both <xref:System.Memory%601> and <xref:System.Span%601>.</span></span>  <span data-ttu-id="9d801-170">Pokyny jsou nezbytné protože:</span><span class="sxs-lookup"><span data-stu-id="9d801-170">Guidelines are necessary because:</span></span>

- <span data-ttu-id="9d801-171">Je možné pro součást zachovat odkaz na blok paměti po její vlastník vydala.</span><span class="sxs-lookup"><span data-stu-id="9d801-171">It is possible for a component to retain a reference to a memory block after its owner has released it.</span></span>

- <span data-ttu-id="9d801-172">Je možné pro součást ovládajících vyrovnávací paměti ve stejnou dobu, která funguje jiné součásti, v procesu došlo k poškození dat ve vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9d801-172">It is possible for a component to operate on a buffer at the same time that another component is operating on it, in the process corrupting the data in the buffer.</span></span>

- <span data-ttu-id="9d801-173">Zatímco povahy přidělený na zásobník <xref:System.Span%601> optimalizuje výkon a zpřístupňuje <xref:System.Span%601> upřednostňovaný typ pro provozování na blok paměti je také Predmety <xref:System.Span%601> na určitá omezení hlavní omezení.</span><span class="sxs-lookup"><span data-stu-id="9d801-173">While the stack-allocated nature of <xref:System.Span%601> optimizes performance and makes <xref:System.Span%601> the preferred type for operating on a memory block, it also subjects <xref:System.Span%601> to some major restrictions restrictions.</span></span> <span data-ttu-id="9d801-174">Je důležité vědět, kdy se má použít <xref:System.Span%601> a kdy použít <xref:System.Memory%601>.</span><span class="sxs-lookup"><span data-stu-id="9d801-174">It is important to know when to use a <xref:System.Span%601> and when to use <xref:System.Memory%601>.</span></span>

<span data-ttu-id="9d801-175">Toto jsou naše doporučení pro používání úspěšně <xref:System.Memory%601> a jeho souvisejících typů.</span><span class="sxs-lookup"><span data-stu-id="9d801-175">The following are our recommendations for successfully using <xref:System.Memory%601> and its related types.</span></span> <span data-ttu-id="9d801-176">Mějte na paměti tyto pokyny, které platí pro <xref:System.Memory%601> a <xref:System.Span%601> platí také pro <xref:System.ReadOnlyMemory%601> a <xref:System.ReadOnlySpan%601> Pokud jsme explicitně mějte na paměti jinak.</span><span class="sxs-lookup"><span data-stu-id="9d801-176">Note that guidance that applies to <xref:System.Memory%601> and <xref:System.Span%601> also applies to <xref:System.ReadOnlyMemory%601> and <xref:System.ReadOnlySpan%601> unless we explicitly note otherwise.</span></span>

<span data-ttu-id="9d801-177">**Pravidlo #1: Synchronní rozhraní API, použijte Span\<T > místo v paměti\<T > jako parametr, pokud je to možné.**</span><span class="sxs-lookup"><span data-stu-id="9d801-177">**Rule #1: For a synchronous API, use Span\<T> instead of Memory\<T> as a parameter if possible.**</span></span>

<span data-ttu-id="9d801-178"><xref:System.Span%601> nabízí větší variabilitu než <xref:System.Memory%601> a může představovat širší vyrovnávacích pamětí souvislé paměti.</span><span class="sxs-lookup"><span data-stu-id="9d801-178"><xref:System.Span%601> is more versatile than <xref:System.Memory%601> and can represent a wider variety of contiguous memory buffers.</span></span> <span data-ttu-id="9d801-179"><xref:System.Span%601> také nabízí vyšší výkon než <xref:System.Memory%601>>.</span><span class="sxs-lookup"><span data-stu-id="9d801-179"><xref:System.Span%601> also offers better performance than <xref:System.Memory%601>>.</span></span> <span data-ttu-id="9d801-180">Nakonec můžete použít <xref:System.Memory%601.Span?displayProperty=nameWithType> vlastnost převést <xref:System.Memory%601> instance na <xref:System.Span%601>, i když Span\<T > - na - paměti\<T > Převod není možný.</span><span class="sxs-lookup"><span data-stu-id="9d801-180">Finally, you can use the <xref:System.Memory%601.Span?displayProperty=nameWithType> property to convert a <xref:System.Memory%601> instance to a <xref:System.Span%601>, although Span\<T>-to-Memory\<T> conversion isn't possible.</span></span> <span data-ttu-id="9d801-181">Pokud vaše volající náhodou <xref:System.Memory%601> instance, budou moct volat vaše metody s atributem <xref:System.Span%601> parametry přesto.</span><span class="sxs-lookup"><span data-stu-id="9d801-181">So if your callers happen to have a <xref:System.Memory%601> instance, they'll be able to call your methods with <xref:System.Span%601> parameters anyway.</span></span>

<span data-ttu-id="9d801-182">Pomocí parametru typu <xref:System.Span%601> místo typu <xref:System.Memory%601> také umožňuje zapisovat správná implementace metody náročné.</span><span class="sxs-lookup"><span data-stu-id="9d801-182">Using a parameter of type <xref:System.Span%601> instead of type <xref:System.Memory%601> also helps you write a correct consuming method implementation.</span></span> <span data-ttu-id="9d801-183">Získáte automaticky kontroluje za kompilace, ujistěte se, že se o přístup k vyrovnávací paměti nad rámec vaše metoda zapůjčení, (více dále).</span><span class="sxs-lookup"><span data-stu-id="9d801-183">You'll automatically get compile-time checks to ensure that you're not attempting to access the buffer beyond your method's lease (more on this later).</span></span>

<span data-ttu-id="9d801-184">V některých případech budete muset použít <xref:System.Memory%601> parametr namísto <xref:System.Span%601> parametr, i když jste plně synchronní.</span><span class="sxs-lookup"><span data-stu-id="9d801-184">Sometimes, you'll have to use a <xref:System.Memory%601> parameter instead of a <xref:System.Span%601> parameter, even if you're fully synchronous.</span></span> <span data-ttu-id="9d801-185">Například rozhraní API, které nejvíc potřebujete přijímá pouze <xref:System.Memory%601> argumenty.</span><span class="sxs-lookup"><span data-stu-id="9d801-185">Perhaps an API that you depend accepts only <xref:System.Memory%601> arguments.</span></span> <span data-ttu-id="9d801-186">To je v pořádku, ale mějte na paměti o kompromisech při použití <xref:System.Memory%601> synchronně.</span><span class="sxs-lookup"><span data-stu-id="9d801-186">This is fine, but be aware of the tradeoffs involved when using <xref:System.Memory%601> synchronously.</span></span>

<a name="rule-2" />

<span data-ttu-id="9d801-187">**Pravidlo #2: Použít ReadOnlySpan\<T > nebo ReadOnlyMemory\<T > Pokud vyrovnávací paměť by měl být jen pro čtení.**</span><span class="sxs-lookup"><span data-stu-id="9d801-187">**Rule #2: Use ReadOnlySpan\<T> or ReadOnlyMemory\<T> if the buffer should be read-only.**</span></span>

<span data-ttu-id="9d801-188">V předchozích příkladech `DisplayBufferToConsole` metoda četl pouze z vyrovnávací paměti; nezmění obsah vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9d801-188">In the earlier examples, the `DisplayBufferToConsole` method only reads from the buffer; it doesn't modify the contents of the buffer.</span></span> <span data-ttu-id="9d801-189">Podpis metody by měl být změněn na následující.</span><span class="sxs-lookup"><span data-stu-id="9d801-189">The method signature should be changed to the following.</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlyMemory<char> buffer);
```

<span data-ttu-id="9d801-190">Ve skutečnosti Pokud spojili jsme toto pravidlo a pravidlo č. 1, můžeme udělat ještě lépe a přepíše podpis metody následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9d801-190">In fact, if we combine this rule and Rule #1, we can do even better and rewrite the method signature as follows:</span></span>

```csharp
void DisplayBufferToConsole(ReadOnlySpan<char> buffer);
```

<span data-ttu-id="9d801-191">`DisplayBufferToConsole` Metoda nyní funguje s prakticky všem typ vyrovnávací paměti, který si dokážete představit: `T[]`, přidělit úložiště [stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md), a tak dále.</span><span class="sxs-lookup"><span data-stu-id="9d801-191">The `DisplayBufferToConsole` method now works with virtually every buffer type imaginable: `T[]`, storage allocated with [stackalloc](~/docs/csharp/language-reference/keywords/stackalloc.md), and so on.</span></span> <span data-ttu-id="9d801-192">Dokonce můžete předat <xref:System.String> přímo do ní!</span><span class="sxs-lookup"><span data-stu-id="9d801-192">You can even pass a <xref:System.String> directly into it!</span></span>

<span data-ttu-id="9d801-193">**Pravidlo #3: Pokud vaše metoda přijímá paměti\<T > a vrátí `void`, nesmí používat paměť\<T > po vrácení metodu instance.**</span><span class="sxs-lookup"><span data-stu-id="9d801-193">**Rule #3: If your method accepts Memory\<T> and returns `void`, you must not use the Memory\<T> instance after your method returns.**</span></span>

<span data-ttu-id="9d801-194">To se týká koncept "pronájmu", již bylo zmíněno dříve.</span><span class="sxs-lookup"><span data-stu-id="9d801-194">This relates to the "lease" concept mentioned earlier.</span></span> <span data-ttu-id="9d801-195">Metody vracející hodnotu void zapůjčení <xref:System.Memory%601> instance začíná, když se zadá metodu a končí při ukončení metodu.</span><span class="sxs-lookup"><span data-stu-id="9d801-195">A void-returning method's lease on the <xref:System.Memory%601> instance begins when the method is entered, and it ends when the method exits.</span></span> <span data-ttu-id="9d801-196">Podívejte se na následující příklad volá `Log` ve smyčce založena na vstup z konzoly.</span><span class="sxs-lookup"><span data-stu-id="9d801-196">Consider the following example, which calls `Log` in a loop based on input from the console.</span></span>

[!code-csharp[void-returning](~/samples/snippets/standard/buffers/memory-t/void-returning/void-returning.cs#1)]

<span data-ttu-id="9d801-197">Pokud `Log` je plně synchronní metoda, tento kód se bude chovat podle očekávání, protože existuje pouze jeden příjemce aktivní instance paměti v daném okamžiku.</span><span class="sxs-lookup"><span data-stu-id="9d801-197">If `Log` is a fully synchronous method, this code will behave as expected because there is only one active consumer of the memory instance at any given time.</span></span>
<span data-ttu-id="9d801-198">Ale Představte si, že `Log` má tuto implementaci.</span><span class="sxs-lookup"><span data-stu-id="9d801-198">But imagine instead that `Log` has this implementation.</span></span>

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

<span data-ttu-id="9d801-199">V této implementaci `Log` porušuje jeho zapůjčení, protože pořád se pokouší použít <xref:System.Memory%601> instance na pozadí po vrátila původní metodu.</span><span class="sxs-lookup"><span data-stu-id="9d801-199">In this implementation, `Log` violates its lease because it still attempts to use the <xref:System.Memory%601> instance in the background after the original method has returned.</span></span> <span data-ttu-id="9d801-200">`Main` Metoda může mutovat vyrovnávací paměti při `Log` pokouší číst z něj, což by mohlo způsobit poškození dat.</span><span class="sxs-lookup"><span data-stu-id="9d801-200">The `Main` method could mutate the buffer while `Log` attempts to read from it, which could result in data corruption.</span></span>

<span data-ttu-id="9d801-201">Chcete-li to vyřešit několika způsoby:</span><span class="sxs-lookup"><span data-stu-id="9d801-201">There are several ways to resolve this:</span></span>

- <span data-ttu-id="9d801-202">`Log` Metoda může vrátit <xref:System.Threading.Tasks.Task> místo `void`, jako následující provádění `Log` metodu.</span><span class="sxs-lookup"><span data-stu-id="9d801-202">The `Log` method can return a <xref:System.Threading.Tasks.Task> instead of `void`, as the following implementation of the `Log` method does.</span></span>

   [!code-csharp[task-returning](~/samples/snippets/standard/buffers/memory-t/task-returning2/task-returning2.cs#1)]

- <span data-ttu-id="9d801-203">`Log` můžete místo toho implementovat následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9d801-203">`Log` can instead be implemented as follows:</span></span>

   [!code-csharp[defensive-copy](~/samples/snippets/standard/buffers/memory-t/task-returning/task-returning.cs#1)]

<span data-ttu-id="9d801-204">**Pravidlo #4: Pokud vaše metoda přijímá paměťově\<T > a vrátí úlohu, nesmí používat paměť\<T > instance za úkol přejde do konečného stavu.**</span><span class="sxs-lookup"><span data-stu-id="9d801-204">**Rule #4: If your method accepts a Memory\<T> and returns a Task, you must not use the Memory\<T> instance after the Task transitions to a terminal state.**</span></span>

<span data-ttu-id="9d801-205">Toto je pouze asynchronní variantu pravidlo č. 3.</span><span class="sxs-lookup"><span data-stu-id="9d801-205">This is just the async variant of Rule #3.</span></span> <span data-ttu-id="9d801-206">`Log` Metoda z předchozího příkladu je pro dosažení souladu s tímto pravidlem zapisovat následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9d801-206">The `Log` method from the earlier example can be written as follows to comply with this rule:</span></span>

[!code-csharp[task-returning-async](~/samples/snippets/standard/buffers/memory-t/void-returning-async/void-returning-async.cs#1)]

<span data-ttu-id="9d801-207">Tady "konečného stavu" znamená, že úkol přejde do dokončeného, došlo k chybě, nebo bylo zrušeno stavu.</span><span class="sxs-lookup"><span data-stu-id="9d801-207">Here, "terminal state" means that the task transitions to a completed, faulted, or canceled state.</span></span> <span data-ttu-id="9d801-208">Jinými slovy znamená, že "konečného stavu" "cokoli, co způsobilo await vyvolat nebo pokračovat v provádění."</span><span class="sxs-lookup"><span data-stu-id="9d801-208">In other words, "terminal state" means "anything that would cause await to throw or to continue execution."</span></span>

<span data-ttu-id="9d801-209">Tento návod se vztahuje k metody, které vracejí <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>, nebo podobné.</span><span class="sxs-lookup"><span data-stu-id="9d801-209">This guidance applies to methods that return <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.ValueTask%601>, or any similar type.</span></span>

<span data-ttu-id="9d801-210">**Pravidlo #5: Pokud váš konstruktor přijímá paměti\<T > jako parametr, metodami instance vytvořený objekt se předpokládá se, že příjemci paměti\<T > instance.**</span><span class="sxs-lookup"><span data-stu-id="9d801-210">**Rule #5: If your constructor accepts Memory\<T> as a parameter, instance methods on the constructed object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="9d801-211">Vezměte v úvahu v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9d801-211">Consider the following example:</span></span>

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

<span data-ttu-id="9d801-212">Tady `OddValueExtractor` konstruktor přijímá `ReadOnlyMemory<int>` jako parametr konstruktoru, takže konstruktor samotný je příjemce `ReadOnlyMemory<int>` instance a metodami instance na vrácené hodnoty jsou také příjemci původní `ReadOnlyMemory<int>` instance.</span><span class="sxs-lookup"><span data-stu-id="9d801-212">Here, the `OddValueExtractor` constructor accepts a `ReadOnlyMemory<int>` as a constructor parameter, so the constructor itself is a consumer of the `ReadOnlyMemory<int>` instance, and all instance methods on the returned value are also consumers of the original `ReadOnlyMemory<int>` instance.</span></span> <span data-ttu-id="9d801-213">To znamená, že `TryReadNextOddValue` využívá `ReadOnlyMemory<int>` instance, i když instance není předána přímo `TryReadNextOddValue` metody.</span><span class="sxs-lookup"><span data-stu-id="9d801-213">This means that `TryReadNextOddValue` consumes the `ReadOnlyMemory<int>` instance, even though the instance isn't passed directly to the `TryReadNextOddValue` method.</span></span>

<span data-ttu-id="9d801-214">**Pravidlo #6: Pokud máte nastavitelné paměti\<T >-typovou vlastnost (nebo metodu ekvivalentní instance) na typ, metodami instance tohoto objektu se předpokládá se, že příjemci paměti\<T > instance.**</span><span class="sxs-lookup"><span data-stu-id="9d801-214">**Rule #6: If you have a settable Memory\<T>-typed property (or an equivalent instance method) on your type, instance methods on that object are assumed to be consumers of the Memory\<T> instance.**</span></span>

<span data-ttu-id="9d801-215">Toto je pouze typ variant pravidlo č. 5.</span><span class="sxs-lookup"><span data-stu-id="9d801-215">This is really just a variant of Rule #5.</span></span> <span data-ttu-id="9d801-216">Toto pravidlo existuje, protože vlastnost setter nebo ekvivalentní metody předpokládá, že jsou pro zaznamenání a uložení jejich vstupech tak metody instance na stejný objekt mohou využívat zaznamenaný stav.</span><span class="sxs-lookup"><span data-stu-id="9d801-216">This rule exists because property setters or equivalent methods are assumed to capture and persist their inputs, so instance methods on the same object may utilize the captured state.</span></span>

<span data-ttu-id="9d801-217">Následující příklad spustí toto pravidlo:</span><span class="sxs-lookup"><span data-stu-id="9d801-217">The following example triggers this rule:</span></span>

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

<span data-ttu-id="9d801-218">**Pravidlo #7: Pokud máte IMemoryOwner\<T > odkaz, je nutné na některé bodu dispose jeho nebo přenos vlastnictví (ale ne obojí).**</span><span class="sxs-lookup"><span data-stu-id="9d801-218">**Rule #7: If you have an IMemoryOwner\<T> reference, you must at some point dispose of it or transfer its ownership (but not both).**</span></span>

<span data-ttu-id="9d801-219">Protože <xref:System.Memory%601> instance může být zálohovaný pamětí spravované nebo nespravované, musí volat vlastníka <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> provést, při práci na <xref:System.Memory%601> instance je dokončena.</span><span class="sxs-lookup"><span data-stu-id="9d801-219">Since a <xref:System.Memory%601> instance may be backed by either managed or unmanaged memory, the owner must call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> when work performed on the <xref:System.Memory%601> instance is complete.</span></span> <span data-ttu-id="9d801-220">Alternativně může vlastník přenos vlastnictví <xref:System.Buffers.IMemoryOwner%601> instance na jinou komponentu, v tomto okamžiku nabývající součást zodpovědná za volání <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> včas (podrobněji dále).</span><span class="sxs-lookup"><span data-stu-id="9d801-220">Alternatively, the owner may transfer ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component, at which point the acquiring component becomes responsible for calling <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType> at the appropriate time (more on this later).</span></span>

<span data-ttu-id="9d801-221">Nepodařilo se zavolat <xref:System.Buffers.MemoryPool%601.Dispose%2A> metoda může vést k nevracení nespravované paměti nebo jiných snížení výkonu.</span><span class="sxs-lookup"><span data-stu-id="9d801-221">Failure to call the <xref:System.Buffers.MemoryPool%601.Dispose%2A> method may lead to unmanaged memory leaks or other performance degradation.</span></span>

<span data-ttu-id="9d801-222">Toto pravidlo platí také pro kód, který volá metody pro vytváření objektů jako <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9d801-222">This rule also applies to code that calls factory methods like <xref:System.Buffers.MemoryPool%601.Rent%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9d801-223">Volající se stává vlastníkem vráceného <xref:System.Buffers.IMemoryOwner%601> a je zodpovědná za uvolnění instance po dokončení.</span><span class="sxs-lookup"><span data-stu-id="9d801-223">The caller becomes the owner of the returned <xref:System.Buffers.IMemoryOwner%601> and is responsible for disposing of the instance when finished.</span></span>

<span data-ttu-id="9d801-224">**Pravidlo #8: Pokud máte IMemoryOwner\<T > parametr povrchu vaše rozhraní API, abyste přijali vlastnictví této instance.**</span><span class="sxs-lookup"><span data-stu-id="9d801-224">**Rule #8: If you have an IMemoryOwner\<T> parameter in your API surface, you are accepting ownership of that instance.**</span></span>

<span data-ttu-id="9d801-225">Přijímá instanci tohoto typu signalizuje, že vaše komponenta si klade za cíl převzít vlastnictví této instance.</span><span class="sxs-lookup"><span data-stu-id="9d801-225">Accepting an instance of this type signals that your component intends to take ownership of this instance.</span></span> <span data-ttu-id="9d801-226">Vaše komponenta je zodpovědná za správné odstranění podle pravidlo č. 7.</span><span class="sxs-lookup"><span data-stu-id="9d801-226">Your component becomes responsible for proper disposal according to Rule #7.</span></span>

<span data-ttu-id="9d801-227">Jakékoli součásti, která převede vlastnictví <xref:System.Buffers.IMemoryOwner%601> instance na jinou komponentu byste již nebudete používat tuto instanci po dokončení volání metody.</span><span class="sxs-lookup"><span data-stu-id="9d801-227">Any component that transfers ownership of the <xref:System.Buffers.IMemoryOwner%601> instance to a different component should no longer use that instance after the method call completes.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9d801-228">Pokud váš konstruktor přijímá <xref:System.Buffers.IMemoryOwner%601> jako parametr, jeho typ by měly implementovat <xref:System.IDisposable>a vaše <xref:System.IDisposable.Dispose%2A> metoda by měla volat <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="9d801-228">If your constructor accepts <xref:System.Buffers.IMemoryOwner%601> as a parameter, its type should implement <xref:System.IDisposable>, and your <xref:System.IDisposable.Dispose%2A> method should call <xref:System.Buffers.MemoryPool%601.Dispose%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="9d801-229">**Pravidlo #9: Chcete-li obtékání metodu synchronní p/invoke, vaše rozhraní API by měla přijímat rozpětí\<T > jako parametr.**</span><span class="sxs-lookup"><span data-stu-id="9d801-229">**Rule #9: If you're wrapping a synchronous p/invoke method, your API should accept Span\<T> as a parameter.**</span></span>

<span data-ttu-id="9d801-230">Podle pravidel č. 1 <xref:System.Span%601> je obecně správný typ má být použit pro synchronní rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="9d801-230">According to Rule #1, <xref:System.Span%601> is generally the correct type to use for synchronous APIs.</span></span> <span data-ttu-id="9d801-231">Můžete připnout <xref:System.Span%601> \<T > přes instance [ `fixed` ](~/docs/csharp/language-reference/keywords/fixed-statement.md) – klíčové slovo, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9d801-231">You can pin <xref:System.Span%601>\<T> instances via the [`fixed`](~/docs/csharp/language-reference/keywords/fixed-statement.md) keyword, as in the following example.</span></span>

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

<span data-ttu-id="9d801-232">V předchozím příkladu `pbData` může mít hodnotu null, je-li například, vstupní značka je prázdný.</span><span class="sxs-lookup"><span data-stu-id="9d801-232">In the previous example, `pbData` can be null if, for example, the input span is empty.</span></span> <span data-ttu-id="9d801-233">Pokud exportované metoda naprosto vyžaduje, aby `pbData` mít hodnotu null, i když `cbData` je 0, metody lze provést následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="9d801-233">If the exported method absolutely requires that `pbData` be non-null, even if `cbData` is 0, the method can be implemented as follows:</span></span>

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

<span data-ttu-id="9d801-234">**Pravidlo #10: Chcete-li obtékání metody asynchronní p/invoke, vaše rozhraní API by měla přijímat paměti\<T > jako parametr.**</span><span class="sxs-lookup"><span data-stu-id="9d801-234">**Rule #10: If you're wrapping an asynchronous p/invoke method, your API should accept Memory\<T> as a parameter.**</span></span>

<span data-ttu-id="9d801-235">Protože nelze použít [ `fixed` ](~/docs/csharp/language-reference/keywords/fixed-statement.md) – klíčové slovo v asynchronních operací, je použít <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> metodu pro Připnutí <xref:System.Memory%601> instancí, bez ohledu na typ, který představuje instanci souvislé paměti.</span><span class="sxs-lookup"><span data-stu-id="9d801-235">Since you cannot use the [`fixed`](~/docs/csharp/language-reference/keywords/fixed-statement.md) keyword across asynchronous operations, you use the <xref:System.Memory%601.Pin%2A?displayProperty=nameWithType> method to pin <xref:System.Memory%601> instances, regardless of the kind of contiguous memory the instance represents.</span></span> <span data-ttu-id="9d801-236">Následující příklad ukazuje, jak pomocí tohoto rozhraní API provádět volání rozhraní asynchronní p/invoke.</span><span class="sxs-lookup"><span data-stu-id="9d801-236">The following example shows how to use this API to perform an asynchronous p/invoke call.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9d801-237">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d801-237">See also</span></span>

- <xref:System.Memory%601?displayProperty=nameWithType>
- <xref:System.Buffers.IMemoryOwner%601?displayProperty=nameWithType>
- <xref:System.Span%601?displayProperty=nameWithType>
