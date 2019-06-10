---
title: Literály
description: Seznamte se s typy literálu v F# programovací jazyk.
ms.date: 06/08/2019
ms.openlocfilehash: 93329cd868ff7a2daaffa1b87ba838bbbc98015c
ms.sourcegitcommit: 5ae6affa0b171be3bb5f4729fb68ea4fe799f959
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2019
ms.locfileid: "66816229"
---
# <a name="literals"></a><span data-ttu-id="94836-103">Literály</span><span class="sxs-lookup"><span data-stu-id="94836-103">Literals</span></span>

> [!NOTE]
> <span data-ttu-id="94836-104">Rozhraní API referenčních odkazů v tomto článku se dostanete na webu MSDN (prozatím).</span><span class="sxs-lookup"><span data-stu-id="94836-104">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="94836-105">Toto téma obsahuje tabulku, která ukazuje, jak určit typ literály v F#.</span><span class="sxs-lookup"><span data-stu-id="94836-105">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="94836-106">Typy literálu</span><span class="sxs-lookup"><span data-stu-id="94836-106">Literal Types</span></span>

<span data-ttu-id="94836-107">Následující tabulka uvádí typy literálu v F#.</span><span class="sxs-lookup"><span data-stu-id="94836-107">The following table shows the literal types in F#.</span></span> <span data-ttu-id="94836-108">Znaky, které představují číslice v šestnáctkové soustavě nerozlišují; znaky, které označují typ rozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="94836-108">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="94836-109">Type</span><span class="sxs-lookup"><span data-stu-id="94836-109">Type</span></span>|<span data-ttu-id="94836-110">Popis</span><span class="sxs-lookup"><span data-stu-id="94836-110">Description</span></span>|<span data-ttu-id="94836-111">Přípona nebo předpona</span><span class="sxs-lookup"><span data-stu-id="94836-111">Suffix or prefix</span></span>|<span data-ttu-id="94836-112">Příklady</span><span class="sxs-lookup"><span data-stu-id="94836-112">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="94836-113">sbyte</span><span class="sxs-lookup"><span data-stu-id="94836-113">sbyte</span></span>|<span data-ttu-id="94836-114">8bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="94836-114">signed 8-bit integer</span></span>|<span data-ttu-id="94836-115">y</span><span class="sxs-lookup"><span data-stu-id="94836-115">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="94836-116">byte</span><span class="sxs-lookup"><span data-stu-id="94836-116">byte</span></span>|<span data-ttu-id="94836-117">přirozené číslo bez znaménka 8 bitů</span><span class="sxs-lookup"><span data-stu-id="94836-117">unsigned 8-bit natural number</span></span>|<span data-ttu-id="94836-118">UY</span><span class="sxs-lookup"><span data-stu-id="94836-118">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="94836-119">int16</span><span class="sxs-lookup"><span data-stu-id="94836-119">int16</span></span>|<span data-ttu-id="94836-120">16bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="94836-120">signed 16-bit integer</span></span>|<span data-ttu-id="94836-121">s</span><span class="sxs-lookup"><span data-stu-id="94836-121">s</span></span>|`86s`|
|<span data-ttu-id="94836-122">uint16</span><span class="sxs-lookup"><span data-stu-id="94836-122">uint16</span></span>|<span data-ttu-id="94836-123">přirozené číslo bez znaménka 16 bitů</span><span class="sxs-lookup"><span data-stu-id="94836-123">unsigned 16-bit natural number</span></span>|<span data-ttu-id="94836-124">USA</span><span class="sxs-lookup"><span data-stu-id="94836-124">us</span></span>|`86us`|
|<span data-ttu-id="94836-125">int</span><span class="sxs-lookup"><span data-stu-id="94836-125">int</span></span><br /><br /><span data-ttu-id="94836-126">int32</span><span class="sxs-lookup"><span data-stu-id="94836-126">int32</span></span>|<span data-ttu-id="94836-127">32bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="94836-127">signed 32-bit integer</span></span>|<span data-ttu-id="94836-128">l nebo žádný</span><span class="sxs-lookup"><span data-stu-id="94836-128">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="94836-129">uint</span><span class="sxs-lookup"><span data-stu-id="94836-129">uint</span></span><br /><br /><span data-ttu-id="94836-130">uint32</span><span class="sxs-lookup"><span data-stu-id="94836-130">uint32</span></span>|<span data-ttu-id="94836-131">přirozené číslo bez znaménka 32-bit</span><span class="sxs-lookup"><span data-stu-id="94836-131">unsigned 32-bit natural number</span></span>|<span data-ttu-id="94836-132">u nebo ul</span><span class="sxs-lookup"><span data-stu-id="94836-132">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="94836-133">nativeint –</span><span class="sxs-lookup"><span data-stu-id="94836-133">nativeint</span></span>|<span data-ttu-id="94836-134">Nativní ukazatel na číslo se znaménkem přirozeného</span><span class="sxs-lookup"><span data-stu-id="94836-134">native pointer to a signed natural number</span></span>|<span data-ttu-id="94836-135">n</span><span class="sxs-lookup"><span data-stu-id="94836-135">n</span></span>|`123n`|
|<span data-ttu-id="94836-136">unativeint –</span><span class="sxs-lookup"><span data-stu-id="94836-136">unativeint</span></span>|<span data-ttu-id="94836-137">Nativní ukazatel jako přirozené číslo bez znaménka</span><span class="sxs-lookup"><span data-stu-id="94836-137">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="94836-138">zrušení</span><span class="sxs-lookup"><span data-stu-id="94836-138">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="94836-139">int64</span><span class="sxs-lookup"><span data-stu-id="94836-139">int64</span></span>|<span data-ttu-id="94836-140">64bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="94836-140">signed 64-bit integer</span></span>|<span data-ttu-id="94836-141">L</span><span class="sxs-lookup"><span data-stu-id="94836-141">L</span></span>|`86L`|
|<span data-ttu-id="94836-142">uint64</span><span class="sxs-lookup"><span data-stu-id="94836-142">uint64</span></span>|<span data-ttu-id="94836-143">přirozené číslo bez znaménka 64-bit</span><span class="sxs-lookup"><span data-stu-id="94836-143">unsigned 64-bit natural number</span></span>|<span data-ttu-id="94836-144">UL</span><span class="sxs-lookup"><span data-stu-id="94836-144">UL</span></span>|`86UL`|
|<span data-ttu-id="94836-145">jeden, float32.</span><span class="sxs-lookup"><span data-stu-id="94836-145">single, float32</span></span>|<span data-ttu-id="94836-146">32bitové číslo s plovoucí desetinnou</span><span class="sxs-lookup"><span data-stu-id="94836-146">32-bit floating point number</span></span>|<span data-ttu-id="94836-147">F nebo f</span><span class="sxs-lookup"><span data-stu-id="94836-147">F or f</span></span>|<span data-ttu-id="94836-148">`4.14F` Nebo `4.14f`</span><span class="sxs-lookup"><span data-stu-id="94836-148">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="94836-149">lf</span><span class="sxs-lookup"><span data-stu-id="94836-149">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="94836-150">plovoucí; Double</span><span class="sxs-lookup"><span data-stu-id="94836-150">float; double</span></span>|<span data-ttu-id="94836-151">64bitové číslo s plovoucí desetinnou</span><span class="sxs-lookup"><span data-stu-id="94836-151">64-bit floating point number</span></span>|<span data-ttu-id="94836-152">žádná</span><span class="sxs-lookup"><span data-stu-id="94836-152">none</span></span>|<span data-ttu-id="94836-153">`4.14` nebo `2.3E+32` nebo `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="94836-153">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="94836-154">LF</span><span class="sxs-lookup"><span data-stu-id="94836-154">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="94836-155">bigint</span><span class="sxs-lookup"><span data-stu-id="94836-155">bigint</span></span>|<span data-ttu-id="94836-156">celé číslo, ne pouze 64bitové znázornění</span><span class="sxs-lookup"><span data-stu-id="94836-156">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="94836-157">I</span><span class="sxs-lookup"><span data-stu-id="94836-157">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="94836-158">decimal</span><span class="sxs-lookup"><span data-stu-id="94836-158">decimal</span></span>|<span data-ttu-id="94836-159">desetinné číslo, které jsou reprezentovány jako pevný bod nebo racionální číslo</span><span class="sxs-lookup"><span data-stu-id="94836-159">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="94836-160">M nebo m</span><span class="sxs-lookup"><span data-stu-id="94836-160">M or m</span></span>|<span data-ttu-id="94836-161">`0.7833M` Nebo `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="94836-161">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="94836-162">Char</span><span class="sxs-lookup"><span data-stu-id="94836-162">Char</span></span>|<span data-ttu-id="94836-163">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="94836-163">Unicode character</span></span>|<span data-ttu-id="94836-164">žádná</span><span class="sxs-lookup"><span data-stu-id="94836-164">none</span></span>|`'a'`|
|<span data-ttu-id="94836-165">String</span><span class="sxs-lookup"><span data-stu-id="94836-165">String</span></span>|<span data-ttu-id="94836-166">Řetězec znaků Unicode</span><span class="sxs-lookup"><span data-stu-id="94836-166">Unicode string</span></span>|<span data-ttu-id="94836-167">žádná</span><span class="sxs-lookup"><span data-stu-id="94836-167">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="94836-168">or</span><span class="sxs-lookup"><span data-stu-id="94836-168">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="94836-169">or</span><span class="sxs-lookup"><span data-stu-id="94836-169">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="94836-170">or</span><span class="sxs-lookup"><span data-stu-id="94836-170">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="94836-171">Viz také [řetězce](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="94836-171">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="94836-172">byte</span><span class="sxs-lookup"><span data-stu-id="94836-172">byte</span></span>|<span data-ttu-id="94836-173">Znak ASCII</span><span class="sxs-lookup"><span data-stu-id="94836-173">ASCII character</span></span>|<span data-ttu-id="94836-174">B</span><span class="sxs-lookup"><span data-stu-id="94836-174">B</span></span>|`'a'B`|
|<span data-ttu-id="94836-175">Byte</span><span class="sxs-lookup"><span data-stu-id="94836-175">byte[]</span></span>|<span data-ttu-id="94836-176">Řetězec ASCII</span><span class="sxs-lookup"><span data-stu-id="94836-176">ASCII string</span></span>|<span data-ttu-id="94836-177">B</span><span class="sxs-lookup"><span data-stu-id="94836-177">B</span></span>|`"text"B`|
|<span data-ttu-id="94836-178">Řetězec nebo byte]</span><span class="sxs-lookup"><span data-stu-id="94836-178">String or byte[]</span></span>|<span data-ttu-id="94836-179">řetězec verbatim</span><span class="sxs-lookup"><span data-stu-id="94836-179">verbatim string</span></span>|<span data-ttu-id="94836-180">předponu @</span><span class="sxs-lookup"><span data-stu-id="94836-180">@ prefix</span></span>|<span data-ttu-id="94836-181">`@"\\server\share"` (Unicode)</span><span class="sxs-lookup"><span data-stu-id="94836-181">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="94836-182">`@"\\server\share"B` (ASCII)</span><span class="sxs-lookup"><span data-stu-id="94836-182">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="named-literals"></a><span data-ttu-id="94836-183">Pojmenované literály</span><span class="sxs-lookup"><span data-stu-id="94836-183">Named literals</span></span>

<span data-ttu-id="94836-184">Hodnoty, které mají být konstantami, mohou být označeny [literálu](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) atribut.</span><span class="sxs-lookup"><span data-stu-id="94836-184">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="94836-185">Tento atribut má efekt sestavení hodnoty se zkompiluje jako konstanta.</span><span class="sxs-lookup"><span data-stu-id="94836-185">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="94836-186">Ve vzoru porovnávání výrazů identifikátory, které začínají malými písmeny, jsou vždy považovány za proměnné ke svázání, nikoli jako literály, takže obecně používejte počáteční velká písmena při definování literálů.</span><span class="sxs-lookup"><span data-stu-id="94836-186">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="94836-187">Poznámky</span><span class="sxs-lookup"><span data-stu-id="94836-187">Remarks</span></span>

<span data-ttu-id="94836-188">Řetězce Unicode mohou obsahovat explicitní kódování, kterou lze zadat pomocí `\u` 16bitové šestnáctkové nebo UTF-32 kódování, kterou lze zadat pomocí `\U` za nímž následuje 32-bit šestnáctkový kód, který představuje Unicode náhradní pár.</span><span class="sxs-lookup"><span data-stu-id="94836-188">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents a Unicode surrogate pair.</span></span>

<span data-ttu-id="94836-189">Použití jiných operátorů bitového jiných než `|||` není povolený.</span><span class="sxs-lookup"><span data-stu-id="94836-189">The use of other bitwise operators other than `|||` isn't allowed.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="94836-190">Celá čísla v jiných základů</span><span class="sxs-lookup"><span data-stu-id="94836-190">Integers in other bases</span></span>

<span data-ttu-id="94836-191">Je taky možné specifikovat podepsaný 32bitová celá čísla v šestnáctkové soustavě, osmičkové nebo binární pomocí `0x`, `0o` nebo `0b` předpony v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="94836-191">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="94836-192">Podtržítka v numerických literálech</span><span class="sxs-lookup"><span data-stu-id="94836-192">Underscores in numeric literals</span></span>

<span data-ttu-id="94836-193">Číslice můžete oddělit znakem podtržítka (`_`).</span><span class="sxs-lookup"><span data-stu-id="94836-193">You can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="94836-194">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94836-194">See also</span></span>

- [<span data-ttu-id="94836-195">Core.literalattribute – třída</span><span class="sxs-lookup"><span data-stu-id="94836-195">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
