---
title: Literály (F#)
description: 'Další informace o literálu typy v programovacím jazyce F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 961d6a10122c5d5c691d394efa8d2b7b31a80453
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="literals"></a><span data-ttu-id="8ac36-103">Literály</span><span class="sxs-lookup"><span data-stu-id="8ac36-103">Literals</span></span>

> [!NOTE]
<span data-ttu-id="8ac36-104">Referenční dokumentace rozhraní API odkazů v tomto článku se dostanete na webu MSDN (prozatím).</span><span class="sxs-lookup"><span data-stu-id="8ac36-104">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="8ac36-105">Toto téma obsahuje tabulku, která ukazuje, jak zadat typ literál v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="8ac36-105">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="8ac36-106">Typy literálu</span><span class="sxs-lookup"><span data-stu-id="8ac36-106">Literal Types</span></span>
<span data-ttu-id="8ac36-107">V následující tabulce jsou uvedeny typy literálu v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="8ac36-107">The following table shows the literal types in F#.</span></span> <span data-ttu-id="8ac36-108">Znaky, které představují číslic v šestnáctkové soustavě nerozlišují; znaky, které identifikují typ rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="8ac36-108">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="8ac36-109">Typ</span><span class="sxs-lookup"><span data-stu-id="8ac36-109">Type</span></span>|<span data-ttu-id="8ac36-110">Popis</span><span class="sxs-lookup"><span data-stu-id="8ac36-110">Description</span></span>|<span data-ttu-id="8ac36-111">Přípony ani předpony</span><span class="sxs-lookup"><span data-stu-id="8ac36-111">Suffix or prefix</span></span>|<span data-ttu-id="8ac36-112">Příklady</span><span class="sxs-lookup"><span data-stu-id="8ac36-112">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="8ac36-113">sbyte</span><span class="sxs-lookup"><span data-stu-id="8ac36-113">sbyte</span></span>|<span data-ttu-id="8ac36-114">8bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="8ac36-114">signed 8-bit integer</span></span>|<span data-ttu-id="8ac36-115">y</span><span class="sxs-lookup"><span data-stu-id="8ac36-115">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="8ac36-116">byte</span><span class="sxs-lookup"><span data-stu-id="8ac36-116">byte</span></span>|<span data-ttu-id="8ac36-117">nepodepsané 8bitové přirozený číslo</span><span class="sxs-lookup"><span data-stu-id="8ac36-117">unsigned 8-bit natural number</span></span>|<span data-ttu-id="8ac36-118">UY</span><span class="sxs-lookup"><span data-stu-id="8ac36-118">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="8ac36-119">Int16</span><span class="sxs-lookup"><span data-stu-id="8ac36-119">int16</span></span>|<span data-ttu-id="8ac36-120">16bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="8ac36-120">signed 16-bit integer</span></span>|<span data-ttu-id="8ac36-121">s</span><span class="sxs-lookup"><span data-stu-id="8ac36-121">s</span></span>|`86s`|
|<span data-ttu-id="8ac36-122">UInt16</span><span class="sxs-lookup"><span data-stu-id="8ac36-122">uint16</span></span>|<span data-ttu-id="8ac36-123">nepodepsané 16bitové přirozený číslo</span><span class="sxs-lookup"><span data-stu-id="8ac36-123">unsigned 16-bit natural number</span></span>|<span data-ttu-id="8ac36-124">nám</span><span class="sxs-lookup"><span data-stu-id="8ac36-124">us</span></span>|`86us`|
|<span data-ttu-id="8ac36-125">int</span><span class="sxs-lookup"><span data-stu-id="8ac36-125">int</span></span><br /><br /><span data-ttu-id="8ac36-126">int32</span><span class="sxs-lookup"><span data-stu-id="8ac36-126">int32</span></span>|<span data-ttu-id="8ac36-127">32bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="8ac36-127">signed 32-bit integer</span></span>|<span data-ttu-id="8ac36-128">l nebo hodnotu none</span><span class="sxs-lookup"><span data-stu-id="8ac36-128">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="8ac36-129">uint</span><span class="sxs-lookup"><span data-stu-id="8ac36-129">uint</span></span><br /><br /><span data-ttu-id="8ac36-130">UInt32</span><span class="sxs-lookup"><span data-stu-id="8ac36-130">uint32</span></span>|<span data-ttu-id="8ac36-131">nepodepsané 32bitové číslo přirozený</span><span class="sxs-lookup"><span data-stu-id="8ac36-131">unsigned 32-bit natural number</span></span>|<span data-ttu-id="8ac36-132">u nebo ul</span><span class="sxs-lookup"><span data-stu-id="8ac36-132">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="8ac36-133">unativeint –</span><span class="sxs-lookup"><span data-stu-id="8ac36-133">unativeint</span></span>|<span data-ttu-id="8ac36-134">Nativní ukazatel jako číslo bez znaménka přirozený</span><span class="sxs-lookup"><span data-stu-id="8ac36-134">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="8ac36-135">zrušení</span><span class="sxs-lookup"><span data-stu-id="8ac36-135">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="8ac36-136">int64</span><span class="sxs-lookup"><span data-stu-id="8ac36-136">int64</span></span>|<span data-ttu-id="8ac36-137">64bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="8ac36-137">signed 64-bit integer</span></span>|<span data-ttu-id="8ac36-138">L</span><span class="sxs-lookup"><span data-stu-id="8ac36-138">L</span></span>|`86L`|
|<span data-ttu-id="8ac36-139">UInt64</span><span class="sxs-lookup"><span data-stu-id="8ac36-139">uint64</span></span>|<span data-ttu-id="8ac36-140">nepodepsané číslo přirozený 64-bit</span><span class="sxs-lookup"><span data-stu-id="8ac36-140">unsigned 64-bit natural number</span></span>|<span data-ttu-id="8ac36-141">UL</span><span class="sxs-lookup"><span data-stu-id="8ac36-141">UL</span></span>|`86UL`|
|<span data-ttu-id="8ac36-142">jeden, float32</span><span class="sxs-lookup"><span data-stu-id="8ac36-142">single, float32</span></span>|<span data-ttu-id="8ac36-143">32bitové číslo s plovoucí desetinnou</span><span class="sxs-lookup"><span data-stu-id="8ac36-143">32-bit floating point number</span></span>|<span data-ttu-id="8ac36-144">F nebo f</span><span class="sxs-lookup"><span data-stu-id="8ac36-144">F or f</span></span>|<span data-ttu-id="8ac36-145">`4.14F` Nebo `4.14f`</span><span class="sxs-lookup"><span data-stu-id="8ac36-145">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="8ac36-146">LF</span><span class="sxs-lookup"><span data-stu-id="8ac36-146">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="8ac36-147">float; Double</span><span class="sxs-lookup"><span data-stu-id="8ac36-147">float; double</span></span>|<span data-ttu-id="8ac36-148">číslo s plovoucí desetinnou 64-bit</span><span class="sxs-lookup"><span data-stu-id="8ac36-148">64-bit floating point number</span></span>|<span data-ttu-id="8ac36-149">žádná</span><span class="sxs-lookup"><span data-stu-id="8ac36-149">none</span></span>|<span data-ttu-id="8ac36-150">`4.14` nebo `2.3E+32` nebo `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="8ac36-150">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="8ac36-151">LF</span><span class="sxs-lookup"><span data-stu-id="8ac36-151">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="8ac36-152">bigint</span><span class="sxs-lookup"><span data-stu-id="8ac36-152">bigint</span></span>|<span data-ttu-id="8ac36-153">mimo jiné k reprezentaci 64bitové celé číslo</span><span class="sxs-lookup"><span data-stu-id="8ac36-153">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="8ac36-154">I</span><span class="sxs-lookup"><span data-stu-id="8ac36-154">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="8ac36-155">decimal</span><span class="sxs-lookup"><span data-stu-id="8ac36-155">decimal</span></span>|<span data-ttu-id="8ac36-156">desetinná čísla reprezentován jako dlouhodobý bod nebo racionální číslo</span><span class="sxs-lookup"><span data-stu-id="8ac36-156">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="8ac36-157">M nebo m</span><span class="sxs-lookup"><span data-stu-id="8ac36-157">M or m</span></span>|<span data-ttu-id="8ac36-158">`0.7833M` Nebo `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="8ac36-158">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="8ac36-159">Char</span><span class="sxs-lookup"><span data-stu-id="8ac36-159">Char</span></span>|<span data-ttu-id="8ac36-160">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="8ac36-160">Unicode character</span></span>|<span data-ttu-id="8ac36-161">žádná</span><span class="sxs-lookup"><span data-stu-id="8ac36-161">none</span></span>|`'a'`|
|<span data-ttu-id="8ac36-162">String</span><span class="sxs-lookup"><span data-stu-id="8ac36-162">String</span></span>|<span data-ttu-id="8ac36-163">Řetězec znaků Unicode</span><span class="sxs-lookup"><span data-stu-id="8ac36-163">Unicode string</span></span>|<span data-ttu-id="8ac36-164">žádná</span><span class="sxs-lookup"><span data-stu-id="8ac36-164">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="8ac36-165">or</span><span class="sxs-lookup"><span data-stu-id="8ac36-165">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="8ac36-166">or</span><span class="sxs-lookup"><span data-stu-id="8ac36-166">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="8ac36-167">or</span><span class="sxs-lookup"><span data-stu-id="8ac36-167">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="8ac36-168">Viz také [řetězce](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="8ac36-168">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="8ac36-169">byte</span><span class="sxs-lookup"><span data-stu-id="8ac36-169">byte</span></span>|<span data-ttu-id="8ac36-170">Znaků ASCII</span><span class="sxs-lookup"><span data-stu-id="8ac36-170">ASCII character</span></span>|<span data-ttu-id="8ac36-171">B</span><span class="sxs-lookup"><span data-stu-id="8ac36-171">B</span></span>|`'a'B`|
|<span data-ttu-id="8ac36-172">Byte</span><span class="sxs-lookup"><span data-stu-id="8ac36-172">byte[]</span></span>|<span data-ttu-id="8ac36-173">Řetězec ASCII</span><span class="sxs-lookup"><span data-stu-id="8ac36-173">ASCII string</span></span>|<span data-ttu-id="8ac36-174">B</span><span class="sxs-lookup"><span data-stu-id="8ac36-174">B</span></span>|`"text"B`|
|<span data-ttu-id="8ac36-175">Řetězec nebo byte]</span><span class="sxs-lookup"><span data-stu-id="8ac36-175">String or byte[]</span></span>|<span data-ttu-id="8ac36-176">řetězec typu verbatim</span><span class="sxs-lookup"><span data-stu-id="8ac36-176">verbatim string</span></span>|<span data-ttu-id="8ac36-177">předponu @</span><span class="sxs-lookup"><span data-stu-id="8ac36-177">@ prefix</span></span>|<span data-ttu-id="8ac36-178">`@"\\server\share"` (Kódování Unicode)</span><span class="sxs-lookup"><span data-stu-id="8ac36-178">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="8ac36-179">`@"\\server\share"B` (ASCII)</span><span class="sxs-lookup"><span data-stu-id="8ac36-179">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="remarks"></a><span data-ttu-id="8ac36-180">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8ac36-180">Remarks</span></span>
<span data-ttu-id="8ac36-181">Řetězců v kódu Unicode může obsahovat explicitní kódování, kterou můžete zadat pomocí `\u` následovaný kódem v šestnáctkové soustavě 16bitové nebo kódování UTF-32, který můžete zadat pomocí `\U` následuje 32bitové šestnáctkové kód, který představuje typu Unicode náhradní pár.</span><span class="sxs-lookup"><span data-stu-id="8ac36-181">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents a Unicode surrogate pair.</span></span>

<span data-ttu-id="8ac36-182">Od verze F # 3.1, můžete použít `+` přihlásit spojí textové literály.</span><span class="sxs-lookup"><span data-stu-id="8ac36-182">As of F# 3.1, you can use the `+` sign to combine string literals.</span></span> <span data-ttu-id="8ac36-183">Můžete také použít bitové hodnotě nebo (`|||`) operátor kombinovat příznaky výčtu.</span><span class="sxs-lookup"><span data-stu-id="8ac36-183">You can also use the bitwise or (`|||`) operator to combine enum flags.</span></span> <span data-ttu-id="8ac36-184">Například následující kód je právní v F # 3.1:</span><span class="sxs-lookup"><span data-stu-id="8ac36-184">For example, the following code is legal in F# 3.1:</span></span>

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

<span data-ttu-id="8ac36-185">Použití jiné bitové operátory není povoleno.</span><span class="sxs-lookup"><span data-stu-id="8ac36-185">The use of other bitwise operators isn't allowed.</span></span>


## <a name="named-literals"></a><span data-ttu-id="8ac36-186">Pojmenované literály</span><span class="sxs-lookup"><span data-stu-id="8ac36-186">Named Literals</span></span>
<span data-ttu-id="8ac36-187">Může být označen hodnoty, které by měla být konstanty [literálu](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) atribut.</span><span class="sxs-lookup"><span data-stu-id="8ac36-187">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="8ac36-188">Tento atribut má za následek způsobuje hodnotu sestavují jako konstanta.</span><span class="sxs-lookup"><span data-stu-id="8ac36-188">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="8ac36-189">Ve vzoru výraz identifikátory, které začínají malá písmena jsou vždy považovány za proměnné vázat, nikoli jako literály, takže obvykle používejte pro počáteční kapitálek definujete literály.</span><span class="sxs-lookup"><span data-stu-id="8ac36-189">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="8ac36-190">Celá čísla v jiných databázích</span><span class="sxs-lookup"><span data-stu-id="8ac36-190">Integers In Other Bases</span></span>

<span data-ttu-id="8ac36-191">Podepsaná celá čísla 32-bit lze zadat také v šestnáctkové, osmičkové nebo binární pomocí `0x`, `0o` nebo `0b` předpony v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="8ac36-191">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="8ac36-192">Podtržítka v číselné literály</span><span class="sxs-lookup"><span data-stu-id="8ac36-192">Underscores in Numeric Literals</span></span>

<span data-ttu-id="8ac36-193">Od verze 4.1 F #, můžete oddělit číslic znak podtržítka (`_`).</span><span class="sxs-lookup"><span data-stu-id="8ac36-193">Starting with F# 4.1, you can separate digits with the underscore character (`_`).</span></span>

```fsharp
let DeadBeef = 0xDEAD_BEEF

let DeadBeefAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let ExampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="8ac36-194">Viz také</span><span class="sxs-lookup"><span data-stu-id="8ac36-194">See Also</span></span>

[<span data-ttu-id="8ac36-195">Core.literalattribute – třída</span><span class="sxs-lookup"><span data-stu-id="8ac36-195">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
