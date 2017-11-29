---
title: "Literály (F#)"
description: "Další informace o literálu typy v programovacím jazyce F #."
keywords: "Visual f #, f #, funkční programování"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 4b1d6e9d-f933-4cd4-966d-d643152c27e4
ms.openlocfilehash: 6bb1f233b6846e226c4e73aee00b8cf77735fe2d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="literals"></a><span data-ttu-id="da37d-104">Literály</span><span class="sxs-lookup"><span data-stu-id="da37d-104">Literals</span></span>

> [!NOTE]
<span data-ttu-id="da37d-105">Referenční dokumentace rozhraní API odkazů v tomto článku se dostanete na webu MSDN (prozatím).</span><span class="sxs-lookup"><span data-stu-id="da37d-105">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="da37d-106">Toto téma obsahuje tabulku, která ukazuje, jak zadat typ literál v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="da37d-106">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="da37d-107">Typy literálu</span><span class="sxs-lookup"><span data-stu-id="da37d-107">Literal Types</span></span>
<span data-ttu-id="da37d-108">V následující tabulce jsou uvedeny typy literálu v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="da37d-108">The following table shows the literal types in F#.</span></span> <span data-ttu-id="da37d-109">Znaky, které představují číslic v šestnáctkové soustavě nerozlišují; znaky, které identifikují typ rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="da37d-109">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="da37d-110">Typ</span><span class="sxs-lookup"><span data-stu-id="da37d-110">Type</span></span>|<span data-ttu-id="da37d-111">Popis</span><span class="sxs-lookup"><span data-stu-id="da37d-111">Description</span></span>|<span data-ttu-id="da37d-112">Přípony ani předpony</span><span class="sxs-lookup"><span data-stu-id="da37d-112">Suffix or prefix</span></span>|<span data-ttu-id="da37d-113">Příklady</span><span class="sxs-lookup"><span data-stu-id="da37d-113">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="da37d-114">sbyte</span><span class="sxs-lookup"><span data-stu-id="da37d-114">sbyte</span></span>|<span data-ttu-id="da37d-115">8bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="da37d-115">signed 8-bit integer</span></span>|<span data-ttu-id="da37d-116">y</span><span class="sxs-lookup"><span data-stu-id="da37d-116">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="da37d-117">byte</span><span class="sxs-lookup"><span data-stu-id="da37d-117">byte</span></span>|<span data-ttu-id="da37d-118">nepodepsané 8bitové přirozený číslo</span><span class="sxs-lookup"><span data-stu-id="da37d-118">unsigned 8-bit natural number</span></span>|<span data-ttu-id="da37d-119">UY</span><span class="sxs-lookup"><span data-stu-id="da37d-119">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="da37d-120">Int16</span><span class="sxs-lookup"><span data-stu-id="da37d-120">int16</span></span>|<span data-ttu-id="da37d-121">16bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="da37d-121">signed 16-bit integer</span></span>|<span data-ttu-id="da37d-122">s</span><span class="sxs-lookup"><span data-stu-id="da37d-122">s</span></span>|`86s`|
|<span data-ttu-id="da37d-123">UInt16</span><span class="sxs-lookup"><span data-stu-id="da37d-123">uint16</span></span>|<span data-ttu-id="da37d-124">nepodepsané 16bitové přirozený číslo</span><span class="sxs-lookup"><span data-stu-id="da37d-124">unsigned 16-bit natural number</span></span>|<span data-ttu-id="da37d-125">nám</span><span class="sxs-lookup"><span data-stu-id="da37d-125">us</span></span>|`86us`|
|<span data-ttu-id="da37d-126">int</span><span class="sxs-lookup"><span data-stu-id="da37d-126">int</span></span><br /><br /><span data-ttu-id="da37d-127">Int32</span><span class="sxs-lookup"><span data-stu-id="da37d-127">int32</span></span>|<span data-ttu-id="da37d-128">32bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="da37d-128">signed 32-bit integer</span></span>|<span data-ttu-id="da37d-129">l nebo hodnotu none</span><span class="sxs-lookup"><span data-stu-id="da37d-129">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="da37d-130">uint</span><span class="sxs-lookup"><span data-stu-id="da37d-130">uint</span></span><br /><br /><span data-ttu-id="da37d-131">UInt32</span><span class="sxs-lookup"><span data-stu-id="da37d-131">uint32</span></span>|<span data-ttu-id="da37d-132">nepodepsané 32bitové číslo přirozený</span><span class="sxs-lookup"><span data-stu-id="da37d-132">unsigned 32-bit natural number</span></span>|<span data-ttu-id="da37d-133">u nebo ul</span><span class="sxs-lookup"><span data-stu-id="da37d-133">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="da37d-134">unativeint –</span><span class="sxs-lookup"><span data-stu-id="da37d-134">unativeint</span></span>|<span data-ttu-id="da37d-135">Nativní ukazatel jako číslo bez znaménka přirozený</span><span class="sxs-lookup"><span data-stu-id="da37d-135">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="da37d-136">zrušení</span><span class="sxs-lookup"><span data-stu-id="da37d-136">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="da37d-137">Int64</span><span class="sxs-lookup"><span data-stu-id="da37d-137">int64</span></span>|<span data-ttu-id="da37d-138">64bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="da37d-138">signed 64-bit integer</span></span>|<span data-ttu-id="da37d-139">L</span><span class="sxs-lookup"><span data-stu-id="da37d-139">L</span></span>|`86L`|
|<span data-ttu-id="da37d-140">UInt64</span><span class="sxs-lookup"><span data-stu-id="da37d-140">uint64</span></span>|<span data-ttu-id="da37d-141">nepodepsané číslo přirozený 64-bit</span><span class="sxs-lookup"><span data-stu-id="da37d-141">unsigned 64-bit natural number</span></span>|<span data-ttu-id="da37d-142">UL</span><span class="sxs-lookup"><span data-stu-id="da37d-142">UL</span></span>|`86UL`|
|<span data-ttu-id="da37d-143">jeden, float32</span><span class="sxs-lookup"><span data-stu-id="da37d-143">single, float32</span></span>|<span data-ttu-id="da37d-144">32bitové číslo s plovoucí desetinnou</span><span class="sxs-lookup"><span data-stu-id="da37d-144">32-bit floating point number</span></span>|<span data-ttu-id="da37d-145">F nebo f</span><span class="sxs-lookup"><span data-stu-id="da37d-145">F or f</span></span>|<span data-ttu-id="da37d-146">`4.14F`nebo`4.14f`</span><span class="sxs-lookup"><span data-stu-id="da37d-146">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="da37d-147">LF</span><span class="sxs-lookup"><span data-stu-id="da37d-147">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="da37d-148">float; Double</span><span class="sxs-lookup"><span data-stu-id="da37d-148">float; double</span></span>|<span data-ttu-id="da37d-149">číslo s plovoucí desetinnou 64-bit</span><span class="sxs-lookup"><span data-stu-id="da37d-149">64-bit floating point number</span></span>|<span data-ttu-id="da37d-150">žádná</span><span class="sxs-lookup"><span data-stu-id="da37d-150">none</span></span>|<span data-ttu-id="da37d-151">`4.14`nebo `2.3E+32` nebo`2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="da37d-151">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="da37d-152">LF</span><span class="sxs-lookup"><span data-stu-id="da37d-152">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="da37d-153">bigint</span><span class="sxs-lookup"><span data-stu-id="da37d-153">bigint</span></span>|<span data-ttu-id="da37d-154">mimo jiné k reprezentaci 64bitové celé číslo</span><span class="sxs-lookup"><span data-stu-id="da37d-154">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="da37d-155">I</span><span class="sxs-lookup"><span data-stu-id="da37d-155">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="da37d-156">decimal</span><span class="sxs-lookup"><span data-stu-id="da37d-156">decimal</span></span>|<span data-ttu-id="da37d-157">desetinná čísla reprezentován jako dlouhodobý bod nebo racionální číslo</span><span class="sxs-lookup"><span data-stu-id="da37d-157">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="da37d-158">M nebo m</span><span class="sxs-lookup"><span data-stu-id="da37d-158">M or m</span></span>|<span data-ttu-id="da37d-159">`0.7833M`nebo`0.7833m`</span><span class="sxs-lookup"><span data-stu-id="da37d-159">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="da37d-160">Char</span><span class="sxs-lookup"><span data-stu-id="da37d-160">Char</span></span>|<span data-ttu-id="da37d-161">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="da37d-161">Unicode character</span></span>|<span data-ttu-id="da37d-162">žádná</span><span class="sxs-lookup"><span data-stu-id="da37d-162">none</span></span>|`'a'`|
|<span data-ttu-id="da37d-163">String</span><span class="sxs-lookup"><span data-stu-id="da37d-163">String</span></span>|<span data-ttu-id="da37d-164">Řetězec znaků Unicode</span><span class="sxs-lookup"><span data-stu-id="da37d-164">Unicode string</span></span>|<span data-ttu-id="da37d-165">žádná</span><span class="sxs-lookup"><span data-stu-id="da37d-165">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="da37d-166">or</span><span class="sxs-lookup"><span data-stu-id="da37d-166">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="da37d-167">or</span><span class="sxs-lookup"><span data-stu-id="da37d-167">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="da37d-168">or</span><span class="sxs-lookup"><span data-stu-id="da37d-168">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="da37d-169">Viz také [řetězce](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="da37d-169">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="da37d-170">byte</span><span class="sxs-lookup"><span data-stu-id="da37d-170">byte</span></span>|<span data-ttu-id="da37d-171">Znaků ASCII</span><span class="sxs-lookup"><span data-stu-id="da37d-171">ASCII character</span></span>|<span data-ttu-id="da37d-172">B</span><span class="sxs-lookup"><span data-stu-id="da37d-172">B</span></span>|`'a'B`|
|<span data-ttu-id="da37d-173">Byte]</span><span class="sxs-lookup"><span data-stu-id="da37d-173">byte[]</span></span>|<span data-ttu-id="da37d-174">Řetězec ASCII</span><span class="sxs-lookup"><span data-stu-id="da37d-174">ASCII string</span></span>|<span data-ttu-id="da37d-175">B</span><span class="sxs-lookup"><span data-stu-id="da37d-175">B</span></span>|`"text"B`|
|<span data-ttu-id="da37d-176">Řetězec nebo byte]</span><span class="sxs-lookup"><span data-stu-id="da37d-176">String or byte[]</span></span>|<span data-ttu-id="da37d-177">řetězec typu verbatim</span><span class="sxs-lookup"><span data-stu-id="da37d-177">verbatim string</span></span>|<span data-ttu-id="da37d-178">předponu @</span><span class="sxs-lookup"><span data-stu-id="da37d-178">@ prefix</span></span>|<span data-ttu-id="da37d-179">`@"\\server\share"`(Kódování Unicode)</span><span class="sxs-lookup"><span data-stu-id="da37d-179">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="da37d-180">`@"\\server\share"B`(ASCII)</span><span class="sxs-lookup"><span data-stu-id="da37d-180">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="remarks"></a><span data-ttu-id="da37d-181">Poznámky</span><span class="sxs-lookup"><span data-stu-id="da37d-181">Remarks</span></span>
<span data-ttu-id="da37d-182">Řetězců v kódu Unicode může obsahovat explicitní kódování, kterou můžete zadat pomocí `\u` následovaný kódem v šestnáctkové soustavě 16bitové nebo kódování UTF-32, který můžete zadat pomocí `\U` následuje 32bitové šestnáctkové kód, který představuje typu Unicode náhradní pár.</span><span class="sxs-lookup"><span data-stu-id="da37d-182">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents a Unicode surrogate pair.</span></span>

<span data-ttu-id="da37d-183">Od verze F # 3.1, můžete použít `+` přihlásit spojí textové literály.</span><span class="sxs-lookup"><span data-stu-id="da37d-183">As of F# 3.1, you can use the `+` sign to combine string literals.</span></span> <span data-ttu-id="da37d-184">Můžete také použít bitové hodnotě nebo (`|||`) operátor kombinovat příznaky výčtu.</span><span class="sxs-lookup"><span data-stu-id="da37d-184">You can also use the bitwise or (`|||`) operator to combine enum flags.</span></span> <span data-ttu-id="da37d-185">Například následující kód je právní v F # 3.1:</span><span class="sxs-lookup"><span data-stu-id="da37d-185">For example, the following code is legal in F# 3.1:</span></span>

```fsharp
[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

<span data-ttu-id="da37d-186">Použití jiné bitové operátory není povoleno.</span><span class="sxs-lookup"><span data-stu-id="da37d-186">The use of other bitwise operators isn't allowed.</span></span>


## <a name="named-literals"></a><span data-ttu-id="da37d-187">Pojmenované literály</span><span class="sxs-lookup"><span data-stu-id="da37d-187">Named Literals</span></span>
<span data-ttu-id="da37d-188">Může být označen hodnoty, které by měla být konstanty [literálu](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) atribut.</span><span class="sxs-lookup"><span data-stu-id="da37d-188">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="da37d-189">Tento atribut má za následek způsobuje hodnotu sestavují jako konstanta.</span><span class="sxs-lookup"><span data-stu-id="da37d-189">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="da37d-190">Ve vzoru výraz identifikátory, které začínají malá písmena jsou vždy považovány za proměnné vázat, nikoli jako literály, takže obvykle používejte pro počáteční kapitálek definujete literály.</span><span class="sxs-lookup"><span data-stu-id="da37d-190">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="da37d-191">Celá čísla v jiných databázích</span><span class="sxs-lookup"><span data-stu-id="da37d-191">Integers In Other Bases</span></span>

<span data-ttu-id="da37d-192">Podepsaná celá čísla 32-bit lze zadat také v šestnáctkové, osmičkové nebo binární pomocí `0x`, `0o` nebo `0b` předpony v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="da37d-192">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="da37d-193">Podtržítka v číselné literály</span><span class="sxs-lookup"><span data-stu-id="da37d-193">Underscores in Numeric Literals</span></span>

<span data-ttu-id="da37d-194">Od verze 4.1 F #, můžete oddělit číslic znak podtržítka (`_`).</span><span class="sxs-lookup"><span data-stu-id="da37d-194">Starting with F# 4.1, you can separate digits with the underscore character (`_`).</span></span>

```fsharp
let DeadBeef = 0xDEAD_BEEF

let DeadBeefAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let ExampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="da37d-195">Viz také</span><span class="sxs-lookup"><span data-stu-id="da37d-195">See Also</span></span>

[<span data-ttu-id="da37d-196">Core.literalattribute – třída</span><span class="sxs-lookup"><span data-stu-id="da37d-196">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
