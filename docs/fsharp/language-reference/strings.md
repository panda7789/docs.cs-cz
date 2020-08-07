---
title: Řetězce
description: 'Přečtěte si, jak typ řetězce F # představuje neměnný text jako posloupnost znaků Unicode.'
ms.date: 07/05/2019
ms.openlocfilehash: 67a6506b4b8c479da1022c069a7f53402f904b4d
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855410"
---
# <a name="strings"></a><span data-ttu-id="3bbe7-103">Řetězce</span><span class="sxs-lookup"><span data-stu-id="3bbe7-103">Strings</span></span>

<span data-ttu-id="3bbe7-104">`string`Typ představuje neproměnlivý text jako posloupnost znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-104">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="3bbe7-105">`string`je alias pro `System.String` v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-105">`string` is an alias for `System.String` in .NET.</span></span>

> [!NOTE]
> <span data-ttu-id="3bbe7-106">Reference k rozhraní docs.microsoft.com API pro F # není dokončená.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-106">The docs.microsoft.com API reference for F# is not complete.</span></span> <span data-ttu-id="3bbe7-107">Pokud narazíte na nefunkční odkazy, místo toho použijte [dokumentaci základní knihovny F #](https://fsharp.github.io/fsharp-core-docs/) .</span><span class="sxs-lookup"><span data-stu-id="3bbe7-107">If you encounter any broken links, reference [F# Core Library Documentation](https://fsharp.github.io/fsharp-core-docs/) instead.</span></span>

## <a name="remarks"></a><span data-ttu-id="3bbe7-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3bbe7-108">Remarks</span></span>

<span data-ttu-id="3bbe7-109">Řetězcové literály jsou odděleny znakem uvozovky (").</span><span class="sxs-lookup"><span data-stu-id="3bbe7-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="3bbe7-110">Znak zpětného lomítka ( \\ ) se používá ke kódování určitých speciálních znaků.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="3bbe7-111">Zpětné lomítko a další znak dohromady se označují jako *řídicí sekvence*.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="3bbe7-112">Řídicí sekvence, které jsou podporovány v literálech řetězce F #, jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="3bbe7-113">Znak</span><span class="sxs-lookup"><span data-stu-id="3bbe7-113">Character</span></span>|<span data-ttu-id="3bbe7-114">Řídicí sekvence</span><span class="sxs-lookup"><span data-stu-id="3bbe7-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="3bbe7-115">Výstrahy</span><span class="sxs-lookup"><span data-stu-id="3bbe7-115">Alert</span></span>|`\a`|
|<span data-ttu-id="3bbe7-116">Backspace</span><span class="sxs-lookup"><span data-stu-id="3bbe7-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="3bbe7-117">Informační kanál formuláře</span><span class="sxs-lookup"><span data-stu-id="3bbe7-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="3bbe7-118">Nového</span><span class="sxs-lookup"><span data-stu-id="3bbe7-118">Newline</span></span>|`\n`|
|<span data-ttu-id="3bbe7-119">Návrat na začátek řádku</span><span class="sxs-lookup"><span data-stu-id="3bbe7-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="3bbe7-120">Karta</span><span class="sxs-lookup"><span data-stu-id="3bbe7-120">Tab</span></span>|`\t`|
|<span data-ttu-id="3bbe7-121">Vertikální tabulátor</span><span class="sxs-lookup"><span data-stu-id="3bbe7-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="3bbe7-122">Zpětné lomítko</span><span class="sxs-lookup"><span data-stu-id="3bbe7-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="3bbe7-123">Znak uvozovek</span><span class="sxs-lookup"><span data-stu-id="3bbe7-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="3bbe7-124">Apostrof</span><span class="sxs-lookup"><span data-stu-id="3bbe7-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="3bbe7-125">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="3bbe7-125">Unicode character</span></span>|<span data-ttu-id="3bbe7-126">`\DDD`(kde `D` označuje desítkovou číslici; rozsah 000-255; například `\231` = "ç")</span><span class="sxs-lookup"><span data-stu-id="3bbe7-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="3bbe7-127">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="3bbe7-127">Unicode character</span></span>|<span data-ttu-id="3bbe7-128">`\xHH`(kde `H` označuje hexadecimální číslo; rozsah 00-FF; například `\xE7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="3bbe7-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="3bbe7-129">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="3bbe7-129">Unicode character</span></span>|<span data-ttu-id="3bbe7-130">`\uHHHH`(UTF-16) (kde `H` označuje šestnáctkovou číslici; rozsah 0000-FFFF;  například `\u00E7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="3bbe7-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="3bbe7-131">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="3bbe7-131">Unicode character</span></span>|<span data-ttu-id="3bbe7-132">`\U00HHHHHH`(UTF-32) (kde `H` označuje hexadecimální číslici, rozsah 000000-10FFFF;  například `\U0001F47D` = " 👽 ")</span><span class="sxs-lookup"><span data-stu-id="3bbe7-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="3bbe7-133">`\DDD`Řídicí sekvence je Desítkový zápis, nikoli osmičkový zápis podobně jako ve většině ostatních jazyků.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="3bbe7-134">Proto číslice `8` a `9` jsou platné a sekvence `\032` představuje mezeru (U + 0020), zatímco stejný bod kódu v osmičkové notaci by byl `\040` .</span><span class="sxs-lookup"><span data-stu-id="3bbe7-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="3bbe7-135">S omezením na rozsah 0-255 (0xFF), `\DDD` `\x` řídicí sekvence a jsou efektivně nastaveny jako znaková sada [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) , protože se shoduje s 256 prvními body kódu Unicode.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

## <a name="verbatim-strings"></a><span data-ttu-id="3bbe7-136">Doslovné řetězce</span><span class="sxs-lookup"><span data-stu-id="3bbe7-136">Verbatim Strings</span></span>

<span data-ttu-id="3bbe7-137">Pokud předchází symbol @, je literál doslovného řetězce.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-137">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="3bbe7-138">To znamená, že všechny řídicí sekvence jsou ignorovány s tím rozdílem, že dva znaky uvozovek jsou interpretovány jako jeden znak uvozovky.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-138">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

## <a name="triple-quoted-strings"></a><span data-ttu-id="3bbe7-139">Trojité řetězce v uvozovkách</span><span class="sxs-lookup"><span data-stu-id="3bbe7-139">Triple Quoted Strings</span></span>

<span data-ttu-id="3bbe7-140">Navíc může být řetězec uzavřen třemi uvozovkami.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-140">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="3bbe7-141">V tomto případě jsou všechny řídicí sekvence ignorovány, včetně znaků dvojité uvozovky.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-141">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="3bbe7-142">Chcete-li zadat řetězec, který obsahuje vložený řetězec v uvozovkách, můžete buď použít doslovné řetězec nebo trojitý řetězec v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-142">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="3bbe7-143">Pokud použijete doslovné řetězec, je nutné zadat dva znaky uvozovek, které označují znak jednoduché uvozovky.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-143">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="3bbe7-144">Použijete-li řetězec v uvozovkách, lze použít znaky jednoduchých uvozovek bez jejich analyzování jako konce řetězce.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-144">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="3bbe7-145">Tato technika může být užitečná při práci s XML nebo jinými strukturami, které zahrnují vložené uvozovky.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-145">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="3bbe7-146">V kódu jsou řetězce, které mají zalomení řádků, přijaty a zalomení řádků jsou interpretovány jako newlines, pokud znak zpětného lomítka není poslední znak před koncem řádku.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-146">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="3bbe7-147">Počáteční prázdné místo na dalším řádku se při použití znaku zpětného lomítka ignoruje.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-147">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="3bbe7-148">Následující kód vytvoří řetězec `str1` , který má hodnotu `"abc\ndef"` a řetězec `str2` , který má hodnotu `"abcdef"` .</span><span class="sxs-lookup"><span data-stu-id="3bbe7-148">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a><span data-ttu-id="3bbe7-149">Indexování řetězců a vytváření řezů</span><span class="sxs-lookup"><span data-stu-id="3bbe7-149">String Indexing and Slicing</span></span>

<span data-ttu-id="3bbe7-150">K jednotlivým znakům v řetězci můžete přistupovat pomocí syntaxe typu pole, a to následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-150">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="3bbe7-151">Výstup je `b` .</span><span class="sxs-lookup"><span data-stu-id="3bbe7-151">The output is `b`.</span></span>

<span data-ttu-id="3bbe7-152">Nebo můžete extrahovat podřetězce pomocí syntaxe řezu pole, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-152">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="3bbe7-153">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-153">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="3bbe7-154">Řetězce ASCII můžete reprezentovat poli bajtů bez znaménka, typ `byte[]` .</span><span class="sxs-lookup"><span data-stu-id="3bbe7-154">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="3bbe7-155">Přidáte příponu `B` do řetězcového literálu, který označuje, že se jedná o řetězec ASCII.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-155">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="3bbe7-156">Řetězcové literály ASCII používané s poli bajtů podporují stejné řídicí sekvence jako řetězce Unicode, s výjimkou řídicích sekvencí Unicode.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-156">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="3bbe7-157">Operátory řetězce</span><span class="sxs-lookup"><span data-stu-id="3bbe7-157">String Operators</span></span>

<span data-ttu-id="3bbe7-158">`+`Operátor lze použít k zřetězení řetězců a udržování kompatibility s funkcemi pro zpracování .NET Framework řetězců.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-158">The `+` operator can be used to concatenate strings, maintaining compatibility with the .NET Framework string handling features.</span></span> <span data-ttu-id="3bbe7-159">Následující příklad znázorňuje zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-159">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="3bbe7-160">String – Třída</span><span class="sxs-lookup"><span data-stu-id="3bbe7-160">String Class</span></span>

<span data-ttu-id="3bbe7-161">Vzhledem k tomu, že typ řetězce v jazyce F # je ve skutečnosti .NET Framework `System.String` typ, `System.String` jsou k dispozici všichni členové.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-161">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="3bbe7-162">To zahrnuje `+` operátor, který se používá ke zřetězení řetězců, `Length` vlastnost a `Chars` vlastnost, která vrací řetězec jako pole znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-162">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="3bbe7-163">Další informace o řetězcích naleznete v tématu `System.String` .</span><span class="sxs-lookup"><span data-stu-id="3bbe7-163">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="3bbe7-164">Pomocí `Chars` vlastnosti `System.String` můžete k jednotlivým znakům v řetězci přistupovat zadáním indexu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-164">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="3bbe7-165">Řetězec – modul</span><span class="sxs-lookup"><span data-stu-id="3bbe7-165">String Module</span></span>

<span data-ttu-id="3bbe7-166">Další funkce pro zpracování řetězců je obsažena v `String` modulu v `FSharp.Core` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3bbe7-166">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="3bbe7-167">Další informace najdete v tématu [modul Core. String](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="3bbe7-167">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="3bbe7-168">Viz také</span><span class="sxs-lookup"><span data-stu-id="3bbe7-168">See also</span></span>

- [<span data-ttu-id="3bbe7-169">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="3bbe7-169">F# Language Reference</span></span>](index.md)
