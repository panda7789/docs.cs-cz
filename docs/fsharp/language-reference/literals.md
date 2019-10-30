---
title: Literály
description: Seznamte se s typy literálů F# v programovacím jazyce.
ms.date: 06/28/2019
ms.openlocfilehash: 9792a24ac28eb402e35e78574cd6a2bf9526734d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041033"
---
# <a name="literals"></a><span data-ttu-id="d62fb-103">Literály</span><span class="sxs-lookup"><span data-stu-id="d62fb-103">Literals</span></span>

> [!NOTE]
> <span data-ttu-id="d62fb-104">Odkazy na reference k rozhraní API v tomto článku vás převezmou na MSDN (teď).</span><span class="sxs-lookup"><span data-stu-id="d62fb-104">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="d62fb-105">Toto téma obsahuje tabulku, která ukazuje, jak zadat typ literálu v F#.</span><span class="sxs-lookup"><span data-stu-id="d62fb-105">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="d62fb-106">Typy literálů</span><span class="sxs-lookup"><span data-stu-id="d62fb-106">Literal Types</span></span>

<span data-ttu-id="d62fb-107">V následující tabulce jsou uvedeny typy literálů F#v.</span><span class="sxs-lookup"><span data-stu-id="d62fb-107">The following table shows the literal types in F#.</span></span> <span data-ttu-id="d62fb-108">Znaky, které představují číslice v šestnáctkovém zápisu, nerozlišují velká a malá písmena; znaky, které identifikují typ, rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="d62fb-108">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="d62fb-109">Typ</span><span class="sxs-lookup"><span data-stu-id="d62fb-109">Type</span></span>|<span data-ttu-id="d62fb-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d62fb-110">Description</span></span>|<span data-ttu-id="d62fb-111">Přípona nebo předpona</span><span class="sxs-lookup"><span data-stu-id="d62fb-111">Suffix or prefix</span></span>|<span data-ttu-id="d62fb-112">Příklady</span><span class="sxs-lookup"><span data-stu-id="d62fb-112">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="d62fb-113">sbyte</span><span class="sxs-lookup"><span data-stu-id="d62fb-113">sbyte</span></span>|<span data-ttu-id="d62fb-114">8bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="d62fb-114">signed 8-bit integer</span></span>|<span data-ttu-id="d62fb-115">y</span><span class="sxs-lookup"><span data-stu-id="d62fb-115">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="d62fb-116">byte</span><span class="sxs-lookup"><span data-stu-id="d62fb-116">byte</span></span>|<span data-ttu-id="d62fb-117">8bitové přirozené číslo bez znaménka</span><span class="sxs-lookup"><span data-stu-id="d62fb-117">unsigned 8-bit natural number</span></span>|<span data-ttu-id="d62fb-118">uy</span><span class="sxs-lookup"><span data-stu-id="d62fb-118">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="d62fb-119">Int16</span><span class="sxs-lookup"><span data-stu-id="d62fb-119">int16</span></span>|<span data-ttu-id="d62fb-120">16bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="d62fb-120">signed 16-bit integer</span></span>|<span data-ttu-id="d62fb-121">s</span><span class="sxs-lookup"><span data-stu-id="d62fb-121">s</span></span>|`86s`|
|<span data-ttu-id="d62fb-122">UInt16</span><span class="sxs-lookup"><span data-stu-id="d62fb-122">uint16</span></span>|<span data-ttu-id="d62fb-123">16bitové přirozené číslo bez znaménka</span><span class="sxs-lookup"><span data-stu-id="d62fb-123">unsigned 16-bit natural number</span></span>|<span data-ttu-id="d62fb-124">vylepšení</span><span class="sxs-lookup"><span data-stu-id="d62fb-124">us</span></span>|`86us`|
|<span data-ttu-id="d62fb-125">int</span><span class="sxs-lookup"><span data-stu-id="d62fb-125">int</span></span><br /><br /><span data-ttu-id="d62fb-126">Uvedena</span><span class="sxs-lookup"><span data-stu-id="d62fb-126">int32</span></span>|<span data-ttu-id="d62fb-127">Podepsané 32 – celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="d62fb-127">signed 32-bit integer</span></span>|<span data-ttu-id="d62fb-128">l nebo None</span><span class="sxs-lookup"><span data-stu-id="d62fb-128">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="d62fb-129">uint</span><span class="sxs-lookup"><span data-stu-id="d62fb-129">uint</span></span><br /><br /><span data-ttu-id="d62fb-130">UInt32</span><span class="sxs-lookup"><span data-stu-id="d62fb-130">uint32</span></span>|<span data-ttu-id="d62fb-131">nepodepsané 32 – přirozené číslo v bitech</span><span class="sxs-lookup"><span data-stu-id="d62fb-131">unsigned 32-bit natural number</span></span>|<span data-ttu-id="d62fb-132">u nebo ul</span><span class="sxs-lookup"><span data-stu-id="d62fb-132">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="d62fb-133">nativeint –</span><span class="sxs-lookup"><span data-stu-id="d62fb-133">nativeint</span></span>|<span data-ttu-id="d62fb-134">nativní ukazatel na podepsané přirozené číslo</span><span class="sxs-lookup"><span data-stu-id="d62fb-134">native pointer to a signed natural number</span></span>|<span data-ttu-id="d62fb-135">N</span><span class="sxs-lookup"><span data-stu-id="d62fb-135">n</span></span>|`123n`|
|<span data-ttu-id="d62fb-136">unativeint –</span><span class="sxs-lookup"><span data-stu-id="d62fb-136">unativeint</span></span>|<span data-ttu-id="d62fb-137">nativní ukazatel jako přirozené číslo bez znaménka</span><span class="sxs-lookup"><span data-stu-id="d62fb-137">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="d62fb-138">instalován</span><span class="sxs-lookup"><span data-stu-id="d62fb-138">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="d62fb-139">Int64</span><span class="sxs-lookup"><span data-stu-id="d62fb-139">int64</span></span>|<span data-ttu-id="d62fb-140">Podepsané 64 – celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="d62fb-140">signed 64-bit integer</span></span>|<span data-ttu-id="d62fb-141">L</span><span class="sxs-lookup"><span data-stu-id="d62fb-141">L</span></span>|`86L`|
|<span data-ttu-id="d62fb-142">UInt64</span><span class="sxs-lookup"><span data-stu-id="d62fb-142">uint64</span></span>|<span data-ttu-id="d62fb-143">nepodepsané 64 – přirozené číslo v bitech</span><span class="sxs-lookup"><span data-stu-id="d62fb-143">unsigned 64-bit natural number</span></span>|<span data-ttu-id="d62fb-144">UL</span><span class="sxs-lookup"><span data-stu-id="d62fb-144">UL</span></span>|`86UL`|
|<span data-ttu-id="d62fb-145">Single, float32</span><span class="sxs-lookup"><span data-stu-id="d62fb-145">single, float32</span></span>|<span data-ttu-id="d62fb-146">32-bitové číslo s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="d62fb-146">32-bit floating point number</span></span>|<span data-ttu-id="d62fb-147">F nebo f</span><span class="sxs-lookup"><span data-stu-id="d62fb-147">F or f</span></span>|<span data-ttu-id="d62fb-148">`4.14F` nebo `4.14f`</span><span class="sxs-lookup"><span data-stu-id="d62fb-148">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="d62fb-149">znaky</span><span class="sxs-lookup"><span data-stu-id="d62fb-149">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="d62fb-150">Plovák klepat</span><span class="sxs-lookup"><span data-stu-id="d62fb-150">float; double</span></span>|<span data-ttu-id="d62fb-151">64-bitové číslo s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="d62fb-151">64-bit floating point number</span></span>|<span data-ttu-id="d62fb-152">žádná</span><span class="sxs-lookup"><span data-stu-id="d62fb-152">none</span></span>|<span data-ttu-id="d62fb-153">`4.14` nebo `2.3E+32` nebo `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="d62fb-153">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="d62fb-154">ZNAKY</span><span class="sxs-lookup"><span data-stu-id="d62fb-154">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="d62fb-155">bigint</span><span class="sxs-lookup"><span data-stu-id="d62fb-155">bigint</span></span>|<span data-ttu-id="d62fb-156">celé číslo není omezeno na 64-bitovou reprezentaci</span><span class="sxs-lookup"><span data-stu-id="d62fb-156">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="d62fb-157">I</span><span class="sxs-lookup"><span data-stu-id="d62fb-157">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="d62fb-158">decimal</span><span class="sxs-lookup"><span data-stu-id="d62fb-158">decimal</span></span>|<span data-ttu-id="d62fb-159">desetinné číslo reprezentované jako pevný bod nebo racionální číslo</span><span class="sxs-lookup"><span data-stu-id="d62fb-159">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="d62fb-160">M nebo m</span><span class="sxs-lookup"><span data-stu-id="d62fb-160">M or m</span></span>|<span data-ttu-id="d62fb-161">`0.7833M` nebo `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="d62fb-161">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="d62fb-162">Char</span><span class="sxs-lookup"><span data-stu-id="d62fb-162">Char</span></span>|<span data-ttu-id="d62fb-163">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="d62fb-163">Unicode character</span></span>|<span data-ttu-id="d62fb-164">žádná</span><span class="sxs-lookup"><span data-stu-id="d62fb-164">none</span></span>|<span data-ttu-id="d62fb-165">`'a'` nebo `'\u0061'`</span><span class="sxs-lookup"><span data-stu-id="d62fb-165">`'a'` or `'\u0061'`</span></span>|
|<span data-ttu-id="d62fb-166">String</span><span class="sxs-lookup"><span data-stu-id="d62fb-166">String</span></span>|<span data-ttu-id="d62fb-167">Řetězec Unicode</span><span class="sxs-lookup"><span data-stu-id="d62fb-167">Unicode string</span></span>|<span data-ttu-id="d62fb-168">žádná</span><span class="sxs-lookup"><span data-stu-id="d62fb-168">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="d62fb-169">or</span><span class="sxs-lookup"><span data-stu-id="d62fb-169">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="d62fb-170">or</span><span class="sxs-lookup"><span data-stu-id="d62fb-170">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="d62fb-171">or</span><span class="sxs-lookup"><span data-stu-id="d62fb-171">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="d62fb-172">Viz také [řetězce](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="d62fb-172">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="d62fb-173">byte</span><span class="sxs-lookup"><span data-stu-id="d62fb-173">byte</span></span>|<span data-ttu-id="d62fb-174">Znak ASCII</span><span class="sxs-lookup"><span data-stu-id="d62fb-174">ASCII character</span></span>|<span data-ttu-id="d62fb-175">B</span><span class="sxs-lookup"><span data-stu-id="d62fb-175">B</span></span>|`'a'B`|
|<span data-ttu-id="d62fb-176">Byte []</span><span class="sxs-lookup"><span data-stu-id="d62fb-176">byte[]</span></span>|<span data-ttu-id="d62fb-177">Řetězec ASCII</span><span class="sxs-lookup"><span data-stu-id="d62fb-177">ASCII string</span></span>|<span data-ttu-id="d62fb-178">B</span><span class="sxs-lookup"><span data-stu-id="d62fb-178">B</span></span>|`"text"B`|
|<span data-ttu-id="d62fb-179">Řetězec nebo Byte []</span><span class="sxs-lookup"><span data-stu-id="d62fb-179">String or byte[]</span></span>|<span data-ttu-id="d62fb-180">řetězec doslovného řetězce</span><span class="sxs-lookup"><span data-stu-id="d62fb-180">verbatim string</span></span>|<span data-ttu-id="d62fb-181">@ prefix</span><span class="sxs-lookup"><span data-stu-id="d62fb-181">@ prefix</span></span>|<span data-ttu-id="d62fb-182">`@"\\server\share"` (Unicode)</span><span class="sxs-lookup"><span data-stu-id="d62fb-182">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="d62fb-183">`@"\\server\share"B` (ASCII)</span><span class="sxs-lookup"><span data-stu-id="d62fb-183">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="named-literals"></a><span data-ttu-id="d62fb-184">Pojmenované literály</span><span class="sxs-lookup"><span data-stu-id="d62fb-184">Named literals</span></span>

<span data-ttu-id="d62fb-185">Hodnoty, které mají být konstanty, mohou být označeny atributem [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) .</span><span class="sxs-lookup"><span data-stu-id="d62fb-185">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="d62fb-186">Tento atribut má vliv, který způsobí, že se hodnota zkompiluje jako konstanta.</span><span class="sxs-lookup"><span data-stu-id="d62fb-186">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="d62fb-187">V výrazech porovnávání se vzorem se identifikátory začínající malým písmenem vždy považují za proměnné, které mají být vázány, nikoli jako literály, takže při definování literálů byste obecně měli použít počáteční velká písmena.</span><span class="sxs-lookup"><span data-stu-id="d62fb-187">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

```fsharp
[<Literal>]
let SomeJson = """{"numbers":[1,2,3,4,5]}"""

[<Literal>]
let Literal1 = "a" + "b"

[<Literal>]
let FileLocation =   __SOURCE_DIRECTORY__ + "/" + __SOURCE_FILE__

[<Literal>]
let Literal2 = 1 ||| 64

[<Literal>]
let Literal3 = System.IO.FileAccess.Read ||| System.IO.FileAccess.Write
```

## <a name="remarks"></a><span data-ttu-id="d62fb-188">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d62fb-188">Remarks</span></span>

<span data-ttu-id="d62fb-189">Řetězce Unicode mohou obsahovat explicitní kódování, která lze zadat pomocí `\u` následovaný 16 bitovým hexadecimálním kódem (0000-FFFF) nebo kódováním UTF-32, které lze zadat pomocí `\U` následovaným 32 šestnáctkovým kódem, který představuje libovolnou znakovou sadu Unicode bod kódu (00000000-0010FFFF).</span><span class="sxs-lookup"><span data-stu-id="d62fb-189">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code (0000 - FFFF), or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents any Unicode code point (00000000 - 0010FFFF).</span></span>

<span data-ttu-id="d62fb-190">Použití jiných bitových operátorů kromě `|||` není povoleno.</span><span class="sxs-lookup"><span data-stu-id="d62fb-190">The use of other bitwise operators other than `|||` isn't allowed.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="d62fb-191">Celá čísla v jiných základech</span><span class="sxs-lookup"><span data-stu-id="d62fb-191">Integers in other bases</span></span>

<span data-ttu-id="d62fb-192">Podepsaná 32. celá čísla se znaménkem lze zadat také v šestnáctkovém, osmičkovém nebo binárním formátu pomocí `0x`, `0o` nebo předpony `0b`.</span><span class="sxs-lookup"><span data-stu-id="d62fb-192">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="d62fb-193">Podtržítka v numerických literálech</span><span class="sxs-lookup"><span data-stu-id="d62fb-193">Underscores in numeric literals</span></span>

<span data-ttu-id="d62fb-194">Můžete oddělit číslice znakem podtržítka (`_`).</span><span class="sxs-lookup"><span data-stu-id="d62fb-194">You can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="d62fb-195">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d62fb-195">See also</span></span>

- [<span data-ttu-id="d62fb-196">Core. LiteralAttribute – – třída</span><span class="sxs-lookup"><span data-stu-id="d62fb-196">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
