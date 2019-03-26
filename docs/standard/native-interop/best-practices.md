---
title: Nativní interoperabilita osvědčené postupy – .NET
description: Podívejte se na osvědčené postupy pro propojení s nativními komponentami v rozhraní .NET.
author: jkoritzinsky
ms.author: jekoritz
ms.date: 01/18/2019
ms.openlocfilehash: 5b65f80d3a81fab0d74ce26aec3b454c716a5d51
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58412055"
---
# <a name="native-interoperability-best-practices"></a><span data-ttu-id="b1ce8-103">Osvědčené postupy nativní interoperabilita</span><span class="sxs-lookup"><span data-stu-id="b1ce8-103">Native interoperability best practices</span></span>

<span data-ttu-id="b1ce8-104">.NET nabízí celou řadu způsobů, jak přizpůsobit interoperabilitu nativní kód.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-104">.NET gives you a variety of ways to customize your native interoperability code.</span></span> <span data-ttu-id="b1ce8-105">Tento článek obsahuje pokyny, které následují .NET týmy Microsoftu pro interoperabilitu nativní.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-105">This article includes the guidance that Microsoft's .NET teams follow for native interoperability.</span></span>

## <a name="general-guidance"></a><span data-ttu-id="b1ce8-106">Obecné pokyny</span><span class="sxs-lookup"><span data-stu-id="b1ce8-106">General guidance</span></span>

<span data-ttu-id="b1ce8-107">Pokyny v této části platí pro všechny scénáře spolupráce.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-107">The guidance in this section applies to all interop scenarios.</span></span>

- <span data-ttu-id="b1ce8-108">**PROVEĎTE ✔️** používat stejné pojmenování a malá a velká písmena jako nativní metody, kterou chcete volat pro metody a parametrů.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-108">**✔️ DO** use the same naming and capitalization for your methods and parameters as the native method you want to call.</span></span>
- <span data-ttu-id="b1ce8-109">**✔️ ZVAŽTE** pomocí stejného pojmenování a velkých písmen pro konstantní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-109">**✔️ CONSIDER** using the same naming and capitalization for constant values.</span></span>
- <span data-ttu-id="b1ce8-110">**PROVEĎTE ✔️** typy .NET, které se nachází nejblíže mapují na nativní typ použít.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-110">**✔️ DO** use .NET types that map closest to the native type.</span></span> <span data-ttu-id="b1ce8-111">Například v C#, použijte `uint` Pokud je nativní typ `unsigned int`.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-111">For example, in C#, use `uint` when the native type is `unsigned int`.</span></span>
- <span data-ttu-id="b1ce8-112">**PROVEĎTE ✔️** používat pouze `[In]` a `[Out]` atributy, pokud chcete, aby chování se liší od výchozí chování.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-112">**✔️ DO** only use `[In]` and `[Out]` attributes when the behavior you want differs from the default behavior.</span></span>
- <span data-ttu-id="b1ce8-113">**✔️ ZVAŽTE** pomocí <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> pro fond vyrovnávací paměti vaší nativní pole.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-113">**✔️ CONSIDER** using <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> to pool your native array buffers.</span></span>
- <span data-ttu-id="b1ce8-114">**✔️ ZVAŽTE** ve třídě se stejným názvem a velká písmena jako nativní knihovnu pro zabalení vaší deklarace P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-114">**✔️ CONSIDER** wrapping your P/Invoke declarations in a class with the same name and capitalization as your native library.</span></span>
  - <span data-ttu-id="b1ce8-115">To umožňuje vaší `[DllImport]` atributů, které mají používat C# `nameof` funkci jazyka předat název nativní knihovnu a ujistěte se, že název nativní knihovny nebyla mít překlep.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-115">This allows your `[DllImport]` attributes to use the C# `nameof` language feature to pass in the name of the native library and ensure that you didn't misspell the name of the native library.</span></span>

## <a name="dllimport-attribute-settings"></a><span data-ttu-id="b1ce8-116">Nastavení atributu DllImport</span><span class="sxs-lookup"><span data-stu-id="b1ce8-116">DllImport attribute settings</span></span>

| <span data-ttu-id="b1ce8-117">Nastavení</span><span class="sxs-lookup"><span data-stu-id="b1ce8-117">Setting</span></span> | <span data-ttu-id="b1ce8-118">Výchozí</span><span class="sxs-lookup"><span data-stu-id="b1ce8-118">Default</span></span> | <span data-ttu-id="b1ce8-119">Doporučení</span><span class="sxs-lookup"><span data-stu-id="b1ce8-119">Recommendation</span></span> | <span data-ttu-id="b1ce8-120">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="b1ce8-120">Details</span></span> |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  <span data-ttu-id="b1ce8-121">Ponechat výchozí</span><span class="sxs-lookup"><span data-stu-id="b1ce8-121">keep default</span></span>  | <span data-ttu-id="b1ce8-122">Pokud to explicitně nastavená na false, neúspěšných vrácené hodnoty HRESULT bude převeden na výjimky (a vrácená hodnota v definici změní na hodnotu null v důsledku).</span><span class="sxs-lookup"><span data-stu-id="b1ce8-122">When this is explicitly set to false, failed HRESULT return values will be turned into exceptions (and the return value in the definition becomes null as a result).</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | <span data-ttu-id="b1ce8-123">závisí na rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b1ce8-123">depends on the API</span></span>  | <span data-ttu-id="b1ce8-124">Nastavte tuto hodnotu na hodnotu true, pokud používá funkce GetLastError rozhraní API a použít Marshal.GetLastWin32Error má být získána hodnota.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-124">Set this to true if the API uses GetLastError and use Marshal.GetLastWin32Error to get the value.</span></span> <span data-ttu-id="b1ce8-125">Pokud rozhraní API nastavte podmínku, která říká, že došlo k chybě, zobrazí chybová zpráva před provedením další volání vyhnout neúmyslně jej přepsat.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-125">If the API sets a condition that says it has an error, get the error before making other calls to avoid inadvertently having it overwritten.</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | <span data-ttu-id="b1ce8-126">`CharSet.None`, který spadne zpět na `CharSet.Ansi` chování</span><span class="sxs-lookup"><span data-stu-id="b1ce8-126">`CharSet.None`, which falls back to `CharSet.Ansi` behavior</span></span>  | <span data-ttu-id="b1ce8-127">Explicitně `CharSet.Unicode` nebo `CharSet.Ansi` když řetězce nebo znaků, jsou k dispozici v definici</span><span class="sxs-lookup"><span data-stu-id="b1ce8-127">Explicitly  use `CharSet.Unicode` or `CharSet.Ansi` when strings or characters are present in the definition</span></span> | <span data-ttu-id="b1ce8-128">Určuje chování sběrného systému řetězců a co `ExactSpelling` když `false`.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-128">This specifies marshalling behavior of strings and what `ExactSpelling` does when `false`.</span></span> <span data-ttu-id="b1ce8-129">Všimněte si, že `CharSet.Ansi` je ve skutečnosti UTF8 v systému Unix.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-129">Note that `CharSet.Ansi` is actually UTF8 on Unix.</span></span> <span data-ttu-id="b1ce8-130">_Většina_ času Windows používá kódování Unicode, zatímco Unix používá UTF8.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-130">_Most_ of the time Windows uses Unicode while Unix uses UTF8.</span></span> <span data-ttu-id="b1ce8-131">Další informace o naleznete [dokumentaci o znakových sad](./charset.md).</span><span class="sxs-lookup"><span data-stu-id="b1ce8-131">See more information on the [documentation on charsets](./charset.md).</span></span> |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | <span data-ttu-id="b1ce8-132">Nastavte tuto hodnotu na true a získat výhody mírné výkonu jako modul runtime nebude hledat názvy alternativní funkcí s příponou buď "A" nebo "W" v závislosti na hodnotu `CharSet` nastavení ("A" pro `CharSet.Ansi` a "W" pro `CharSet.Unicode`).</span><span class="sxs-lookup"><span data-stu-id="b1ce8-132">Set this to true and gain a slight perf benefit as the runtime will not look for alternate function names with either an "A" or "W" suffix depending on the value of the `CharSet` setting ("A" for `CharSet.Ansi` and "W" for `CharSet.Unicode`).</span></span> |

## <a name="string-parameters"></a><span data-ttu-id="b1ce8-133">Parametry řetězce</span><span class="sxs-lookup"><span data-stu-id="b1ce8-133">String parameters</span></span>

<span data-ttu-id="b1ce8-134">Když je znakové sady Unicode nebo argument je explicitně označena jako `[MarshalAs(UnmanagedType.LPWSTR)]` _a_ řetězec je předán podle hodnoty (ne `ref` nebo `out`), řetězec připnuté, který se používá nativní kód (spíše než zkopíruje).</span><span class="sxs-lookup"><span data-stu-id="b1ce8-134">When the CharSet is Unicode or the argument is explicitly marked as `[MarshalAs(UnmanagedType.LPWSTR)]` _and_ the string is passed by value (not `ref` or `out`), the string will be pinned and used directly by native code (rather than copied).</span></span>

<span data-ttu-id="b1ce8-135">Mějte na paměti k označení `[DllImport]` jako `Charset.Unicode` Pokud chcete explicitně ANSI zacházení s řetězci.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-135">Remember to mark the `[DllImport]` as `Charset.Unicode` unless you explicitly want ANSI treatment of your strings.</span></span>

<span data-ttu-id="b1ce8-136">**❌ NEPODPORUJÍ** použít `[Out] string` parametry.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-136">**❌ DO NOT** use `[Out] string` parameters.</span></span> <span data-ttu-id="b1ce8-137">Řetězec, předán podle hodnoty s parametry `[Out]` atribut můžou destabilizovat modul runtime, pokud řetězec je interned řetězec.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-137">String parameters passed by value with the `[Out]` attribute can destabilize the runtime if the string is an interned string.</span></span> <span data-ttu-id="b1ce8-138">Další informace o interning řetězce v dokumentaci k <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-138">See more information about string interning in the documentation for <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="b1ce8-139">**❌ Nepoužívejte** `StringBuilder` parametry.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-139">**❌ AVOID** `StringBuilder` parameters.</span></span> <span data-ttu-id="b1ce8-140">`StringBuilder` zařazování *vždy* vytvoří kopii nativní vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-140">`StringBuilder` marshalling *always* creates a native buffer copy.</span></span> <span data-ttu-id="b1ce8-141">V důsledku toho může být velmi neefektivní.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-141">As such, it can be extremely inefficient.</span></span> <span data-ttu-id="b1ce8-142">Využijte Typický scénář volání Windows API, která přebírá řetězec:</span><span class="sxs-lookup"><span data-stu-id="b1ce8-142">Take the typical scenario of calling a Windows API that takes a string:</span></span>

1. <span data-ttu-id="b1ce8-143">Vytvoření SB požadovanou kapacitu (přidělí kapacita managed) **{1}**</span><span class="sxs-lookup"><span data-stu-id="b1ce8-143">Create a SB of the desired capacity (allocates managed capacity) **{1}**</span></span>
2. <span data-ttu-id="b1ce8-144">Vyvolat</span><span class="sxs-lookup"><span data-stu-id="b1ce8-144">Invoke</span></span>
   1. <span data-ttu-id="b1ce8-145">Přidělí nativní vyrovnávací paměť **{2}**</span><span class="sxs-lookup"><span data-stu-id="b1ce8-145">Allocates a native buffer **{2}**</span></span>  
   2. <span data-ttu-id="b1ce8-146">Zkopíruje obsah, když `[In]` _(výchozí nastavení pro `StringBuilder` parametr)_</span><span class="sxs-lookup"><span data-stu-id="b1ce8-146">Copies the contents if `[In]` _(the default for a `StringBuilder` parameter)_</span></span>  
   3. <span data-ttu-id="b1ce8-147">Zkopíruje nativní vyrovnávací paměť do nově přiděleného spravovaného pole, když `[Out]` **{3}** _(také výchozí `StringBuilder`)_</span><span class="sxs-lookup"><span data-stu-id="b1ce8-147">Copies the native buffer into a newly allocated managed array if `[Out]` **{3}** _(also the default for `StringBuilder`)_</span></span>  
3. <span data-ttu-id="b1ce8-148">`ToString()` přiděluje další spravovaného pole **{4}**</span><span class="sxs-lookup"><span data-stu-id="b1ce8-148">`ToString()` allocates yet another managed array **{4}**</span></span>

<span data-ttu-id="b1ce8-149">To znamená *{4}* přidělení získat řetězec z nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-149">That is *{4}* allocations to get a string out of native code.</span></span> <span data-ttu-id="b1ce8-150">Nejlepší způsobů, jak toto omezení je znovu použít `StringBuilder` v jiného volání, ale tím se ušetří stále pouze *1* přidělení.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-150">The best you can do to limit this is to reuse the `StringBuilder` in another call but this still only saves *1* allocation.</span></span> <span data-ttu-id="b1ce8-151">Je mnohem lepší použít a ukládat do vyrovnávací paměti pro znaky z mezipaměti `ArrayPool`-pak můžete získat k přidělení pro `ToString()` při dalších volání.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-151">It's much better to use and cache a character buffer from `ArrayPool`- you can then get down to just the allocation for the `ToString()` on subsequent calls.</span></span>

<span data-ttu-id="b1ce8-152">Problém s `StringBuilder` je, že vždy kopíruje návratové vyrovnávací paměti zálohování do první hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-152">The other issue with `StringBuilder` is that it always copies the return buffer back up to the first null.</span></span> <span data-ttu-id="b1ce8-153">Pokud back předaný řetězec není ukončený nebo je dvojitou hodnotu null ukončující řetězec, je deklarace P/Invoke nesprávný nejlépe.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-153">If the passed back string isn't terminated or is a double-null-terminated string, your P/Invoke is incorrect at best.</span></span>

<span data-ttu-id="b1ce8-154">Pokud jste *proveďte* použít `StringBuilder`, jeden poslední gotcha je, že se kapacita **není** zahrnout skryté null, který je vždy zahrnuté v zprostředkovatele komunikace s objekty.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-154">If you *do* use `StringBuilder`, one last gotcha is that the capacity does **not** include a hidden null, which is always accounted for in interop.</span></span> <span data-ttu-id="b1ce8-155">Je běžné, že lidé se to získat nesprávná, protože většina rozhraní API má velikost vyrovnávací paměti *včetně* hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-155">It's common for people to get this wrong as most APIs want the size of the buffer *including* the null.</span></span> <span data-ttu-id="b1ce8-156">Výsledkem může být ztraceny, a zbytečné přidělení.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-156">This can result in wasted/unnecessary allocations.</span></span> <span data-ttu-id="b1ce8-157">Kromě toho tato gotcha zabraňuje modulu runtime optimalizace `StringBuilder` minimalizovat kopie sběrného systému.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-157">Additionally, this gotcha prevents the runtime from optimizing `StringBuilder` marshalling to minimize copies.</span></span>

<span data-ttu-id="b1ce8-158">**✔️ ZVAŽTE** pomocí `char[]`s ze `ArrayPool`.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-158">**✔️ CONSIDER** using `char[]`s from an `ArrayPool`.</span></span>

<span data-ttu-id="b1ce8-159">Další informace o zařazování pro řetězce, naleznete v tématu [výchozí zařazování pro řetězce](../../framework/interop/default-marshaling-for-strings.md) a [přizpůsobení zařazování pro řetězce](customize-parameter-marshalling.md#customizing-string-parameters).</span><span class="sxs-lookup"><span data-stu-id="b1ce8-159">For more information on string marshalling, see [Default Marshalling for Strings](../../framework/interop/default-marshaling-for-strings.md) and [Customizing string marshalling](customize-parameter-marshalling.md#customizing-string-parameters).</span></span>

> <span data-ttu-id="b1ce8-160">__Specifické pro Windows__</span><span class="sxs-lookup"><span data-stu-id="b1ce8-160">__Windows Specific__</span></span>  
> <span data-ttu-id="b1ce8-161">Pro `[Out]` řetězce CLR použije `CoTaskMemFree` ve výchozím nastavení uvolnit řetězce nebo `SysStringFree` pro řetězce, které jsou označeny jako `UnmanagedType.BSTR`.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-161">For `[Out]` strings the CLR will use `CoTaskMemFree` by default to free strings or `SysStringFree` for strings that are marked as `UnmanagedType.BSTR`.</span></span>  
<span data-ttu-id="b1ce8-162">**Většina rozhraní API s řetězci výstupní vyrovnávací paměť:**</span><span class="sxs-lookup"><span data-stu-id="b1ce8-162">**For most APIs with an output string buffer:**</span></span>  
> <span data-ttu-id="b1ce8-163">Předaný v znaku musí obsahovat počet hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-163">The passed in character count must include the null.</span></span> <span data-ttu-id="b1ce8-164">Pokud vrácená hodnota je menší než předaný počet znaků v úspěšném volání a hodnota je počet znaků *bez* koncovou hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-164">If the returned value is less than the passed in character count the call has succeeded and the value is the number of characters *without* the trailing null.</span></span> <span data-ttu-id="b1ce8-165">Jinak je požadovaná velikost vyrovnávací paměti počet *včetně* znak null.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-165">Otherwise the count is the required size of the buffer *including* the null character.</span></span>  
> - <span data-ttu-id="b1ce8-166">Předejte 5, 4 získat: Řetězec je 4 znaky dlouhý s koncovou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-166">Pass in 5, get 4: The string is 4 characters long with a trailing null.</span></span>
> - <span data-ttu-id="b1ce8-167">Předejte 5, 6 získat: Řetězec je 5 znaků, třeba 6 znaků vyrovnávací paměť pro uchování hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-167">Pass in 5, get 6: The string is 5 characters long, need a 6 character buffer to hold the null.</span></span>  
> [<span data-ttu-id="b1ce8-168">Datové typy Windows pro řetězce</span><span class="sxs-lookup"><span data-stu-id="b1ce8-168">Windows Data Types for Strings</span></span>](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a><span data-ttu-id="b1ce8-169">Logické parametry a pole</span><span class="sxs-lookup"><span data-stu-id="b1ce8-169">Boolean parameters and fields</span></span>

<span data-ttu-id="b1ce8-170">Logické hodnoty jsou snadno schválně pokazí.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-170">Booleans are easy to mess up.</span></span> <span data-ttu-id="b1ce8-171">Ve výchozím nastavení, .NET `bool` je zařazeno do Windows `BOOL`, kde je to hodnota 4 bajty.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-171">By default, a .NET `bool` is marshalled to a Windows `BOOL`, where it's a 4-byte value.</span></span> <span data-ttu-id="b1ce8-172">Ale `_Bool`, a `bool` jsou typy v jazyce C a C++ *jeden* bajtů.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-172">However, the `_Bool`, and `bool` types in C and C++ are a *single* byte.</span></span> <span data-ttu-id="b1ce8-173">To může vést k náročné sledovat chyby jako poloviční návratová hodnota se zahodí, který bude pouze *potenciálně* změnit výsledek.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-173">This can lead to hard to track down bugs as half the return value will be discarded, which will only *potentially* change the result.</span></span> <span data-ttu-id="b1ce8-174">Další informace o zařazování .NET `bool` hodnoty do jazyka C nebo C++ `bool` typy, naleznete v dokumentaci [přizpůsobení zařazování pro pole logickou](customize-struct-marshalling.md#customizing-boolean-field-marshalling).</span><span class="sxs-lookup"><span data-stu-id="b1ce8-174">For more for information on marshalling .NET `bool` values to C or C++ `bool` types, see the documentation on [customizing boolean field marshalling](customize-struct-marshalling.md#customizing-boolean-field-marshalling).</span></span>

## <a name="guids"></a><span data-ttu-id="b1ce8-175">Identifikátory GUID</span><span class="sxs-lookup"><span data-stu-id="b1ce8-175">GUIDs</span></span>

<span data-ttu-id="b1ce8-176">Lze použít přímo v signaturách identifikátory GUID.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-176">GUIDs are usable directly in signatures.</span></span> <span data-ttu-id="b1ce8-177">Mnoho rozhraní Windows API využít `GUID&` zadejte aliasy jako `REFIID`.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-177">Many Windows APIs take `GUID&` type aliases like `REFIID`.</span></span> <span data-ttu-id="b1ce8-178">Když předány podle odkazu, je můžete předat buď `ref` nebo se `[MarshalAs(UnmanagedType.LPStruct)]` atribut.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-178">When passed by ref, they can either be passed by `ref` or with the `[MarshalAs(UnmanagedType.LPStruct)]` attribute.</span></span>

| <span data-ttu-id="b1ce8-179">GUID</span><span class="sxs-lookup"><span data-stu-id="b1ce8-179">GUID</span></span> | <span data-ttu-id="b1ce8-180">Identifikátor GUID podle odkazu</span><span class="sxs-lookup"><span data-stu-id="b1ce8-180">By-ref GUID</span></span> |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

<span data-ttu-id="b1ce8-181">**❌ NEPODPORUJÍ** použití `[MarshalAs(UnmanagedType.LPStruct)]` pro nic jiného než `ref` parametry identifikátor GUID.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-181">**❌ DO NOT** Use `[MarshalAs(UnmanagedType.LPStruct)]` for anything other than `ref` GUID parameters.</span></span>

## <a name="blittable-types"></a><span data-ttu-id="b1ce8-182">Přenositelné typy</span><span class="sxs-lookup"><span data-stu-id="b1ce8-182">Blittable types</span></span>

<span data-ttu-id="b1ce8-183">Přenositelné typy jsou typy, které mají stejnou reprezentaci úrovni bitů v spravovaného a nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-183">Blittable types are types that have the same bit-level representation in managed and native code.</span></span> <span data-ttu-id="b1ce8-184">Proto není nutné pro převod na jiném formátu tak být zařazeno do a z nativního kódu a jak to zvyšuje výkon se bude upřednostňovat.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-184">As such they do not need to be converted to another format to be marshalled to and from native code, and as this improves performance they should be preferred.</span></span>

<span data-ttu-id="b1ce8-185">**Přenositelné typy:**</span><span class="sxs-lookup"><span data-stu-id="b1ce8-185">**Blittable types:**</span></span>

- <span data-ttu-id="b1ce8-186">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span><span class="sxs-lookup"><span data-stu-id="b1ce8-186">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span></span>
- <span data-ttu-id="b1ce8-187">-nested jednorozměrné pole přenositelné typy (například `int[]`)</span><span class="sxs-lookup"><span data-stu-id="b1ce8-187">non-nested one-dimensional arrays of blittable types (for example, `int[]`)</span></span>
- <span data-ttu-id="b1ce8-188">struktury a třídy s pevným rozložením, které mít pouze hodnotu přenositelné typy pro instanci pole</span><span class="sxs-lookup"><span data-stu-id="b1ce8-188">structs and classes with fixed layout that only have blittable value types for instance fields</span></span>
  - <span data-ttu-id="b1ce8-189">pevné rozložení vyžaduje `[StructLayout(LayoutKind.Sequential)]` nebo `[StructLayout(LayoutKind.Explicit)]`</span><span class="sxs-lookup"><span data-stu-id="b1ce8-189">fixed layout requires `[StructLayout(LayoutKind.Sequential)]` or `[StructLayout(LayoutKind.Explicit)]`</span></span>
  - <span data-ttu-id="b1ce8-190">struktury jsou `LayoutKind.Sequential` jsou standardně třídy `LayoutKind.Auto`</span><span class="sxs-lookup"><span data-stu-id="b1ce8-190">structs are `LayoutKind.Sequential` by default, classes are `LayoutKind.Auto`</span></span>

<span data-ttu-id="b1ce8-191">**NENÍ typu blittable:**</span><span class="sxs-lookup"><span data-stu-id="b1ce8-191">**NOT blittable:**</span></span>

- `bool`

<span data-ttu-id="b1ce8-192">**NĚKDY blittable:**</span><span class="sxs-lookup"><span data-stu-id="b1ce8-192">**SOMETIMES blittable:**</span></span>

- <span data-ttu-id="b1ce8-193">`char`, `string`</span><span class="sxs-lookup"><span data-stu-id="b1ce8-193">`char`, `string`</span></span>

<span data-ttu-id="b1ce8-194">Když přenositelné typy jsou předány podle odkazu, se jednoduše připnout podle marshaller namísto kopírování do zprostředkující vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-194">When blittable types are passed by reference, they're simply pinned by the marshaller instead of being copied to an intermediate buffer.</span></span> <span data-ttu-id="b1ce8-195">(Třídy jsou ze své podstaty předány podle odkazu, struktur jsou předány podle odkazu při použití s `ref` nebo `out`.)</span><span class="sxs-lookup"><span data-stu-id="b1ce8-195">(Classes are inherently passed by reference, structs are passed by reference when used with `ref` or `out`.)</span></span>

<span data-ttu-id="b1ce8-196">`char` přenositelné v jednorozměrné pole je **nebo** Pokud se jedná o typ, který ji obsahuje je explicitně označena `[StructLayout]` s `CharSet = CharSet.Unicode`.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-196">`char` is blittable in a one-dimensional array **or** if it's part of a type that contains it's explicitly marked with `[StructLayout]` with `CharSet = CharSet.Unicode`.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

<span data-ttu-id="b1ce8-197">`string` je typu blittable, pokud není obsažen v jiném typu a je předávána jako argument, který je označen `[MarshalAs(UnmanagedType.LPWStr)]` nebo `[DllImport]` má `CharSet = CharSet.Unicode` nastavit.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-197">`string` is blittable if it isn't contained in another type and it's being passed as an argument that is marked with `[MarshalAs(UnmanagedType.LPWStr)]` or the `[DllImport]` has `CharSet = CharSet.Unicode` set.</span></span>

<span data-ttu-id="b1ce8-198">Můžete zobrazit, pokud je typu blittable pokusem o vytvoření připnutého `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-198">You can see if a type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="b1ce8-199">Pokud typ není řetězec nebo považovat za blittable, `GCHandle.Alloc` vyvolá výjimku `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-199">If the type isn't a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="b1ce8-200">**PROVEĎTE ✔️** Ujistěte se, vaši blittable struktury, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-200">**✔️ DO** make your structures blittable when possible.</span></span>

<span data-ttu-id="b1ce8-201">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="b1ce8-201">For more information, see:</span></span>

- [<span data-ttu-id="b1ce8-202">Přenositelné a nepřenositelné typy</span><span class="sxs-lookup"><span data-stu-id="b1ce8-202">Blittable and Non-Blittable Types</span></span>](../../framework/interop/blittable-and-non-blittable-types.md)  
- [<span data-ttu-id="b1ce8-203">Zařazování typů</span><span class="sxs-lookup"><span data-stu-id="b1ce8-203">Type Marshalling</span></span>](type-marshalling.md)

## <a name="keeping-managed-objects-alive"></a><span data-ttu-id="b1ce8-204">Ponechání spravovaných objektů, které jsou aktivní</span><span class="sxs-lookup"><span data-stu-id="b1ce8-204">Keeping managed objects alive</span></span>

<span data-ttu-id="b1ce8-205">`GC.KeepAlive()` zajistí, že objekt zůstane v oboru až do dosažení metodu KeepAlive.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-205">`GC.KeepAlive()` will ensure an object stays in scope until the KeepAlive method is hit.</span></span>

<span data-ttu-id="b1ce8-206">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) Umožňuje marshaller k zachování objektu po dobu trvání P/Invoke.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-206">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) allows the marshaller to keep an object alive for the duration of a P/Invoke.</span></span> <span data-ttu-id="b1ce8-207">Je možné místo `IntPtr` v podpisy metod.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-207">It can be used instead of `IntPtr` in method signatures.</span></span> <span data-ttu-id="b1ce8-208">`SafeHandle` efektivně nahrazuje této třídy a místo toho by měla sloužit.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-208">`SafeHandle` effectively replaces this class and should be used instead.</span></span>

<span data-ttu-id="b1ce8-209">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) Umožňuje Připnutí spravovaný objekt a získávání nativní ukazatel na ni.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-209">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) allows pinning a managed object and getting the native pointer to it.</span></span> <span data-ttu-id="b1ce8-210">Základní model je:</span><span class="sxs-lookup"><span data-stu-id="b1ce8-210">The basic pattern is:</span></span>  

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

<span data-ttu-id="b1ce8-211">Připnutí není výchozí nastavení pro `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-211">Pinning isn't the default for `GCHandle`.</span></span> <span data-ttu-id="b1ce8-212">Další hlavní vzor je odkaz na spravovaný objekt prostřednictvím nativního kódu a zpět do spravovaného kódu, obvykle pomocí zpětného volání při předávání.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-212">The other major pattern is for passing a reference to a managed object through native code and back to managed code, usually with a callback.</span></span> <span data-ttu-id="b1ce8-213">Toto je vzor:</span><span class="sxs-lookup"><span data-stu-id="b1ce8-213">Here is the pattern:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

<span data-ttu-id="b1ce8-214">Nezapomeňte, že `GCHandle` musí být explicitně uvolněna, aby nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-214">Don't forget that `GCHandle` needs to be explicitly freed to avoid memory leaks.</span></span>

## <a name="common-windows-data-types"></a><span data-ttu-id="b1ce8-215">Běžné typy dat Windows</span><span class="sxs-lookup"><span data-stu-id="b1ce8-215">Common Windows data types</span></span>

<span data-ttu-id="b1ce8-216">Tady je seznam datových typů používaných v rozhraní Windows API a které C# typů pro použití při volání do kódu Windows.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-216">Here is a list of data types commonly used in Windows APIs and which C# types to use when calling into the Windows code.</span></span>

<span data-ttu-id="b1ce8-217">Následující typy mají stejnou velikost na 32bitová verze a 64bitová verze Windows, bez ohledu na jejich názvy.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-217">The following types are the same size on 32-bit and 64-bit Windows, despite their names.</span></span>

| <span data-ttu-id="b1ce8-218">Šířka</span><span class="sxs-lookup"><span data-stu-id="b1ce8-218">Width</span></span> | <span data-ttu-id="b1ce8-219">Windows</span><span class="sxs-lookup"><span data-stu-id="b1ce8-219">Windows</span></span>          | <span data-ttu-id="b1ce8-220">C (Windows)</span><span class="sxs-lookup"><span data-stu-id="b1ce8-220">C (Windows)</span></span>          | <span data-ttu-id="b1ce8-221">C#</span><span class="sxs-lookup"><span data-stu-id="b1ce8-221">C#</span></span>       | <span data-ttu-id="b1ce8-222">Alternativní</span><span class="sxs-lookup"><span data-stu-id="b1ce8-222">Alternative</span></span>                          |
|:------|:-----------------|:---------------------|:---------|:-------------------------------------|
| <span data-ttu-id="b1ce8-223">32</span><span class="sxs-lookup"><span data-stu-id="b1ce8-223">32</span></span>    | `BOOL`           | `int`                | `int`    | `bool`                               |
| <span data-ttu-id="b1ce8-224">8</span><span class="sxs-lookup"><span data-stu-id="b1ce8-224">8</span></span>     | `BOOLEAN`        | `unsigned char`      | `byte`   | `[MarshalAs(UnmanagedType.U1)] bool` |
| <span data-ttu-id="b1ce8-225">8</span><span class="sxs-lookup"><span data-stu-id="b1ce8-225">8</span></span>     | `BYTE`           | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="b1ce8-226">8</span><span class="sxs-lookup"><span data-stu-id="b1ce8-226">8</span></span>     | `CHAR`           | `char`               | `sbyte`  |                                      |
| <span data-ttu-id="b1ce8-227">8</span><span class="sxs-lookup"><span data-stu-id="b1ce8-227">8</span></span>     | `UCHAR`          | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="b1ce8-228">16</span><span class="sxs-lookup"><span data-stu-id="b1ce8-228">16</span></span>    | `SHORT`          | `short`              | `short`  |                                      |
| <span data-ttu-id="b1ce8-229">16</span><span class="sxs-lookup"><span data-stu-id="b1ce8-229">16</span></span>    | `CSHORT`         | `short`              | `short`  |                                      |
| <span data-ttu-id="b1ce8-230">16</span><span class="sxs-lookup"><span data-stu-id="b1ce8-230">16</span></span>    | `USHORT`         | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="b1ce8-231">16</span><span class="sxs-lookup"><span data-stu-id="b1ce8-231">16</span></span>    | `WORD`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="b1ce8-232">16</span><span class="sxs-lookup"><span data-stu-id="b1ce8-232">16</span></span>    | `ATOM`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="b1ce8-233">32</span><span class="sxs-lookup"><span data-stu-id="b1ce8-233">32</span></span>    | `INT`            | `int`                | `int`    |                                      |
| <span data-ttu-id="b1ce8-234">32</span><span class="sxs-lookup"><span data-stu-id="b1ce8-234">32</span></span>    | `LONG`           | `long`               | `int`    |                                      |
| <span data-ttu-id="b1ce8-235">32</span><span class="sxs-lookup"><span data-stu-id="b1ce8-235">32</span></span>    | `ULONG`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="b1ce8-236">32</span><span class="sxs-lookup"><span data-stu-id="b1ce8-236">32</span></span>    | `DWORD`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="b1ce8-237">64</span><span class="sxs-lookup"><span data-stu-id="b1ce8-237">64</span></span>    | `QWORD`          | `long long`          | `long`   |                                      |
| <span data-ttu-id="b1ce8-238">64</span><span class="sxs-lookup"><span data-stu-id="b1ce8-238">64</span></span>    | `LARGE_INTEGER`  | `long long`          | `long`   |                                      |
| <span data-ttu-id="b1ce8-239">64</span><span class="sxs-lookup"><span data-stu-id="b1ce8-239">64</span></span>    | `LONGLONG`       | `long long`          | `long`   |                                      |
| <span data-ttu-id="b1ce8-240">64</span><span class="sxs-lookup"><span data-stu-id="b1ce8-240">64</span></span>    | `ULONGLONG`      | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="b1ce8-241">64</span><span class="sxs-lookup"><span data-stu-id="b1ce8-241">64</span></span>    | `ULARGE_INTEGER` | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="b1ce8-242">32</span><span class="sxs-lookup"><span data-stu-id="b1ce8-242">32</span></span>    | `HRESULT`        | `long`               | `int`    |                                      |
| <span data-ttu-id="b1ce8-243">32</span><span class="sxs-lookup"><span data-stu-id="b1ce8-243">32</span></span>    | `NTSTATUS`       | `long`               | `int`    |                                      |


<span data-ttu-id="b1ce8-244">Následující typy ukazatelů, se podle šířku platformy.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-244">The following types, being pointers, do follow the width of the platform.</span></span> <span data-ttu-id="b1ce8-245">Použití `IntPtr` / `UIntPtr` pro tyto.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-245">Use `IntPtr`/`UIntPtr` for these.</span></span>

| <span data-ttu-id="b1ce8-246">Podepsané typy ukazatelů (použijte `IntPtr`)</span><span class="sxs-lookup"><span data-stu-id="b1ce8-246">Signed Pointer Types (use `IntPtr`)</span></span> | <span data-ttu-id="b1ce8-247">Typy ukazatelů, bez znaménka (použijte `UIntPtr`)</span><span class="sxs-lookup"><span data-stu-id="b1ce8-247">Unsigned Pointer Types (use `UIntPtr`)</span></span> |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

<span data-ttu-id="b1ce8-248">Windows `PVOID` tedy C `void*` můžete zařadit jako buď `IntPtr` nebo `UIntPtr`, ale dáváte přednost `void*` Pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-248">A Windows `PVOID` which is a C `void*` can be marshaled as either `IntPtr` or `UIntPtr`, but prefer `void*` when possible.</span></span>

[<span data-ttu-id="b1ce8-249">Datové typy Windows</span><span class="sxs-lookup"><span data-stu-id="b1ce8-249">Windows Data Types</span></span>](/windows/desktop/WinProg/windows-data-types)

[<span data-ttu-id="b1ce8-250">Rozsahy datových typů</span><span class="sxs-lookup"><span data-stu-id="b1ce8-250">Data Type Ranges</span></span>](/cpp/cpp/data-type-ranges)

## <a name="structs"></a><span data-ttu-id="b1ce8-251">Struktury</span><span class="sxs-lookup"><span data-stu-id="b1ce8-251">Structs</span></span>

<span data-ttu-id="b1ce8-252">Spravované struktury jsou vytvořeny v zásobníku a se neodeberou, dokud se metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-252">Managed structs are created on the stack and aren't removed until the method returns.</span></span> <span data-ttu-id="b1ce8-253">Podle definice a pak, že nejsou "připnuté" (nebudete získáte přesunout uvolňování paměti).</span><span class="sxs-lookup"><span data-stu-id="b1ce8-253">By definition then, they are "pinned" (it won't get moved by the GC).</span></span> <span data-ttu-id="b1ce8-254">Můžete také jednoduše provést adresu v nezabezpečený kód bloky Pokud nativního kódu nebude používat ukazatel ukazující za aktuální metody.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-254">You can also simply take the address in unsafe code blocks if native code won't use the pointer past the end of the current method.</span></span>

<span data-ttu-id="b1ce8-255">Přenositelné struktury jsou výrazně výkonnější jako může být jednoduše použít přímo ve vrstvě sběrného systému.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-255">Blittable structs are much more performant as they can simply be used directly by the marshalling layer.</span></span> <span data-ttu-id="b1ce8-256">Pokuste se uskutečnit blittable struktury (například vyhnout `bool`).</span><span class="sxs-lookup"><span data-stu-id="b1ce8-256">Try to make structs blittable (for example, avoid `bool`).</span></span> <span data-ttu-id="b1ce8-257">Další informace najdete v tématu [přenositelné typy](#blittable-types) oddílu.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-257">For more information, see the [Blittable Types](#blittable-types) section.</span></span>

<span data-ttu-id="b1ce8-258">*Pokud* struktury je typu blittable, použijte `sizeof()` místo `Marshal.SizeOf<MyStruct>()` pro zajištění lepšího výkonu.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-258">*If* the struct is blittable, use `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for better performance.</span></span> <span data-ttu-id="b1ce8-259">Jak je uvedeno výše, můžete ověřit, že je typu blittable pokusem o vytvoření připnutého `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-259">As mentioned above, you can validate that the type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="b1ce8-260">Pokud typ není řetězec nebo považovat za blittable, `GCHandle.Alloc` vyvolá výjimku `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-260">If the type is not a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="b1ce8-261">Odkazy na struktury v definicích se musí buď předávat `ref` nebo použijte `unsafe` a `*`.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-261">Pointers to structs in definitions must either be passed by `ref` or use `unsafe` and `*`.</span></span>

<span data-ttu-id="b1ce8-262">**PROVEĎTE ✔️** odpovídat spravovaná struktura co nejpřesněji tvar a názvy, které se používají v dokumentaci oficiální platforma nebo hlavičce.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-262">**✔️ DO** match the managed struct as closely as possible to the shape and names that are used in the official platform documentation or header.</span></span>

<span data-ttu-id="b1ce8-263">**PROVEĎTE ✔️** použít C# `sizeof()` místo `Marshal.SizeOf<MyStruct>()` pro struktury blittable ke zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-263">**✔️ DO** use the C# `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for blittable structures to improve performance.</span></span>

<span data-ttu-id="b1ce8-264">Pole, jako jsou `INT_PTR Reserved1[2]` musí být zařazen do dvou `IntPtr` pole, `Reserved1a` a `Reserved1b`.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-264">An array like `INT_PTR Reserved1[2]` has to be marshaled to two `IntPtr` fields, `Reserved1a` and `Reserved1b`.</span></span> <span data-ttu-id="b1ce8-265">Pokud je nativní pole primitivní typ, můžeme použít `fixed` – klíčové slovo pro zápis o něco více čistě.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-265">When the native array is a primitive type, we can use the `fixed` keyword to write it a little more cleanly.</span></span> <span data-ttu-id="b1ce8-266">Například `SYSTEM_PROCESS_INFORMATION` vypadá přibližně takto v hlavičce nativní:</span><span class="sxs-lookup"><span data-stu-id="b1ce8-266">For example, `SYSTEM_PROCESS_INFORMATION` looks like this in the native header:</span></span>

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

<span data-ttu-id="b1ce8-267">V C#, nám můžete napsat takto:</span><span class="sxs-lookup"><span data-stu-id="b1ce8-267">In C#, we can write it like this:</span></span>

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

<span data-ttu-id="b1ce8-268">Existují však některé možná úskalí s pevných vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-268">However, there are some gotchas with fixed buffers.</span></span> <span data-ttu-id="b1ce8-269">Nepřenositelné typy pevných vyrovnávacích pamětí nesmí být zařazeno správně, tak místní pole vyžaduje rozbalen navýšení kapacity na několik jednotlivá pole.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-269">Fixed buffers of non-blittable types won't be correctly marshalled, so the in-place array needs to be expanded out to multiple individual fields.</span></span> <span data-ttu-id="b1ce8-270">Navíc v rozhraní .NET Framework a .NET Core před 3.0, pokud je vnořená struktura obsahující vyrovnávací paměť pevné pole v rámci nepřenositelné struktury pole vyrovnávací paměť pevné nesmí být zařazeno správně do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="b1ce8-270">Additionally, in .NET Framework and .NET Core before 3.0, if a struct containing a fixed buffer field is nested within a non-blittable struct, the fixed buffer field won't be correctly marshalled to native code.</span></span>
