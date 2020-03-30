---
title: Nativní osvědčené postupy interoperability – .NET
description: Seznamte se s doporučenými postupy pro propojení s nativními součástmi v rozhraní .NET.
ms.date: 01/18/2019
ms.openlocfilehash: e5d96471e796dca712d25d2d9e2609508180d83f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391218"
---
# <a name="native-interoperability-best-practices"></a><span data-ttu-id="e4e2e-103">Nativní osvědčené postupy interoperability</span><span class="sxs-lookup"><span data-stu-id="e4e2e-103">Native interoperability best practices</span></span>

<span data-ttu-id="e4e2e-104">Rozhraní .NET nabízí různé způsoby přizpůsobení nativního kódu interoperability.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-104">.NET gives you a variety of ways to customize your native interoperability code.</span></span> <span data-ttu-id="e4e2e-105">Tento článek obsahuje pokyny, které microsoft .NET týmy postupujte pro nativní interoperabilitu.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-105">This article includes the guidance that Microsoft's .NET teams follow for native interoperability.</span></span>

## <a name="general-guidance"></a><span data-ttu-id="e4e2e-106">Obecné pokyny</span><span class="sxs-lookup"><span data-stu-id="e4e2e-106">General guidance</span></span>

<span data-ttu-id="e4e2e-107">Pokyny v této části platí pro všechny scénáře interop.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-107">The guidance in this section applies to all interop scenarios.</span></span>

- <span data-ttu-id="e4e2e-108">✔️ do použít stejné pojmenování a velká písmena pro vaše metody a parametry jako nativní metody, které chcete volat.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-108">✔️ DO use the same naming and capitalization for your methods and parameters as the native method you want to call.</span></span>
- <span data-ttu-id="e4e2e-109">✔️ zvážit použití stejného pojmenování a velkých písmen pro konstantní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-109">✔️ CONSIDER using the same naming and capitalization for constant values.</span></span>
- <span data-ttu-id="e4e2e-110">✔️ DO použijte typy .NET, které mapují nejblíže k nativnímu typu.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-110">✔️ DO use .NET types that map closest to the native type.</span></span> <span data-ttu-id="e4e2e-111">Například v jazyce `uint` C# použijte, `unsigned int`když je nativní typ .</span><span class="sxs-lookup"><span data-stu-id="e4e2e-111">For example, in C#, use `uint` when the native type is `unsigned int`.</span></span>
- <span data-ttu-id="e4e2e-112">✔️ do `[In]` a `[Out]` atributy pouze v případě, že chování, které chcete, se liší od výchozího chování.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-112">✔️ DO only use `[In]` and `[Out]` attributes when the behavior you want differs from the default behavior.</span></span>
- <span data-ttu-id="e4e2e-113">✔️ zvážit <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> použití k fondu nativní vyrovnávací paměti pole.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-113">✔️ CONSIDER using <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> to pool your native array buffers.</span></span>
- <span data-ttu-id="e4e2e-114">✔️ ZVAŽTe zabalení deklarací P/Invoke do třídy se stejným názvem a velkými písmeny jako nativní knihovna.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-114">✔️ CONSIDER wrapping your P/Invoke declarations in a class with the same name and capitalization as your native library.</span></span>
  - <span data-ttu-id="e4e2e-115">To umožňuje `[DllImport]` atributy pomocí funkce `nameof` jazyka C# předat název nativní knihovny a ujistěte se, že jste nechybově název nativní knihovny.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-115">This allows your `[DllImport]` attributes to use the C# `nameof` language feature to pass in the name of the native library and ensure that you didn't misspell the name of the native library.</span></span>

## <a name="dllimport-attribute-settings"></a><span data-ttu-id="e4e2e-116">Nastavení atributu DllImport</span><span class="sxs-lookup"><span data-stu-id="e4e2e-116">DllImport attribute settings</span></span>

| <span data-ttu-id="e4e2e-117">Nastavení</span><span class="sxs-lookup"><span data-stu-id="e4e2e-117">Setting</span></span> | <span data-ttu-id="e4e2e-118">Výchozí</span><span class="sxs-lookup"><span data-stu-id="e4e2e-118">Default</span></span> | <span data-ttu-id="e4e2e-119">Doporučení</span><span class="sxs-lookup"><span data-stu-id="e4e2e-119">Recommendation</span></span> | <span data-ttu-id="e4e2e-120">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e4e2e-120">Details</span></span> |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  <span data-ttu-id="e4e2e-121">zachovat výchozí nastavení</span><span class="sxs-lookup"><span data-stu-id="e4e2e-121">keep default</span></span>  | <span data-ttu-id="e4e2e-122">Pokud je to explicitně nastaveno na false, vrácené hodnoty HRESULT se změní na výjimky (a vrácená hodnota v definici se stane nulovou jako výsledek).</span><span class="sxs-lookup"><span data-stu-id="e4e2e-122">When this is explicitly set to false, failed HRESULT return values will be turned into exceptions (and the return value in the definition becomes null as a result).</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | <span data-ttu-id="e4e2e-123">závisí na API</span><span class="sxs-lookup"><span data-stu-id="e4e2e-123">depends on the API</span></span>  | <span data-ttu-id="e4e2e-124">Nastavte tuto hodnotu na hodnotu true, pokud rozhraní API používá GetLastError a k získání hodnoty použijte marshal.GetLastWin32Error.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-124">Set this to true if the API uses GetLastError and use Marshal.GetLastWin32Error to get the value.</span></span> <span data-ttu-id="e4e2e-125">Pokud rozhraní API nastaví podmínku, která říká, že má chybu, získejte chybu před provedením dalších volání, aby nedošlo k nechtěnému přepsání.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-125">If the API sets a condition that says it has an error, get the error before making other calls to avoid inadvertently having it overwritten.</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | <span data-ttu-id="e4e2e-126">`CharSet.None`, který se `CharSet.Ansi` vrací k chování</span><span class="sxs-lookup"><span data-stu-id="e4e2e-126">`CharSet.None`, which falls back to `CharSet.Ansi` behavior</span></span>  | <span data-ttu-id="e4e2e-127">Explicitně `CharSet.Unicode` `CharSet.Ansi` použít nebo pokud jsou v definici přítomny řetězce nebo znaky</span><span class="sxs-lookup"><span data-stu-id="e4e2e-127">Explicitly  use `CharSet.Unicode` or `CharSet.Ansi` when strings or characters are present in the definition</span></span> | <span data-ttu-id="e4e2e-128">To určuje zařazování chování `ExactSpelling` řetězců `false`a co dělá, když .</span><span class="sxs-lookup"><span data-stu-id="e4e2e-128">This specifies marshaling behavior of strings and what `ExactSpelling` does when `false`.</span></span> <span data-ttu-id="e4e2e-129">Všimněte `CharSet.Ansi` si, že je vlastně UTF8 na Unixu.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-129">Note that `CharSet.Ansi` is actually UTF8 on Unix.</span></span> <span data-ttu-id="e4e2e-130">_Většinu_ času systém Windows používá Unicode, zatímco Unix používá UTF8.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-130">_Most_ of the time Windows uses Unicode while Unix uses UTF8.</span></span> <span data-ttu-id="e4e2e-131">Další informace o dokumentaci ke [znakové sady](./charset.md).</span><span class="sxs-lookup"><span data-stu-id="e4e2e-131">See more information on the [documentation on charsets](./charset.md).</span></span> |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | <span data-ttu-id="e4e2e-132">Nastavte tuto hodnotu na hodnotu true a získejte nepatrnou výhodu perf, protože modul runtime nebude hledat alternativní `CharSet` názvy funkcí `CharSet.Ansi` s příponou `CharSet.Unicode`"A" nebo "W" v závislosti na hodnotě nastavení ("A" pro a "W" pro ).</span><span class="sxs-lookup"><span data-stu-id="e4e2e-132">Set this to true and gain a slight perf benefit as the runtime will not look for alternate function names with either an "A" or "W" suffix depending on the value of the `CharSet` setting ("A" for `CharSet.Ansi` and "W" for `CharSet.Unicode`).</span></span> |

## <a name="string-parameters"></a><span data-ttu-id="e4e2e-133">Parametry řetězce</span><span class="sxs-lookup"><span data-stu-id="e4e2e-133">String parameters</span></span>

<span data-ttu-id="e4e2e-134">Pokud CharSet je Unicode nebo argument `[MarshalAs(UnmanagedType.LPWSTR)]` je explicitně označen jako `ref` _a_ řetězec je předán hodnotou (ne nebo `out`), řetězec bude připnut a používán přímo nativní kód (spíše než zkopírovat).</span><span class="sxs-lookup"><span data-stu-id="e4e2e-134">When the CharSet is Unicode or the argument is explicitly marked as `[MarshalAs(UnmanagedType.LPWSTR)]` _and_ the string is passed by value (not `ref` or `out`), the string will be pinned and used directly by native code (rather than copied).</span></span>

<span data-ttu-id="e4e2e-135">Nezapomeňte označit `[DllImport]` jako, `Charset.Unicode` pokud výslovně chcete ANSI léčbu vašich řetězců.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-135">Remember to mark the `[DllImport]` as `Charset.Unicode` unless you explicitly want ANSI treatment of your strings.</span></span>

<span data-ttu-id="e4e2e-136">❌Nepoužívejte `[Out] string` parametry.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-136">❌ DO NOT use `[Out] string` parameters.</span></span> <span data-ttu-id="e4e2e-137">Parametry řetězce předané `[Out]` hodnotou s atributem mohou destabilizovat dobu runtime, pokud je řetězec internovaný řetězec.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-137">String parameters passed by value with the `[Out]` attribute can destabilize the runtime if the string is an interned string.</span></span> <span data-ttu-id="e4e2e-138">Další informace o interning řetězce <xref:System.String.Intern%2A?displayProperty=nameWithType>v dokumentaci pro .</span><span class="sxs-lookup"><span data-stu-id="e4e2e-138">See more information about string interning in the documentation for <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="e4e2e-139">❌Vyhněte se `StringBuilder` parametrům.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-139">❌ AVOID `StringBuilder` parameters.</span></span> <span data-ttu-id="e4e2e-140">`StringBuilder`zařazování *vždy* vytvoří nativní kopii vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-140">`StringBuilder` marshaling *always* creates a native buffer copy.</span></span> <span data-ttu-id="e4e2e-141">Jako takový může být extrémně neefektivní.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-141">As such, it can be extremely inefficient.</span></span> <span data-ttu-id="e4e2e-142">Vezměte si typický scénář volání rozhraní API systému Windows, který přebírá řetězec:</span><span class="sxs-lookup"><span data-stu-id="e4e2e-142">Take the typical scenario of calling a Windows API that takes a string:</span></span>

1. <span data-ttu-id="e4e2e-143">Vytvoření SB požadované kapacity (přiděluje spravovanou kapacitu)**{1}**</span><span class="sxs-lookup"><span data-stu-id="e4e2e-143">Create a SB of the desired capacity (allocates managed capacity) **{1}**</span></span>
2. <span data-ttu-id="e4e2e-144">Invoke</span><span class="sxs-lookup"><span data-stu-id="e4e2e-144">Invoke</span></span>
   1. <span data-ttu-id="e4e2e-145">Přidělí nativní vyrovnávací paměť.**{2}**</span><span class="sxs-lookup"><span data-stu-id="e4e2e-145">Allocates a native buffer **{2}**</span></span>
   2. <span data-ttu-id="e4e2e-146">Zkopíruje obsah, pokud `[In]` _(výchozí pro `StringBuilder` parametr)_</span><span class="sxs-lookup"><span data-stu-id="e4e2e-146">Copies the contents if `[In]` _(the default for a `StringBuilder` parameter)_</span></span>
   3. <span data-ttu-id="e4e2e-147">Zkopíruje nativní vyrovnávací paměť do `[Out]` **{3}** nově přiděleného spravovaného pole, pokud _(také výchozí `StringBuilder`pro)_</span><span class="sxs-lookup"><span data-stu-id="e4e2e-147">Copies the native buffer into a newly allocated managed array if `[Out]` **{3}** _(also the default for `StringBuilder`)_</span></span>
3. <span data-ttu-id="e4e2e-148">`ToString()`přiděluje další spravované pole**{4}**</span><span class="sxs-lookup"><span data-stu-id="e4e2e-148">`ToString()` allocates yet another managed array **{4}**</span></span>

<span data-ttu-id="e4e2e-149">To *{4}* je přidělení získat řetězec z nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-149">That is *{4}* allocations to get a string out of native code.</span></span> <span data-ttu-id="e4e2e-150">To nejlepší, co můžete udělat pro `StringBuilder` omezení je znovu použít v jiném volání, ale to stále šetří pouze *1* přidělení.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-150">The best you can do to limit this is to reuse the `StringBuilder` in another call but this still only saves *1* allocation.</span></span> <span data-ttu-id="e4e2e-151">Je mnohem lepší použít a uložit do `ArrayPool`mezipaměti vyrovnávací paměť znaků z `ToString()` - pak se můžete dostat dolů pouze přidělení pro následné volání.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-151">It's much better to use and cache a character buffer from `ArrayPool`- you can then get down to just the allocation for the `ToString()` on subsequent calls.</span></span>

<span data-ttu-id="e4e2e-152">Další problém `StringBuilder` s je, že vždy zkopíruje zpětnou vyrovnávací paměť zpět zpět až do první null.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-152">The other issue with `StringBuilder` is that it always copies the return buffer back up to the first null.</span></span> <span data-ttu-id="e4e2e-153">Pokud předaný zpětný řetězec není ukončen nebo je řetězec s dvojitou hodnotou null, je p/invoke přinejlepším nesprávný.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-153">If the passed back string isn't terminated or is a double-null-terminated string, your P/Invoke is incorrect at best.</span></span>

<span data-ttu-id="e4e2e-154">Pokud *používáte* `StringBuilder`, jeden poslední gotcha je, že kapacita **neobsahuje** skryté null, který je vždy zaúčtovánv interop.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-154">If you *do* use `StringBuilder`, one last gotcha is that the capacity does **not** include a hidden null, which is always accounted for in interop.</span></span> <span data-ttu-id="e4e2e-155">Je běžné, že lidé si to špatně jako většina api chtějí velikost vyrovnávací paměti *včetně* null.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-155">It's common for people to get this wrong as most APIs want the size of the buffer *including* the null.</span></span> <span data-ttu-id="e4e2e-156">To může mít za následek zbytečné přidělení.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-156">This can result in wasted/unnecessary allocations.</span></span> <span data-ttu-id="e4e2e-157">Navíc tento gotcha zabraňuje runtime optimalizace `StringBuilder` zařazování minimalizovat kopie.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-157">Additionally, this gotcha prevents the runtime from optimizing `StringBuilder` marshaling to minimize copies.</span></span>

<span data-ttu-id="e4e2e-158">✔️ ZVÁŽIT `char[]`použití `ArrayPool`s z .</span><span class="sxs-lookup"><span data-stu-id="e4e2e-158">✔️ CONSIDER using `char[]`s from an `ArrayPool`.</span></span>

<span data-ttu-id="e4e2e-159">Další informace o zařazování řetězců naleznete [v tématu Default Marshaling for Strings](../../framework/interop/default-marshaling-for-strings.md) and [Customizing string marshaling](customize-parameter-marshaling.md#customizing-string-parameters).</span><span class="sxs-lookup"><span data-stu-id="e4e2e-159">For more information on string marshaling, see [Default Marshaling for Strings](../../framework/interop/default-marshaling-for-strings.md) and [Customizing string marshaling](customize-parameter-marshaling.md#customizing-string-parameters).</span></span>

> <span data-ttu-id="e4e2e-160">__Specifické pro Windows__ Pro `[Out]` řetězce clr bude `CoTaskMemFree` ve výchozím nastavení `SysStringFree` používat k uvolnění řetězců `UnmanagedType.BSTR`nebo pro řetězce, které jsou označeny jako .</span><span class="sxs-lookup"><span data-stu-id="e4e2e-160">__Windows Specific__ For `[Out]` strings the CLR will use `CoTaskMemFree` by default to free strings or `SysStringFree` for strings that are marked as `UnmanagedType.BSTR`.</span></span>
> <span data-ttu-id="e4e2e-161">**Pro většinu api s vyrovnávací pamětí výstupního řetězce:** Předaný počet znaků musí obsahovat null.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-161">**For most APIs with an output string buffer:** The passed in character count must include the null.</span></span> <span data-ttu-id="e4e2e-162">Pokud vrácená hodnota je menší než předán v počtu znaků volání proběhlo úspěšně a hodnota je počet znaků *bez* koncové null.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-162">If the returned value is less than the passed in character count the call has succeeded and the value is the number of characters *without* the trailing null.</span></span> <span data-ttu-id="e4e2e-163">V opačném případě je počet požadovanou velikost vyrovnávací paměti *včetně* nulového znaku.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-163">Otherwise the count is the required size of the buffer *including* the null character.</span></span>
>
> - <span data-ttu-id="e4e2e-164">Pass in 5, get 4: Řetězec je 4 znaky dlouhé s koncovou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-164">Pass in 5, get 4: The string is 4 characters long with a trailing null.</span></span>
> - <span data-ttu-id="e4e2e-165">Předat v 5, získat 6: Řetězec je 5 znaků dlouhý, potřebují 6 znaků vyrovnávací paměti pro uložení null.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-165">Pass in 5, get 6: The string is 5 characters long, need a 6 character buffer to hold the null.</span></span>
> [<span data-ttu-id="e4e2e-166">Datové typy systému Windows pro řetězce</span><span class="sxs-lookup"><span data-stu-id="e4e2e-166">Windows Data Types for Strings</span></span>](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a><span data-ttu-id="e4e2e-167">Logické parametry a pole</span><span class="sxs-lookup"><span data-stu-id="e4e2e-167">Boolean parameters and fields</span></span>

<span data-ttu-id="e4e2e-168">Booleans jsou snadno zkazit.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-168">Booleans are easy to mess up.</span></span> <span data-ttu-id="e4e2e-169">Ve výchozím nastavení `bool` je rozhraní .NET `BOOL`zařazeno do systému Windows , kde je hodnota 4 bajtů.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-169">By default, a .NET `bool` is marshaled to a Windows `BOOL`, where it's a 4-byte value.</span></span> <span data-ttu-id="e4e2e-170">Však `_Bool`, `bool` a typy v Jazyce C a C++ jsou *jeden* bajt.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-170">However, the `_Bool`, and `bool` types in C and C++ are a *single* byte.</span></span> <span data-ttu-id="e4e2e-171">To může vést k obtížné vystopovat chyby jako polovina vrácená hodnota bude zahozena, což bude pouze *potenciálně* změnit výsledek.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-171">This can lead to hard to track down bugs as half the return value will be discarded, which will only *potentially* change the result.</span></span> <span data-ttu-id="e4e2e-172">Další informace o zařazování hodnot `bool` .NET `bool` do typů jazyka C nebo C++ naleznete v dokumentaci k [přizpůsobení zařazování logického pole](customize-struct-marshaling.md#customizing-boolean-field-marshaling).</span><span class="sxs-lookup"><span data-stu-id="e4e2e-172">For more for information on marshaling .NET `bool` values to C or C++ `bool` types, see the documentation on [customizing boolean field marshaling](customize-struct-marshaling.md#customizing-boolean-field-marshaling).</span></span>

## <a name="guids"></a><span data-ttu-id="e4e2e-173">Guid</span><span class="sxs-lookup"><span data-stu-id="e4e2e-173">GUIDs</span></span>

<span data-ttu-id="e4e2e-174">Identifikátory GUID jsou použitelné přímo v podpisech.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-174">GUIDs are usable directly in signatures.</span></span> <span data-ttu-id="e4e2e-175">Mnoho oken API `GUID&` systému `REFIID`Windows trvat aliasy typu jako .</span><span class="sxs-lookup"><span data-stu-id="e4e2e-175">Many Windows APIs take `GUID&` type aliases like `REFIID`.</span></span> <span data-ttu-id="e4e2e-176">Při předání ref, mohou být `ref` předány `[MarshalAs(UnmanagedType.LPStruct)]` nebo s atributem.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-176">When passed by ref, they can either be passed by `ref` or with the `[MarshalAs(UnmanagedType.LPStruct)]` attribute.</span></span>

| <span data-ttu-id="e4e2e-177">GUID</span><span class="sxs-lookup"><span data-stu-id="e4e2e-177">GUID</span></span> | <span data-ttu-id="e4e2e-178">Identifikátor GUID pro odkaz na odkaz</span><span class="sxs-lookup"><span data-stu-id="e4e2e-178">By-ref GUID</span></span> |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

<span data-ttu-id="e4e2e-179">❌NEPOUŽÍVEJTE `[MarshalAs(UnmanagedType.LPStruct)]` pro nic `ref` jiného než parametry GUID.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-179">❌ DO NOT Use `[MarshalAs(UnmanagedType.LPStruct)]` for anything other than `ref` GUID parameters.</span></span>

## <a name="blittable-types"></a><span data-ttu-id="e4e2e-180">Přenositelné typy</span><span class="sxs-lookup"><span data-stu-id="e4e2e-180">Blittable types</span></span>

<span data-ttu-id="e4e2e-181">Přenositelné typy jsou typy, které mají stejnou reprezentaci na úrovni bitů ve spravovaném a nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-181">Blittable types are types that have the same bit-level representation in managed and native code.</span></span> <span data-ttu-id="e4e2e-182">Jako takové není nutné převést do jiného formátu, který má být zařazen do a z nativního kódu, a protože to zlepšuje výkon, měly by být upřednostňovány.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-182">As such they do not need to be converted to another format to be marshaled to and from native code, and as this improves performance they should be preferred.</span></span>

<span data-ttu-id="e4e2e-183">**Přenositelné typy:**</span><span class="sxs-lookup"><span data-stu-id="e4e2e-183">**Blittable types:**</span></span>

- <span data-ttu-id="e4e2e-184">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span><span class="sxs-lookup"><span data-stu-id="e4e2e-184">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span></span>
- <span data-ttu-id="e4e2e-185">nevnořená jednorozměrná pole přenositelných typů `int[]`(například)</span><span class="sxs-lookup"><span data-stu-id="e4e2e-185">non-nested one-dimensional arrays of blittable types (for example, `int[]`)</span></span>
- <span data-ttu-id="e4e2e-186">struktury a třídy s pevným rozložením, které mají pouze přenositelné typy hodnot pro pole instancí</span><span class="sxs-lookup"><span data-stu-id="e4e2e-186">structs and classes with fixed layout that only have blittable value types for instance fields</span></span>
  - <span data-ttu-id="e4e2e-187">pevné rozložení `[StructLayout(LayoutKind.Sequential)]` vyžaduje nebo`[StructLayout(LayoutKind.Explicit)]`</span><span class="sxs-lookup"><span data-stu-id="e4e2e-187">fixed layout requires `[StructLayout(LayoutKind.Sequential)]` or `[StructLayout(LayoutKind.Explicit)]`</span></span>
  - <span data-ttu-id="e4e2e-188">struktury jsou `LayoutKind.Sequential` ve výchozím nastavení, třídy jsou`LayoutKind.Auto`</span><span class="sxs-lookup"><span data-stu-id="e4e2e-188">structs are `LayoutKind.Sequential` by default, classes are `LayoutKind.Auto`</span></span>

<span data-ttu-id="e4e2e-189">**NENÍ přenositelný:**</span><span class="sxs-lookup"><span data-stu-id="e4e2e-189">**NOT blittable:**</span></span>

- `bool`

<span data-ttu-id="e4e2e-190">**Někdy přenositelný:**</span><span class="sxs-lookup"><span data-stu-id="e4e2e-190">**SOMETIMES blittable:**</span></span>

- <span data-ttu-id="e4e2e-191">`char`, `string`</span><span class="sxs-lookup"><span data-stu-id="e4e2e-191">`char`, `string`</span></span>

<span data-ttu-id="e4e2e-192">Při přenositelné typy jsou předány odkazem, jsou jednoduše připnul zařazovacím roštinou namísto zkopírování do zprostředkující vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-192">When blittable types are passed by reference, they're simply pinned by the marshaller instead of being copied to an intermediate buffer.</span></span> <span data-ttu-id="e4e2e-193">(Třídy jsou ze své podstaty předány odkazem, `ref` `out`struktury jsou předávány odkazem při použití s nebo .)</span><span class="sxs-lookup"><span data-stu-id="e4e2e-193">(Classes are inherently passed by reference, structs are passed by reference when used with `ref` or `out`.)</span></span>

<span data-ttu-id="e4e2e-194">`char`je přenositelná v jednorozměrném poli **nebo** pokud je součástí typu, který `[StructLayout]` obsahuje, je explicitně označen . `CharSet = CharSet.Unicode`</span><span class="sxs-lookup"><span data-stu-id="e4e2e-194">`char` is blittable in a one-dimensional array **or** if it's part of a type that contains it's explicitly marked with `[StructLayout]` with `CharSet = CharSet.Unicode`.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

<span data-ttu-id="e4e2e-195">`string`je přenositelný, pokud není obsažen v jiném typu a je předáván `[MarshalAs(UnmanagedType.LPWStr)]` jako `[DllImport]` argument, který je označen nebo má `CharSet = CharSet.Unicode` nastaveno.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-195">`string` is blittable if it isn't contained in another type and it's being passed as an argument that is marked with `[MarshalAs(UnmanagedType.LPWStr)]` or the `[DllImport]` has `CharSet = CharSet.Unicode` set.</span></span>

<span data-ttu-id="e4e2e-196">Můžete zjistit, zda je typ přenositelný pokusem `GCHandle`o vytvoření připnutého .</span><span class="sxs-lookup"><span data-stu-id="e4e2e-196">You can see if a type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="e4e2e-197">Pokud typ není řetězec nebo považován za `GCHandle.Alloc` přenositelný, bude hodit `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-197">If the type isn't a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="e4e2e-198">✔️ DO, aby vaše struktury blittable, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-198">✔️ DO make your structures blittable when possible.</span></span>

<span data-ttu-id="e4e2e-199">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="e4e2e-199">For more information, see:</span></span>

- [<span data-ttu-id="e4e2e-200">Přenositelné a nepřenositelné typy</span><span class="sxs-lookup"><span data-stu-id="e4e2e-200">Blittable and Non-Blittable Types</span></span>](../../framework/interop/blittable-and-non-blittable-types.md)
- [<span data-ttu-id="e4e2e-201">Zařazování typu</span><span class="sxs-lookup"><span data-stu-id="e4e2e-201">Type Marshaling</span></span>](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a><span data-ttu-id="e4e2e-202">Udržování spravovaných objektů při životě</span><span class="sxs-lookup"><span data-stu-id="e4e2e-202">Keeping managed objects alive</span></span>

<span data-ttu-id="e4e2e-203">`GC.KeepAlive()`zajistí, že objekt zůstane v oboru, dokud není přístupná metoda KeepAlive.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-203">`GC.KeepAlive()` will ensure an object stays in scope until the KeepAlive method is hit.</span></span>

<span data-ttu-id="e4e2e-204">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef)umožňuje zařazovacímu objektu udržovat objekt naživu po dobu trvání P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-204">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) allows the marshaller to keep an object alive for the duration of a P/Invoke.</span></span> <span data-ttu-id="e4e2e-205">Lze jej použít `IntPtr` místo v podpisech metody.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-205">It can be used instead of `IntPtr` in method signatures.</span></span> <span data-ttu-id="e4e2e-206">`SafeHandle`účinně nahrazuje tuto třídu a místo toho by měly být použity.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-206">`SafeHandle` effectively replaces this class and should be used instead.</span></span>

<span data-ttu-id="e4e2e-207">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle)umožňuje připnutí spravovaného objektu a získání nativního ukazatele.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-207">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) allows pinning a managed object and getting the native pointer to it.</span></span> <span data-ttu-id="e4e2e-208">Základní vzorec je:</span><span class="sxs-lookup"><span data-stu-id="e4e2e-208">The basic pattern is:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

<span data-ttu-id="e4e2e-209">Připnutí není výchozí `GCHandle`pro .</span><span class="sxs-lookup"><span data-stu-id="e4e2e-209">Pinning isn't the default for `GCHandle`.</span></span> <span data-ttu-id="e4e2e-210">Další hlavní vzor je pro předávání odkazu na spravovaný objekt prostřednictvím nativního kódu a zpět na spravovaný kód, obvykle s zpětným voláním.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-210">The other major pattern is for passing a reference to a managed object through native code and back to managed code, usually with a callback.</span></span> <span data-ttu-id="e4e2e-211">Zde je vzor:</span><span class="sxs-lookup"><span data-stu-id="e4e2e-211">Here is the pattern:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

<span data-ttu-id="e4e2e-212">Nezapomeňte, že `GCHandle` je třeba explicitně uvolnit, aby se zabránilo nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-212">Don't forget that `GCHandle` needs to be explicitly freed to avoid memory leaks.</span></span>

## <a name="common-windows-data-types"></a><span data-ttu-id="e4e2e-213">Běžné datové typy systému Windows</span><span class="sxs-lookup"><span data-stu-id="e4e2e-213">Common Windows data types</span></span>

<span data-ttu-id="e4e2e-214">Zde je seznam datových typů běžně používaných v systému Windows API a které c# typy použít při volání do kódu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-214">Here is a list of data types commonly used in Windows APIs and which C# types to use when calling into the Windows code.</span></span>

<span data-ttu-id="e4e2e-215">Následující typy mají stejnou velikost v 32bitovém a 64bitovém systému Windows, a to navzdory jejich názvům.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-215">The following types are the same size on 32-bit and 64-bit Windows, despite their names.</span></span>

| <span data-ttu-id="e4e2e-216">impulzu</span><span class="sxs-lookup"><span data-stu-id="e4e2e-216">Width</span></span> | <span data-ttu-id="e4e2e-217">Windows</span><span class="sxs-lookup"><span data-stu-id="e4e2e-217">Windows</span></span>          | <span data-ttu-id="e4e2e-218">C (Windows)</span><span class="sxs-lookup"><span data-stu-id="e4e2e-218">C (Windows)</span></span>          | <span data-ttu-id="e4e2e-219">C#</span><span class="sxs-lookup"><span data-stu-id="e4e2e-219">C#</span></span>       | <span data-ttu-id="e4e2e-220">Alternativní</span><span class="sxs-lookup"><span data-stu-id="e4e2e-220">Alternative</span></span>                          |
|:------|:-----------------|:---------------------|:---------|:-------------------------------------|
| <span data-ttu-id="e4e2e-221">32</span><span class="sxs-lookup"><span data-stu-id="e4e2e-221">32</span></span>    | `BOOL`           | `int`                | `int`    | `bool`                               |
| <span data-ttu-id="e4e2e-222">8</span><span class="sxs-lookup"><span data-stu-id="e4e2e-222">8</span></span>     | `BOOLEAN`        | `unsigned char`      | `byte`   | `[MarshalAs(UnmanagedType.U1)] bool` |
| <span data-ttu-id="e4e2e-223">8</span><span class="sxs-lookup"><span data-stu-id="e4e2e-223">8</span></span>     | `BYTE`           | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="e4e2e-224">8</span><span class="sxs-lookup"><span data-stu-id="e4e2e-224">8</span></span>     | `CHAR`           | `char`               | `sbyte`  |                                      |
| <span data-ttu-id="e4e2e-225">8</span><span class="sxs-lookup"><span data-stu-id="e4e2e-225">8</span></span>     | `UCHAR`          | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="e4e2e-226">16</span><span class="sxs-lookup"><span data-stu-id="e4e2e-226">16</span></span>    | `SHORT`          | `short`              | `short`  |                                      |
| <span data-ttu-id="e4e2e-227">16</span><span class="sxs-lookup"><span data-stu-id="e4e2e-227">16</span></span>    | `CSHORT`         | `short`              | `short`  |                                      |
| <span data-ttu-id="e4e2e-228">16</span><span class="sxs-lookup"><span data-stu-id="e4e2e-228">16</span></span>    | `USHORT`         | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="e4e2e-229">16</span><span class="sxs-lookup"><span data-stu-id="e4e2e-229">16</span></span>    | `WORD`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="e4e2e-230">16</span><span class="sxs-lookup"><span data-stu-id="e4e2e-230">16</span></span>    | `ATOM`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="e4e2e-231">32</span><span class="sxs-lookup"><span data-stu-id="e4e2e-231">32</span></span>    | `INT`            | `int`                | `int`    |                                      |
| <span data-ttu-id="e4e2e-232">32</span><span class="sxs-lookup"><span data-stu-id="e4e2e-232">32</span></span>    | `LONG`           | `long`               | `int`    |                                      |
| <span data-ttu-id="e4e2e-233">32</span><span class="sxs-lookup"><span data-stu-id="e4e2e-233">32</span></span>    | `ULONG`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="e4e2e-234">32</span><span class="sxs-lookup"><span data-stu-id="e4e2e-234">32</span></span>    | `DWORD`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="e4e2e-235">64</span><span class="sxs-lookup"><span data-stu-id="e4e2e-235">64</span></span>    | `QWORD`          | `long long`          | `long`   |                                      |
| <span data-ttu-id="e4e2e-236">64</span><span class="sxs-lookup"><span data-stu-id="e4e2e-236">64</span></span>    | `LARGE_INTEGER`  | `long long`          | `long`   |                                      |
| <span data-ttu-id="e4e2e-237">64</span><span class="sxs-lookup"><span data-stu-id="e4e2e-237">64</span></span>    | `LONGLONG`       | `long long`          | `long`   |                                      |
| <span data-ttu-id="e4e2e-238">64</span><span class="sxs-lookup"><span data-stu-id="e4e2e-238">64</span></span>    | `ULONGLONG`      | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="e4e2e-239">64</span><span class="sxs-lookup"><span data-stu-id="e4e2e-239">64</span></span>    | `ULARGE_INTEGER` | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="e4e2e-240">32</span><span class="sxs-lookup"><span data-stu-id="e4e2e-240">32</span></span>    | `HRESULT`        | `long`               | `int`    |                                      |
| <span data-ttu-id="e4e2e-241">32</span><span class="sxs-lookup"><span data-stu-id="e4e2e-241">32</span></span>    | `NTSTATUS`       | `long`               | `int`    |                                      |

<span data-ttu-id="e4e2e-242">Následující typy, které jsou ukazatele, postupujte podle šířky platformy.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-242">The following types, being pointers, do follow the width of the platform.</span></span> <span data-ttu-id="e4e2e-243">`IntPtr` / Použij `UIntPtr` na tohle.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-243">Use `IntPtr`/`UIntPtr` for these.</span></span>

| <span data-ttu-id="e4e2e-244">Typy podepsaných `IntPtr`ukazatelů (použití)</span><span class="sxs-lookup"><span data-stu-id="e4e2e-244">Signed Pointer Types (use `IntPtr`)</span></span> | <span data-ttu-id="e4e2e-245">Nepodepsané typy ukazatelů `UIntPtr`(použití)</span><span class="sxs-lookup"><span data-stu-id="e4e2e-245">Unsigned Pointer Types (use `UIntPtr`)</span></span> |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

<span data-ttu-id="e4e2e-246">Systém `PVOID` Windows, který `void*` je C může `IntPtr` `UIntPtr`být zařazen `void*` jako buď nebo , ale raději, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-246">A Windows `PVOID` which is a C `void*` can be marshaled as either `IntPtr` or `UIntPtr`, but prefer `void*` when possible.</span></span>

[<span data-ttu-id="e4e2e-247">Datové typy systému Windows</span><span class="sxs-lookup"><span data-stu-id="e4e2e-247">Windows Data Types</span></span>](/windows/desktop/WinProg/windows-data-types)

[<span data-ttu-id="e4e2e-248">Rozsahy datových typů</span><span class="sxs-lookup"><span data-stu-id="e4e2e-248">Data Type Ranges</span></span>](/cpp/cpp/data-type-ranges)

## <a name="structs"></a><span data-ttu-id="e4e2e-249">Struktury</span><span class="sxs-lookup"><span data-stu-id="e4e2e-249">Structs</span></span>

<span data-ttu-id="e4e2e-250">Spravované struktury jsou vytvořeny v zásobníku a nejsou odebrány, dokud se metoda nevrátí.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-250">Managed structs are created on the stack and aren't removed until the method returns.</span></span> <span data-ttu-id="e4e2e-251">Podle definice pak jsou "připnuté" (nebude se pohybovat gc).</span><span class="sxs-lookup"><span data-stu-id="e4e2e-251">By definition then, they are "pinned" (it won't get moved by the GC).</span></span> <span data-ttu-id="e4e2e-252">Můžete také jednoduše vzít adresu v nebezpečných bloků kódu, pokud nativní kód nebude používat ukazatel za koncem aktuální metody.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-252">You can also simply take the address in unsafe code blocks if native code won't use the pointer past the end of the current method.</span></span>

<span data-ttu-id="e4e2e-253">Přenositelné struktury jsou mnohem výkonnější, protože mohou být jednoduše použity přímo zařazovací vrstvou.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-253">Blittable structs are much more performant as they can simply be used directly by the marshaling layer.</span></span> <span data-ttu-id="e4e2e-254">Snažte se, aby struktury blittable `bool`(například vyhnout ).</span><span class="sxs-lookup"><span data-stu-id="e4e2e-254">Try to make structs blittable (for example, avoid `bool`).</span></span> <span data-ttu-id="e4e2e-255">Další informace naleznete v části [Blittable Types.](#blittable-types)</span><span class="sxs-lookup"><span data-stu-id="e4e2e-255">For more information, see the [Blittable Types](#blittable-types) section.</span></span>

<span data-ttu-id="e4e2e-256">*Pokud* je struktura přenosná, `sizeof()` použijte `Marshal.SizeOf<MyStruct>()` místo pro lepší výkon.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-256">*If* the struct is blittable, use `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for better performance.</span></span> <span data-ttu-id="e4e2e-257">Jak bylo uvedeno výše, můžete ověřit, že typ je přenositelný `GCHandle`pokusem o vytvoření připnutého .</span><span class="sxs-lookup"><span data-stu-id="e4e2e-257">As mentioned above, you can validate that the type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="e4e2e-258">Pokud typ není řetězec nebo považován za `GCHandle.Alloc` přenositelný, bude hodit `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-258">If the type is not a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="e4e2e-259">Ukazatele na struktury v definicích musí být `ref` buď `unsafe` `*`předány, nebo použít a .</span><span class="sxs-lookup"><span data-stu-id="e4e2e-259">Pointers to structs in definitions must either be passed by `ref` or use `unsafe` and `*`.</span></span>

<span data-ttu-id="e4e2e-260">✔️ DO odpovídají spravované struktury co nejblíže k tvaru a názvy, které se používají v dokumentaci oficiální platformy nebo záhlaví.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-260">✔️ DO match the managed struct as closely as possible to the shape and names that are used in the official platform documentation or header.</span></span>

<span data-ttu-id="e4e2e-261">✔️ do použít `sizeof()` C# `Marshal.SizeOf<MyStruct>()` místo pro přenositelné struktury ke zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-261">✔️ DO use the C# `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for blittable structures to improve performance.</span></span>

<span data-ttu-id="e4e2e-262">❌Vyhněte se použití `System.Delegate` nebo `System.MulticastDelegate` pole představují pole ukazatele funkce ve strukturách.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-262">❌ AVOID using `System.Delegate` or `System.MulticastDelegate` fields to represent function pointer fields in structures.</span></span>

<span data-ttu-id="e4e2e-263">Vzhledem k tomu, <xref:System.Delegate?displayProperty=fullName> a <xref:System.MulticastDelegate?displayProperty=fullName> nemají požadovaný podpis, nezaručují, že delegát předán v bude odpovídat podpisu nativní kód očekává.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-263">Since <xref:System.Delegate?displayProperty=fullName> and <xref:System.MulticastDelegate?displayProperty=fullName> don't have a required signature, they don't guarantee that the delegate passed in will match the signature the native code expects.</span></span> <span data-ttu-id="e4e2e-264">Navíc v rozhraní .NET Framework a .NET Core může `System.Delegate` zařazování struktury obsahující nebo `System.MulticastDelegate` z jeho nativní reprezentace do spravovaného objektu destabilizovat dobu runtime, pokud hodnota pole v nativní reprezentaci není ukazatelem funkce, který zabalí spravovaného delegáta.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-264">Additionally, in .NET Framework and .NET Core, marshaling a struct containing a `System.Delegate` or `System.MulticastDelegate` from its native representation to a managed object can destabilize the runtime if the value of the field in the native representation isn't a function pointer that wraps a managed delegate.</span></span> <span data-ttu-id="e4e2e-265">V rozhraní .NET 5 a novějších verzích není podporováno zařazování pole `System.Delegate` nebo `System.MulticastDelegate` z nativní reprezentace do spravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-265">In .NET 5 and later versions, marshaling a `System.Delegate` or `System.MulticastDelegate` field from a native representation to a managed object is not supported.</span></span> <span data-ttu-id="e4e2e-266">Místo nebo `System.Delegate` `System.MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-266">Use a specific delegate type instead of `System.Delegate` or `System.MulticastDelegate`.</span></span>

### <a name="fixed-buffers"></a><span data-ttu-id="e4e2e-267">Pevné vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="e4e2e-267">Fixed Buffers</span></span>

<span data-ttu-id="e4e2e-268">Pole jako `INT_PTR Reserved1[2]` musí být zařazeno `IntPtr` do `Reserved1a` `Reserved1b`dvou polí a .</span><span class="sxs-lookup"><span data-stu-id="e4e2e-268">An array like `INT_PTR Reserved1[2]` has to be marshaled to two `IntPtr` fields, `Reserved1a` and `Reserved1b`.</span></span> <span data-ttu-id="e4e2e-269">Když nativní pole je primitivní typ, `fixed` můžeme použít klíčové slovo napsat trochu čistěji.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-269">When the native array is a primitive type, we can use the `fixed` keyword to write it a little more cleanly.</span></span> <span data-ttu-id="e4e2e-270">Například `SYSTEM_PROCESS_INFORMATION` vypadá takto v nativní záhlaví:</span><span class="sxs-lookup"><span data-stu-id="e4e2e-270">For example, `SYSTEM_PROCESS_INFORMATION` looks like this in the native header:</span></span>

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

<span data-ttu-id="e4e2e-271">V C#, můžeme napsat takto:</span><span class="sxs-lookup"><span data-stu-id="e4e2e-271">In C#, we can write it like this:</span></span>

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

<span data-ttu-id="e4e2e-272">Nicméně, tam jsou některé gotchas s pevnými vyrovnávacími pamětí.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-272">However, there are some gotchas with fixed buffers.</span></span> <span data-ttu-id="e4e2e-273">Pevné vyrovnávací paměti nepřenositelných typů nebudou správně zařazeny, takže pole na místě musí být rozbaleno do více jednotlivých polí.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-273">Fixed buffers of non-blittable types won't be correctly marshaled, so the in-place array needs to be expanded out to multiple individual fields.</span></span> <span data-ttu-id="e4e2e-274">Navíc v rozhraní .NET Framework a .NET Core před 3.0, pokud je struktura obsahující pevné vyrovnávací pole vnořena do nepřenositelné struktury, nebude pevné vyrovnávací pole správně zařazeno do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="e4e2e-274">Additionally, in .NET Framework and .NET Core before 3.0, if a struct containing a fixed buffer field is nested within a non-blittable struct, the fixed buffer field won't be correctly marshaled to native code.</span></span>
