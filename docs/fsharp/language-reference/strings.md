---
title: Řetězce (F#)
description: 'Zjistěte, jak typ "řetězec" jazyka F # představuje neměnné text jako posloupnost znaků Unicode.'
ms.date: 05/16/2016
ms.openlocfilehash: 21971602093bc84b0df47d4ae46a14fb936c28bb
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43799340"
---
# <a name="strings"></a><span data-ttu-id="a36ca-103">Řetězce</span><span class="sxs-lookup"><span data-stu-id="a36ca-103">Strings</span></span>

> [!NOTE]
<span data-ttu-id="a36ca-104">Rozhraní API referenčních odkazů v tomto článku se dostanete na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="a36ca-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="a36ca-105">Reference k rozhraní API webu docs.microsoft.com není dokončena.</span><span class="sxs-lookup"><span data-stu-id="a36ca-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="a36ca-106">`string` Typ představuje neměnné text jako posloupnost znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="a36ca-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="a36ca-107">`string` je alias pro `System.String` v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a36ca-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="a36ca-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a36ca-108">Remarks</span></span>

<span data-ttu-id="a36ca-109">Řetězcové literály jsou oddělené znakem uvozovky (").</span><span class="sxs-lookup"><span data-stu-id="a36ca-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="a36ca-110">Znak zpětného lomítka ( \\ ) slouží ke kódování některé speciální znaky.</span><span class="sxs-lookup"><span data-stu-id="a36ca-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="a36ca-111">Zpětné lomítko a další znak společně se nazývají *sekvence escape*.</span><span class="sxs-lookup"><span data-stu-id="a36ca-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="a36ca-112">Řídicí sekvence, které jsou podporované v F # řetězec, který literály jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="a36ca-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="a36ca-113">Znak</span><span class="sxs-lookup"><span data-stu-id="a36ca-113">Character</span></span>|<span data-ttu-id="a36ca-114">Řídicí sekvence</span><span class="sxs-lookup"><span data-stu-id="a36ca-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="a36ca-115">Backspace</span><span class="sxs-lookup"><span data-stu-id="a36ca-115">Backspace</span></span>|`\b`|
|<span data-ttu-id="a36ca-116">nový řádek</span><span class="sxs-lookup"><span data-stu-id="a36ca-116">Newline</span></span>|`\n`|
|<span data-ttu-id="a36ca-117">Návrat na začátek řádku</span><span class="sxs-lookup"><span data-stu-id="a36ca-117">Carriage return</span></span>|`\r`|
|<span data-ttu-id="a36ca-118">Tabulátor</span><span class="sxs-lookup"><span data-stu-id="a36ca-118">Tab</span></span>|`\t`|
|<span data-ttu-id="a36ca-119">Zpětné lomítko</span><span class="sxs-lookup"><span data-stu-id="a36ca-119">Backslash</span></span>|`\\`|
|<span data-ttu-id="a36ca-120">Znak uvozovek</span><span class="sxs-lookup"><span data-stu-id="a36ca-120">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="a36ca-121">Apostrof</span><span class="sxs-lookup"><span data-stu-id="a36ca-121">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="a36ca-122">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="a36ca-122">Unicode character</span></span>|<span data-ttu-id="a36ca-123">`\uXXXX` nebo `\UXXXX` (kde `X` označuje šestnáctková číslice)</span><span class="sxs-lookup"><span data-stu-id="a36ca-123">`\uXXXX` or `\UXXXX` (where `X` indicates a hexadecimal digit)</span></span>|

<span data-ttu-id="a36ca-124">Předchází-li symbolem @, je literál doslovný řetězec.</span><span class="sxs-lookup"><span data-stu-id="a36ca-124">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="a36ca-125">To znamená, že jsou ignorovány všechny řídicí sekvence, s tím rozdílem, že jsou dva znaky uvozovek interpretován jako znak jeden znak uvozovek.</span><span class="sxs-lookup"><span data-stu-id="a36ca-125">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

<span data-ttu-id="a36ca-126">Kromě toho řetězec může být uzavřená v trojité uvozovky.</span><span class="sxs-lookup"><span data-stu-id="a36ca-126">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="a36ca-127">V tomto případě jsou ignorovány všechny řídicí sekvence, včetně dvojité uvozovky znaků.</span><span class="sxs-lookup"><span data-stu-id="a36ca-127">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="a36ca-128">Pokud chcete zadat řetězec, který obsahuje vložený řetězec v uvozovkách, můžete použít buď doslovný řetězec nebo řetězce uvozené třemi uvozovkami.</span><span class="sxs-lookup"><span data-stu-id="a36ca-128">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="a36ca-129">Pokud používáte doslovný řetězec, musíte zadat dva znaky uvozovek označuje znak jednoduché uvozovky.</span><span class="sxs-lookup"><span data-stu-id="a36ca-129">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="a36ca-130">Pokud používáte řetězce uvozené třemi uvozovkami, můžete použít jednoduché uvozovky znaků bez je analyzován jako konec řetězce.</span><span class="sxs-lookup"><span data-stu-id="a36ca-130">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="a36ca-131">Tato technika může být užitečné při práci s XML nebo jiných struktur, které zahrnují uvozovky.</span><span class="sxs-lookup"><span data-stu-id="a36ca-131">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="a36ca-132">V kódu jsou přijaty řetězce, které mají konce řádků a zalomení řádků jsou interpretovány literálně jako vložení znaků newline, není-li znak zpětného lomítka před koncem řádku poslední znak.</span><span class="sxs-lookup"><span data-stu-id="a36ca-132">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="a36ca-133">Úvodních mezer na dalším řádku je ignorován, pokud se používá znak zpětného lomítka.</span><span class="sxs-lookup"><span data-stu-id="a36ca-133">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="a36ca-134">Následující kód vytvoří řetězec `str1` , která má hodnotu `"abc\ndef"` a řetězec `str2` , která má hodnotu `"abcdef"`.</span><span class="sxs-lookup"><span data-stu-id="a36ca-134">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

<span data-ttu-id="a36ca-135">Jednotlivé znaky v řetězci můžete přistupovat pomocí syntaxe jako pole.</span><span class="sxs-lookup"><span data-stu-id="a36ca-135">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="a36ca-136">Výstup je `b`.</span><span class="sxs-lookup"><span data-stu-id="a36ca-136">The output is `b`.</span></span>

<span data-ttu-id="a36ca-137">Nebo extrahujete dílčí řetězce pomocí syntaxe řez pole, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a36ca-137">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="a36ca-138">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="a36ca-138">The output is as follows.</span></span>

```
abc
def
```

<span data-ttu-id="a36ca-139">Může představovat řetězce ASCII pomocí polí bajtů bez znaménka, typ `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="a36ca-139">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="a36ca-140">Přidat příponu `B` na řetězcový literál, že je řetězec ve formátu ASCII.</span><span class="sxs-lookup"><span data-stu-id="a36ca-140">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="a36ca-141">Použít s pole bajtů ASCII řetězcové literály podporují stejné sekvence escape jako řetězce Unicode, s výjimkou řídicí sekvence Unicode.</span><span class="sxs-lookup"><span data-stu-id="a36ca-141">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="a36ca-142">Operátory řetězce</span><span class="sxs-lookup"><span data-stu-id="a36ca-142">String Operators</span></span>

<span data-ttu-id="a36ca-143">Existují dva způsoby, jak zřetězení řetězců: pomocí `+` operátor nebo s použitím `^` operátor.</span><span class="sxs-lookup"><span data-stu-id="a36ca-143">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="a36ca-144">`+` Operátor udržuje kompatibilitu s zpracování funkce rozhraní .NET Framework řetězce.</span><span class="sxs-lookup"><span data-stu-id="a36ca-144">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="a36ca-145">Následující příklad ukazuje zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="a36ca-145">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="a36ca-146">Třída String</span><span class="sxs-lookup"><span data-stu-id="a36ca-146">String Class</span></span>

<span data-ttu-id="a36ca-147">Protože typ řetězce v jazyce F # je ve skutečnosti na rozhraní .NET Framework `System.String` typ, všechny `System.String` členy jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a36ca-147">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="a36ca-148">Jedná se o `+` operátor, který slouží k řetězení řetězců, `Length` vlastnost a `Chars` vlastnost, která vrací řetězec jako pole znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="a36ca-148">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="a36ca-149">Další informace o řetězcích naleznete v tématu `System.String`.</span><span class="sxs-lookup"><span data-stu-id="a36ca-149">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="a36ca-150">S použitím `Chars` vlastnost `System.String`, dostanete jednotlivých znaků v řetězci tak, že zadáte indexu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="a36ca-150">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="a36ca-151">Řetězec modulu</span><span class="sxs-lookup"><span data-stu-id="a36ca-151">String Module</span></span>

<span data-ttu-id="a36ca-152">Další funkce pro manipulaci s řetězci jsou součástí `String` v modulu `FSharp.Core` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="a36ca-152">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="a36ca-153">Další informace najdete v tématu [Core.String – modul](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="a36ca-153">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="a36ca-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a36ca-154">See also</span></span>

- [<span data-ttu-id="a36ca-155">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="a36ca-155">F# Language Reference</span></span>](index.md)
