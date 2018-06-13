---
title: Řetězce (F#)
description: "Zjistěte, jak typu 'řetězec' F # představuje neměnné text jako posloupnosti znaků Unicode."
ms.date: 05/16/2016
ms.openlocfilehash: bdd1d1a542e70bcd95fce51e75d0c1ddffceb008
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33564856"
---
# <a name="strings"></a><span data-ttu-id="94439-103">Řetězce</span><span class="sxs-lookup"><span data-stu-id="94439-103">Strings</span></span>

> [!NOTE]
<span data-ttu-id="94439-104">Referenční dokumentace rozhraní API odkazů v tomto článku se dostanete na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="94439-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="94439-105">Referenční dokumentace rozhraní API docs.microsoft.com není dokončena.</span><span class="sxs-lookup"><span data-stu-id="94439-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="94439-106">`string` Typ představuje neměnné text jako posloupnosti znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="94439-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="94439-107">`string` je alias `System.String` v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="94439-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="94439-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="94439-108">Remarks</span></span>
<span data-ttu-id="94439-109">Textové literály jsou odděleny znak dvojité uvozovky (").</span><span class="sxs-lookup"><span data-stu-id="94439-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="94439-110">Znak zpětného lomítka (\) se používá ke kódování některé speciální znaky.</span><span class="sxs-lookup"><span data-stu-id="94439-110">The backslash character (\) is used to encode certain special characters.</span></span> <span data-ttu-id="94439-111">Zpětné lomítko a další znak, který je společně se označují jako *řídicí sekvenci*.</span><span class="sxs-lookup"><span data-stu-id="94439-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="94439-112">Řídicí sekvence v F # řetězec, který v následující tabulce jsou uvedeny literály podporovány.</span><span class="sxs-lookup"><span data-stu-id="94439-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="94439-113">Znak</span><span class="sxs-lookup"><span data-stu-id="94439-113">Character</span></span>|<span data-ttu-id="94439-114">Řídicí sekvence</span><span class="sxs-lookup"><span data-stu-id="94439-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="94439-115">Backspace</span><span class="sxs-lookup"><span data-stu-id="94439-115">Backspace</span></span>|<span data-ttu-id="94439-116">\b</span><span class="sxs-lookup"><span data-stu-id="94439-116">\b</span></span>|
|<span data-ttu-id="94439-117">Nový řádek</span><span class="sxs-lookup"><span data-stu-id="94439-117">Newline</span></span>|<span data-ttu-id="94439-118">\n</span><span class="sxs-lookup"><span data-stu-id="94439-118">\n</span></span>|
|<span data-ttu-id="94439-119">Návrat na začátek řádku</span><span class="sxs-lookup"><span data-stu-id="94439-119">Carriage return</span></span>|<span data-ttu-id="94439-120">\r</span><span class="sxs-lookup"><span data-stu-id="94439-120">\r</span></span>|
|<span data-ttu-id="94439-121">Tabulátor</span><span class="sxs-lookup"><span data-stu-id="94439-121">Tab</span></span>|<span data-ttu-id="94439-122">\t</span><span class="sxs-lookup"><span data-stu-id="94439-122">\t</span></span>|
|<span data-ttu-id="94439-123">Zpětné lomítko</span><span class="sxs-lookup"><span data-stu-id="94439-123">Backslash</span></span>|\\|
|<span data-ttu-id="94439-124">Uvozovky</span><span class="sxs-lookup"><span data-stu-id="94439-124">Quotation mark</span></span>|\"|
|<span data-ttu-id="94439-125">Apostrof</span><span class="sxs-lookup"><span data-stu-id="94439-125">Apostrophe</span></span>|\'|
|<span data-ttu-id="94439-126">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="94439-126">Unicode character</span></span>|<span data-ttu-id="94439-127">\u*XXXX* nebo \U*XXXXXXXX* (kde *X* označuje šestnáctková číslice)</span><span class="sxs-lookup"><span data-stu-id="94439-127">\u*XXXX* or \U*XXXXXXXX* (where *X* indicates a hexadecimal digit)</span></span>|

<span data-ttu-id="94439-128">Pokud před sebou symbolem @, je literál typu verbatim řetězec.</span><span class="sxs-lookup"><span data-stu-id="94439-128">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="94439-129">To znamená, že jsou ignorovány všechny řídicí sekvence, s tím rozdílem, že dva znaky uvozovek se interpretují jako uvozovky jeden znak.</span><span class="sxs-lookup"><span data-stu-id="94439-129">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

<span data-ttu-id="94439-130">Kromě toho může být řetězec uzavřena do uvozovek. Trojitá.</span><span class="sxs-lookup"><span data-stu-id="94439-130">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="94439-131">V takovém případě jsou ignorovány všechny řídicí sekvence, včetně znaků dvojité uvozovky.</span><span class="sxs-lookup"><span data-stu-id="94439-131">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="94439-132">Pokud chcete zadat řetězec, který obsahuje vložený řetězec v uvozovkách, můžete použít buď typu verbatim řetězec nebo řetězec uvozené třemi uvozovkami.</span><span class="sxs-lookup"><span data-stu-id="94439-132">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="94439-133">Pokud používáte řetězec typu verbatim, musíte zadat dva znaky uvozovek udávajících znak jednoduché uvozovky.</span><span class="sxs-lookup"><span data-stu-id="94439-133">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="94439-134">Pokud používáte řetězce uvozené třemi uvozovkami, můžete vytvořit jednoduché uvozovky znaky bez nich při analýze jako konci řetězce.</span><span class="sxs-lookup"><span data-stu-id="94439-134">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="94439-135">Tento postup může být užitečné při práci s XML nebo jiné struktury, které zahrnují uvozovky.</span><span class="sxs-lookup"><span data-stu-id="94439-135">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="94439-136">V kódu jsou podmínky přijaty řetězce, které mají konce řádků a konce řádků se interpretují oznámena jako vložení znaků newline, pokud je znak zpětného lomítka poslední znak před koncem řádku.</span><span class="sxs-lookup"><span data-stu-id="94439-136">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="94439-137">Úvodní mezery na další řádek je ignorována, pokud se používá znak zpětného lomítka.</span><span class="sxs-lookup"><span data-stu-id="94439-137">Leading whitespace on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="94439-138">Následující kód vytvoří řetězec `str1` s hodnotou `"abc\n     def"` řetězec a `str2` s hodnotou `"abcdef"`.</span><span class="sxs-lookup"><span data-stu-id="94439-138">The following code produces a string `str1` that has value `"abc\n     def"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

<span data-ttu-id="94439-139">Pomocí syntaxe pro pole, dostanete jednotlivé znaky v řetězci.</span><span class="sxs-lookup"><span data-stu-id="94439-139">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="94439-140">Výstupem je `b`.</span><span class="sxs-lookup"><span data-stu-id="94439-140">The output is `b`.</span></span>

<span data-ttu-id="94439-141">Nebo můžete rozbalit dílčích řetězců pomocí syntaxe řez pole, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="94439-141">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="94439-142">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="94439-142">The output is as follows.</span></span>

```
abc
def
```

<span data-ttu-id="94439-143">Může představovat ASCII řetězce podle pole bajtů bez znaménka, typ `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="94439-143">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="94439-144">Můžete přidat příponu `B` na řetězcový literál to znamená, že je řetězec ve formátu ASCII.</span><span class="sxs-lookup"><span data-stu-id="94439-144">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="94439-145">Použít s pole bajtů ASCII textové literály podporují stejné řídicí sekvence jako řetězců v kódu Unicode, s výjimkou řídicích sekvencí kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="94439-145">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]
    
## <a name="string-operators"></a><span data-ttu-id="94439-146">Operátory řetězce</span><span class="sxs-lookup"><span data-stu-id="94439-146">String Operators</span></span>
<span data-ttu-id="94439-147">Zřetězení řetězců dvěma způsoby: pomocí `+` operátor nebo pomocí `^` operátor.</span><span class="sxs-lookup"><span data-stu-id="94439-147">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="94439-148">`+` Operátor udržuje kompatibilitu s zpracování funkce řetězce rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="94439-148">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="94439-149">Následující příklad ilustruje zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="94439-149">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]
    
## <a name="string-class"></a><span data-ttu-id="94439-150">Řetězec – třída</span><span class="sxs-lookup"><span data-stu-id="94439-150">String Class</span></span>
<span data-ttu-id="94439-151">Protože je ve skutečnosti rozhraní .NET Framework typ řetězce v jazyce F # `System.String` typ, všechny `System.String` členové jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="94439-151">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="94439-152">To zahrnuje `+` operátor, který slouží ke zřetězení řetězců `Length` vlastnost a `Chars` vlastnost, která vrací řetězec jako pole znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="94439-152">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="94439-153">Další informace o řetězcích najdete v tématu `System.String`.</span><span class="sxs-lookup"><span data-stu-id="94439-153">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="94439-154">Pomocí `Chars` vlastnost `System.String`, dostanete jednotlivé znaky v řetězci zadáním index, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="94439-154">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]
    
## <a name="string-module"></a><span data-ttu-id="94439-155">Řetězec modulu</span><span class="sxs-lookup"><span data-stu-id="94439-155">String Module</span></span>
<span data-ttu-id="94439-156">Další funkce pro zpracování řetězce je součástí `String` modulu v `FSharp.Core` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="94439-156">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="94439-157">Další informace najdete v tématu [Core.String – modul](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="94439-157">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="94439-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="94439-158">See Also</span></span>
[<span data-ttu-id="94439-159">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="94439-159">F# Language Reference</span></span>](index.md)
