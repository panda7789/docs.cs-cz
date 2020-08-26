---
title: Řetězce
description: 'Přečtěte si, jak typ řetězce F # představuje neměnný text jako posloupnost znaků Unicode.'
ms.date: 08/15/2020
ms.openlocfilehash: f6ec36feeb197bf785c702e7b626cf5cf80696ab
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812208"
---
# <a name="strings"></a><span data-ttu-id="be80c-103">Řetězce</span><span class="sxs-lookup"><span data-stu-id="be80c-103">Strings</span></span>

<span data-ttu-id="be80c-104">`string`Typ představuje neproměnlivý text jako posloupnost znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="be80c-104">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="be80c-105">`string` je alias pro `System.String` v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="be80c-105">`string` is an alias for `System.String` in .NET.</span></span>

## <a name="remarks"></a><span data-ttu-id="be80c-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="be80c-106">Remarks</span></span>

<span data-ttu-id="be80c-107">Řetězcové literály jsou odděleny znakem uvozovky (").</span><span class="sxs-lookup"><span data-stu-id="be80c-107">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="be80c-108">Znak zpětného lomítka ( \\ ) se používá ke kódování určitých speciálních znaků.</span><span class="sxs-lookup"><span data-stu-id="be80c-108">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="be80c-109">Zpětné lomítko a další znak dohromady se označují jako *řídicí sekvence*.</span><span class="sxs-lookup"><span data-stu-id="be80c-109">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="be80c-110">Řídicí sekvence, které jsou podporovány v literálech řetězce F #, jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="be80c-110">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="be80c-111">Znak</span><span class="sxs-lookup"><span data-stu-id="be80c-111">Character</span></span>|<span data-ttu-id="be80c-112">Řídicí sekvence</span><span class="sxs-lookup"><span data-stu-id="be80c-112">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="be80c-113">Výstrahy</span><span class="sxs-lookup"><span data-stu-id="be80c-113">Alert</span></span>|`\a`|
|<span data-ttu-id="be80c-114">Backspace</span><span class="sxs-lookup"><span data-stu-id="be80c-114">Backspace</span></span>|`\b`|
|<span data-ttu-id="be80c-115">Informační kanál formuláře</span><span class="sxs-lookup"><span data-stu-id="be80c-115">Form feed</span></span>|`\f`|
|<span data-ttu-id="be80c-116">Nového</span><span class="sxs-lookup"><span data-stu-id="be80c-116">Newline</span></span>|`\n`|
|<span data-ttu-id="be80c-117">Návrat na začátek řádku</span><span class="sxs-lookup"><span data-stu-id="be80c-117">Carriage return</span></span>|`\r`|
|<span data-ttu-id="be80c-118">Karta</span><span class="sxs-lookup"><span data-stu-id="be80c-118">Tab</span></span>|`\t`|
|<span data-ttu-id="be80c-119">Vertikální tabulátor</span><span class="sxs-lookup"><span data-stu-id="be80c-119">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="be80c-120">Zpětné lomítko</span><span class="sxs-lookup"><span data-stu-id="be80c-120">Backslash</span></span>|`\\`|
|<span data-ttu-id="be80c-121">Znak uvozovek</span><span class="sxs-lookup"><span data-stu-id="be80c-121">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="be80c-122">Apostrof</span><span class="sxs-lookup"><span data-stu-id="be80c-122">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="be80c-123">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="be80c-123">Unicode character</span></span>|<span data-ttu-id="be80c-124">`\DDD` (kde `D` označuje desítkovou číslici; rozsah 000-255; například `\231` = "ç")</span><span class="sxs-lookup"><span data-stu-id="be80c-124">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="be80c-125">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="be80c-125">Unicode character</span></span>|<span data-ttu-id="be80c-126">`\xHH` (kde `H` označuje hexadecimální číslo; rozsah 00-FF; například `\xE7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="be80c-126">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="be80c-127">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="be80c-127">Unicode character</span></span>|<span data-ttu-id="be80c-128">`\uHHHH` (UTF-16) (kde `H` označuje šestnáctkovou číslici; rozsah 0000-FFFF;  například `\u00E7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="be80c-128">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="be80c-129">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="be80c-129">Unicode character</span></span>|<span data-ttu-id="be80c-130">`\U00HHHHHH` (UTF-32) (kde `H` označuje hexadecimální číslici, rozsah 000000-10FFFF;  například `\U0001F47D` = " 👽 ")</span><span class="sxs-lookup"><span data-stu-id="be80c-130">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="be80c-131">`\DDD`Řídicí sekvence je Desítkový zápis, nikoli osmičkový zápis podobně jako ve většině ostatních jazyků.</span><span class="sxs-lookup"><span data-stu-id="be80c-131">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="be80c-132">Proto číslice `8` a `9` jsou platné a sekvence `\032` představuje mezeru (U + 0020), zatímco stejný bod kódu v osmičkové notaci by byl `\040` .</span><span class="sxs-lookup"><span data-stu-id="be80c-132">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="be80c-133">S omezením na rozsah 0-255 (0xFF), `\DDD` `\x` řídicí sekvence a jsou efektivně nastaveny jako znaková sada [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) , protože se shoduje s 256 prvními body kódu Unicode.</span><span class="sxs-lookup"><span data-stu-id="be80c-133">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

## <a name="verbatim-strings"></a><span data-ttu-id="be80c-134">Doslovné řetězce</span><span class="sxs-lookup"><span data-stu-id="be80c-134">Verbatim Strings</span></span>

<span data-ttu-id="be80c-135">Pokud předchází symbol @, je literál doslovného řetězce.</span><span class="sxs-lookup"><span data-stu-id="be80c-135">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="be80c-136">To znamená, že všechny řídicí sekvence jsou ignorovány s tím rozdílem, že dva znaky uvozovek jsou interpretovány jako jeden znak uvozovky.</span><span class="sxs-lookup"><span data-stu-id="be80c-136">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

## <a name="triple-quoted-strings"></a><span data-ttu-id="be80c-137">Trojité řetězce v uvozovkách</span><span class="sxs-lookup"><span data-stu-id="be80c-137">Triple Quoted Strings</span></span>

<span data-ttu-id="be80c-138">Navíc může být řetězec uzavřen třemi uvozovkami.</span><span class="sxs-lookup"><span data-stu-id="be80c-138">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="be80c-139">V tomto případě jsou všechny řídicí sekvence ignorovány, včetně znaků dvojité uvozovky.</span><span class="sxs-lookup"><span data-stu-id="be80c-139">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="be80c-140">Chcete-li zadat řetězec, který obsahuje vložený řetězec v uvozovkách, můžete buď použít doslovné řetězec nebo trojitý řetězec v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="be80c-140">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="be80c-141">Pokud použijete doslovné řetězec, je nutné zadat dva znaky uvozovek, které označují znak jednoduché uvozovky.</span><span class="sxs-lookup"><span data-stu-id="be80c-141">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="be80c-142">Použijete-li řetězec v uvozovkách, lze použít znaky jednoduchých uvozovek bez jejich analyzování jako konce řetězce.</span><span class="sxs-lookup"><span data-stu-id="be80c-142">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="be80c-143">Tato technika může být užitečná při práci s XML nebo jinými strukturami, které zahrnují vložené uvozovky.</span><span class="sxs-lookup"><span data-stu-id="be80c-143">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="be80c-144">V kódu jsou řetězce, které mají zalomení řádků, přijaty a zalomení řádků jsou interpretovány jako newlines, pokud znak zpětného lomítka není poslední znak před koncem řádku.</span><span class="sxs-lookup"><span data-stu-id="be80c-144">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="be80c-145">Počáteční prázdné místo na dalším řádku se při použití znaku zpětného lomítka ignoruje.</span><span class="sxs-lookup"><span data-stu-id="be80c-145">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="be80c-146">Následující kód vytvoří řetězec `str1` , který má hodnotu `"abc\ndef"` a řetězec `str2` , který má hodnotu `"abcdef"` .</span><span class="sxs-lookup"><span data-stu-id="be80c-146">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a><span data-ttu-id="be80c-147">Indexování řetězců a vytváření řezů</span><span class="sxs-lookup"><span data-stu-id="be80c-147">String Indexing and Slicing</span></span>

<span data-ttu-id="be80c-148">K jednotlivým znakům v řetězci můžete přistupovat pomocí syntaxe typu pole, a to následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="be80c-148">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="be80c-149">Výstup je `b`.</span><span class="sxs-lookup"><span data-stu-id="be80c-149">The output is `b`.</span></span>

<span data-ttu-id="be80c-150">Nebo můžete extrahovat podřetězce pomocí syntaxe řezu pole, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="be80c-150">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="be80c-151">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="be80c-151">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="be80c-152">Řetězce ASCII můžete reprezentovat poli bajtů bez znaménka, typ `byte[]` .</span><span class="sxs-lookup"><span data-stu-id="be80c-152">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="be80c-153">Přidáte příponu `B` do řetězcového literálu, který označuje, že se jedná o řetězec ASCII.</span><span class="sxs-lookup"><span data-stu-id="be80c-153">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="be80c-154">Řetězcové literály ASCII používané s poli bajtů podporují stejné řídicí sekvence jako řetězce Unicode, s výjimkou řídicích sekvencí Unicode.</span><span class="sxs-lookup"><span data-stu-id="be80c-154">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="be80c-155">Operátory řetězce</span><span class="sxs-lookup"><span data-stu-id="be80c-155">String Operators</span></span>

<span data-ttu-id="be80c-156">`+`Operátor lze použít k zřetězení řetězců a udržování kompatibility s funkcemi pro zpracování .NET Framework řetězců.</span><span class="sxs-lookup"><span data-stu-id="be80c-156">The `+` operator can be used to concatenate strings, maintaining compatibility with the .NET Framework string handling features.</span></span> <span data-ttu-id="be80c-157">Následující příklad znázorňuje zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="be80c-157">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="be80c-158">String – Třída</span><span class="sxs-lookup"><span data-stu-id="be80c-158">String Class</span></span>

<span data-ttu-id="be80c-159">Vzhledem k tomu, že typ řetězce v jazyce F # je ve skutečnosti .NET Framework `System.String` typ, `System.String` jsou k dispozici všichni členové.</span><span class="sxs-lookup"><span data-stu-id="be80c-159">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="be80c-160">To zahrnuje `+` operátor, který se používá ke zřetězení řetězců, `Length` vlastnost a `Chars` vlastnost, která vrací řetězec jako pole znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="be80c-160">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="be80c-161">Další informace o řetězcích naleznete v tématu `System.String` .</span><span class="sxs-lookup"><span data-stu-id="be80c-161">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="be80c-162">Pomocí `Chars` vlastnosti `System.String` můžete k jednotlivým znakům v řetězci přistupovat zadáním indexu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="be80c-162">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="be80c-163">Řetězec – modul</span><span class="sxs-lookup"><span data-stu-id="be80c-163">String Module</span></span>

<span data-ttu-id="be80c-164">Další funkce pro zpracování řetězců je obsažena v `String` modulu v `FSharp.Core` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="be80c-164">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="be80c-165">Další informace naleznete v tématu [String Module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-stringmodule.html).</span><span class="sxs-lookup"><span data-stu-id="be80c-165">For more information, see [String Module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-stringmodule.html).</span></span>

## <a name="see-also"></a><span data-ttu-id="be80c-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="be80c-166">See also</span></span>

- [<span data-ttu-id="be80c-167">Referenční dokumentace jazyka F #</span><span class="sxs-lookup"><span data-stu-id="be80c-167">F# Language Reference</span></span>](index.md)
