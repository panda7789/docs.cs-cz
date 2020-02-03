---
title: Nativní osvědčené postupy interoperability – .NET
description: Seznamte se s osvědčenými postupy pro propojení s nativními komponentami v .NET.
ms.date: 01/18/2019
ms.openlocfilehash: 9486256b815856c0c283f5fe231be3d35d6e8f00
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742747"
---
# <a name="native-interoperability-best-practices"></a><span data-ttu-id="ccbbf-103">Nativní osvědčené postupy interoperability</span><span class="sxs-lookup"><span data-stu-id="ccbbf-103">Native interoperability best practices</span></span>

<span data-ttu-id="ccbbf-104">.NET nabízí různé způsoby přizpůsobení nativního kódu interoperability.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-104">.NET gives you a variety of ways to customize your native interoperability code.</span></span> <span data-ttu-id="ccbbf-105">Tento článek obsahuje pokyny, které tým .NET Microsoftu sleduje pro zajištění nativní interoperability.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-105">This article includes the guidance that Microsoft's .NET teams follow for native interoperability.</span></span>

## <a name="general-guidance"></a><span data-ttu-id="ccbbf-106">Obecné pokyny</span><span class="sxs-lookup"><span data-stu-id="ccbbf-106">General guidance</span></span>

<span data-ttu-id="ccbbf-107">Pokyny v této části se vztahují na všechny scénáře spolupráce.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-107">The guidance in this section applies to all interop scenarios.</span></span>

- <span data-ttu-id="ccbbf-108">✔️ použít stejné názvy a velká písmena pro vaše metody a parametry jako nativní metodu, kterou chcete volat.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-108">✔️ DO use the same naming and capitalization for your methods and parameters as the native method you want to call.</span></span>
- <span data-ttu-id="ccbbf-109">✔️ Zvažte použití stejných názvů a velkých a malých písmen pro konstantní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-109">✔️ CONSIDER using the same naming and capitalization for constant values.</span></span>
- <span data-ttu-id="ccbbf-110">✔️ použít typy .NET, které jsou mapovány nejblíže k nativnímu typu.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-110">✔️ DO use .NET types that map closest to the native type.</span></span> <span data-ttu-id="ccbbf-111">Například v C#nástroji použijte `uint`, pokud je nativní typ `unsigned int`.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-111">For example, in C#, use `uint` when the native type is `unsigned int`.</span></span>
- <span data-ttu-id="ccbbf-112">✔️ použít pouze atributy `[In]` a `[Out]`, pokud se chování, které požadujete, se liší od výchozího chování.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-112">✔️ DO only use `[In]` and `[Out]` attributes when the behavior you want differs from the default behavior.</span></span>
- <span data-ttu-id="ccbbf-113">✔️ Zvažte použití <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> pro fond vašich nativních vyrovnávacích pamětí polí.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-113">✔️ CONSIDER using <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> to pool your native array buffers.</span></span>
- <span data-ttu-id="ccbbf-114">✔️ Zvažte zabalení deklarací volání nespravovaného kódu ve třídě se stejným názvem a velkými písmeny jako vaše nativní knihovna.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-114">✔️ CONSIDER wrapping your P/Invoke declarations in a class with the same name and capitalization as your native library.</span></span>
  - <span data-ttu-id="ccbbf-115">To umožňuje, aby atributy `[DllImport]` používaly C# funkci jazyka `nameof` k předání názvu nativní knihovny a zajistila, že jste nezadali název nativní knihovny.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-115">This allows your `[DllImport]` attributes to use the C# `nameof` language feature to pass in the name of the native library and ensure that you didn't misspell the name of the native library.</span></span>

## <a name="dllimport-attribute-settings"></a><span data-ttu-id="ccbbf-116">Nastavení atributu DllImport</span><span class="sxs-lookup"><span data-stu-id="ccbbf-116">DllImport attribute settings</span></span>

| <span data-ttu-id="ccbbf-117">Nastavení</span><span class="sxs-lookup"><span data-stu-id="ccbbf-117">Setting</span></span> | <span data-ttu-id="ccbbf-118">Výchozí</span><span class="sxs-lookup"><span data-stu-id="ccbbf-118">Default</span></span> | <span data-ttu-id="ccbbf-119">Doporučení</span><span class="sxs-lookup"><span data-stu-id="ccbbf-119">Recommendation</span></span> | <span data-ttu-id="ccbbf-120">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="ccbbf-120">Details</span></span> |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  <span data-ttu-id="ccbbf-121">zachovat výchozí</span><span class="sxs-lookup"><span data-stu-id="ccbbf-121">keep default</span></span>  | <span data-ttu-id="ccbbf-122">Pokud je toto nastavení explicitně nastaveno na hodnotu false, neúspěšné návratové hodnoty HRESULT budou převedeny na výjimky (a návratová hodnota v definici bude jako výsledek null).</span><span class="sxs-lookup"><span data-stu-id="ccbbf-122">When this is explicitly set to false, failed HRESULT return values will be turned into exceptions (and the return value in the definition becomes null as a result).</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | <span data-ttu-id="ccbbf-123">závisí na rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ccbbf-123">depends on the API</span></span>  | <span data-ttu-id="ccbbf-124">Tuto hodnotu nastavte na true, pokud rozhraní API používá GetLastError, a k získání hodnoty použijte Marshal. GetLastWin32Error.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-124">Set this to true if the API uses GetLastError and use Marshal.GetLastWin32Error to get the value.</span></span> <span data-ttu-id="ccbbf-125">Pokud rozhraní API nastaví podmínku, která říká, že obsahuje chybu, před dalším voláním zajistěte chybu, aby se zabránilo nechtěnému přepsání.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-125">If the API sets a condition that says it has an error, get the error before making other calls to avoid inadvertently having it overwritten.</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | <span data-ttu-id="ccbbf-126">`CharSet.None`, což se vrátí k chování `CharSet.Ansi`</span><span class="sxs-lookup"><span data-stu-id="ccbbf-126">`CharSet.None`, which falls back to `CharSet.Ansi` behavior</span></span>  | <span data-ttu-id="ccbbf-127">Explicitně použít `CharSet.Unicode` nebo `CharSet.Ansi`, když jsou v definici přítomné řetězce nebo znaky</span><span class="sxs-lookup"><span data-stu-id="ccbbf-127">Explicitly  use `CharSet.Unicode` or `CharSet.Ansi` when strings or characters are present in the definition</span></span> | <span data-ttu-id="ccbbf-128">To určuje chování zařazování řetězců a to, co `ExactSpelling` provede `false`.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-128">This specifies marshaling behavior of strings and what `ExactSpelling` does when `false`.</span></span> <span data-ttu-id="ccbbf-129">Všimněte si, že `CharSet.Ansi` je ve skutečnosti UTF8 v systému UNIX.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-129">Note that `CharSet.Ansi` is actually UTF8 on Unix.</span></span> <span data-ttu-id="ccbbf-130">_Většina_ času v systému Windows používá kódování Unicode, zatímco systém UNIX používá UTF8.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-130">_Most_ of the time Windows uses Unicode while Unix uses UTF8.</span></span> <span data-ttu-id="ccbbf-131">Další informace najdete v [dokumentaci k charset](./charset.md).</span><span class="sxs-lookup"><span data-stu-id="ccbbf-131">See more information on the [documentation on charsets](./charset.md).</span></span> |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | <span data-ttu-id="ccbbf-132">Nastavte tuto hodnotu na true a získejte mírné zvýhodnění výkonu, protože modul runtime nebude hledat alternativní názvy funkcí s příponou "A" nebo "W" v závislosti na hodnotě nastavení `CharSet` ("A" pro `CharSet.Ansi` a "W" pro `CharSet.Unicode`).</span><span class="sxs-lookup"><span data-stu-id="ccbbf-132">Set this to true and gain a slight perf benefit as the runtime will not look for alternate function names with either an "A" or "W" suffix depending on the value of the `CharSet` setting ("A" for `CharSet.Ansi` and "W" for `CharSet.Unicode`).</span></span> |

## <a name="string-parameters"></a><span data-ttu-id="ccbbf-133">Řetězcové parametry</span><span class="sxs-lookup"><span data-stu-id="ccbbf-133">String parameters</span></span>

<span data-ttu-id="ccbbf-134">Pokud je znaková sada Unicode nebo je argument explicitně označen jako `[MarshalAs(UnmanagedType.LPWSTR)]` _a_ řetězec je předán podle hodnoty (ne `ref` nebo `out`), řetězec bude připnuté a použit přímo pomocí nativního kódu (místo kopírování).</span><span class="sxs-lookup"><span data-stu-id="ccbbf-134">When the CharSet is Unicode or the argument is explicitly marked as `[MarshalAs(UnmanagedType.LPWSTR)]` _and_ the string is passed by value (not `ref` or `out`), the string will be pinned and used directly by native code (rather than copied).</span></span>

<span data-ttu-id="ccbbf-135">Nezapomeňte označit `[DllImport]` jako `Charset.Unicode`, pokud nechcete, aby byly řetězce explicitně vhodné pro zpracování ANSI.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-135">Remember to mark the `[DllImport]` as `Charset.Unicode` unless you explicitly want ANSI treatment of your strings.</span></span>

<span data-ttu-id="ccbbf-136">❌ nepoužívat parametry `[Out] string`.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-136">❌ DO NOT use `[Out] string` parameters.</span></span> <span data-ttu-id="ccbbf-137">Řetězcové parametry předávané hodnotou s atributem `[Out]` mohou destabilizovat modul runtime, pokud je řetězec interně řetězec.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-137">String parameters passed by value with the `[Out]` attribute can destabilize the runtime if the string is an interned string.</span></span> <span data-ttu-id="ccbbf-138">Další informace o přehlašování řetězců najdete v dokumentaci k <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-138">See more information about string interning in the documentation for <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="ccbbf-139">❌ se vyhnout parametrům `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-139">❌ AVOID `StringBuilder` parameters.</span></span> <span data-ttu-id="ccbbf-140">`StringBuilder` zařazování *vždy* vytvoří nativní kopii vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-140">`StringBuilder` marshaling *always* creates a native buffer copy.</span></span> <span data-ttu-id="ccbbf-141">V takovém případě může být mimořádně neefektivní.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-141">As such, it can be extremely inefficient.</span></span> <span data-ttu-id="ccbbf-142">Vyjistěte si Typický scénář volání rozhraní API systému Windows, které přijímá řetězec:</span><span class="sxs-lookup"><span data-stu-id="ccbbf-142">Take the typical scenario of calling a Windows API that takes a string:</span></span>

1. <span data-ttu-id="ccbbf-143">Vytvořte SB požadované kapacity (přidělení spravované kapacity) **{1}**</span><span class="sxs-lookup"><span data-stu-id="ccbbf-143">Create a SB of the desired capacity (allocates managed capacity) **{1}**</span></span>
2. <span data-ttu-id="ccbbf-144">Invoke</span><span class="sxs-lookup"><span data-stu-id="ccbbf-144">Invoke</span></span>
   1. <span data-ttu-id="ccbbf-145">Přidělí nativní vyrovnávací paměť **{2}**</span><span class="sxs-lookup"><span data-stu-id="ccbbf-145">Allocates a native buffer **{2}**</span></span>
   2. <span data-ttu-id="ccbbf-146">Zkopíruje obsah, pokud je `[In]` _(výchozí hodnota pro `StringBuilder` parametr)_ .</span><span class="sxs-lookup"><span data-stu-id="ccbbf-146">Copies the contents if `[In]` _(the default for a `StringBuilder` parameter)_</span></span>
   3. <span data-ttu-id="ccbbf-147">Zkopíruje nativní vyrovnávací paměť do nově přiděleného spravovaného pole, pokud `[Out]` **{3}** _(také výchozí `StringBuilder`)_ .</span><span class="sxs-lookup"><span data-stu-id="ccbbf-147">Copies the native buffer into a newly allocated managed array if `[Out]` **{3}** _(also the default for `StringBuilder`)_</span></span>
3. <span data-ttu-id="ccbbf-148">`ToString()` přiděluje ještě jiné spravované pole **{4}**</span><span class="sxs-lookup"><span data-stu-id="ccbbf-148">`ToString()` allocates yet another managed array **{4}**</span></span>

<span data-ttu-id="ccbbf-149">To je *{4}* přidělení pro získání řetězce z nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-149">That is *{4}* allocations to get a string out of native code.</span></span> <span data-ttu-id="ccbbf-150">To nejlepší můžete udělat tak, že tento `StringBuilder` znovu použijete při jiném volání, ale bude se dál ukládat jenom *1* přidělení.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-150">The best you can do to limit this is to reuse the `StringBuilder` in another call but this still only saves *1* allocation.</span></span> <span data-ttu-id="ccbbf-151">Je mnohem lepší použít a ukládat do mezipaměti znaková vyrovnávací paměť z `ArrayPool`. pak se můžete dostat až do přidělení `ToString()` při dalších voláních.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-151">It's much better to use and cache a character buffer from `ArrayPool`- you can then get down to just the allocation for the `ToString()` on subsequent calls.</span></span>

<span data-ttu-id="ccbbf-152">Dalším problémem s `StringBuilder` je, že se vždy zkopíruje návratovou vyrovnávací paměť zpět na první hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-152">The other issue with `StringBuilder` is that it always copies the return buffer back up to the first null.</span></span> <span data-ttu-id="ccbbf-153">Pokud předaný řetězec není ukončen nebo se jedná o řetězec zakončený hodnotou null, vaše volání nespravovaného volání není správné.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-153">If the passed back string isn't terminated or is a double-null-terminated string, your P/Invoke is incorrect at best.</span></span>

<span data-ttu-id="ccbbf-154">Pokud *použijete* `StringBuilder`, jedna poslední gotcha je, že **kapacita neobsahuje skrytý** znak null, který je vždycky zavedený pro v interoperabilitě.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-154">If you *do* use `StringBuilder`, one last gotcha is that the capacity does **not** include a hidden null, which is always accounted for in interop.</span></span> <span data-ttu-id="ccbbf-155">Je běžné, že lidé mají špatný přístup, protože většina rozhraní API má velikost vyrovnávací paměti, *včetně* hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-155">It's common for people to get this wrong as most APIs want the size of the buffer *including* the null.</span></span> <span data-ttu-id="ccbbf-156">To může vést k plýtvání/zbytečným přidělením.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-156">This can result in wasted/unnecessary allocations.</span></span> <span data-ttu-id="ccbbf-157">Kromě toho tento gotcha brání modulu runtime v optimalizaci `StringBuilder` zařazování pro minimalizaci kopií.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-157">Additionally, this gotcha prevents the runtime from optimizing `StringBuilder` marshaling to minimize copies.</span></span>

<span data-ttu-id="ccbbf-158">✔️ Zvažte použití `char[]`s z `ArrayPool`.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-158">✔️ CONSIDER using `char[]`s from an `ArrayPool`.</span></span>

<span data-ttu-id="ccbbf-159">Další informace o zařazování řetězců naleznete v tématu [Výchozí zařazování pro řetězce](../../framework/interop/default-marshaling-for-strings.md) a [přizpůsobení zařazování řetězců](customize-parameter-marshaling.md#customizing-string-parameters).</span><span class="sxs-lookup"><span data-stu-id="ccbbf-159">For more information on string marshaling, see [Default Marshaling for Strings](../../framework/interop/default-marshaling-for-strings.md) and [Customizing string marshaling](customize-parameter-marshaling.md#customizing-string-parameters).</span></span>

> <span data-ttu-id="ccbbf-160">__Specifické pro systém Windows__ U `[Out]` řetězců bude CLR standardně používat `CoTaskMemFree` k uvolnění řetězců nebo `SysStringFree` pro řetězce, které jsou označeny jako `UnmanagedType.BSTR`.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-160">__Windows Specific__ For `[Out]` strings the CLR will use `CoTaskMemFree` by default to free strings or `SysStringFree` for strings that are marked as `UnmanagedType.BSTR`.</span></span>
> <span data-ttu-id="ccbbf-161">**Pro většinu rozhraní API výstupní vyrovnávací paměť řetězců:** Počet předaných znaků musí obsahovat hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-161">**For most APIs with an output string buffer:** The passed in character count must include the null.</span></span> <span data-ttu-id="ccbbf-162">Pokud je vrácená hodnota menší než předaný počet znaků, volání bylo úspěšné a hodnota je počet znaků *bez* koncové hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-162">If the returned value is less than the passed in character count the call has succeeded and the value is the number of characters *without* the trailing null.</span></span> <span data-ttu-id="ccbbf-163">V opačném případě je požadovaná velikost vyrovnávací paměti, *včetně* znaku null.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-163">Otherwise the count is the required size of the buffer *including* the null character.</span></span>
>
> - <span data-ttu-id="ccbbf-164">Průchod 5, Get 4: řetězec má 4 znaky dlouhé s koncovou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-164">Pass in 5, get 4: The string is 4 characters long with a trailing null.</span></span>
> - <span data-ttu-id="ccbbf-165">Průchod 5, Get 6: řetězec má délku 5 znaků, pro uložení hodnoty null je zapotřebí vyrovnávací paměť 6 znaků.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-165">Pass in 5, get 6: The string is 5 characters long, need a 6 character buffer to hold the null.</span></span>
> [<span data-ttu-id="ccbbf-166">Datové typy Windows pro řetězce</span><span class="sxs-lookup"><span data-stu-id="ccbbf-166">Windows Data Types for Strings</span></span>](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a><span data-ttu-id="ccbbf-167">Logické parametry a pole</span><span class="sxs-lookup"><span data-stu-id="ccbbf-167">Boolean parameters and fields</span></span>

<span data-ttu-id="ccbbf-168">Logické hodnoty se dají snadno vytvořit.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-168">Booleans are easy to mess up.</span></span> <span data-ttu-id="ccbbf-169">Ve výchozím nastavení je `bool` .NET zařazena do `BOOL`systému Windows, kde je hodnota 4 bajty.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-169">By default, a .NET `bool` is marshaled to a Windows `BOOL`, where it's a 4-byte value.</span></span> <span data-ttu-id="ccbbf-170">Nicméně `_Bool`a `bool` typy v jazyce C a C++ jsou *jedním* bajtem.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-170">However, the `_Bool`, and `bool` types in C and C++ are a *single* byte.</span></span> <span data-ttu-id="ccbbf-171">To může vést k tomu, že je možné sledovat chyby jako polovinu, návratová hodnota bude zahozena, což *může pouze změnit* výsledek.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-171">This can lead to hard to track down bugs as half the return value will be discarded, which will only *potentially* change the result.</span></span> <span data-ttu-id="ccbbf-172">Další informace o zařazování hodnot `bool` .NET do typů C nebo C++ `bool` naleznete v dokumentaci k [přizpůsobení zařazování logických polí](customize-struct-marshaling.md#customizing-boolean-field-marshaling).</span><span class="sxs-lookup"><span data-stu-id="ccbbf-172">For more for information on marshaling .NET `bool` values to C or C++ `bool` types, see the documentation on [customizing boolean field marshaling](customize-struct-marshaling.md#customizing-boolean-field-marshaling).</span></span>

## <a name="guids"></a><span data-ttu-id="ccbbf-173">Identifikátory GUID</span><span class="sxs-lookup"><span data-stu-id="ccbbf-173">GUIDs</span></span>

<span data-ttu-id="ccbbf-174">Identifikátory GUID lze použít přímo v signaturách.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-174">GUIDs are usable directly in signatures.</span></span> <span data-ttu-id="ccbbf-175">Mnoho rozhraní API systému Windows přijímá `GUID&` aliasy typu, jako je `REFIID`.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-175">Many Windows APIs take `GUID&` type aliases like `REFIID`.</span></span> <span data-ttu-id="ccbbf-176">Při předání odkazem, mohou být buď předány `ref` nebo s atributem `[MarshalAs(UnmanagedType.LPStruct)]`.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-176">When passed by ref, they can either be passed by `ref` or with the `[MarshalAs(UnmanagedType.LPStruct)]` attribute.</span></span>

| <span data-ttu-id="ccbbf-177">GUID</span><span class="sxs-lookup"><span data-stu-id="ccbbf-177">GUID</span></span> | <span data-ttu-id="ccbbf-178">Identifikátor GUID podle odkazu</span><span class="sxs-lookup"><span data-stu-id="ccbbf-178">By-ref GUID</span></span> |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

<span data-ttu-id="ccbbf-179">❌ nepoužívejte `[MarshalAs(UnmanagedType.LPStruct)]` pro jinou hodnotu než `ref` parametry GUID.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-179">❌ DO NOT Use `[MarshalAs(UnmanagedType.LPStruct)]` for anything other than `ref` GUID parameters.</span></span>

## <a name="blittable-types"></a><span data-ttu-id="ccbbf-180">Typy přenosit</span><span class="sxs-lookup"><span data-stu-id="ccbbf-180">Blittable types</span></span>

<span data-ttu-id="ccbbf-181">Přenositelné typy jsou typy, které mají stejné reprezentace na úrovni bitů ve spravovaném a nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-181">Blittable types are types that have the same bit-level representation in managed and native code.</span></span> <span data-ttu-id="ccbbf-182">Vzhledem k tomu, že není nutné je převádět do jiného formátu, aby bylo možné je zařadit do a z nativního kódu a jak to zlepšuje výkon, by měly být upřednostňovány.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-182">As such they do not need to be converted to another format to be marshaled to and from native code, and as this improves performance they should be preferred.</span></span>

<span data-ttu-id="ccbbf-183">**Typy přenositeli:**</span><span class="sxs-lookup"><span data-stu-id="ccbbf-183">**Blittable types:**</span></span>

- <span data-ttu-id="ccbbf-184">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span><span class="sxs-lookup"><span data-stu-id="ccbbf-184">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span></span>
- <span data-ttu-id="ccbbf-185">nevnořená jednorozměrná pole typů s více typy (například `int[]`)</span><span class="sxs-lookup"><span data-stu-id="ccbbf-185">non-nested one-dimensional arrays of blittable types (for example, `int[]`)</span></span>
- <span data-ttu-id="ccbbf-186">struktury a třídy s pevným rozložením, které pro pole instancí mají jenom typy přenositelné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-186">structs and classes with fixed layout that only have blittable value types for instance fields</span></span>
  - <span data-ttu-id="ccbbf-187">pevné rozložení vyžaduje `[StructLayout(LayoutKind.Sequential)]` nebo `[StructLayout(LayoutKind.Explicit)]`</span><span class="sxs-lookup"><span data-stu-id="ccbbf-187">fixed layout requires `[StructLayout(LayoutKind.Sequential)]` or `[StructLayout(LayoutKind.Explicit)]`</span></span>
  - <span data-ttu-id="ccbbf-188">struktury jsou ve výchozím nastavení `LayoutKind.Sequential` třídy `LayoutKind.Auto`</span><span class="sxs-lookup"><span data-stu-id="ccbbf-188">structs are `LayoutKind.Sequential` by default, classes are `LayoutKind.Auto`</span></span>

<span data-ttu-id="ccbbf-189">**Nenositelný odkaz:**</span><span class="sxs-lookup"><span data-stu-id="ccbbf-189">**NOT blittable:**</span></span>

- `bool`

<span data-ttu-id="ccbbf-190">**NĚKDY přenositelná:**</span><span class="sxs-lookup"><span data-stu-id="ccbbf-190">**SOMETIMES blittable:**</span></span>

- <span data-ttu-id="ccbbf-191">`char`, `string`</span><span class="sxs-lookup"><span data-stu-id="ccbbf-191">`char`, `string`</span></span>

<span data-ttu-id="ccbbf-192">Když jsou přenositelné typy předány odkazem, jsou místo kopírování do mezilehlé vyrovnávací paměti jednoduše připnuté serializátorem.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-192">When blittable types are passed by reference, they're simply pinned by the marshaller instead of being copied to an intermediate buffer.</span></span> <span data-ttu-id="ccbbf-193">(Třídy jsou ze své podstaty předány odkazem, struktury jsou předány odkazem při použití s `ref` nebo `out`.)</span><span class="sxs-lookup"><span data-stu-id="ccbbf-193">(Classes are inherently passed by reference, structs are passed by reference when used with `ref` or `out`.)</span></span>

<span data-ttu-id="ccbbf-194">`char` je přímo v jednorozměrném poli, **nebo** Pokud je součástí typu, který obsahuje explicitně označený `[StructLayout]` s `CharSet = CharSet.Unicode`.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-194">`char` is blittable in a one-dimensional array **or** if it's part of a type that contains it's explicitly marked with `[StructLayout]` with `CharSet = CharSet.Unicode`.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

<span data-ttu-id="ccbbf-195">`string` je přenositelná, pokud není obsažena v jiném typu a je předávána jako argument označený `[MarshalAs(UnmanagedType.LPWStr)]` nebo `[DllImport]` `CharSet = CharSet.Unicode` nastaven.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-195">`string` is blittable if it isn't contained in another type and it's being passed as an argument that is marked with `[MarshalAs(UnmanagedType.LPWStr)]` or the `[DllImport]` has `CharSet = CharSet.Unicode` set.</span></span>

<span data-ttu-id="ccbbf-196">Když se pokusíte vytvořit připnutý `GCHandle`, můžete zjistit, jestli je typ přenositelný.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-196">You can see if a type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="ccbbf-197">Pokud typ není řetězec nebo se považuje za Nepřenositelný, `GCHandle.Alloc` vyvolá `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-197">If the type isn't a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="ccbbf-198">✔️ PROVEĎTE přenositeli struktury, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-198">✔️ DO make your structures blittable when possible.</span></span>

<span data-ttu-id="ccbbf-199">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="ccbbf-199">For more information, see:</span></span>

- [<span data-ttu-id="ccbbf-200">Přenositelné a nepřenositelné typy</span><span class="sxs-lookup"><span data-stu-id="ccbbf-200">Blittable and Non-Blittable Types</span></span>](../../framework/interop/blittable-and-non-blittable-types.md)
- [<span data-ttu-id="ccbbf-201">Zařazování typů</span><span class="sxs-lookup"><span data-stu-id="ccbbf-201">Type Marshaling</span></span>](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a><span data-ttu-id="ccbbf-202">Udržování spravovaných objektů</span><span class="sxs-lookup"><span data-stu-id="ccbbf-202">Keeping managed objects alive</span></span>

<span data-ttu-id="ccbbf-203">`GC.KeepAlive()` zajistí, že objekt zůstane v oboru, dokud nebude dosaženo metody udržení naživu.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-203">`GC.KeepAlive()` will ensure an object stays in scope until the KeepAlive method is hit.</span></span>

<span data-ttu-id="ccbbf-204">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) umožňuje zařazování zachovat objekt aktivní po dobu trvání volání nespravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-204">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) allows the marshaller to keep an object alive for the duration of a P/Invoke.</span></span> <span data-ttu-id="ccbbf-205">Dá se použít místo `IntPtr` v signaturách metody.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-205">It can be used instead of `IntPtr` in method signatures.</span></span> <span data-ttu-id="ccbbf-206">`SafeHandle` efektivně nahrazuje tuto třídu a měla by se používat místo toho.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-206">`SafeHandle` effectively replaces this class and should be used instead.</span></span>

<span data-ttu-id="ccbbf-207">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) umožňuje připnutí spravovaného objektu a získání nativního ukazatele na něj.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-207">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) allows pinning a managed object and getting the native pointer to it.</span></span> <span data-ttu-id="ccbbf-208">Základní vzor je:</span><span class="sxs-lookup"><span data-stu-id="ccbbf-208">The basic pattern is:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

<span data-ttu-id="ccbbf-209">Připnutí není výchozím nastavením pro `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-209">Pinning isn't the default for `GCHandle`.</span></span> <span data-ttu-id="ccbbf-210">Druhým hlavním vzorem je předání odkazu spravovanému objektu prostřednictvím nativního kódu a zpět ke spravovanému kódu, obvykle pomocí zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-210">The other major pattern is for passing a reference to a managed object through native code and back to managed code, usually with a callback.</span></span> <span data-ttu-id="ccbbf-211">Tady je vzor:</span><span class="sxs-lookup"><span data-stu-id="ccbbf-211">Here is the pattern:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

<span data-ttu-id="ccbbf-212">Nezapomeňte, že `GCHandle` musí být explicitně uvolněny, aby nedošlo k nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-212">Don't forget that `GCHandle` needs to be explicitly freed to avoid memory leaks.</span></span>

## <a name="common-windows-data-types"></a><span data-ttu-id="ccbbf-213">Běžné datové typy Windows</span><span class="sxs-lookup"><span data-stu-id="ccbbf-213">Common Windows data types</span></span>

<span data-ttu-id="ccbbf-214">Tady je seznam datových typů, které se běžně používají v rozhraních API C# systému Windows, a typy, které se mají použít při volání do kódu Windows.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-214">Here is a list of data types commonly used in Windows APIs and which C# types to use when calling into the Windows code.</span></span>

<span data-ttu-id="ccbbf-215">Následující typy mají stejnou velikost v 32 a 64 bitovém systému Windows, bez ohledu na jejich názvy.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-215">The following types are the same size on 32-bit and 64-bit Windows, despite their names.</span></span>

| <span data-ttu-id="ccbbf-216">Šířka</span><span class="sxs-lookup"><span data-stu-id="ccbbf-216">Width</span></span> | <span data-ttu-id="ccbbf-217">Windows</span><span class="sxs-lookup"><span data-stu-id="ccbbf-217">Windows</span></span>          | <span data-ttu-id="ccbbf-218">C (Windows)</span><span class="sxs-lookup"><span data-stu-id="ccbbf-218">C (Windows)</span></span>          | <span data-ttu-id="ccbbf-219">C#</span><span class="sxs-lookup"><span data-stu-id="ccbbf-219">C#</span></span>       | <span data-ttu-id="ccbbf-220">Jiné</span><span class="sxs-lookup"><span data-stu-id="ccbbf-220">Alternative</span></span>                          |
|:------|:-----------------|:---------------------|:---------|:-------------------------------------|
| <span data-ttu-id="ccbbf-221">32</span><span class="sxs-lookup"><span data-stu-id="ccbbf-221">32</span></span>    | `BOOL`           | `int`                | `int`    | `bool`                               |
| <span data-ttu-id="ccbbf-222">8</span><span class="sxs-lookup"><span data-stu-id="ccbbf-222">8</span></span>     | `BOOLEAN`        | `unsigned char`      | `byte`   | `[MarshalAs(UnmanagedType.U1)] bool` |
| <span data-ttu-id="ccbbf-223">8</span><span class="sxs-lookup"><span data-stu-id="ccbbf-223">8</span></span>     | `BYTE`           | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="ccbbf-224">8</span><span class="sxs-lookup"><span data-stu-id="ccbbf-224">8</span></span>     | `CHAR`           | `char`               | `sbyte`  |                                      |
| <span data-ttu-id="ccbbf-225">8</span><span class="sxs-lookup"><span data-stu-id="ccbbf-225">8</span></span>     | `UCHAR`          | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="ccbbf-226">16</span><span class="sxs-lookup"><span data-stu-id="ccbbf-226">16</span></span>    | `SHORT`          | `short`              | `short`  |                                      |
| <span data-ttu-id="ccbbf-227">16</span><span class="sxs-lookup"><span data-stu-id="ccbbf-227">16</span></span>    | `CSHORT`         | `short`              | `short`  |                                      |
| <span data-ttu-id="ccbbf-228">16</span><span class="sxs-lookup"><span data-stu-id="ccbbf-228">16</span></span>    | `USHORT`         | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="ccbbf-229">16</span><span class="sxs-lookup"><span data-stu-id="ccbbf-229">16</span></span>    | `WORD`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="ccbbf-230">16</span><span class="sxs-lookup"><span data-stu-id="ccbbf-230">16</span></span>    | `ATOM`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="ccbbf-231">32</span><span class="sxs-lookup"><span data-stu-id="ccbbf-231">32</span></span>    | `INT`            | `int`                | `int`    |                                      |
| <span data-ttu-id="ccbbf-232">32</span><span class="sxs-lookup"><span data-stu-id="ccbbf-232">32</span></span>    | `LONG`           | `long`               | `int`    |                                      |
| <span data-ttu-id="ccbbf-233">32</span><span class="sxs-lookup"><span data-stu-id="ccbbf-233">32</span></span>    | `ULONG`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="ccbbf-234">32</span><span class="sxs-lookup"><span data-stu-id="ccbbf-234">32</span></span>    | `DWORD`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="ccbbf-235">64</span><span class="sxs-lookup"><span data-stu-id="ccbbf-235">64</span></span>    | `QWORD`          | `long long`          | `long`   |                                      |
| <span data-ttu-id="ccbbf-236">64</span><span class="sxs-lookup"><span data-stu-id="ccbbf-236">64</span></span>    | `LARGE_INTEGER`  | `long long`          | `long`   |                                      |
| <span data-ttu-id="ccbbf-237">64</span><span class="sxs-lookup"><span data-stu-id="ccbbf-237">64</span></span>    | `LONGLONG`       | `long long`          | `long`   |                                      |
| <span data-ttu-id="ccbbf-238">64</span><span class="sxs-lookup"><span data-stu-id="ccbbf-238">64</span></span>    | `ULONGLONG`      | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="ccbbf-239">64</span><span class="sxs-lookup"><span data-stu-id="ccbbf-239">64</span></span>    | `ULARGE_INTEGER` | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="ccbbf-240">32</span><span class="sxs-lookup"><span data-stu-id="ccbbf-240">32</span></span>    | `HRESULT`        | `long`               | `int`    |                                      |
| <span data-ttu-id="ccbbf-241">32</span><span class="sxs-lookup"><span data-stu-id="ccbbf-241">32</span></span>    | `NTSTATUS`       | `long`               | `int`    |                                      |

<span data-ttu-id="ccbbf-242">Následující typy jsou ukazatele, které následují po šířce platformy.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-242">The following types, being pointers, do follow the width of the platform.</span></span> <span data-ttu-id="ccbbf-243">Pro tyto `UIntPtr` použijte `IntPtr`/.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-243">Use `IntPtr`/`UIntPtr` for these.</span></span>

| <span data-ttu-id="ccbbf-244">Typy podepsaných ukazatelů (použijte `IntPtr`)</span><span class="sxs-lookup"><span data-stu-id="ccbbf-244">Signed Pointer Types (use `IntPtr`)</span></span> | <span data-ttu-id="ccbbf-245">Typ ukazatele bez znaménka (použijte `UIntPtr`)</span><span class="sxs-lookup"><span data-stu-id="ccbbf-245">Unsigned Pointer Types (use `UIntPtr`)</span></span> |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

<span data-ttu-id="ccbbf-246">`PVOID` systému Windows, což je `void*` jazyka C, lze zařadit jako `IntPtr` nebo `UIntPtr`, ale preferovat `void*`, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-246">A Windows `PVOID` which is a C `void*` can be marshaled as either `IntPtr` or `UIntPtr`, but prefer `void*` when possible.</span></span>

[<span data-ttu-id="ccbbf-247">Datové typy Windows</span><span class="sxs-lookup"><span data-stu-id="ccbbf-247">Windows Data Types</span></span>](/windows/desktop/WinProg/windows-data-types)

[<span data-ttu-id="ccbbf-248">Rozsahy datových typů</span><span class="sxs-lookup"><span data-stu-id="ccbbf-248">Data Type Ranges</span></span>](/cpp/cpp/data-type-ranges)

## <a name="structs"></a><span data-ttu-id="ccbbf-249">Struktury</span><span class="sxs-lookup"><span data-stu-id="ccbbf-249">Structs</span></span>

<span data-ttu-id="ccbbf-250">Spravované struktury se vytvoří v zásobníku a neodstraňují se, dokud se metoda nevrátí.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-250">Managed structs are created on the stack and aren't removed until the method returns.</span></span> <span data-ttu-id="ccbbf-251">Podle definice pak jsou "připnuté" (nebudou přesunuty do GC).</span><span class="sxs-lookup"><span data-stu-id="ccbbf-251">By definition then, they are "pinned" (it won't get moved by the GC).</span></span> <span data-ttu-id="ccbbf-252">Můžete také jednoduše převzít adresu z nebezpečných bloků kódu, pokud nativní kód nebude používat ukazatel za koncem aktuální metody.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-252">You can also simply take the address in unsafe code blocks if native code won't use the pointer past the end of the current method.</span></span>

<span data-ttu-id="ccbbf-253">Přenositelné struktury jsou mnohem větší, protože je lze jednoduše použít přímo zařazovací vrstvou.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-253">Blittable structs are much more performant as they can simply be used directly by the marshaling layer.</span></span> <span data-ttu-id="ccbbf-254">Snažte se nastavit struktury jako přenositelné (například vyhnout `bool`).</span><span class="sxs-lookup"><span data-stu-id="ccbbf-254">Try to make structs blittable (for example, avoid `bool`).</span></span> <span data-ttu-id="ccbbf-255">Další informace najdete v části [typy přenosit](#blittable-types) .</span><span class="sxs-lookup"><span data-stu-id="ccbbf-255">For more information, see the [Blittable Types](#blittable-types) section.</span></span>

<span data-ttu-id="ccbbf-256">*Pokud* je struktura přenositelná, použijte k zajištění lepšího výkonu `sizeof()` místo `Marshal.SizeOf<MyStruct>()`.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-256">*If* the struct is blittable, use `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for better performance.</span></span> <span data-ttu-id="ccbbf-257">Jak je uvedeno výše, můžete ověřit, že typ je přenositelný, a pokusit se vytvořit připnutý `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-257">As mentioned above, you can validate that the type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="ccbbf-258">Pokud typ není řetězec nebo se považuje za Nepřenositelný, `GCHandle.Alloc` vyvolá `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-258">If the type is not a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="ccbbf-259">Ukazatele na struktury v definicích musí být buď předány `ref`, nebo používat `unsafe` a `*`.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-259">Pointers to structs in definitions must either be passed by `ref` or use `unsafe` and `*`.</span></span>

<span data-ttu-id="ccbbf-260">✔️ podle tvaru a názvů, které se používají v dokumentaci k oficiální platformě nebo v hlavičce, co nejvíce porovnává se spravovanou strukturou.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-260">✔️ DO match the managed struct as closely as possible to the shape and names that are used in the official platform documentation or header.</span></span>

<span data-ttu-id="ccbbf-261">pro zvýšení výkonu ✔️ C# použít `sizeof()` místo `Marshal.SizeOf<MyStruct>()` pro přenositelné struktury.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-261">✔️ DO use the C# `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for blittable structures to improve performance.</span></span>

<span data-ttu-id="ccbbf-262">Pole jako `INT_PTR Reserved1[2]` musí být zařazeno do dvou `IntPtr` polí `Reserved1a` a `Reserved1b`.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-262">An array like `INT_PTR Reserved1[2]` has to be marshaled to two `IntPtr` fields, `Reserved1a` and `Reserved1b`.</span></span> <span data-ttu-id="ccbbf-263">Pokud je nativním polem primitivní typ, můžeme použít klíčové slovo `fixed` k jeho zapsání trochu efektivněji.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-263">When the native array is a primitive type, we can use the `fixed` keyword to write it a little more cleanly.</span></span> <span data-ttu-id="ccbbf-264">Například `SYSTEM_PROCESS_INFORMATION` vypadat jako v nativní hlavičce:</span><span class="sxs-lookup"><span data-stu-id="ccbbf-264">For example, `SYSTEM_PROCESS_INFORMATION` looks like this in the native header:</span></span>

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

<span data-ttu-id="ccbbf-265">V C#nástroji můžeme zapisovat takto:</span><span class="sxs-lookup"><span data-stu-id="ccbbf-265">In C#, we can write it like this:</span></span>

```csharp
internal unsafe struct SYSTEM_PROCESS_INFORMATION
{
    internal uint NextEntryOffset;
    internal uint NumberOfThreads;
    private fixed byte Reserved1[48];
    internal Interop.UNICODE_STRING ImageName;
    ...
}
```

<span data-ttu-id="ccbbf-266">Existuje však několik možná úskalí s pevnými vyrovnávacími pamětmi.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-266">However, there are some gotchas with fixed buffers.</span></span> <span data-ttu-id="ccbbf-267">Pevné vyrovnávací paměti nepřenositelného typu nebudou správně zařazeny, takže musí být místní pole rozšířeno na více jednotlivých polí.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-267">Fixed buffers of non-blittable types won't be correctly marshaled, so the in-place array needs to be expanded out to multiple individual fields.</span></span> <span data-ttu-id="ccbbf-268">V .NET Framework a .NET Core před 3,0 platí, že pokud je struktura obsahující pevné pole vyrovnávací paměti vnořena do nepřenositelné struktury, pole pevné vyrovnávací paměti se správně nezazařazuje do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="ccbbf-268">Additionally, in .NET Framework and .NET Core before 3.0, if a struct containing a fixed buffer field is nested within a non-blittable struct, the fixed buffer field won't be correctly marshaled to native code.</span></span>
