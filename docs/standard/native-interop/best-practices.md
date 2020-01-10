---
title: Nativní osvědčené postupy interoperability – .NET
description: Seznamte se s osvědčenými postupy pro propojení s nativními komponentami v .NET.
ms.date: 01/18/2019
ms.openlocfilehash: 7fe0dd0545f8ba800174f8be18bb2f11f39463f9
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75706397"
---
# <a name="native-interoperability-best-practices"></a><span data-ttu-id="2e843-103">Nativní osvědčené postupy interoperability</span><span class="sxs-lookup"><span data-stu-id="2e843-103">Native interoperability best practices</span></span>

<span data-ttu-id="2e843-104">.NET nabízí různé způsoby přizpůsobení nativního kódu interoperability.</span><span class="sxs-lookup"><span data-stu-id="2e843-104">.NET gives you a variety of ways to customize your native interoperability code.</span></span> <span data-ttu-id="2e843-105">Tento článek obsahuje pokyny, které tým .NET Microsoftu sleduje pro zajištění nativní interoperability.</span><span class="sxs-lookup"><span data-stu-id="2e843-105">This article includes the guidance that Microsoft's .NET teams follow for native interoperability.</span></span>

## <a name="general-guidance"></a><span data-ttu-id="2e843-106">Obecné pokyny</span><span class="sxs-lookup"><span data-stu-id="2e843-106">General guidance</span></span>

<span data-ttu-id="2e843-107">Pokyny v této části se vztahují na všechny scénáře spolupráce.</span><span class="sxs-lookup"><span data-stu-id="2e843-107">The guidance in this section applies to all interop scenarios.</span></span>

- <span data-ttu-id="2e843-108">**✔️** použít stejné názvy a velká písmena pro vaše metody a parametry jako nativní metodu, kterou chcete volat.</span><span class="sxs-lookup"><span data-stu-id="2e843-108">**✔️ DO** use the same naming and capitalization for your methods and parameters as the native method you want to call.</span></span>
- <span data-ttu-id="2e843-109">**✔️ zvažte** použití stejných názvů a velkých a malých písmen pro konstantní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2e843-109">**✔️ CONSIDER** using the same naming and capitalization for constant values.</span></span>
- <span data-ttu-id="2e843-110">**✔️** použít typy .NET, které jsou mapovány nejblíže k nativnímu typu.</span><span class="sxs-lookup"><span data-stu-id="2e843-110">**✔️ DO** use .NET types that map closest to the native type.</span></span> <span data-ttu-id="2e843-111">Například v C#nástroji použijte `uint`, pokud je nativní typ `unsigned int`.</span><span class="sxs-lookup"><span data-stu-id="2e843-111">For example, in C#, use `uint` when the native type is `unsigned int`.</span></span>
- <span data-ttu-id="2e843-112">**✔️** použít pouze atributy `[In]` a `[Out]`, pokud se chování, které požadujete, se liší od výchozího chování.</span><span class="sxs-lookup"><span data-stu-id="2e843-112">**✔️ DO** only use `[In]` and `[Out]` attributes when the behavior you want differs from the default behavior.</span></span>
- <span data-ttu-id="2e843-113">**✔️ zvažte** použití <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> pro fond vašich nativních vyrovnávacích pamětí polí.</span><span class="sxs-lookup"><span data-stu-id="2e843-113">**✔️ CONSIDER** using <xref:System.Buffers.ArrayPool%601?displayProperty=nameWithType> to pool your native array buffers.</span></span>
- <span data-ttu-id="2e843-114">**✔️ zvažte** zabalení deklarací volání nespravovaného kódu ve třídě se stejným názvem a velkými písmeny jako vaše nativní knihovna.</span><span class="sxs-lookup"><span data-stu-id="2e843-114">**✔️ CONSIDER** wrapping your P/Invoke declarations in a class with the same name and capitalization as your native library.</span></span>
  - <span data-ttu-id="2e843-115">To umožňuje, aby atributy `[DllImport]` používaly C# funkci jazyka `nameof` k předání názvu nativní knihovny a zajistila, že jste nezadali název nativní knihovny.</span><span class="sxs-lookup"><span data-stu-id="2e843-115">This allows your `[DllImport]` attributes to use the C# `nameof` language feature to pass in the name of the native library and ensure that you didn't misspell the name of the native library.</span></span>

## <a name="dllimport-attribute-settings"></a><span data-ttu-id="2e843-116">Nastavení atributu DllImport</span><span class="sxs-lookup"><span data-stu-id="2e843-116">DllImport attribute settings</span></span>

| <span data-ttu-id="2e843-117">Nastavení</span><span class="sxs-lookup"><span data-stu-id="2e843-117">Setting</span></span> | <span data-ttu-id="2e843-118">Výchozí</span><span class="sxs-lookup"><span data-stu-id="2e843-118">Default</span></span> | <span data-ttu-id="2e843-119">Doporučení</span><span class="sxs-lookup"><span data-stu-id="2e843-119">Recommendation</span></span> | <span data-ttu-id="2e843-120">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="2e843-120">Details</span></span> |
|---------|---------|----------------|---------|
| <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>   | `true` |  <span data-ttu-id="2e843-121">zachovat výchozí</span><span class="sxs-lookup"><span data-stu-id="2e843-121">keep default</span></span>  | <span data-ttu-id="2e843-122">Pokud je toto nastavení explicitně nastaveno na hodnotu false, neúspěšné návratové hodnoty HRESULT budou převedeny na výjimky (a návratová hodnota v definici bude jako výsledek null).</span><span class="sxs-lookup"><span data-stu-id="2e843-122">When this is explicitly set to false, failed HRESULT return values will be turned into exceptions (and the return value in the definition becomes null as a result).</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError> | `false`  | <span data-ttu-id="2e843-123">závisí na rozhraní API</span><span class="sxs-lookup"><span data-stu-id="2e843-123">depends on the API</span></span>  | <span data-ttu-id="2e843-124">Tuto hodnotu nastavte na true, pokud rozhraní API používá GetLastError, a k získání hodnoty použijte Marshal. GetLastWin32Error.</span><span class="sxs-lookup"><span data-stu-id="2e843-124">Set this to true if the API uses GetLastError and use Marshal.GetLastWin32Error to get the value.</span></span> <span data-ttu-id="2e843-125">Pokud rozhraní API nastaví podmínku, která říká, že obsahuje chybu, před dalším voláním zajistěte chybu, aby se zabránilo nechtěnému přepsání.</span><span class="sxs-lookup"><span data-stu-id="2e843-125">If the API sets a condition that says it has an error, get the error before making other calls to avoid inadvertently having it overwritten.</span></span>|
| <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> | <span data-ttu-id="2e843-126">`CharSet.None`, což se vrátí k chování `CharSet.Ansi`</span><span class="sxs-lookup"><span data-stu-id="2e843-126">`CharSet.None`, which falls back to `CharSet.Ansi` behavior</span></span>  | <span data-ttu-id="2e843-127">Explicitně použít `CharSet.Unicode` nebo `CharSet.Ansi`, když jsou v definici přítomné řetězce nebo znaky</span><span class="sxs-lookup"><span data-stu-id="2e843-127">Explicitly  use `CharSet.Unicode` or `CharSet.Ansi` when strings or characters are present in the definition</span></span> | <span data-ttu-id="2e843-128">To určuje chování zařazování řetězců a to, co `ExactSpelling` provede `false`.</span><span class="sxs-lookup"><span data-stu-id="2e843-128">This specifies marshaling behavior of strings and what `ExactSpelling` does when `false`.</span></span> <span data-ttu-id="2e843-129">Všimněte si, že `CharSet.Ansi` je ve skutečnosti UTF8 v systému UNIX.</span><span class="sxs-lookup"><span data-stu-id="2e843-129">Note that `CharSet.Ansi` is actually UTF8 on Unix.</span></span> <span data-ttu-id="2e843-130">_Většina_ času v systému Windows používá kódování Unicode, zatímco systém UNIX používá UTF8.</span><span class="sxs-lookup"><span data-stu-id="2e843-130">_Most_ of the time Windows uses Unicode while Unix uses UTF8.</span></span> <span data-ttu-id="2e843-131">Další informace najdete v [dokumentaci k charset](./charset.md).</span><span class="sxs-lookup"><span data-stu-id="2e843-131">See more information on the [documentation on charsets](./charset.md).</span></span> |
| <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> | `false` | `true`             | <span data-ttu-id="2e843-132">Nastavte tuto hodnotu na true a získejte mírné zvýhodnění výkonu, protože modul runtime nebude hledat alternativní názvy funkcí s příponou "A" nebo "W" v závislosti na hodnotě nastavení `CharSet` ("A" pro `CharSet.Ansi` a "W" pro `CharSet.Unicode`).</span><span class="sxs-lookup"><span data-stu-id="2e843-132">Set this to true and gain a slight perf benefit as the runtime will not look for alternate function names with either an "A" or "W" suffix depending on the value of the `CharSet` setting ("A" for `CharSet.Ansi` and "W" for `CharSet.Unicode`).</span></span> |

## <a name="string-parameters"></a><span data-ttu-id="2e843-133">Řetězcové parametry</span><span class="sxs-lookup"><span data-stu-id="2e843-133">String parameters</span></span>

<span data-ttu-id="2e843-134">Pokud je znaková sada Unicode nebo je argument explicitně označen jako `[MarshalAs(UnmanagedType.LPWSTR)]` _a_ řetězec je předán podle hodnoty (ne `ref` nebo `out`), řetězec bude připnuté a použit přímo pomocí nativního kódu (místo kopírování).</span><span class="sxs-lookup"><span data-stu-id="2e843-134">When the CharSet is Unicode or the argument is explicitly marked as `[MarshalAs(UnmanagedType.LPWSTR)]` _and_ the string is passed by value (not `ref` or `out`), the string will be pinned and used directly by native code (rather than copied).</span></span>

<span data-ttu-id="2e843-135">Nezapomeňte označit `[DllImport]` jako `Charset.Unicode`, pokud nechcete, aby byly řetězce explicitně vhodné pro zpracování ANSI.</span><span class="sxs-lookup"><span data-stu-id="2e843-135">Remember to mark the `[DllImport]` as `Charset.Unicode` unless you explicitly want ANSI treatment of your strings.</span></span>

<span data-ttu-id="2e843-136">**❌** nepoužívat parametry `[Out] string`.</span><span class="sxs-lookup"><span data-stu-id="2e843-136">**❌ DO NOT** use `[Out] string` parameters.</span></span> <span data-ttu-id="2e843-137">Řetězcové parametry předávané hodnotou s atributem `[Out]` mohou destabilizovat modul runtime, pokud je řetězec interně řetězec.</span><span class="sxs-lookup"><span data-stu-id="2e843-137">String parameters passed by value with the `[Out]` attribute can destabilize the runtime if the string is an interned string.</span></span> <span data-ttu-id="2e843-138">Další informace o přehlašování řetězců najdete v dokumentaci k <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2e843-138">See more information about string interning in the documentation for <xref:System.String.Intern%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="2e843-139">**❌ se vyhnout** parametrům `StringBuilder`.</span><span class="sxs-lookup"><span data-stu-id="2e843-139">**❌ AVOID** `StringBuilder` parameters.</span></span> <span data-ttu-id="2e843-140">`StringBuilder` zařazování *vždy* vytvoří nativní kopii vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="2e843-140">`StringBuilder` marshaling *always* creates a native buffer copy.</span></span> <span data-ttu-id="2e843-141">V takovém případě může být mimořádně neefektivní.</span><span class="sxs-lookup"><span data-stu-id="2e843-141">As such, it can be extremely inefficient.</span></span> <span data-ttu-id="2e843-142">Vyjistěte si Typický scénář volání rozhraní API systému Windows, které přijímá řetězec:</span><span class="sxs-lookup"><span data-stu-id="2e843-142">Take the typical scenario of calling a Windows API that takes a string:</span></span>

1. <span data-ttu-id="2e843-143">Vytvořte SB požadované kapacity (přidělení spravované kapacity) **{1}**</span><span class="sxs-lookup"><span data-stu-id="2e843-143">Create a SB of the desired capacity (allocates managed capacity) **{1}**</span></span>
2. <span data-ttu-id="2e843-144">Vyvolání</span><span class="sxs-lookup"><span data-stu-id="2e843-144">Invoke</span></span>
   1. <span data-ttu-id="2e843-145">Přidělí nativní vyrovnávací paměť **{2}**</span><span class="sxs-lookup"><span data-stu-id="2e843-145">Allocates a native buffer **{2}**</span></span>  
   2. <span data-ttu-id="2e843-146">Zkopíruje obsah, pokud je `[In]` _(výchozí hodnota pro `StringBuilder` parametr)_ .</span><span class="sxs-lookup"><span data-stu-id="2e843-146">Copies the contents if `[In]` _(the default for a `StringBuilder` parameter)_</span></span>  
   3. <span data-ttu-id="2e843-147">Zkopíruje nativní vyrovnávací paměť do nově přiděleného spravovaného pole, pokud `[Out]` **{3}** _(také výchozí `StringBuilder`)_ .</span><span class="sxs-lookup"><span data-stu-id="2e843-147">Copies the native buffer into a newly allocated managed array if `[Out]` **{3}** _(also the default for `StringBuilder`)_</span></span>  
3. <span data-ttu-id="2e843-148">`ToString()` přiděluje ještě jiné spravované pole **{4}**</span><span class="sxs-lookup"><span data-stu-id="2e843-148">`ToString()` allocates yet another managed array **{4}**</span></span>

<span data-ttu-id="2e843-149">To je *{4}* přidělení pro získání řetězce z nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="2e843-149">That is *{4}* allocations to get a string out of native code.</span></span> <span data-ttu-id="2e843-150">To nejlepší můžete udělat tak, že tento `StringBuilder` znovu použijete při jiném volání, ale bude se dál ukládat jenom *1* přidělení.</span><span class="sxs-lookup"><span data-stu-id="2e843-150">The best you can do to limit this is to reuse the `StringBuilder` in another call but this still only saves *1* allocation.</span></span> <span data-ttu-id="2e843-151">Je mnohem lepší použít a ukládat do mezipaměti znaková vyrovnávací paměť z `ArrayPool`. pak se můžete dostat až do přidělení `ToString()` při dalších voláních.</span><span class="sxs-lookup"><span data-stu-id="2e843-151">It's much better to use and cache a character buffer from `ArrayPool`- you can then get down to just the allocation for the `ToString()` on subsequent calls.</span></span>

<span data-ttu-id="2e843-152">Dalším problémem s `StringBuilder` je, že se vždy zkopíruje návratovou vyrovnávací paměť zpět na první hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="2e843-152">The other issue with `StringBuilder` is that it always copies the return buffer back up to the first null.</span></span> <span data-ttu-id="2e843-153">Pokud předaný řetězec není ukončen nebo se jedná o řetězec zakončený hodnotou null, vaše volání nespravovaného volání není správné.</span><span class="sxs-lookup"><span data-stu-id="2e843-153">If the passed back string isn't terminated or is a double-null-terminated string, your P/Invoke is incorrect at best.</span></span>

<span data-ttu-id="2e843-154">Pokud *použijete* `StringBuilder`, jedna poslední gotcha je, že **kapacita neobsahuje skrytý** znak null, který je vždycky zavedený pro v interoperabilitě.</span><span class="sxs-lookup"><span data-stu-id="2e843-154">If you *do* use `StringBuilder`, one last gotcha is that the capacity does **not** include a hidden null, which is always accounted for in interop.</span></span> <span data-ttu-id="2e843-155">Je běžné, že lidé mají špatný přístup, protože většina rozhraní API má velikost vyrovnávací paměti, *včetně* hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="2e843-155">It's common for people to get this wrong as most APIs want the size of the buffer *including* the null.</span></span> <span data-ttu-id="2e843-156">To může vést k plýtvání/zbytečným přidělením.</span><span class="sxs-lookup"><span data-stu-id="2e843-156">This can result in wasted/unnecessary allocations.</span></span> <span data-ttu-id="2e843-157">Kromě toho tento gotcha brání modulu runtime v optimalizaci `StringBuilder` zařazování pro minimalizaci kopií.</span><span class="sxs-lookup"><span data-stu-id="2e843-157">Additionally, this gotcha prevents the runtime from optimizing `StringBuilder` marshaling to minimize copies.</span></span>

<span data-ttu-id="2e843-158">**✔️ zvažte** použití `char[]`s z `ArrayPool`.</span><span class="sxs-lookup"><span data-stu-id="2e843-158">**✔️ CONSIDER** using `char[]`s from an `ArrayPool`.</span></span>

<span data-ttu-id="2e843-159">Další informace o zařazování řetězců naleznete v tématu [Výchozí zařazování pro řetězce](../../framework/interop/default-marshaling-for-strings.md) a [přizpůsobení zařazování řetězců](customize-parameter-marshaling.md#customizing-string-parameters).</span><span class="sxs-lookup"><span data-stu-id="2e843-159">For more information on string marshaling, see [Default Marshaling for Strings](../../framework/interop/default-marshaling-for-strings.md) and [Customizing string marshaling](customize-parameter-marshaling.md#customizing-string-parameters).</span></span>

> <span data-ttu-id="2e843-160">__Specifické pro systém Windows__</span><span class="sxs-lookup"><span data-stu-id="2e843-160">__Windows Specific__</span></span>  
> <span data-ttu-id="2e843-161">U `[Out]` řetězců bude CLR standardně používat `CoTaskMemFree` k uvolnění řetězců nebo `SysStringFree` pro řetězce, které jsou označeny jako `UnmanagedType.BSTR`.</span><span class="sxs-lookup"><span data-stu-id="2e843-161">For `[Out]` strings the CLR will use `CoTaskMemFree` by default to free strings or `SysStringFree` for strings that are marked as `UnmanagedType.BSTR`.</span></span>  
<span data-ttu-id="2e843-162">**Pro většinu rozhraní API výstupní vyrovnávací paměť řetězců:**</span><span class="sxs-lookup"><span data-stu-id="2e843-162">**For most APIs with an output string buffer:**</span></span>  
> <span data-ttu-id="2e843-163">Počet předaných znaků musí obsahovat hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="2e843-163">The passed in character count must include the null.</span></span> <span data-ttu-id="2e843-164">Pokud je vrácená hodnota menší než předaný počet znaků, volání bylo úspěšné a hodnota je počet znaků *bez* koncové hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="2e843-164">If the returned value is less than the passed in character count the call has succeeded and the value is the number of characters *without* the trailing null.</span></span> <span data-ttu-id="2e843-165">V opačném případě je požadovaná velikost vyrovnávací paměti, *včetně* znaku null.</span><span class="sxs-lookup"><span data-stu-id="2e843-165">Otherwise the count is the required size of the buffer *including* the null character.</span></span>  
>
> - <span data-ttu-id="2e843-166">Průchod 5, Get 4: řetězec má 4 znaky dlouhé s koncovou hodnotou null.</span><span class="sxs-lookup"><span data-stu-id="2e843-166">Pass in 5, get 4: The string is 4 characters long with a trailing null.</span></span>
> - <span data-ttu-id="2e843-167">Průchod 5, Get 6: řetězec má délku 5 znaků, pro uložení hodnoty null je zapotřebí vyrovnávací paměť 6 znaků.</span><span class="sxs-lookup"><span data-stu-id="2e843-167">Pass in 5, get 6: The string is 5 characters long, need a 6 character buffer to hold the null.</span></span>  
> [<span data-ttu-id="2e843-168">Datové typy Windows pro řetězce</span><span class="sxs-lookup"><span data-stu-id="2e843-168">Windows Data Types for Strings</span></span>](/windows/desktop/Intl/windows-data-types-for-strings)

## <a name="boolean-parameters-and-fields"></a><span data-ttu-id="2e843-169">Logické parametry a pole</span><span class="sxs-lookup"><span data-stu-id="2e843-169">Boolean parameters and fields</span></span>

<span data-ttu-id="2e843-170">Logické hodnoty se dají snadno vytvořit.</span><span class="sxs-lookup"><span data-stu-id="2e843-170">Booleans are easy to mess up.</span></span> <span data-ttu-id="2e843-171">Ve výchozím nastavení je `bool` .NET zařazena do `BOOL`systému Windows, kde je hodnota 4 bajty.</span><span class="sxs-lookup"><span data-stu-id="2e843-171">By default, a .NET `bool` is marshaled to a Windows `BOOL`, where it's a 4-byte value.</span></span> <span data-ttu-id="2e843-172">Nicméně `_Bool`a `bool` typy v jazyce C a C++ jsou *jedním* bajtem.</span><span class="sxs-lookup"><span data-stu-id="2e843-172">However, the `_Bool`, and `bool` types in C and C++ are a *single* byte.</span></span> <span data-ttu-id="2e843-173">To může vést k tomu, že je možné sledovat chyby jako polovinu, návratová hodnota bude zahozena, což *může pouze změnit* výsledek.</span><span class="sxs-lookup"><span data-stu-id="2e843-173">This can lead to hard to track down bugs as half the return value will be discarded, which will only *potentially* change the result.</span></span> <span data-ttu-id="2e843-174">Další informace o zařazování hodnot `bool` .NET do typů C nebo C++ `bool` naleznete v dokumentaci k [přizpůsobení zařazování logických polí](customize-struct-marshaling.md#customizing-boolean-field-marshaling).</span><span class="sxs-lookup"><span data-stu-id="2e843-174">For more for information on marshaling .NET `bool` values to C or C++ `bool` types, see the documentation on [customizing boolean field marshaling](customize-struct-marshaling.md#customizing-boolean-field-marshaling).</span></span>

## <a name="guids"></a><span data-ttu-id="2e843-175">Identifikátory GUID</span><span class="sxs-lookup"><span data-stu-id="2e843-175">GUIDs</span></span>

<span data-ttu-id="2e843-176">Identifikátory GUID lze použít přímo v signaturách.</span><span class="sxs-lookup"><span data-stu-id="2e843-176">GUIDs are usable directly in signatures.</span></span> <span data-ttu-id="2e843-177">Mnoho rozhraní API systému Windows přijímá `GUID&` aliasy typu, jako je `REFIID`.</span><span class="sxs-lookup"><span data-stu-id="2e843-177">Many Windows APIs take `GUID&` type aliases like `REFIID`.</span></span> <span data-ttu-id="2e843-178">Při předání odkazem, mohou být buď předány `ref` nebo s atributem `[MarshalAs(UnmanagedType.LPStruct)]`.</span><span class="sxs-lookup"><span data-stu-id="2e843-178">When passed by ref, they can either be passed by `ref` or with the `[MarshalAs(UnmanagedType.LPStruct)]` attribute.</span></span>

| <span data-ttu-id="2e843-179">GUID</span><span class="sxs-lookup"><span data-stu-id="2e843-179">GUID</span></span> | <span data-ttu-id="2e843-180">Identifikátor GUID podle odkazu</span><span class="sxs-lookup"><span data-stu-id="2e843-180">By-ref GUID</span></span> |
|------|-------------|
| `KNOWNFOLDERID` | `REFKNOWNFOLDERID` |

<span data-ttu-id="2e843-181">**❌** Použijte `[MarshalAs(UnmanagedType.LPStruct)]` pro jinou hodnotu než `ref` parametry GUID.</span><span class="sxs-lookup"><span data-stu-id="2e843-181">**❌ DO NOT** Use `[MarshalAs(UnmanagedType.LPStruct)]` for anything other than `ref` GUID parameters.</span></span>

## <a name="blittable-types"></a><span data-ttu-id="2e843-182">Typy přenosit</span><span class="sxs-lookup"><span data-stu-id="2e843-182">Blittable types</span></span>

<span data-ttu-id="2e843-183">Přenositelné typy jsou typy, které mají stejné reprezentace na úrovni bitů ve spravovaném a nativním kódu.</span><span class="sxs-lookup"><span data-stu-id="2e843-183">Blittable types are types that have the same bit-level representation in managed and native code.</span></span> <span data-ttu-id="2e843-184">Vzhledem k tomu, že není nutné je převádět do jiného formátu, aby bylo možné je zařadit do a z nativního kódu a jak to zlepšuje výkon, by měly být upřednostňovány.</span><span class="sxs-lookup"><span data-stu-id="2e843-184">As such they do not need to be converted to another format to be marshaled to and from native code, and as this improves performance they should be preferred.</span></span>

<span data-ttu-id="2e843-185">**Typy přenositeli:**</span><span class="sxs-lookup"><span data-stu-id="2e843-185">**Blittable types:**</span></span>

- <span data-ttu-id="2e843-186">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span><span class="sxs-lookup"><span data-stu-id="2e843-186">`byte`, `sbyte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `single`, `double`</span></span>
- <span data-ttu-id="2e843-187">nevnořená jednorozměrná pole typů s více typy (například `int[]`)</span><span class="sxs-lookup"><span data-stu-id="2e843-187">non-nested one-dimensional arrays of blittable types (for example, `int[]`)</span></span>
- <span data-ttu-id="2e843-188">struktury a třídy s pevným rozložením, které pro pole instancí mají jenom typy přenositelné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2e843-188">structs and classes with fixed layout that only have blittable value types for instance fields</span></span>
  - <span data-ttu-id="2e843-189">pevné rozložení vyžaduje `[StructLayout(LayoutKind.Sequential)]` nebo `[StructLayout(LayoutKind.Explicit)]`</span><span class="sxs-lookup"><span data-stu-id="2e843-189">fixed layout requires `[StructLayout(LayoutKind.Sequential)]` or `[StructLayout(LayoutKind.Explicit)]`</span></span>
  - <span data-ttu-id="2e843-190">struktury jsou ve výchozím nastavení `LayoutKind.Sequential` třídy `LayoutKind.Auto`</span><span class="sxs-lookup"><span data-stu-id="2e843-190">structs are `LayoutKind.Sequential` by default, classes are `LayoutKind.Auto`</span></span>

<span data-ttu-id="2e843-191">**Nenositelný odkaz:**</span><span class="sxs-lookup"><span data-stu-id="2e843-191">**NOT blittable:**</span></span>

- `bool`

<span data-ttu-id="2e843-192">**NĚKDY přenositelná:**</span><span class="sxs-lookup"><span data-stu-id="2e843-192">**SOMETIMES blittable:**</span></span>

- <span data-ttu-id="2e843-193">`char`, `string`</span><span class="sxs-lookup"><span data-stu-id="2e843-193">`char`, `string`</span></span>

<span data-ttu-id="2e843-194">Když jsou přenositelné typy předány odkazem, jsou místo kopírování do mezilehlé vyrovnávací paměti jednoduše připnuté serializátorem.</span><span class="sxs-lookup"><span data-stu-id="2e843-194">When blittable types are passed by reference, they're simply pinned by the marshaller instead of being copied to an intermediate buffer.</span></span> <span data-ttu-id="2e843-195">(Třídy jsou ze své podstaty předány odkazem, struktury jsou předány odkazem při použití s `ref` nebo `out`.)</span><span class="sxs-lookup"><span data-stu-id="2e843-195">(Classes are inherently passed by reference, structs are passed by reference when used with `ref` or `out`.)</span></span>

<span data-ttu-id="2e843-196">`char` je přímo v jednorozměrném poli, **nebo** Pokud je součástí typu, který obsahuje explicitně označený `[StructLayout]` s `CharSet = CharSet.Unicode`.</span><span class="sxs-lookup"><span data-stu-id="2e843-196">`char` is blittable in a one-dimensional array **or** if it's part of a type that contains it's explicitly marked with `[StructLayout]` with `CharSet = CharSet.Unicode`.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential, CharSet = CharSet.Unicode)]
public struct UnicodeCharStruct
{
    public char c;
}
```

<span data-ttu-id="2e843-197">`string` je přenositelná, pokud není obsažena v jiném typu a je předávána jako argument označený `[MarshalAs(UnmanagedType.LPWStr)]` nebo `[DllImport]` `CharSet = CharSet.Unicode` nastaven.</span><span class="sxs-lookup"><span data-stu-id="2e843-197">`string` is blittable if it isn't contained in another type and it's being passed as an argument that is marked with `[MarshalAs(UnmanagedType.LPWStr)]` or the `[DllImport]` has `CharSet = CharSet.Unicode` set.</span></span>

<span data-ttu-id="2e843-198">Když se pokusíte vytvořit připnutý `GCHandle`, můžete zjistit, jestli je typ přenositelný.</span><span class="sxs-lookup"><span data-stu-id="2e843-198">You can see if a type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="2e843-199">Pokud typ není řetězec nebo se považuje za Nepřenositelný, `GCHandle.Alloc` vyvolá `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="2e843-199">If the type isn't a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="2e843-200">**✔️ proveďte** přenositeli struktury, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="2e843-200">**✔️ DO** make your structures blittable when possible.</span></span>

<span data-ttu-id="2e843-201">Další informace najdete v části .</span><span class="sxs-lookup"><span data-stu-id="2e843-201">For more information, see:</span></span>

- [<span data-ttu-id="2e843-202">Přenositelné a nepřenositelné typy</span><span class="sxs-lookup"><span data-stu-id="2e843-202">Blittable and Non-Blittable Types</span></span>](../../framework/interop/blittable-and-non-blittable-types.md)  
- [<span data-ttu-id="2e843-203">Zařazování typů</span><span class="sxs-lookup"><span data-stu-id="2e843-203">Type Marshaling</span></span>](type-marshaling.md)

## <a name="keeping-managed-objects-alive"></a><span data-ttu-id="2e843-204">Udržování spravovaných objektů</span><span class="sxs-lookup"><span data-stu-id="2e843-204">Keeping managed objects alive</span></span>

<span data-ttu-id="2e843-205">`GC.KeepAlive()` zajistí, že objekt zůstane v oboru, dokud nebude dosaženo metody udržení naživu.</span><span class="sxs-lookup"><span data-stu-id="2e843-205">`GC.KeepAlive()` will ensure an object stays in scope until the KeepAlive method is hit.</span></span>

<span data-ttu-id="2e843-206">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) umožňuje zařazování zachovat objekt aktivní po dobu trvání volání nespravovaného objektu.</span><span class="sxs-lookup"><span data-stu-id="2e843-206">[`HandleRef`](xref:System.Runtime.InteropServices.HandleRef) allows the marshaller to keep an object alive for the duration of a P/Invoke.</span></span> <span data-ttu-id="2e843-207">Dá se použít místo `IntPtr` v signaturách metody.</span><span class="sxs-lookup"><span data-stu-id="2e843-207">It can be used instead of `IntPtr` in method signatures.</span></span> <span data-ttu-id="2e843-208">`SafeHandle` efektivně nahrazuje tuto třídu a měla by se používat místo toho.</span><span class="sxs-lookup"><span data-stu-id="2e843-208">`SafeHandle` effectively replaces this class and should be used instead.</span></span>

<span data-ttu-id="2e843-209">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) umožňuje připnutí spravovaného objektu a získání nativního ukazatele na něj.</span><span class="sxs-lookup"><span data-stu-id="2e843-209">[`GCHandle`](xref:System.Runtime.InteropServices.GCHandle) allows pinning a managed object and getting the native pointer to it.</span></span> <span data-ttu-id="2e843-210">Základní vzor je:</span><span class="sxs-lookup"><span data-stu-id="2e843-210">The basic pattern is:</span></span>  

```csharp
GCHandle handle = GCHandle.Alloc(obj, GCHandleType.Pinned);
IntPtr ptr = handle.AddrOfPinnedObject();
handle.Free();
```

<span data-ttu-id="2e843-211">Připnutí není výchozím nastavením pro `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="2e843-211">Pinning isn't the default for `GCHandle`.</span></span> <span data-ttu-id="2e843-212">Druhým hlavním vzorem je předání odkazu spravovanému objektu prostřednictvím nativního kódu a zpět ke spravovanému kódu, obvykle pomocí zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="2e843-212">The other major pattern is for passing a reference to a managed object through native code and back to managed code, usually with a callback.</span></span> <span data-ttu-id="2e843-213">Tady je vzor:</span><span class="sxs-lookup"><span data-stu-id="2e843-213">Here is the pattern:</span></span>

```csharp
GCHandle handle = GCHandle.Alloc(obj);
SomeNativeEnumerator(callbackDelegate, GCHandle.ToIntPtr(handle));

// In the callback
GCHandle handle = GCHandle.FromIntPtr(param);
object managedObject = handle.Target;

// After the last callback
handle.Free();
```

<span data-ttu-id="2e843-214">Nezapomeňte, že `GCHandle` musí být explicitně uvolněny, aby nedošlo k nevracení paměti.</span><span class="sxs-lookup"><span data-stu-id="2e843-214">Don't forget that `GCHandle` needs to be explicitly freed to avoid memory leaks.</span></span>

## <a name="common-windows-data-types"></a><span data-ttu-id="2e843-215">Běžné datové typy Windows</span><span class="sxs-lookup"><span data-stu-id="2e843-215">Common Windows data types</span></span>

<span data-ttu-id="2e843-216">Tady je seznam datových typů, které se běžně používají v rozhraních API C# systému Windows, a typy, které se mají použít při volání do kódu Windows.</span><span class="sxs-lookup"><span data-stu-id="2e843-216">Here is a list of data types commonly used in Windows APIs and which C# types to use when calling into the Windows code.</span></span>

<span data-ttu-id="2e843-217">Následující typy mají stejnou velikost v 32 a 64 bitovém systému Windows, bez ohledu na jejich názvy.</span><span class="sxs-lookup"><span data-stu-id="2e843-217">The following types are the same size on 32-bit and 64-bit Windows, despite their names.</span></span>

| <span data-ttu-id="2e843-218">Šířka</span><span class="sxs-lookup"><span data-stu-id="2e843-218">Width</span></span> | <span data-ttu-id="2e843-219">Windows</span><span class="sxs-lookup"><span data-stu-id="2e843-219">Windows</span></span>          | <span data-ttu-id="2e843-220">C (Windows)</span><span class="sxs-lookup"><span data-stu-id="2e843-220">C (Windows)</span></span>          | <span data-ttu-id="2e843-221">C#</span><span class="sxs-lookup"><span data-stu-id="2e843-221">C#</span></span>       | <span data-ttu-id="2e843-222">Jiné</span><span class="sxs-lookup"><span data-stu-id="2e843-222">Alternative</span></span>                          |
|:------|:-----------------|:---------------------|:---------|:-------------------------------------|
| <span data-ttu-id="2e843-223">32</span><span class="sxs-lookup"><span data-stu-id="2e843-223">32</span></span>    | `BOOL`           | `int`                | `int`    | `bool`                               |
| <span data-ttu-id="2e843-224">8</span><span class="sxs-lookup"><span data-stu-id="2e843-224">8</span></span>     | `BOOLEAN`        | `unsigned char`      | `byte`   | `[MarshalAs(UnmanagedType.U1)] bool` |
| <span data-ttu-id="2e843-225">8</span><span class="sxs-lookup"><span data-stu-id="2e843-225">8</span></span>     | `BYTE`           | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="2e843-226">8</span><span class="sxs-lookup"><span data-stu-id="2e843-226">8</span></span>     | `CHAR`           | `char`               | `sbyte`  |                                      |
| <span data-ttu-id="2e843-227">8</span><span class="sxs-lookup"><span data-stu-id="2e843-227">8</span></span>     | `UCHAR`          | `unsigned char`      | `byte`   |                                      |
| <span data-ttu-id="2e843-228">16</span><span class="sxs-lookup"><span data-stu-id="2e843-228">16</span></span>    | `SHORT`          | `short`              | `short`  |                                      |
| <span data-ttu-id="2e843-229">16</span><span class="sxs-lookup"><span data-stu-id="2e843-229">16</span></span>    | `CSHORT`         | `short`              | `short`  |                                      |
| <span data-ttu-id="2e843-230">16</span><span class="sxs-lookup"><span data-stu-id="2e843-230">16</span></span>    | `USHORT`         | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="2e843-231">16</span><span class="sxs-lookup"><span data-stu-id="2e843-231">16</span></span>    | `WORD`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="2e843-232">16</span><span class="sxs-lookup"><span data-stu-id="2e843-232">16</span></span>    | `ATOM`           | `unsigned short`     | `ushort` |                                      |
| <span data-ttu-id="2e843-233">32</span><span class="sxs-lookup"><span data-stu-id="2e843-233">32</span></span>    | `INT`            | `int`                | `int`    |                                      |
| <span data-ttu-id="2e843-234">32</span><span class="sxs-lookup"><span data-stu-id="2e843-234">32</span></span>    | `LONG`           | `long`               | `int`    |                                      |
| <span data-ttu-id="2e843-235">32</span><span class="sxs-lookup"><span data-stu-id="2e843-235">32</span></span>    | `ULONG`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="2e843-236">32</span><span class="sxs-lookup"><span data-stu-id="2e843-236">32</span></span>    | `DWORD`          | `unsigned long`      | `uint`   |                                      |
| <span data-ttu-id="2e843-237">64</span><span class="sxs-lookup"><span data-stu-id="2e843-237">64</span></span>    | `QWORD`          | `long long`          | `long`   |                                      |
| <span data-ttu-id="2e843-238">64</span><span class="sxs-lookup"><span data-stu-id="2e843-238">64</span></span>    | `LARGE_INTEGER`  | `long long`          | `long`   |                                      |
| <span data-ttu-id="2e843-239">64</span><span class="sxs-lookup"><span data-stu-id="2e843-239">64</span></span>    | `LONGLONG`       | `long long`          | `long`   |                                      |
| <span data-ttu-id="2e843-240">64</span><span class="sxs-lookup"><span data-stu-id="2e843-240">64</span></span>    | `ULONGLONG`      | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="2e843-241">64</span><span class="sxs-lookup"><span data-stu-id="2e843-241">64</span></span>    | `ULARGE_INTEGER` | `unsigned long long` | `ulong`  |                                      |
| <span data-ttu-id="2e843-242">32</span><span class="sxs-lookup"><span data-stu-id="2e843-242">32</span></span>    | `HRESULT`        | `long`               | `int`    |                                      |
| <span data-ttu-id="2e843-243">32</span><span class="sxs-lookup"><span data-stu-id="2e843-243">32</span></span>    | `NTSTATUS`       | `long`               | `int`    |                                      |

<span data-ttu-id="2e843-244">Následující typy jsou ukazatele, které následují po šířce platformy.</span><span class="sxs-lookup"><span data-stu-id="2e843-244">The following types, being pointers, do follow the width of the platform.</span></span> <span data-ttu-id="2e843-245">Pro tyto `UIntPtr` použijte `IntPtr`/.</span><span class="sxs-lookup"><span data-stu-id="2e843-245">Use `IntPtr`/`UIntPtr` for these.</span></span>

| <span data-ttu-id="2e843-246">Typy podepsaných ukazatelů (použijte `IntPtr`)</span><span class="sxs-lookup"><span data-stu-id="2e843-246">Signed Pointer Types (use `IntPtr`)</span></span> | <span data-ttu-id="2e843-247">Typ ukazatele bez znaménka (použijte `UIntPtr`)</span><span class="sxs-lookup"><span data-stu-id="2e843-247">Unsigned Pointer Types (use `UIntPtr`)</span></span> |
|:------------------------------------|:---------------------------------------|
| `HANDLE`                            | `WPARAM`                               |
| `HWND`                              | `UINT_PTR`                             |
| `HINSTANCE`                         | `ULONG_PTR`                            |
| `LPARAM`                            | `SIZE_T`                               |
| `LRESULT`                           |                                        |
| `LONG_PTR`                          |                                        |
| `INT_PTR`                           |                                        |

<span data-ttu-id="2e843-248">`PVOID` systému Windows, což je `void*` jazyka C, lze zařadit jako `IntPtr` nebo `UIntPtr`, ale preferovat `void*`, pokud je to možné.</span><span class="sxs-lookup"><span data-stu-id="2e843-248">A Windows `PVOID` which is a C `void*` can be marshaled as either `IntPtr` or `UIntPtr`, but prefer `void*` when possible.</span></span>

[<span data-ttu-id="2e843-249">Datové typy Windows</span><span class="sxs-lookup"><span data-stu-id="2e843-249">Windows Data Types</span></span>](/windows/desktop/WinProg/windows-data-types)

[<span data-ttu-id="2e843-250">Rozsahy datových typů</span><span class="sxs-lookup"><span data-stu-id="2e843-250">Data Type Ranges</span></span>](/cpp/cpp/data-type-ranges)

## <a name="structs"></a><span data-ttu-id="2e843-251">Struktury</span><span class="sxs-lookup"><span data-stu-id="2e843-251">Structs</span></span>

<span data-ttu-id="2e843-252">Spravované struktury se vytvoří v zásobníku a neodstraňují se, dokud se metoda nevrátí.</span><span class="sxs-lookup"><span data-stu-id="2e843-252">Managed structs are created on the stack and aren't removed until the method returns.</span></span> <span data-ttu-id="2e843-253">Podle definice pak jsou "připnuté" (nebudou přesunuty do GC).</span><span class="sxs-lookup"><span data-stu-id="2e843-253">By definition then, they are "pinned" (it won't get moved by the GC).</span></span> <span data-ttu-id="2e843-254">Můžete také jednoduše převzít adresu z nebezpečných bloků kódu, pokud nativní kód nebude používat ukazatel za koncem aktuální metody.</span><span class="sxs-lookup"><span data-stu-id="2e843-254">You can also simply take the address in unsafe code blocks if native code won't use the pointer past the end of the current method.</span></span>

<span data-ttu-id="2e843-255">Přenositelné struktury jsou mnohem větší, protože je lze jednoduše použít přímo zařazovací vrstvou.</span><span class="sxs-lookup"><span data-stu-id="2e843-255">Blittable structs are much more performant as they can simply be used directly by the marshaling layer.</span></span> <span data-ttu-id="2e843-256">Snažte se nastavit struktury jako přenositelné (například vyhnout `bool`).</span><span class="sxs-lookup"><span data-stu-id="2e843-256">Try to make structs blittable (for example, avoid `bool`).</span></span> <span data-ttu-id="2e843-257">Další informace najdete v části [typy přenosit](#blittable-types) .</span><span class="sxs-lookup"><span data-stu-id="2e843-257">For more information, see the [Blittable Types](#blittable-types) section.</span></span>

<span data-ttu-id="2e843-258">*Pokud* je struktura přenositelná, použijte k zajištění lepšího výkonu `sizeof()` místo `Marshal.SizeOf<MyStruct>()`.</span><span class="sxs-lookup"><span data-stu-id="2e843-258">*If* the struct is blittable, use `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for better performance.</span></span> <span data-ttu-id="2e843-259">Jak je uvedeno výše, můžete ověřit, že typ je přenositelný, a pokusit se vytvořit připnutý `GCHandle`.</span><span class="sxs-lookup"><span data-stu-id="2e843-259">As mentioned above, you can validate that the type is blittable by attempting to create a pinned `GCHandle`.</span></span> <span data-ttu-id="2e843-260">Pokud typ není řetězec nebo se považuje za Nepřenositelný, `GCHandle.Alloc` vyvolá `ArgumentException`.</span><span class="sxs-lookup"><span data-stu-id="2e843-260">If the type is not a string or considered blittable, `GCHandle.Alloc` will throw an `ArgumentException`.</span></span>

<span data-ttu-id="2e843-261">Ukazatele na struktury v definicích musí být buď předány `ref`, nebo používat `unsafe` a `*`.</span><span class="sxs-lookup"><span data-stu-id="2e843-261">Pointers to structs in definitions must either be passed by `ref` or use `unsafe` and `*`.</span></span>

<span data-ttu-id="2e843-262">**✔️** podle tvaru a názvů, které se používají v dokumentaci k oficiální platformě nebo v hlavičce, co nejvíce porovnává se spravovanou strukturou.</span><span class="sxs-lookup"><span data-stu-id="2e843-262">**✔️ DO** match the managed struct as closely as possible to the shape and names that are used in the official platform documentation or header.</span></span>

<span data-ttu-id="2e843-263">pro zvýšení výkonu ✔️ C# použít `sizeof()` místo `Marshal.SizeOf<MyStruct>()` pro přenositelné struktury.</span><span class="sxs-lookup"><span data-stu-id="2e843-263">**✔️ DO** use the C# `sizeof()` instead of `Marshal.SizeOf<MyStruct>()` for blittable structures to improve performance.</span></span>

<span data-ttu-id="2e843-264">Pole jako `INT_PTR Reserved1[2]` musí být zařazeno do dvou `IntPtr` polí `Reserved1a` a `Reserved1b`.</span><span class="sxs-lookup"><span data-stu-id="2e843-264">An array like `INT_PTR Reserved1[2]` has to be marshaled to two `IntPtr` fields, `Reserved1a` and `Reserved1b`.</span></span> <span data-ttu-id="2e843-265">Pokud je nativním polem primitivní typ, můžeme použít klíčové slovo `fixed` k jeho zapsání trochu efektivněji.</span><span class="sxs-lookup"><span data-stu-id="2e843-265">When the native array is a primitive type, we can use the `fixed` keyword to write it a little more cleanly.</span></span> <span data-ttu-id="2e843-266">Například `SYSTEM_PROCESS_INFORMATION` vypadat jako v nativní hlavičce:</span><span class="sxs-lookup"><span data-stu-id="2e843-266">For example, `SYSTEM_PROCESS_INFORMATION` looks like this in the native header:</span></span>

```c
typedef struct _SYSTEM_PROCESS_INFORMATION {
    ULONG NextEntryOffset;
    ULONG NumberOfThreads;
    BYTE Reserved1[48];
    UNICODE_STRING ImageName;
...
} SYSTEM_PROCESS_INFORMATION
```

<span data-ttu-id="2e843-267">V C#nástroji můžeme zapisovat takto:</span><span class="sxs-lookup"><span data-stu-id="2e843-267">In C#, we can write it like this:</span></span>

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

<span data-ttu-id="2e843-268">Existuje však několik možná úskalí s pevnými vyrovnávacími pamětmi.</span><span class="sxs-lookup"><span data-stu-id="2e843-268">However, there are some gotchas with fixed buffers.</span></span> <span data-ttu-id="2e843-269">Pevné vyrovnávací paměti nepřenositelného typu nebudou správně zařazeny, takže musí být místní pole rozšířeno na více jednotlivých polí.</span><span class="sxs-lookup"><span data-stu-id="2e843-269">Fixed buffers of non-blittable types won't be correctly marshaled, so the in-place array needs to be expanded out to multiple individual fields.</span></span> <span data-ttu-id="2e843-270">V .NET Framework a .NET Core před 3,0 platí, že pokud je struktura obsahující pevné pole vyrovnávací paměti vnořena do nepřenositelné struktury, pole pevné vyrovnávací paměti se správně nezazařazuje do nativního kódu.</span><span class="sxs-lookup"><span data-stu-id="2e843-270">Additionally, in .NET Framework and .NET Core before 3.0, if a struct containing a fixed buffer field is nested within a non-blittable struct, the fixed buffer field won't be correctly marshaled to native code.</span></span>
