---
title: Řetězce
description: Zjistěte, jak F# typ "řetězec" představuje neměnné text jako posloupnost znaků Unicode.
ms.date: 06/28/2019
ms.openlocfilehash: 8bd7a65a8d8e9e6a2d3930cd1fc9e800342d9a18
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2019
ms.locfileid: "67487774"
---
# <a name="strings"></a><span data-ttu-id="77b37-103">Řetězce</span><span class="sxs-lookup"><span data-stu-id="77b37-103">Strings</span></span>

> [!NOTE]
> <span data-ttu-id="77b37-104">Rozhraní API referenčních odkazů v tomto článku se dostanete na webu MSDN.</span><span class="sxs-lookup"><span data-stu-id="77b37-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="77b37-105">Reference k rozhraní API webu docs.microsoft.com není dokončena.</span><span class="sxs-lookup"><span data-stu-id="77b37-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="77b37-106">`string` Typ představuje neměnné text jako posloupnost znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="77b37-106">The `string` type represents immutable text as a sequence of Unicode characters.</span></span> <span data-ttu-id="77b37-107">`string` je alias pro `System.String` v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="77b37-107">`string` is an alias for `System.String` in the .NET Framework.</span></span>

## <a name="remarks"></a><span data-ttu-id="77b37-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="77b37-108">Remarks</span></span>

<span data-ttu-id="77b37-109">Řetězcové literály jsou oddělené znakem uvozovky (").</span><span class="sxs-lookup"><span data-stu-id="77b37-109">String literals are delimited by the quotation mark (") character.</span></span> <span data-ttu-id="77b37-110">Znak zpětného lomítka ( \\ ) slouží ke kódování některé speciální znaky.</span><span class="sxs-lookup"><span data-stu-id="77b37-110">The backslash character ( \\ ) is used to encode certain special characters.</span></span> <span data-ttu-id="77b37-111">Zpětné lomítko a další znak společně se nazývají *sekvence escape*.</span><span class="sxs-lookup"><span data-stu-id="77b37-111">The backslash and the next character together are known as an *escape sequence*.</span></span> <span data-ttu-id="77b37-112">Řídicí sekvence, které jsou podporovány v F# řetězcové literály jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="77b37-112">Escape sequences supported in F# string literals are shown in the following table.</span></span>

|<span data-ttu-id="77b37-113">Znak</span><span class="sxs-lookup"><span data-stu-id="77b37-113">Character</span></span>|<span data-ttu-id="77b37-114">Řídicí sekvence</span><span class="sxs-lookup"><span data-stu-id="77b37-114">Escape sequence</span></span>|
|---------|---------------|
|<span data-ttu-id="77b37-115">Backspace</span><span class="sxs-lookup"><span data-stu-id="77b37-115">Backspace</span></span>|`\b`|
|<span data-ttu-id="77b37-116">nový řádek</span><span class="sxs-lookup"><span data-stu-id="77b37-116">Newline</span></span>|`\n`|
|<span data-ttu-id="77b37-117">Návrat na začátek řádku</span><span class="sxs-lookup"><span data-stu-id="77b37-117">Carriage return</span></span>|`\r`|
|<span data-ttu-id="77b37-118">Karta</span><span class="sxs-lookup"><span data-stu-id="77b37-118">Tab</span></span>|`\t`|
|<span data-ttu-id="77b37-119">Zpětné lomítko</span><span class="sxs-lookup"><span data-stu-id="77b37-119">Backslash</span></span>|`\\`|
|<span data-ttu-id="77b37-120">Znak uvozovek</span><span class="sxs-lookup"><span data-stu-id="77b37-120">Quotation mark</span></span>|`\"`|
|<span data-ttu-id="77b37-121">Apostrof</span><span class="sxs-lookup"><span data-stu-id="77b37-121">Apostrophe</span></span>|`\'`|
|<span data-ttu-id="77b37-122">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="77b37-122">Unicode character</span></span>|<span data-ttu-id="77b37-123">`\uXXXX` (UTF-16) nebo `\U00XXXXXX` (UTF-32) (kde `X` označuje šestnáctková číslice)</span><span class="sxs-lookup"><span data-stu-id="77b37-123">`\uXXXX` (UTF-16) or `\U00XXXXXX` (UTF-32) (where `X` indicates a hexadecimal digit)</span></span>|

<span data-ttu-id="77b37-124">Předchází-li symbolem @, je literál doslovný řetězec.</span><span class="sxs-lookup"><span data-stu-id="77b37-124">If preceded by the @ symbol, the literal is a verbatim string.</span></span> <span data-ttu-id="77b37-125">To znamená, že jsou ignorovány všechny řídicí sekvence, s tím rozdílem, že jsou dva znaky uvozovek interpretován jako znak jeden znak uvozovek.</span><span class="sxs-lookup"><span data-stu-id="77b37-125">This means that any escape sequences are ignored, except that two quotation mark characters are interpreted as one quotation mark character.</span></span>

<span data-ttu-id="77b37-126">Kromě toho řetězec může být uzavřená v trojité uvozovky.</span><span class="sxs-lookup"><span data-stu-id="77b37-126">Additionally, a string may be enclosed by triple quotes.</span></span> <span data-ttu-id="77b37-127">V tomto případě jsou ignorovány všechny řídicí sekvence, včetně dvojité uvozovky znaků.</span><span class="sxs-lookup"><span data-stu-id="77b37-127">In this case, all escape sequences are ignored, including double quotation mark characters.</span></span> <span data-ttu-id="77b37-128">Pokud chcete zadat řetězec, který obsahuje vložený řetězec v uvozovkách, můžete použít buď doslovný řetězec nebo řetězce uvozené třemi uvozovkami.</span><span class="sxs-lookup"><span data-stu-id="77b37-128">To specify a string that contains an embedded quoted string, you can either use a verbatim string or a triple-quoted string.</span></span> <span data-ttu-id="77b37-129">Pokud používáte doslovný řetězec, musíte zadat dva znaky uvozovek označuje znak jednoduché uvozovky.</span><span class="sxs-lookup"><span data-stu-id="77b37-129">If you use a verbatim string, you  must specify two quotation mark characters to indicate a single quotation mark character.</span></span> <span data-ttu-id="77b37-130">Pokud používáte řetězce uvozené třemi uvozovkami, můžete použít jednoduché uvozovky znaků bez je analyzován jako konec řetězce.</span><span class="sxs-lookup"><span data-stu-id="77b37-130">If you use a triple-quoted string, you can use the single quotation mark characters without them being parsed as the end of the string.</span></span> <span data-ttu-id="77b37-131">Tato technika může být užitečné při práci s XML nebo jiných struktur, které zahrnují uvozovky.</span><span class="sxs-lookup"><span data-stu-id="77b37-131">This technique can be useful when you work with XML or other structures that include embedded quotation marks.</span></span>

```fsharp
// Using a verbatim string
let xmlFragment1 = @"<book author=""Milton, John"" title=""Paradise Lost"">"

// Using a triple-quoted string
let xmlFragment2 = """<book author="Milton, John" title="Paradise Lost">"""
```

<span data-ttu-id="77b37-132">V kódu jsou přijaty řetězce, které mají konce řádků a zalomení řádků jsou interpretovány literálně jako vložení znaků newline, není-li znak zpětného lomítka před koncem řádku poslední znak.</span><span class="sxs-lookup"><span data-stu-id="77b37-132">In code, strings that have line breaks are accepted and the line breaks are interpreted literally as newlines, unless a backslash character is the last character before the line break.</span></span> <span data-ttu-id="77b37-133">Úvodních mezer na dalším řádku je ignorován, pokud se používá znak zpětného lomítka.</span><span class="sxs-lookup"><span data-stu-id="77b37-133">Leading white space on the next line is ignored when the backslash character is used.</span></span> <span data-ttu-id="77b37-134">Následující kód vytvoří řetězec `str1` , která má hodnotu `"abc\ndef"` a řetězec `str2` , která má hodnotu `"abcdef"`.</span><span class="sxs-lookup"><span data-stu-id="77b37-134">The following code produces a string `str1` that has value `"abc\ndef"` and a string `str2` that has value `"abcdef"`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1001.fs)]

<span data-ttu-id="77b37-135">Jednotlivé znaky v řetězci můžete přistupovat pomocí syntaxe jako pole.</span><span class="sxs-lookup"><span data-stu-id="77b37-135">You can access individual characters in a string by using array-like syntax, as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1002.fs)]

<span data-ttu-id="77b37-136">Výstup je `b`.</span><span class="sxs-lookup"><span data-stu-id="77b37-136">The output is `b`.</span></span>

<span data-ttu-id="77b37-137">Nebo extrahujete dílčí řetězce pomocí syntaxe řez pole, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="77b37-137">Or you can extract substrings by using array slice syntax, as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1003.fs)]

<span data-ttu-id="77b37-138">Výstup je následující.</span><span class="sxs-lookup"><span data-stu-id="77b37-138">The output is as follows.</span></span>

```
abc
def
```

<span data-ttu-id="77b37-139">Může představovat řetězce ASCII pomocí polí bajtů bez znaménka, typ `byte[]`.</span><span class="sxs-lookup"><span data-stu-id="77b37-139">You can represent ASCII strings by arrays of unsigned bytes, type `byte[]`.</span></span> <span data-ttu-id="77b37-140">Přidat příponu `B` na řetězcový literál, že je řetězec ve formátu ASCII.</span><span class="sxs-lookup"><span data-stu-id="77b37-140">You add the suffix `B` to a string literal to indicate that it is an ASCII string.</span></span> <span data-ttu-id="77b37-141">Použít s pole bajtů ASCII řetězcové literály podporují stejné sekvence escape jako řetězce Unicode, s výjimkou řídicí sekvence Unicode.</span><span class="sxs-lookup"><span data-stu-id="77b37-141">ASCII string literals used with byte arrays support the same escape sequences as Unicode strings, except for the Unicode escape sequences.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1004.fs)]

## <a name="string-operators"></a><span data-ttu-id="77b37-142">Operátory řetězce</span><span class="sxs-lookup"><span data-stu-id="77b37-142">String Operators</span></span>

<span data-ttu-id="77b37-143">Existují dva způsoby, jak zřetězení řetězců: pomocí `+` operátor nebo s použitím `^` operátor.</span><span class="sxs-lookup"><span data-stu-id="77b37-143">There are two ways to concatenate strings: by using the `+` operator or by using the `^` operator.</span></span> <span data-ttu-id="77b37-144">`+` Operátor udržuje kompatibilitu s zpracování funkce rozhraní .NET Framework řetězce.</span><span class="sxs-lookup"><span data-stu-id="77b37-144">The `+` operator maintains compatibility with the .NET Framework string handling features.</span></span>

<span data-ttu-id="77b37-145">Následující příklad ukazuje zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="77b37-145">The following example illustrates string concatenation.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1006.fs)]

## <a name="string-class"></a><span data-ttu-id="77b37-146">Třída String</span><span class="sxs-lookup"><span data-stu-id="77b37-146">String Class</span></span>

<span data-ttu-id="77b37-147">Protože typ řetězce v F# je ve skutečnosti na rozhraní .NET Framework `System.String` typ, všechny `System.String` členy jsou k dispozici.</span><span class="sxs-lookup"><span data-stu-id="77b37-147">Because the string type in F# is actually a .NET Framework `System.String` type, all the `System.String` members are available.</span></span> <span data-ttu-id="77b37-148">Jedná se o `+` operátor, který slouží k řetězení řetězců, `Length` vlastnost a `Chars` vlastnost, která vrací řetězec jako pole znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="77b37-148">This includes the `+` operator, which is used to concatenate strings, the `Length` property, and the `Chars` property, which returns the string as an array of Unicode characters.</span></span> <span data-ttu-id="77b37-149">Další informace o řetězcích naleznete v tématu `System.String`.</span><span class="sxs-lookup"><span data-stu-id="77b37-149">For more information about strings, see `System.String`.</span></span>

<span data-ttu-id="77b37-150">S použitím `Chars` vlastnost `System.String`, dostanete jednotlivých znaků v řetězci tak, že zadáte indexu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="77b37-150">By using the `Chars` property of `System.String`, you can access the individual characters in a string by specifying an index, as is shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1005.fs)]

## <a name="string-module"></a><span data-ttu-id="77b37-151">Řetězec modulu</span><span class="sxs-lookup"><span data-stu-id="77b37-151">String Module</span></span>

<span data-ttu-id="77b37-152">Další funkce pro manipulaci s řetězci jsou součástí `String` v modulu `FSharp.Core` oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="77b37-152">Additional functionality for string handling is included in the `String` module in the `FSharp.Core` namespace.</span></span> <span data-ttu-id="77b37-153">Další informace najdete v tématu [Core.String – modul](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="77b37-153">For more information, see [Core.String Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.string-module-%5bfsharp%5d).</span></span>

## <a name="see-also"></a><span data-ttu-id="77b37-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77b37-154">See also</span></span>

- [<span data-ttu-id="77b37-155">Referenční dokumentace jazyka F#</span><span class="sxs-lookup"><span data-stu-id="77b37-155">F# Language Reference</span></span>](index.md)
