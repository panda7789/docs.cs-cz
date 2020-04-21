---
title: Řetězce
description: Zjistěte, jak typ F# 'řetězec' představuje neměnný text jako posloupnost znaků Unicode.
ms.date: 07/05/2019
ms.openlocfilehash: 242a2cefa1cce8995090dddd1d1fd7181e0f5e0c
ms.sourcegitcommit: 465547886a1224a5435c3ac349c805e39ce77706
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/21/2020
ms.locfileid: "81739567"
---
# <a name="strings"></a><span data-ttu-id="ef48e-103">Řetězce</span><span class="sxs-lookup"><span data-stu-id="ef48e-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="ef48e-104">Odkazy na odkazy na odkazy na odkazy na rozhraní API v tomto článku přejdete na msdn.</span><span class="sxs-lookup"><span data-stu-id="ef48e-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="ef48e-105">Odkaz na rozhraní API docs.microsoft.com není dokončen.</span><span class="sxs-lookup"><span data-stu-id="ef48e-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="ef48e-106">Typ `string` představuje neměnný text jako posloupnost znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="ef48e-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="ef48e-107">`string`je alias `System.String` v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef48e-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="ef48e-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ef48e-108">Remarks</span></span>

<span data-ttu-id="ef48e-109">Řetězcové literály jsou odděleny znakem uvozovky (").</span><span class="sxs-lookup"><span data-stu-id="ef48e-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="ef48e-110">Znak zpětného \\ lomítka ( ) se používá ke kódování určitých speciálních znaků.</span><span class="sxs-lookup"><span data-stu-id="ef48e-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="ef48e-111">Zpětné lomítko a další znak společně jsou označovány jako *sekvence escape*.</span><span class="sxs-lookup"><span data-stu-id="ef48e-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="ef48e-112">Sekvence escape podporované v literálech řetězce F# jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="ef48e-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="ef48e-113">Znak</span><span class="sxs-lookup"><span data-stu-id="ef48e-113">Character</span></span>|<span data-ttu-id="ef48e-114">Úniková sekvence</span><span class="sxs-lookup"><span data-stu-id="ef48e-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="ef48e-115">Výstrahy</span><span class="sxs-lookup"><span data-stu-id="ef48e-115">Alert</span></span>|`\a`|
|<span data-ttu-id="ef48e-116">Backspace</span><span class="sxs-lookup"><span data-stu-id="ef48e-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="ef48e-117">Informační kanál formuláře</span><span class="sxs-lookup"><span data-stu-id="ef48e-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="ef48e-118">Newline</span><span class="sxs-lookup"><span data-stu-id="ef48e-118">Newline</span></span>|`\n`|
|<span data-ttu-id="ef48e-119">Návrat na začátek řádku</span><span class="sxs-lookup"><span data-stu-id="ef48e-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="ef48e-120">Karta</span><span class="sxs-lookup"><span data-stu-id="ef48e-120">Tab</span></span>|`\t`|
|<span data-ttu-id="ef48e-121">Vertikální tabulátor</span><span class="sxs-lookup"><span data-stu-id="ef48e-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="ef48e-122">Zpětné lomítko</span><span class="sxs-lookup"><span data-stu-id="ef48e-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="ef48e-123">Uvozovky</span><span class="sxs-lookup"><span data-stu-id="ef48e-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="ef48e-124">Apostrof</span><span class="sxs-lookup"><span data-stu-id="ef48e-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="ef48e-125">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="ef48e-125">Unicode character</span></span>|<span data-ttu-id="ef48e-126">`\DDD`(kde `D` označuje desetinnou číslici; rozsah 000 - 255; například `\231` = "ç")</span><span class="sxs-lookup"><span data-stu-id="ef48e-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="ef48e-127">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="ef48e-127">Unicode character</span></span>|<span data-ttu-id="ef48e-128">`\xHH`(kde `H` označuje šestnáctkovou číslici; rozsah 00 - FF; `\xE7` například = "ç")</span><span class="sxs-lookup"><span data-stu-id="ef48e-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="ef48e-129">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="ef48e-129">Unicode character</span></span>|<span data-ttu-id="ef48e-130">`\uHHHH`(UTF-16) (kde `H` označuje šestnáctkovou číslici; rozsah 0000 - FFFF;  například `\u00E7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="ef48e-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="ef48e-131">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="ef48e-131">Unicode character</span></span>|<span data-ttu-id="ef48e-132">`\U00HHHHHH`(UTF-32) (kde `H` označuje šestnáctkovou číslici; rozsah 000000 - 10FFFF;  například `\U0001F47D` =👽" ")</span><span class="sxs-lookup"><span data-stu-id="ef48e-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="ef48e-133">Escape `\DDD` sekvence je desetinné zápisy, nikoli osmičkové zápisy jako ve většině ostatních jazyků.</span><span class="sxs-lookup"><span data-stu-id="ef48e-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="ef48e-134">Proto číslice `8` `9` a jsou platné a `\032` posloupnost představuje mezeru (U + 0020), vzhledem `\040`k tomu, že stejný bod kódu v osmičkové notaci by .</span><span class="sxs-lookup"><span data-stu-id="ef48e-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="ef48e-135">Omezena na rozsah 0 - 255 (0xFF), `\DDD` `\x` a escape sekvence jsou účinně [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) znakovou sadu, protože to odpovídá první 256 bodů kódu Unicode.</span><span class="sxs-lookup"><span data-stu-id="ef48e-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

## <a name="verbatim-strings"></a><span data-ttu-id="ef48e-136">Doslovné řetězce</span><span class="sxs-lookup"><span data-stu-id="ef48e-136">Verbatim Strings</span></span>

<span data-ttu-id="ef48e-137">Pokud předchází symbol @, literál je doslovný řetězec.</span><span class="sxs-lookup"><span data-stu-id="ef48e-137">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="ef48e-138">To znamená, že všechny sekvence escape jsou ignorovány, s tím rozdílem, že dva znaky uvozovek jsou interpretovány jako jeden znak uvozovky.</span><span class="sxs-lookup"><span data-stu-id="ef48e-138">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

## <a name="triple-quoted-strings"></a><span data-ttu-id="ef48e-139">Trojité citované řetězce</span><span class="sxs-lookup"><span data-stu-id="ef48e-139">Triple Quoted Strings</span></span>

<span data-ttu-id="ef48e-140">Řetězec může být navíc uzavřen trojitými uvozovkami.</span><span class="sxs-lookup"><span data-stu-id="ef48e-140">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="ef48e-141">V tomto případě jsou ignorovány všechny sekvence escape, včetně dvojitých uvozovek znaků.</span><span class="sxs-lookup"><span data-stu-id="ef48e-141">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="ef48e-142">Chcete-li zadat řetězec, který obsahuje vložený řetězec v uvozovkách, můžete použít doslovný řetězec nebo řetězec s trojitým uvozovkami.</span><span class="sxs-lookup"><span data-stu-id="ef48e-142">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="ef48e-143">Pokud používáte doslovný řetězec, musíte zadat dva znaky uvozovek, které označují jeden znak uvozovky.</span><span class="sxs-lookup"><span data-stu-id="ef48e-143">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="ef48e-144">Pokud používáte řetězec s trojitým uvozovkami, můžete použít znaky jednoduchých uvozovek, aniž by byly analyzovány jako konec řetězce.</span><span class="sxs-lookup"><span data-stu-id="ef48e-144">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="ef48e-145">Tato technika může být užitečná při práci s XML nebo jinými strukturami, které obsahují vložené uvozovky.</span><span class="sxs-lookup"><span data-stu-id="ef48e-145">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="ef48e-146">V kódu jsou přijaty řetězce, které mají konce řádků a konce řádků jsou interpretovány doslova jako nové řádky, pokud znak zpětného lomítka není posledním znakem před zalomení řádku.</span><span class="sxs-lookup"><span data-stu-id="ef48e-146">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="ef48e-147">Úvodní prázdné místo na dalším řádku je při použití znaku zpětného lomítka ignorováno.</span><span class="sxs-lookup"><span data-stu-id="ef48e-147">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="ef48e-148">Následující kód vytvoří `str1` řetězec, který `"abc\ndef"` má `str2` hodnotu `"abcdef"`a řetězec, který má hodnotu .</span><span class="sxs-lookup"><span data-stu-id="ef48e-148">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

## <a name="string-indexing-and-slicing"></a><span data-ttu-id="ef48e-149">Indexování řetězců a krájení</span><span class="sxs-lookup"><span data-stu-id="ef48e-149">String Indexing and Slicing</span></span>

<span data-ttu-id="ef48e-150">K jednotlivým znakům v řetězci můžete přistupovat pomocí syntaxe podobné poli, a to následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="ef48e-150">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="ef48e-151">Výstup je `b`.</span><span class="sxs-lookup"><span data-stu-id="ef48e-151">The output is `b`.</span></span>

<span data-ttu-id="ef48e-152">Nebo můžete extrahovat podřetězce pomocí syntaxe řezu pole, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="ef48e-152">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="ef48e-153">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="ef48e-153">The output is as follows.</span></span>

```console
abc
def
```

<span data-ttu-id="ef48e-154">Řetězce ASCII můžete reprezentovat podle polí nepodepsaných bajtů, zadejte `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="ef48e-154">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="ef48e-155">Přidáte příponu `B` do literálu řetězce označující, že se jedná o řetězec ASCII.</span><span class="sxs-lookup"><span data-stu-id="ef48e-155">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="ef48e-156">Literály řetězce ASCII používané s bajtovými poli podporují stejné sekvence escape jako řetězce Unicode, s výjimkou řídicích sekvencí Unicode.</span><span class="sxs-lookup"><span data-stu-id="ef48e-156">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="ef48e-157">Operátory řetězce</span><span class="sxs-lookup"><span data-stu-id="ef48e-157">String Operators</span></span>

<span data-ttu-id="ef48e-158">Operátor `+` lze použít ke zřetězení řetězců, zachování kompatibility s funkcemi zpracování řetězce rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ef48e-158">The `+` operator can be used to concatenate strings, maintaining compatibility with the .NET Framework string handling features.</span></span> <span data-ttu-id="ef48e-159">Následující příklad ilustruje zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="ef48e-159">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="ef48e-160">Třída řetězce</span><span class="sxs-lookup"><span data-stu-id="ef48e-160">String Class</span></span>

<span data-ttu-id="ef48e-161">Vzhledem k tomu, že typ řetězce `System.String` v F# je ve skutečnosti typ rozhraní .NET Framework, jsou k dispozici všechny `System.String` členy.</span><span class="sxs-lookup"><span data-stu-id="ef48e-161">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="ef48e-162">To zahrnuje `+` operátor, který se používá ke zřetězení řetězců, `Length` vlastnosti a `Chars` vlastnosti, která vrací řetězec jako pole znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="ef48e-162">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="ef48e-163">Další informace o řetězcích `System.String`naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="ef48e-163">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="ef48e-164">Pomocí vlastnosti `Chars` `System.String`, můžete přistupovat k jednotlivým znakům v řetězci zadáním indexu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="ef48e-164">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="ef48e-165">Modul řetězce</span><span class="sxs-lookup"><span data-stu-id="ef48e-165">String Module</span></span>

<span data-ttu-id="ef48e-166">Další funkce pro zpracování řetězců `String` je součástí `FSharp.Core` modulu v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ef48e-166">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="ef48e-167">Další informace naleznete v tématu [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="ef48e-167">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="ef48e-168">Viz také</span><span class="sxs-lookup"><span data-stu-id="ef48e-168">See also</span></span>

- [<span data-ttu-id="ef48e-169">Referenční příručka jazyka F#</span><span class="sxs-lookup"><span data-stu-id="ef48e-169">F# Language Reference</span></span>](index.md)
