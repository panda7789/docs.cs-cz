---
title: Řetězce
description: Zjistěte, jak F# typ "řetězec" představuje neměnné text jako posloupnost znaků Unicode.
ms.date: 07/05/2019
ms.openlocfilehash: ec895723cc6d21a701a27b5d70d053bb681ce2b3
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67660599"
---
# <a name="strings"></a><span data-ttu-id="032d6-103">Řetězce</span><span class="sxs-lookup"><span data-stu-id="032d6-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="032d6-104">Rozhraní API referenčních odkazů v tomto článku se dostanete na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="032d6-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="032d6-105">Reference k rozhraní API webu docs.microsoft.com není dokončena.</span><span class="sxs-lookup"><span data-stu-id="032d6-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="032d6-106">`string` Typ představuje neměnné text jako posloupnost znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="032d6-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="032d6-107">`string` je alias pro `System.String` v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="032d6-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="032d6-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="032d6-108">Remarks</span></span>

<span data-ttu-id="032d6-109">Řetězcové literály jsou oddělené znakem uvozovky (").</span><span class="sxs-lookup"><span data-stu-id="032d6-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="032d6-110">Znak zpětného lomítka ( \\ ) slouží ke kódování některé speciální znaky.</span><span class="sxs-lookup"><span data-stu-id="032d6-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="032d6-111">Zpětné lomítko a další znak společně se nazývají *sekvence escape*.</span><span class="sxs-lookup"><span data-stu-id="032d6-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="032d6-112">Řídicí sekvence, které jsou podporovány v F# řetězcové literály jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="032d6-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="032d6-113">Znak</span><span class="sxs-lookup"><span data-stu-id="032d6-113">Character</span></span>|<span data-ttu-id="032d6-114">Řídicí sekvence</span><span class="sxs-lookup"><span data-stu-id="032d6-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="032d6-115">Výstrahy</span><span class="sxs-lookup"><span data-stu-id="032d6-115">Alert</span></span>|`\a`|
|<span data-ttu-id="032d6-116">Backspace</span><span class="sxs-lookup"><span data-stu-id="032d6-116">Backspace</span></span>|`\b`|
|<span data-ttu-id="032d6-117">Posun strany</span><span class="sxs-lookup"><span data-stu-id="032d6-117">Form feed</span></span>|`\f`|
|<span data-ttu-id="032d6-118">nový řádek</span><span class="sxs-lookup"><span data-stu-id="032d6-118">Newline</span></span>|`\n`|
|<span data-ttu-id="032d6-119">Návrat na začátek řádku</span><span class="sxs-lookup"><span data-stu-id="032d6-119">Carriage return</span></span>|`\r`|
|<span data-ttu-id="032d6-120">Karta</span><span class="sxs-lookup"><span data-stu-id="032d6-120">Tab</span></span>|`\t`|
|<span data-ttu-id="032d6-121">Vertikální tabulátor</span><span class="sxs-lookup"><span data-stu-id="032d6-121">Vertical tab</span></span>|`\v`|
|<span data-ttu-id="032d6-122">Zpětné lomítko</span><span class="sxs-lookup"><span data-stu-id="032d6-122">Backslash</span></span>|`\\`|
|<span data-ttu-id="032d6-123">Znak uvozovek</span><span class="sxs-lookup"><span data-stu-id="032d6-123">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="032d6-124">Apostrof</span><span class="sxs-lookup"><span data-stu-id="032d6-124">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="032d6-125">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="032d6-125">Unicode character</span></span>|<span data-ttu-id="032d6-126">`\DDD` (kde `D` označuje desítkové číslice; rozsah 000 - 255, například `\231` = "ç")</span><span class="sxs-lookup"><span data-stu-id="032d6-126">`\DDD` (where `D` indicates a decimal digit; range of 000 - 255; for example, `\231` = "ç")</span></span>|
|<span data-ttu-id="032d6-127">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="032d6-127">Unicode character</span></span>|<span data-ttu-id="032d6-128">`\xHH` (kde `H` označuje šestnáctková číslice; rozsahu 00 - FF; například `\xE7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="032d6-128">`\xHH` (where `H` indicates a hexadecimal digit; range of 00 - FF; for example, `\xE7` = "ç")</span></span>|
|<span data-ttu-id="032d6-129">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="032d6-129">Unicode character</span></span>|<span data-ttu-id="032d6-130">`\uHHHH` (UTF-16) (kde `H` označuje šestnáctková číslice; rozsah 0000 - FFFF;  například `\u00E7` = "ç")</span><span class="sxs-lookup"><span data-stu-id="032d6-130">`\uHHHH` (UTF-16) (where `H` indicates a hexadecimal digit; range of 0000 - FFFF;  for example, `\u00E7` = "ç")</span></span>|
|<span data-ttu-id="032d6-131">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="032d6-131">Unicode character</span></span>|<span data-ttu-id="032d6-132">`\U00HHHHHH` (UTF-32) (kde `H` označuje šestnáctková číslice; rozsah 000000 - 10FFFF.;  například `\U0001F47D` = "👽")</span><span class="sxs-lookup"><span data-stu-id="032d6-132">`\U00HHHHHH` (UTF-32) (where `H` indicates a hexadecimal digit; range of 000000 - 10FFFF;  for example, `\U0001F47D` = "👽")</span></span>|

> [!IMPORTANT]
> <span data-ttu-id="032d6-133">`\DDD` Řídicí sekvence je desítkový zápis, nikoli osmičkové soustavě stejně jako v většina jiných jazycích.</span><span class="sxs-lookup"><span data-stu-id="032d6-133">The `\DDD` escape sequence is decimal notation, not octal notation like in most other languages.</span></span> <span data-ttu-id="032d6-134">Proto číslic `8` a `9` jsou platné a sekvencí `\032` představuje mezery (U + 0020), zatímco by tento stejný bod kódu v osmičkové soustavě `\040`.</span><span class="sxs-lookup"><span data-stu-id="032d6-134">Therefore, digits `8` and `9` are valid, and a sequence of `\032` represents a space (U+0020), whereas that same code point in octal notation would be `\040`.</span></span>

> [!NOTE]
> <span data-ttu-id="032d6-135">Je omezené na rozsah 0 – 255 (0xFF) `\DDD` a `\x` řídicí sekvence jsou účinně [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) znaková sada, protože odpovídající prvních 256 kódové body sady Unicode.</span><span class="sxs-lookup"><span data-stu-id="032d6-135">Being constrained to a range of 0 - 255 (0xFF), the `\DDD` and `\x` escape sequences are effectively the [ISO-8859-1](https://en.wikipedia.org/wiki/ISO/IEC_8859-1#Code_page_layout) character set, since that matches the first 256 Unicode code points.</span></span>

<span data-ttu-id="032d6-136">Předchází-li symbolem @, je literál doslovný řetězec.</span><span class="sxs-lookup"><span data-stu-id="032d6-136">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="032d6-137">To znamená, že jsou ignorovány všechny řídicí sekvence, s tím rozdílem, že jsou dva znaky uvozovek interpretován jako znak jeden znak uvozovek.</span><span class="sxs-lookup"><span data-stu-id="032d6-137">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

<span data-ttu-id="032d6-138">Kromě toho řetězec může být uzavřená v trojité uvozovky.</span><span class="sxs-lookup"><span data-stu-id="032d6-138">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="032d6-139">V tomto případě jsou ignorovány všechny řídicí sekvence, včetně dvojité uvozovky znaků.</span><span class="sxs-lookup"><span data-stu-id="032d6-139">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="032d6-140">Pokud chcete zadat řetězec, který obsahuje vložený řetězec v uvozovkách, můžete použít buď doslovný řetězec nebo řetězce uvozené třemi uvozovkami.</span><span class="sxs-lookup"><span data-stu-id="032d6-140">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="032d6-141">Pokud používáte doslovný řetězec, musíte zadat dva znaky uvozovek označuje znak jednoduché uvozovky.</span><span class="sxs-lookup"><span data-stu-id="032d6-141">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="032d6-142">Pokud používáte řetězce uvozené třemi uvozovkami, můžete použít jednoduché uvozovky znaků bez je analyzován jako konec řetězce.</span><span class="sxs-lookup"><span data-stu-id="032d6-142">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="032d6-143">Tato technika může být užitečné při práci s XML nebo jiných struktur, které zahrnují uvozovky.</span><span class="sxs-lookup"><span data-stu-id="032d6-143">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="032d6-144">V kódu jsou přijaty řetězce, které mají konce řádků a zalomení řádků jsou interpretovány literálně jako vložení znaků newline, není-li znak zpětného lomítka před koncem řádku poslední znak.</span><span class="sxs-lookup"><span data-stu-id="032d6-144">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="032d6-145">Úvodních mezer na dalším řádku je ignorován, pokud se používá znak zpětného lomítka.</span><span class="sxs-lookup"><span data-stu-id="032d6-145">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="032d6-146">Následující kód vytvoří řetězec `str1` , která má hodnotu `"abc\ndef"` a řetězec `str2` , která má hodnotu `"abcdef"`.</span><span class="sxs-lookup"><span data-stu-id="032d6-146">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

<span data-ttu-id="032d6-147">Jednotlivé znaky v řetězci můžete přistupovat pomocí syntaxe jako pole.</span><span class="sxs-lookup"><span data-stu-id="032d6-147">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="032d6-148">Výstup je `b`.</span><span class="sxs-lookup"><span data-stu-id="032d6-148">The output is `b`.</span></span>

<span data-ttu-id="032d6-149">Nebo extrahujete dílčí řetězce pomocí syntaxe řez pole, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="032d6-149">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="032d6-150">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="032d6-150">The output is as follows.</span></span>

```
abc
def
```

<span data-ttu-id="032d6-151">Může představovat řetězce ASCII pomocí polí bajtů bez znaménka, typ `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="032d6-151">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="032d6-152">Přidat příponu `B` na řetězcový literál, že je řetězec ve formátu ASCII.</span><span class="sxs-lookup"><span data-stu-id="032d6-152">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="032d6-153">Použít s pole bajtů ASCII řetězcové literály podporují stejné sekvence escape jako řetězce Unicode, s výjimkou řídicí sekvence Unicode.</span><span class="sxs-lookup"><span data-stu-id="032d6-153">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="032d6-154">Operátory řetězce</span><span class="sxs-lookup"><span data-stu-id="032d6-154">String Operators</span></span>

<span data-ttu-id="032d6-155">Existují dva způsoby, jak zřetězení řetězců: pomocí `+` operátor nebo s použitím `^` operátor.</span><span class="sxs-lookup"><span data-stu-id="032d6-155">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="032d6-156">`+` Operátor udržuje kompatibilitu s zpracování funkce rozhraní .NET Framework řetězce.</span><span class="sxs-lookup"><span data-stu-id="032d6-156">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="032d6-157">Následující příklad ukazuje zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="032d6-157">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="032d6-158">Třída String</span><span class="sxs-lookup"><span data-stu-id="032d6-158">String Class</span></span>

<span data-ttu-id="032d6-159">Protože typ řetězce v F# je ve skutečnosti na rozhraní .NET Framework `System.String` typ, všechny `System.String` členy jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="032d6-159">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="032d6-160">Jedná se o `+` operátor, který slouží k řetězení řetězců, `Length` vlastnost a `Chars` vlastnost, která vrací řetězec jako pole znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="032d6-160">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="032d6-161">Další informace o řetězcích naleznete v tématu `System.String`.</span><span class="sxs-lookup"><span data-stu-id="032d6-161">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="032d6-162">S použitím `Chars` vlastnost `System.String`, dostanete jednotlivých znaků v řetězci tak, že zadáte indexu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="032d6-162">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="032d6-163">Řetězec modulu</span><span class="sxs-lookup"><span data-stu-id="032d6-163">String Module</span></span>

<span data-ttu-id="032d6-164">Další funkce pro manipulaci s řetězci jsou součástí `String` v modulu `FSharp.Core` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="032d6-164">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="032d6-165">Další informace najdete v tématu [Core.String – modul](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="032d6-165">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="032d6-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="032d6-166">See also</span></span>

- [<span data-ttu-id="032d6-167">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="032d6-167">F# Language Reference</span></span>](index.md)
