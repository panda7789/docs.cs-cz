---
title: Nativní osvědčené postupy interoperability – .NET
description: Seznamte se s osvědčenými postupy pro propojení s nativními komponentami v .NET.
ms.date: 01/18/2019
ms.openlocfilehash: e5d96471e796dca712d25d2d9e2609508180d83f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391218"
---
# <a name="native-interoperability-best-practices"></a><span data-ttu-id="570f7-103">Nativní osvědčené postupy interoperability</span><span class="sxs-lookup"><span data-stu-id="570f7-103">Native interoperability best practices</span></span>

<span data-ttu-id="570f7-104">.NET nabízí různé způsoby přizpůsobení nativního kódu interoperability.</span><span class="sxs-lookup"><span data-stu-id="570f7-104">.NET gives you a variety of ways to customize your native interoperability code.</span></span> <span data-ttu-id="570f7-105">Tento článek obsahuje pokyny, které tým .NET Microsoftu sleduje pro zajištění nativní interoperability.</span><span class="sxs-lookup"><span data-stu-id="570f7-105">This article includes the guidance that Microsoft's .NET teams follow for native interoperability.</span></span>

## <a name="general-guidance"></a><span data-ttu-id="570f7-106">Obecné pokyny</span><span class="sxs-lookup"><span data-stu-id="570f7-106">General guidance</span></span>

<span data-ttu-id="570f7-107">Pokyny v této části se vztahují na všechny scénáře spolupráce.</span><span class="sxs-lookup"><span data-stu-id="570f7-107">The guidance in this section applies to all interop scenarios.</span></span>

- <span data-ttu-id="570f7-108">✔️ použít stejné názvy a velká písmena pro vaše metody a parametry jako nativní metodu, kterou chcete volat.</span><span class="sxs-lookup"><span data-stu-id="570f7-108">✔️ DO use the same naming and capitalization for your methods and parameters as the native method you want to call.</span></span>
- <span data-ttu-id="570f7-109">✔️ Zvažte použití stejných názvů a velkých a malých písmen pro konstantní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="570f7-109">✔️ CONSIDER using the same naming and capitalization for constant values.</span></span>
- <span data-ttu-id="570f7-110">✔️ použít typy .NET, které jsou mapovány nejblíže k nativnímu typu.</span><span class="sxs-lookup"><span data-stu-id="570f7-110">✔️ DO use .NET types that map closest to the native type.</span></span> <span data-ttu-id="570f7-111">Například v jazyce C# použijte `uint` , pokud je `unsigned int`nativní typ.</span><span class="sxs-lookup"><span data-stu-id="570f7-111">For example, in C#, use `uint` when the native type is `unsigned int`.</span></span>
- <span data-ttu-id="570f7-112">✔️ použít `[In]` pouze atributy a `[Out]` , pokud se chování, které požadujete, se liší od výchozího chování.</span><span class="sxs-lookup"><span data-stu-id="570f7-112">✔️ DO only use `[In]` and `[Out]` attributes when the behavior you want differs from the default behavior.</span></span>
- <span data-ttu-id="570f7-113">✔️ Zvažte použití <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> pro fond vašich nativních vyrovnávacích pamětí pole.</span><span class="sxs-lookup"><span data-stu-id="570f7-113">✔️ CONSIDER using <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> to pool your native array buffers.</span></span>
- <span data-ttu-id="570f7-114">✔️ Zvažte zabalení deklarací volání nespravovaného kódu ve třídě se stejným názvem a velkými písmeny jako vaše nativní knihovna.</span><span class="sxs-lookup"><span data-stu-id="570f7-114">✔️ CONSIDER wrapping your P/Invoke declarations in a class with the same name and capitalization as your native library.</span></span>
  - <span data-ttu-id="570f7-115">To umožňuje, `[DllImport]` aby atributy používaly funkci `nameof` jazyka C# k předání názvu nativní knihovny a aby se zajistilo, že jste nezadali název nativní knihovny.</span><span class="sxs-lookup"><span data-stu-id="570f7-115">This allows your `[DllImport]` attributes to use the C# `nameof` language feature to pass in the name of the native library and ensure that you didn't misspell the name of the native library.</span></span>

## <a name="dllimport-attribute-settings"></a><span data-ttu-id="570f7-116">Nastavení atributu DllImport</span><span class="sxs-lookup"><span data-stu-id="570f7-116">DllImport attribute settings</span></span>

| <span data-ttu-id="570f7-117">Nastavení</span><span class="sxs-lookup"><span data-stu-id="570f7-117">Setting</span></span> | <span data-ttu-id="570f7-118">Výchozí</span><span class="sxs-lookup"><span data-stu-id="570f7-118">Default</span></span> | <span data-ttu-id="570f7-119">Doporučení</span><span class="sxs-lookup"><span data-stu-id="570f7-119">Recommendation</span></span> | <span data-ttu-id="570f7-120">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="570f7-120">Details</span></span> |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  <span data-ttu-id="570f7-121">zachovat výchozí</span><span class="sxs-lookup"><span data-stu-id="570f7-121">keep default</span></span>  | <span data-ttu-id="570f7-122">Pokud je toto nastavení explicitně nastaveno na hodnotu false, neúspěšné návratové hodnoty HRESULT budou převedeny na výjimky (a návratová hodnota v definici bude jako výsledek null).</span><span class="sxs-lookup"><span data-stu-id="570f7-122">When this is explicitly set to false, failed HRESULT return values will be turned into exceptions (and the return value in the definition becomes null as a result).</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | <span data-ttu-id="570f7-123">závisí na rozhraní API</span><span class="sxs-lookup"><span data-stu-id="570f7-123">depends on the API</span></span>  | <span data-ttu-id="570f7-124">Tuto hodnotu nastavte na true, pokud rozhraní API používá GetLastError, a k získání hodnoty použijte Marshal. GetLastWin32Error.</span><span class="sxs-lookup"><span data-stu-id="570f7-124">Set this to true if the API uses GetLastError and use Marshal.GetLastWin32Error to get the value.</span></span> <span data-ttu-id="570f7-125">Pokud rozhraní API nastaví podmínku, která říká, že obsahuje chybu, před dalším voláním zajistěte chybu, aby se zabránilo nechtěnému přepsání.</span><span class="sxs-lookup"><span data-stu-id="570f7-125">If the API sets a condition that says it has an error, get the error before making other calls to avoid inadvertently having it overwritten.</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | <span data-ttu-id="570f7-126">`CharSet.None`, který se vrátí k `CharSet.Ansi` chování</span><span class="sxs-lookup"><span data-stu-id="570f7-126">`CharSet.None`, which falls back to `CharSet.Ansi` behavior</span></span>  | <span data-ttu-id="570f7-127">Explicitně použít `CharSet.Unicode` nebo `CharSet.Ansi` v případě, že jsou v definici přítomné řetězce nebo znaky</span><span class="sxs-lookup"><span data-stu-id="570f7-127">Explicitly  use `CharSet.Unicode` or `CharSet.Ansi` when strings or characters are present in the definition</span></span> | <span data-ttu-id="570f7-128">To určuje chování zařazování řetězců a to, `ExactSpelling` co dělá `false`.</span><span class="sxs-lookup"><span data-stu-id="570f7-128">This specifies marshaling behavior of strings and what `ExactSpelling` does when `false`.</span></span> <span data-ttu-id="570f7-129">Všimněte si `CharSet.Ansi` , že ve skutečnosti je UTF8 v systému UNIX.</span><span class="sxs-lookup"><span data-stu-id="570f7-129">Note that `CharSet.Ansi` is actually UTF8 on Unix.</span></span> <span data-ttu-id="570f7-130">_Většina_ času v systému Windows používá kódování Unicode, zatímco systém UNIX používá UTF8.</span><span class="sxs-lookup"><span data-stu-id="570f7-130">_Most_ of the time Windows uses Unicode while Unix uses UTF8.</span></span> <span data-ttu-id="570f7-131">Další informace najdete v [dokumentaci k charset](./charset.md).</span><span class="sxs-lookup"><span data-stu-id="570f7-131">See more information on the [documentation on charsets](./charset.md).</span></span> |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | <span data-ttu-id="570f7-132">Nastavte tuto hodnotu na true a získejte mírné zvýhodnění výkonu, protože modul runtime nebude hledat alternativní názvy funkcí s příponou "A" nebo "W" v závislosti na hodnotě `CharSet` nastavení ("a" pro `CharSet.Ansi` a "w" pro `CharSet.Unicode`).</span><span class="sxs-lookup"><span data-stu-id="570f7-132">Set this to true and gain a slight perf benefit as the runtime will not look for alternate function names with either an "A" or "W" suffix depending on the value of the `CharSet` setting ("A" for `CharSet.Ansi` and "W" for `CharSet.Unicode`).</span></span> |

## <a name="string-parameters"></a><span data-ttu-id="570f7-133">Řetězcové parametry</span><span class="sxs-lookup"><span data-stu-id="570f7-133">String parameters</span></span>

<span data-ttu-id="570f7-134">Pokud je znaková sada Unicode nebo je argument explicitně označen jako `[MarshalAs(UnmanagedType.LPWSTR)]` _a_ řetězec je předán pomocí hodnoty (ne `ref` nebo `out`), řetězec bude připnuté a použit přímo pomocí nativního kódu (místo kopírování).</span><span class="sxs-lookup"><span data-stu-id="570f7-134">When the CharSet is Unicode or the argument is explicitly marked as `[MarshalAs(UnmanagedType.LPWSTR)]` _and_ the string is passed by value (not `ref` or `out`), the string will be pinned and used directly by native code (rather than copied).</span></span>

<span data-ttu-id="570f7-135">Nezapomeňte označit jako `Charset.Unicode` , `[DllImport]` Pokud explicitně nechcete, aby byly řetězce v kódu ANSI.</span><span class="sxs-lookup"><span data-stu-id="570f7-135">Remember to mark the `[DllImport]` as `Charset.Unicode` unless you explicitly want ANSI treatment of your strings.</span></span>

<span data-ttu-id="570f7-136">❌Nepoužívejte `[Out] string` parametry.</span><span class="sxs-lookup"><span data-stu-id="570f7-136">❌ DO NOT use `[Out] string` parameters.</span></span> <span data-ttu-id="570f7-137">Řetězcové parametry předávané hodnotou s `[Out]` atributem mohou destabilizovat modul runtime, pokud je řetězec interně řetězec.</span><span class="sxs-lookup"><span data-stu-id="570f7-137">String parameters passed by value with the `[Out]` attribute can destabilize the runtime if the string is an interned string.</span></span> <span data-ttu-id="570f7-138">Další informace o přehlašování řetězců najdete v dokumentaci pro <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="570f7-138">See more information about string interning in the documentation for <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="570f7-139">❌Vyhněte se `StringBuilder` parametrům.</span><span class="sxs-lookup"><span data-stu-id="570f7-139">❌ AVOID `StringBuilder` parameters.</span></span> <span data-ttu-id="570f7-140">`StringBuilder`zařazování *vždy* vytvoří nativní kopii vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="570f7-140">`StringBuilder` marshaling *always* creates a native buffer copy.</span></span> <span data-ttu-id="570f7-141">V takovém případě může být mimořádně neefektivní.</span><span class="sxs-lookup"><span data-stu-id="570f7-141">As such, it can be extremely inefficient.</span></span> <span data-ttu-id="570f7-142">Vyjistěte si Typický scénář volání rozhraní API systému Windows, které přijímá řetězec:</span><span class="sxs-lookup"><span data-stu-id="570f7-142">Take the typical scenario of calling a Windows API that takes a string:</span></span>

1. <span data-ttu-id="570f7-143">Vytvořte SB požadované kapacity (přiděluje spravovanou kapacitu).**{1}**</span><span class="sxs-lookup"><span data-stu-id="570f7-143">Create a SB of the desired capacity (allocates managed capacity) **{1}**</span></span>
2. <span data-ttu-id="570f7-144">Invoke</span><span class="sxs-lookup"><span data-stu-id="570f7-144">Invoke</span></span>
   1. <span data-ttu-id="570f7-145">Přiděluje nativní vyrovnávací paměť.**{2}**</span><span class="sxs-lookup"><span data-stu-id="570f7-145">Allocates a native buffer **{2}**</span></span>
   2. <span data-ttu-id="570f7-146">Zkopíruje obsah, pokud `[In]` _(výchozí hodnota `StringBuilder` parametru)_ .</span><span class="sxs-lookup"><span data-stu-id="570f7-146">Copies the contents if `[In]` _(the default for a `StringBuilder` parameter)_</span></span>
   3. <span data-ttu-id="570f7-147">Zkopíruje nativní vyrovnávací paměť do nově přiděleného spravovaného pole `[Out]` **{3}** _(také výchozí pro `StringBuilder`)_ .</span><span class="sxs-lookup"><span data-stu-id="570f7-147">Copies the native buffer into a newly allocated managed array if `[Out]` **{3}** _(also the default for `StringBuilder`)_</span></span>
3. <span data-ttu-id="570f7-148">`ToString()`přidělí ještě jiné spravované pole.**{4}**</span><span class="sxs-lookup"><span data-stu-id="570f7-148">`ToString()` allocates yet another managed array **{4}**</span></span>

<span data-ttu-id="570f7-149">To je *{4}* přidělení pro získání řetězce z nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="570f7-149">That is *{4}* allocations to get a string out of native code.</span></span> <span data-ttu-id="570f7-150">To nejlepší můžete udělat tak, že je znovu použijete v `StringBuilder` jiném volání, ale bude se dál ukládat jenom *1* přidělení.</span><span class="sxs-lookup"><span data-stu-id="570f7-150">The best you can do to limit this is to reuse the `StringBuilder` in another call but this still only saves *1* allocation.</span></span> <span data-ttu-id="570f7-151">Je mnohem lepší použít a ukládat do mezipaměti znaková vyrovnávací paměť `ArrayPool`– můžete se pak dostat až do přidělení pro `ToString()` při následném volání.</span><span class="sxs-lookup"><span data-stu-id="570f7-151">It's much better to use and cache a character buffer from `ArrayPool`- you can then get down to just the allocation for the `ToString()` on subsequent calls.</span></span>

<span data-ttu-id="570f7-152">Dalším problémem `StringBuilder` je, že se vždy zkopíruje návratovou vyrovnávací paměť zpět na první hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="570f7-152">The other issue with `StringBuilder` is that it always copies the return buffer back up to the first null.</span></span> <span data-ttu-id="570f7-153">Pokud předaný řetězec není ukončen nebo se jedná o řetězec zakončený hodnotou null, vaše volání nespravovaného volání není správné.</span><span class="sxs-lookup"><span data-stu-id="570f7-153">If the passed back string isn't terminated or is a double-null-terminated string, your P/Invoke is incorrect at best.</span></span>

<span data-ttu-id="570f7-154">Pokud *použijete* `StringBuilder`, bude jedna poslední gotcha taková, že **kapacita neobsahuje skrytý** znak null, který je vždy zaúčtován v rámci spolupráce.</span><span class="sxs-lookup"><span data-stu-id="570f7-154">If you *do* use `StringBuilder`, one last gotcha is that the capacity does **not** include a hidden null, which is always accounted for in interop.</span></span> <span data-ttu-id="570f7-155">Je běžné, že lidé mají špatný přístup, protože většina rozhraní API má velikost vyrovnávací paměti, *včetně* hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="570f7-155">It's common for people to get this wrong as most APIs want the size of the buffer *including* the null.</span></span> <span data-ttu-id="570f7-156">To může vést k plýtvání/zbytečným přidělením.</span><span class="sxs-lookup"><span data-stu-id="570f7-156">This can result in wasted/unnecessary allocations.</span></span> <span data-ttu-id="570f7-157">Kromě toho tento gotcha brání modulu runtime v optimalizaci `StringBuilder` zařazování pro minimalizaci kopií.</span><span class="sxs-lookup"><span data-stu-id="570f7-157">Additionally, this gotcha prevents the runtime from optimizing `StringBuilder` marshaling to minimize copies.</span></span>

<span data-ttu-id="570f7-158">✔️ Zvažte použití `char[]`s z `ArrayPool`.</span><span class="sxs-lookup"><span data-stu-id="570f7-158">✔️ CONSIDER using `char[]`s from an `ArrayPool`.</span></span>

<span data-ttu-id="570f7-159">Další informace o zařazování řetězců naleznete v tématu [Výchozí zařazování pro řetězce](../../framework/interop/default-marshaling-for-strings.md) a [přizpůsobení zařazování řetězců](customize-parameter-marshaling.md#customizing-string-parameters).</span><span class="sxs-lookup"><span data-stu-id="570f7-159">For more information on string marshaling, see [Default Marshaling for Strings](../../framework/interop/default-marshaling-for-strings.md) and [Customizing string marshaling](customize-parameter-marshaling.md#customizing-string-parameters).</span></span>

> <span data-ttu-id="570f7-160">__Specifické pro systém Windows__ Pro `[Out]` řetězce, které bude CLR `CoTaskMemFree` používat ve výchozím nastavení, pro `SysStringFree` uvolnění řetězců nebo pro řetězce, `UnmanagedType.BSTR`které jsou označeny jako.</span><span class="sxs-lookup"><span data-stu-id="570f7-160">__Windows Specific__ For `[Out]` strings the CLR will use `CoTaskMemFree` by default to free strings or `SysStringFree` for strings that are marked as `UnmanagedType.BSTR`.</span></span>
> <span data-ttu-id="570f7-161">**Pro většinu rozhraní API výstupní vyrovnávací paměť řetězců:** Počet předaných znaků musí obsahovat hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="570f7-161">**For most APIs with an output string buffer:** The passed in character count must include the null.</span></span> <span data-ttu-id="570f7-162">Pokud je vrácená hodnota menší než předaný počet znaků, volání bylo úspěšné a hodnota je počet znaků *bez* koncové hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="570f7-162">If the returned value is less than the passed in character count the call has succeeded and the value is the number of characters *without* the trailing null.</span></span> <span data-ttu-id="570f7-163">V opačném případě je požadovaná velikost vyrovnávací paměti, *včetně* znaku null.</span><span class="sxs-lookup"><span data-stu-id="570f7-163">Otherwise the count is the required size of the buffer *including* the null character.</span></span>
>
> - <span data-ttu-id="570f7-164">Průchod 5, Get 4: řetězec má 4 znaky dlouhé s koncovou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="570f7-164">Pass in 5, get 4: The string is 4 characters long with a trailing null.</span></span>
> - <span data-ttu-id="570f7-165">Průchod 5, Get 6: řetězec má délku 5 znaků, pro uložení hodnoty null je zapotřebí vyrovnávací paměť 6 znaků.</span><span class="sxs-lookup"><span data-stu-id="570f7-165">Pass in 5, get 6: The string is 5 characters long, need a 6 character buffer to hold the null.</span></span>
> [<span data-ttu-id="570f7-166">Datové typy Windows pro řetězce</span><span class="sxs-lookup"><span data-stu-id="570f7-166">Windows Data Types for Strings</span></span>](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a><span data-ttu-id="570f7-167">Logické parametry a pole</span><span class="sxs-lookup"><span data-stu-id="570f7-167">Boolean parameters and fields</span></span>

<span data-ttu-id="570f7-168">Logické hodnoty se dají snadno vytvořit.</span><span class="sxs-lookup"><span data-stu-id="570f7-168">Booleans are easy to mess up.</span></span> <span data-ttu-id="570f7-169">Ve výchozím nastavení je rozhraní `bool` .NET zařazeno do systému Windows `BOOL`, kde je hodnota 4 bajty.</span><span class="sxs-lookup"><span data-stu-id="570f7-169">By default, a .NET `bool` is marshaled to a Windows `BOOL`, where it's a 4-byte value.</span></span> <span data-ttu-id="570f7-170">`_Bool`Nicméně typy a `bool` v jazyce C a C++ jsou *jedinými* bajty.</span><span class="sxs-lookup"><span data-stu-id="570f7-170">However, the `_Bool`, and `bool` types in C and C++ are a *single* byte.</span></span> <span data-ttu-id="570f7-171">To může vést k tomu, že je možné sledovat chyby jako polovinu, návratová hodnota bude zahozena, což *může pouze změnit* výsledek.</span><span class="sxs-lookup"><span data-stu-id="570f7-171">This can lead to hard to track down bugs as half the return value will be discarded, which will only *potentially* change the result.</span></span> <span data-ttu-id="570f7-172">Další informace o zařazování hodnot .NET `bool` do typů C nebo C++ `bool` naleznete v dokumentaci k [přizpůsobení zařazování logických polí](customize-struct-marshaling.md#customizing-boolean-field-marshaling).</span><span class="sxs-lookup"><span data-stu-id="570f7-172">For more for information on marshaling .NET `bool` values to C or C++ `bool` types, see the documentation on [customizing boolean field marshaling](customize-struct-marshaling.md#customizing-boolean-field-marshaling).</span></span>

## <a name="guids"></a><span data-ttu-id="570f7-173">Identifikátory GUID</span><span class="sxs-lookup"><span data-stu-id="570f7-173">GUIDs</span></span>

<span data-ttu-id="570f7-174">Identifikátory GUID lze použít přímo v signaturách.</span><span class="sxs-lookup"><span data-stu-id="570f7-174">GUIDs are usable directly in signatures.</span></span> <span data-ttu-id="570f7-175">Mnoho rozhraní API systému `GUID&` Windows přijímá aliasy typů, jako `REFIID`je.</span><span class="sxs-lookup"><span data-stu-id="570f7-175">Many Windows APIs take `GUID&` type aliases like `REFIID`.</span></span> <span data-ttu-id="570f7-176">Při předání odkazem, mohou být buď předány pomocí `ref` nebo s `[MarshalAs(UnmanagedType.LPStruct)]` atributem.</span><span class="sxs-lookup"><span data-stu-id="570f7-176">When passed by ref, they can either be passed by `ref` or with the `[MarshalAs(UnmanagedType.LPStruct)]` attribute.</span></span>

| <span data-ttu-id="570f7-177">GUID</span><span class="sxs-lookup"><span data-stu-id="570f7-177">GUID</span></span> | <span data-ttu-id="570f7-178">Identifikátor GUID podle odkazu</span><span class="sxs-lookup"><span data-stu-id="570f7-178">By-ref GUID</span></span> |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

<span data-ttu-id="570f7-179">❌Nepoužívejte `[MarshalAs(UnmanagedType.LPStruct)]` pro jiné než `ref` parametry GUID.</span><span class="sxs-lookup"><span data-stu-id="570f7-179">❌ DO NOT Use `[MarshalAs(UnmanagedType.LPStruct)]` for anything other than `ref` GUID parameters.</span></span>

## <a name="blittable-types"></a><span data-ttu-id="570f7-180">Typy přenosit</span><span class="sxs-lookup"><span data-stu-id="570f7-180">Blittable types</span></span>

<span data-ttu-id="570f7-181">Přenositelné typy jsou typy, které mají stejné reprezentace na úrovni bitů ve spravovaném a nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="570f7-181">Blittable types are types that have the same bit-level representation in managed and native code.</span></span> <span data-ttu-id="570f7-182">Vzhledem k tomu, že není nutné je převádět do jiného formátu, aby bylo možné je zařadit do a z nativního kódu a jak to zlepšuje výkon, by měly být upřednostňovány.</span><span class="sxs-lookup"><span data-stu-id="570f7-182">As such they do not need to be converted to another format to be marshaled to and from native code, and as this improves performance they should be preferred.</span></span>

<span data-ttu-id="570f7-183">**Typy přenositeli:**</span><span class="sxs-lookup"><span data-stu-id="570f7-183">**Blittable types:**</span></span>

- <span data-ttu-id="570f7-184">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span><span class="sxs-lookup"><span data-stu-id="570f7-184">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span></span>
- <span data-ttu-id="570f7-185">nevnořená jednorozměrná pole typů s více typy (například `int[]`)</span><span class="sxs-lookup"><span data-stu-id="570f7-185">non-nested one-dimensional arrays of blittable types (for example, `int[]`)</span></span>
- <span data-ttu-id="570f7-186">struktury a třídy s pevným rozložením, které pro pole instancí mají jenom typy přenositelné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="570f7-186">structs and classes with fixed layout that only have blittable value types for instance fields</span></span>
  - <span data-ttu-id="570f7-187">pevné rozložení vyžaduje `[StructLayout(LayoutKind.Sequential)]` nebo`[StructLayout(LayoutKind.Explicit)]`</span><span class="sxs-lookup"><span data-stu-id="570f7-187">fixed layout requires `[StructLayout(LayoutKind.Sequential)]` or `[StructLayout(LayoutKind.Explicit)]`</span></span>
  - <span data-ttu-id="570f7-188">struktury jsou `LayoutKind.Sequential` ve výchozím nastavení třídy`LayoutKind.Auto`</span><span class="sxs-lookup"><span data-stu-id="570f7-188">structs are `LayoutKind.Sequential` by default, classes are `LayoutKind.Auto`</span></span>

<span data-ttu-id="570f7-189">**Nenositelný odkaz:**</span><span class="sxs-lookup"><span data-stu-id="570f7-189">**NOT blittable:**</span></span>

- `bool`

<span data-ttu-id="570f7-190">**NĚKDY přenositelná:**</span><span class="sxs-lookup"><span data-stu-id="570f7-190">**SOMETIMES blittable:**</span></span>

- <span data-ttu-id="570f7-191">`char`, `string`</span><span class="sxs-lookup"><span data-stu-id="570f7-191">`char`, `string`</span></span>

<span data-ttu-id="570f7-192">Když jsou přenositelné typy předány odkazem, jsou místo kopírování do mezilehlé vyrovnávací paměti jednoduše připnuté serializátorem.</span><span class="sxs-lookup"><span data-stu-id="570f7-192">When blittable types are passed by reference, they're simply pinned by the marshaller instead of being copied to an intermediate buffer.</span></span> <span data-ttu-id="570f7-193">(Třídy jsou ze své podstaty předány odkazem, struktury jsou předány odkazem při použití s `ref` nebo `out`.)</span><span class="sxs-lookup"><span data-stu-id="570f7-193">(Classes are inherently passed by reference, structs are passed by reference when used with `ref` or `out`.)</span></span>

<span data-ttu-id="570f7-194">`char`je přímo v jednorozměrném poli **nebo** , pokud je součástí typu, který obsahuje explicitně označený `[StructLayout]` pomocí. `CharSet = CharSet.Unicode`</span><span class="sxs-lookup"><span data-stu-id="570f7-194">`char` is blittable in a one-dimensional array **or** if it's part of a type that contains it's explicitly marked with `[StructLayout]` with `CharSet = CharSet.Unicode`.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

<span data-ttu-id="570f7-195">`string`je chráněná, pokud není obsažena v jiném typu a je předávána jako argument, který je `[MarshalAs(UnmanagedType.LPWStr)]` označen jako `[DllImport]` nebo `CharSet = CharSet.Unicode` má nastaven.</span><span class="sxs-lookup"><span data-stu-id="570f7-195">`string` is blittable if it isn't contained in another type and it's being passed as an argument that is marked with `[MarshalAs(UnmanagedType.LPWStr)]` or the `[DllImport]` has `CharSet = CharSet.Unicode` set.</span></span>

<span data-ttu-id="570f7-196">Když se pokusíte vytvořit připnutý `GCHandle`, můžete zjistit, jestli je typ přenositelný.</span><span class="sxs-lookup"><span data-stu-id="570f7-196">You can see if a type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="570f7-197">Pokud typ není řetězec nebo se považuje za Nepřenositelný `GCHandle.Alloc` , `ArgumentException`vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="570f7-197">If the type isn't a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="570f7-198">✔️ PROVEĎTE přenositeli struktury, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="570f7-198">✔️ DO make your structures blittable when possible.</span></span>

<span data-ttu-id="570f7-199">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="570f7-199">For more information, see:</span></span>

- [<span data-ttu-id="570f7-200">Přenositelné a nepřenositelné typy</span><span class="sxs-lookup"><span data-stu-id="570f7-200">Blittable and Non-Blittable Types</span></span>](../../framework/interop/blittable-and-non-blittable-types.md)
- [<span data-ttu-id="570f7-201">Zařazování typů</span><span class="sxs-lookup"><span data-stu-id="570f7-201">Type Marshaling</span></span>](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a><span data-ttu-id="570f7-202">Udržování spravovaných objektů</span><span class="sxs-lookup"><span data-stu-id="570f7-202">Keeping managed objects alive</span></span>

<span data-ttu-id="570f7-203">`GC.KeepAlive()`zajistí, že objekt zůstane v oboru, dokud nebude dosaženo metody kontroly naživu.</span><span class="sxs-lookup"><span data-stu-id="570f7-203">`GC.KeepAlive()` will ensure an object stays in scope until the KeepAlive method is hit.</span></span>

<span data-ttu-id="570f7-204">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef)umožňuje zařazování zachovat objekt aktivní po dobu trvání volání nespravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="570f7-204">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) allows the marshaller to keep an object alive for the duration of a P/Invoke.</span></span> <span data-ttu-id="570f7-205">Dá se použít místo `IntPtr` signatury metody.</span><span class="sxs-lookup"><span data-stu-id="570f7-205">It can be used instead of `IntPtr` in method signatures.</span></span> <span data-ttu-id="570f7-206">`SafeHandle`efektivně nahrazuje tuto třídu a měla by se používat místo toho.</span><span class="sxs-lookup"><span data-stu-id="570f7-206">`SafeHandle` effectively replaces this class and should be used instead.</span></span>

<span data-ttu-id="570f7-207">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle)umožňuje připnutí spravovaného objektu a získání nativního ukazatele na něj.</span><span class="sxs-lookup"><span data-stu-id="570f7-207">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) allows pinning a managed object and getting the native pointer to it.</span></span> <span data-ttu-id="570f7-208">Základní vzor je:</span><span class="sxs-lookup"><span data-stu-id="570f7-208">The basic pattern is:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

<span data-ttu-id="570f7-209">Připnutí není výchozím nastavením `GCHandle`pro.</span><span class="sxs-lookup"><span data-stu-id="570f7-209">Pinning isn't the default for `GCHandle`.</span></span> <span data-ttu-id="570f7-210">Druhým hlavním vzorem je předání odkazu spravovanému objektu prostřednictvím nativního kódu a zpět ke spravovanému kódu, obvykle pomocí zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="570f7-210">The other major pattern is for passing a reference to a managed object through native code and back to managed code, usually with a callback.</span></span> <span data-ttu-id="570f7-211">Tady je vzor:</span><span class="sxs-lookup"><span data-stu-id="570f7-211">Here is the pattern:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

<span data-ttu-id="570f7-212">Nezapomeňte, že `GCHandle` je nutné explicitně uvolnit, aby nedošlo k nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="570f7-212">Don't forget that `GCHandle` needs to be explicitly freed to avoid memory leaks.</span></span>

## <a name="common-windows-data-types"></a><span data-ttu-id="570f7-213">Běžné datové typy Windows</span><span class="sxs-lookup"><span data-stu-id="570f7-213">Common Windows data types</span></span>

<span data-ttu-id="570f7-214">Tady je seznam datových typů, které se běžně používají v rozhraních API systému Windows a které typy C# se mají použít při volání do kódu Windows.</span><span class="sxs-lookup"><span data-stu-id="570f7-214">Here is a list of data types commonly used in Windows APIs and which C# types to use when calling into the Windows code.</span></span>

<span data-ttu-id="570f7-215">Následující typy mají stejnou velikost v 32 a 64 bitovém systému Windows, bez ohledu na jejich názvy.</span><span class="sxs-lookup"><span data-stu-id="570f7-215">The following types are the same size on 32-bit and 64-bit Windows, despite their names.</span></span>

| <span data-ttu-id="570f7-216">impulzu</span><span class="sxs-lookup"><span data-stu-id="570f7-216">Width</span></span> | <span data-ttu-id="570f7-217">Windows</span><span class="sxs-lookup"><span data-stu-id="570f7-217">Windows</span></span>          | <span data-ttu-id="570f7-218">C (Windows)</span><span class="sxs-lookup"><span data-stu-id="570f7-218">C (Windows)</span></span>          | <span data-ttu-id="570f7-219">C#</span><span class="sxs-lookup"><span data-stu-id="570f7-219">C#</span></span>       | <span data-ttu-id="570f7-220">Jiné</span><span class="sxs-lookup"><span data-stu-id="570f7-220">Alternative</span></span>                          |
|:------|:-----------------|:---------------------|:---------|:-------------------------------------|
| <span data-ttu-id="570f7-221">32</span><span class="sxs-lookup"><span data-stu-id="570f7-221">32</span></span>    | `BOOL`           | `int`                | `int`    | `bool`                               |
| <span data-ttu-id="570f7-222">8</span><span class="sxs-lookup"><span data-stu-id="570f7-222">8</span></span>     | `BOOLEAN`        | `unsigned char`      | `byte`   | `[MarshalAs(UnmanagedType.U1)] bool` |
| <span data-ttu-id="570f7-223">8</span><span class="sxs-lookup"><span data-stu-id="570f7-223">8</span></span>     | `BYTE`           | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="570f7-224">8</span><span class="sxs-lookup"><span data-stu-id="570f7-224">8</span></span>     | `CHAR`           | `char`               | `sbyte`  |                                      |
| <span data-ttu-id="570f7-225">8</span><span class="sxs-lookup"><span data-stu-id="570f7-225">8</span></span>     | `UCHAR`          | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="570f7-226">16</span><span class="sxs-lookup"><span data-stu-id="570f7-226">16</span></span>    | `SHORT`          | `short`              | `short`  |                                      |
| <span data-ttu-id="570f7-227">16</span><span class="sxs-lookup"><span data-stu-id="570f7-227">16</span></span>    | `CSHORT`         | `short`              | `short`  |                                      |
| <span data-ttu-id="570f7-228">16</span><span class="sxs-lookup"><span data-stu-id="570f7-228">16</span></span>    | `USHORT`         | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="570f7-229">16</span><span class="sxs-lookup"><span data-stu-id="570f7-229">16</span></span>    | `WORD`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="570f7-230">16</span><span class="sxs-lookup"><span data-stu-id="570f7-230">16</span></span>    | `ATOM`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="570f7-231">32</span><span class="sxs-lookup"><span data-stu-id="570f7-231">32</span></span>    | `INT`            | `int`                | `int`    |                                      |
| <span data-ttu-id="570f7-232">32</span><span class="sxs-lookup"><span data-stu-id="570f7-232">32</span></span>    | `LONG`           | `long`               | `int`    |                                      |
| <span data-ttu-id="570f7-233">32</span><span class="sxs-lookup"><span data-stu-id="570f7-233">32</span></span>    | `ULONG`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="570f7-234">32</span><span class="sxs-lookup"><span data-stu-id="570f7-234">32</span></span>    | `DWORD`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="570f7-235">64</span><span class="sxs-lookup"><span data-stu-id="570f7-235">64</span></span>    | `QWORD`          | `long long`          | `long`   |                                      |
| <span data-ttu-id="570f7-236">64</span><span class="sxs-lookup"><span data-stu-id="570f7-236">64</span></span>    | `LARGE_INTEGER`  | `long long`          | `long`   |                                      |
| <span data-ttu-id="570f7-237">64</span><span class="sxs-lookup"><span data-stu-id="570f7-237">64</span></span>    | `LONGLONG`       | `long long`          | `long`   |                                      |
| <span data-ttu-id="570f7-238">64</span><span class="sxs-lookup"><span data-stu-id="570f7-238">64</span></span>    | `ULONGLONG`      | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="570f7-239">64</span><span class="sxs-lookup"><span data-stu-id="570f7-239">64</span></span>    | `ULARGE_INTEGER` | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="570f7-240">32</span><span class="sxs-lookup"><span data-stu-id="570f7-240">32</span></span>    | `HRESULT`        | `long`               | `int`    |                                      |
| <span data-ttu-id="570f7-241">32</span><span class="sxs-lookup"><span data-stu-id="570f7-241">32</span></span>    | `NTSTATUS`       | `long`               | `int`    |                                      |

<span data-ttu-id="570f7-242">Následující typy jsou ukazatele, které následují po šířce platformy.</span><span class="sxs-lookup"><span data-stu-id="570f7-242">The following types, being pointers, do follow the width of the platform.</span></span> <span data-ttu-id="570f7-243">`IntPtr` / Použijte `UIntPtr` pro ně.</span><span class="sxs-lookup"><span data-stu-id="570f7-243">Use `IntPtr`/`UIntPtr` for these.</span></span>

| <span data-ttu-id="570f7-244">Typy podepsaných ukazatelů ( `IntPtr`použít)</span><span class="sxs-lookup"><span data-stu-id="570f7-244">Signed Pointer Types (use `IntPtr`)</span></span> | <span data-ttu-id="570f7-245">Typy nepodepsaných ukazatelů `UIntPtr`(použít)</span><span class="sxs-lookup"><span data-stu-id="570f7-245">Unsigned Pointer Types (use `UIntPtr`)</span></span> |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

<span data-ttu-id="570f7-246">Systém Windows `PVOID` , který je v `void*` jazyce C, lze zařadit `IntPtr` jako `UIntPtr`buď nebo, `void*` ale preferovat, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="570f7-246">A Windows `PVOID` which is a C `void*` can be marshaled as either `IntPtr` or `UIntPtr`, but prefer `void*` when possible.</span></span>

[<span data-ttu-id="570f7-247">Datové typy Windows</span><span class="sxs-lookup"><span data-stu-id="570f7-247">Windows Data Types</span></span>](/windows/desktop/WinProg/windows-data-types)

[<span data-ttu-id="570f7-248">Rozsahy datových typů</span><span class="sxs-lookup"><span data-stu-id="570f7-248">Data Type Ranges</span></span>](/cpp/cpp/data-type-ranges)

## <a name="structs"></a><span data-ttu-id="570f7-249">Struktury</span><span class="sxs-lookup"><span data-stu-id="570f7-249">Structs</span></span>

<span data-ttu-id="570f7-250">Spravované struktury se vytvoří v zásobníku a neodstraňují se, dokud se metoda nevrátí.</span><span class="sxs-lookup"><span data-stu-id="570f7-250">Managed structs are created on the stack and aren't removed until the method returns.</span></span> <span data-ttu-id="570f7-251">Podle definice pak jsou "připnuté" (nebudou přesunuty do GC).</span><span class="sxs-lookup"><span data-stu-id="570f7-251">By definition then, they are "pinned" (it won't get moved by the GC).</span></span> <span data-ttu-id="570f7-252">Můžete také jednoduše převzít adresu z nebezpečných bloků kódu, pokud nativní kód nebude používat ukazatel za koncem aktuální metody.</span><span class="sxs-lookup"><span data-stu-id="570f7-252">You can also simply take the address in unsafe code blocks if native code won't use the pointer past the end of the current method.</span></span>

<span data-ttu-id="570f7-253">Přenositelné struktury jsou mnohem větší, protože je lze jednoduše použít přímo zařazovací vrstvou.</span><span class="sxs-lookup"><span data-stu-id="570f7-253">Blittable structs are much more performant as they can simply be used directly by the marshaling layer.</span></span> <span data-ttu-id="570f7-254">Snažte se vytvořit struktury (například Nepoužívejte `bool`).</span><span class="sxs-lookup"><span data-stu-id="570f7-254">Try to make structs blittable (for example, avoid `bool`).</span></span> <span data-ttu-id="570f7-255">Další informace najdete v části [typy přenosit](#blittable-types) .</span><span class="sxs-lookup"><span data-stu-id="570f7-255">For more information, see the [Blittable Types](#blittable-types) section.</span></span>

<span data-ttu-id="570f7-256">*Pokud* je struktura přenositelná, `sizeof()` použijte místo `Marshal.SizeOf<MyStruct>()` pro lepší výkon.</span><span class="sxs-lookup"><span data-stu-id="570f7-256">*If* the struct is blittable, use `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for better performance.</span></span> <span data-ttu-id="570f7-257">Jak je uvedeno výše, můžete ověřit, zda je typ přenositelný, pokus o vytvoření připnutého `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="570f7-257">As mentioned above, you can validate that the type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="570f7-258">Pokud typ není řetězec nebo se považuje za Nepřenositelný, `GCHandle.Alloc` vyvolá `ArgumentException`výjimku.</span><span class="sxs-lookup"><span data-stu-id="570f7-258">If the type is not a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="570f7-259">Ukazatele na struktury v definicích musí být buď předány, `ref` nebo pomocí `unsafe` a `*`.</span><span class="sxs-lookup"><span data-stu-id="570f7-259">Pointers to structs in definitions must either be passed by `ref` or use `unsafe` and `*`.</span></span>

<span data-ttu-id="570f7-260">✔️ podle tvaru a názvů, které se používají v dokumentaci k oficiální platformě nebo v hlavičce, co nejvíce porovnává se spravovanou strukturou.</span><span class="sxs-lookup"><span data-stu-id="570f7-260">✔️ DO match the managed struct as closely as possible to the shape and names that are used in the official platform documentation or header.</span></span>

<span data-ttu-id="570f7-261">pro zlepšení výkonu ✔️ použít `sizeof()` jazyk C# `Marshal.SizeOf<MyStruct>()` místo pro přenositelné struktury.</span><span class="sxs-lookup"><span data-stu-id="570f7-261">✔️ DO use the C# `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for blittable structures to improve performance.</span></span>

<span data-ttu-id="570f7-262">❌Nepoužívejte `System.Delegate` pole `System.MulticastDelegate` nebo pro reprezentace polí ukazatelů na funkce ve strukturách.</span><span class="sxs-lookup"><span data-stu-id="570f7-262">❌ AVOID using `System.Delegate` or `System.MulticastDelegate` fields to represent function pointer fields in structures.</span></span>

<span data-ttu-id="570f7-263">Vzhledem <xref:System.Delegate?displayProperty=fullName> k <xref:System.MulticastDelegate?displayProperty=fullName> tomu, že a nemají požadovaný podpis, nezaručuje, že předaný delegát bude odpovídat podpisu, který nativní kód očekává.</span><span class="sxs-lookup"><span data-stu-id="570f7-263">Since <xref:System.Delegate?displayProperty=fullName> and <xref:System.MulticastDelegate?displayProperty=fullName> don't have a required signature, they don't guarantee that the delegate passed in will match the signature the native code expects.</span></span> <span data-ttu-id="570f7-264">Navíc v .NET Framework a .NET Core zařazování struktury obsahující `System.Delegate` nebo `System.MulticastDelegate` z nativní reprezentace do spravovaného objektu může destabilizovat modul runtime, pokud hodnota pole v nativní reprezentaci není ukazatel na funkci, který balí spravovaného delegáta.</span><span class="sxs-lookup"><span data-stu-id="570f7-264">Additionally, in .NET Framework and .NET Core, marshaling a struct containing a `System.Delegate` or `System.MulticastDelegate` from its native representation to a managed object can destabilize the runtime if the value of the field in the native representation isn't a function pointer that wraps a managed delegate.</span></span> <span data-ttu-id="570f7-265">V rozhraní .NET 5 a novějších verzích není podporováno `System.Delegate` zařazování pole nebo `System.MulticastDelegate` z nativní reprezentace na spravovaný objekt.</span><span class="sxs-lookup"><span data-stu-id="570f7-265">In .NET 5 and later versions, marshaling a `System.Delegate` or `System.MulticastDelegate` field from a native representation to a managed object is not supported.</span></span> <span data-ttu-id="570f7-266">Místo `System.Delegate` nebo `System.MulticastDelegate`použijte konkrétní typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="570f7-266">Use a specific delegate type instead of `System.Delegate` or `System.MulticastDelegate`.</span></span>

### <a name="fixed-buffers"></a><span data-ttu-id="570f7-267">Pevné vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="570f7-267">Fixed Buffers</span></span>

<span data-ttu-id="570f7-268">Pole jako `INT_PTR Reserved1[2]` musí být zařazeno do dvou `IntPtr` polí `Reserved1a` a. `Reserved1b`</span><span class="sxs-lookup"><span data-stu-id="570f7-268">An array like `INT_PTR Reserved1[2]` has to be marshaled to two `IntPtr` fields, `Reserved1a` and `Reserved1b`.</span></span> <span data-ttu-id="570f7-269">Pokud je nativním polem primitivní typ, můžeme pomocí `fixed` klíčového slova ho zapsat trochu efektivněji.</span><span class="sxs-lookup"><span data-stu-id="570f7-269">When the native array is a primitive type, we can use the `fixed` keyword to write it a little more cleanly.</span></span> <span data-ttu-id="570f7-270">Například `SYSTEM_PROCESS_INFORMATION` vypadá jako v nativní hlavičce:</span><span class="sxs-lookup"><span data-stu-id="570f7-270">For example, `SYSTEM_PROCESS_INFORMATION` looks like this in the native header:</span></span>

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

<span data-ttu-id="570f7-271">V jazyce C# je můžeme zapsat takto:</span><span class="sxs-lookup"><span data-stu-id="570f7-271">In C#, we can write it like this:</span></span>

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

<span data-ttu-id="570f7-272">Existuje však několik možná úskalí s pevnými vyrovnávacími pamětmi.</span><span class="sxs-lookup"><span data-stu-id="570f7-272">However, there are some gotchas with fixed buffers.</span></span> <span data-ttu-id="570f7-273">Pevné vyrovnávací paměti nepřenositelného typu nebudou správně zařazeny, takže musí být místní pole rozšířeno na více jednotlivých polí.</span><span class="sxs-lookup"><span data-stu-id="570f7-273">Fixed buffers of non-blittable types won't be correctly marshaled, so the in-place array needs to be expanded out to multiple individual fields.</span></span> <span data-ttu-id="570f7-274">V .NET Framework a .NET Core před 3,0 platí, že pokud je struktura obsahující pevné pole vyrovnávací paměti vnořena do nepřenositelné struktury, pole pevné vyrovnávací paměti se správně nezazařazuje do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="570f7-274">Additionally, in .NET Framework and .NET Core before 3.0, if a struct containing a fixed buffer field is nested within a non-blittable struct, the fixed buffer field won't be correctly marshaled to native code.</span></span>
