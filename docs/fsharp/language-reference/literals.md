---
title: Literály (F#)
description: 'Další informace o typy literálu v programovacím jazyce F #.'
ms.date: 05/16/2016
ms.openlocfilehash: e6d34acd928edce8447c793105b08085ab0757b9
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44035775"
---
# <a name="literals"></a><span data-ttu-id="4cb35-103">Literály</span><span class="sxs-lookup"><span data-stu-id="4cb35-103">Literals</span></span>

> [!NOTE]
<span data-ttu-id="4cb35-104">Rozhraní API referenčních odkazů v tomto článku se dostanete na webu MSDN (prozatím).</span><span class="sxs-lookup"><span data-stu-id="4cb35-104">The API reference links in this article will take you to MSDN (for now).</span></span>

<span data-ttu-id="4cb35-105">Toto téma obsahuje tabulku, která ukazuje, jak určit typ literály v F #.</span><span class="sxs-lookup"><span data-stu-id="4cb35-105">This topic provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="4cb35-106">Typy literálu</span><span class="sxs-lookup"><span data-stu-id="4cb35-106">Literal Types</span></span>

<span data-ttu-id="4cb35-107">Následující tabulka uvádí typy literálu v F #.</span><span class="sxs-lookup"><span data-stu-id="4cb35-107">The following table shows the literal types in F#.</span></span> <span data-ttu-id="4cb35-108">Znaky, které představují číslice v šestnáctkové soustavě nerozlišují; znaky, které označují typ rozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="4cb35-108">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="4cb35-109">Typ</span><span class="sxs-lookup"><span data-stu-id="4cb35-109">Type</span></span>|<span data-ttu-id="4cb35-110">Popis</span><span class="sxs-lookup"><span data-stu-id="4cb35-110">Description</span></span>|<span data-ttu-id="4cb35-111">Přípona nebo předpona</span><span class="sxs-lookup"><span data-stu-id="4cb35-111">Suffix or prefix</span></span>|<span data-ttu-id="4cb35-112">Příklady</span><span class="sxs-lookup"><span data-stu-id="4cb35-112">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="4cb35-113">sbyte</span><span class="sxs-lookup"><span data-stu-id="4cb35-113">sbyte</span></span>|<span data-ttu-id="4cb35-114">8bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="4cb35-114">signed 8-bit integer</span></span>|<span data-ttu-id="4cb35-115">y</span><span class="sxs-lookup"><span data-stu-id="4cb35-115">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="4cb35-116">byte</span><span class="sxs-lookup"><span data-stu-id="4cb35-116">byte</span></span>|<span data-ttu-id="4cb35-117">přirozené číslo bez znaménka 8 bitů</span><span class="sxs-lookup"><span data-stu-id="4cb35-117">unsigned 8-bit natural number</span></span>|<span data-ttu-id="4cb35-118">UY</span><span class="sxs-lookup"><span data-stu-id="4cb35-118">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="4cb35-119">Int16</span><span class="sxs-lookup"><span data-stu-id="4cb35-119">int16</span></span>|<span data-ttu-id="4cb35-120">16bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="4cb35-120">signed 16-bit integer</span></span>|<span data-ttu-id="4cb35-121">s</span><span class="sxs-lookup"><span data-stu-id="4cb35-121">s</span></span>|`86s`|
|<span data-ttu-id="4cb35-122">UInt16</span><span class="sxs-lookup"><span data-stu-id="4cb35-122">uint16</span></span>|<span data-ttu-id="4cb35-123">přirozené číslo bez znaménka 16 bitů</span><span class="sxs-lookup"><span data-stu-id="4cb35-123">unsigned 16-bit natural number</span></span>|<span data-ttu-id="4cb35-124">USA</span><span class="sxs-lookup"><span data-stu-id="4cb35-124">us</span></span>|`86us`|
|<span data-ttu-id="4cb35-125">int</span><span class="sxs-lookup"><span data-stu-id="4cb35-125">int</span></span><br /><br /><span data-ttu-id="4cb35-126">int32</span><span class="sxs-lookup"><span data-stu-id="4cb35-126">int32</span></span>|<span data-ttu-id="4cb35-127">32bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="4cb35-127">signed 32-bit integer</span></span>|<span data-ttu-id="4cb35-128">l nebo žádný</span><span class="sxs-lookup"><span data-stu-id="4cb35-128">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="4cb35-129">uint</span><span class="sxs-lookup"><span data-stu-id="4cb35-129">uint</span></span><br /><br /><span data-ttu-id="4cb35-130">UInt32</span><span class="sxs-lookup"><span data-stu-id="4cb35-130">uint32</span></span>|<span data-ttu-id="4cb35-131">přirozené číslo bez znaménka 32-bit</span><span class="sxs-lookup"><span data-stu-id="4cb35-131">unsigned 32-bit natural number</span></span>|<span data-ttu-id="4cb35-132">u nebo ul</span><span class="sxs-lookup"><span data-stu-id="4cb35-132">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="4cb35-133">unativeint –</span><span class="sxs-lookup"><span data-stu-id="4cb35-133">unativeint</span></span>|<span data-ttu-id="4cb35-134">Nativní ukazatel jako přirozené číslo bez znaménka</span><span class="sxs-lookup"><span data-stu-id="4cb35-134">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="4cb35-135">zrušení</span><span class="sxs-lookup"><span data-stu-id="4cb35-135">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="4cb35-136">int64</span><span class="sxs-lookup"><span data-stu-id="4cb35-136">int64</span></span>|<span data-ttu-id="4cb35-137">64bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="4cb35-137">signed 64-bit integer</span></span>|<span data-ttu-id="4cb35-138">L</span><span class="sxs-lookup"><span data-stu-id="4cb35-138">L</span></span>|`86L`|
|<span data-ttu-id="4cb35-139">UInt64</span><span class="sxs-lookup"><span data-stu-id="4cb35-139">uint64</span></span>|<span data-ttu-id="4cb35-140">přirozené číslo bez znaménka 64-bit</span><span class="sxs-lookup"><span data-stu-id="4cb35-140">unsigned 64-bit natural number</span></span>|<span data-ttu-id="4cb35-141">UL</span><span class="sxs-lookup"><span data-stu-id="4cb35-141">UL</span></span>|`86UL`|
|<span data-ttu-id="4cb35-142">jeden, float32.</span><span class="sxs-lookup"><span data-stu-id="4cb35-142">single, float32</span></span>|<span data-ttu-id="4cb35-143">32bitové číslo s plovoucí desetinnou</span><span class="sxs-lookup"><span data-stu-id="4cb35-143">32-bit floating point number</span></span>|<span data-ttu-id="4cb35-144">F nebo f</span><span class="sxs-lookup"><span data-stu-id="4cb35-144">F or f</span></span>|<span data-ttu-id="4cb35-145">`4.14F` Nebo `4.14f`</span><span class="sxs-lookup"><span data-stu-id="4cb35-145">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="4cb35-146">LF</span><span class="sxs-lookup"><span data-stu-id="4cb35-146">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="4cb35-147">plovoucí; Double</span><span class="sxs-lookup"><span data-stu-id="4cb35-147">float; double</span></span>|<span data-ttu-id="4cb35-148">64bitové číslo s plovoucí desetinnou</span><span class="sxs-lookup"><span data-stu-id="4cb35-148">64-bit floating point number</span></span>|<span data-ttu-id="4cb35-149">žádná</span><span class="sxs-lookup"><span data-stu-id="4cb35-149">none</span></span>|<span data-ttu-id="4cb35-150">`4.14` nebo `2.3E+32` nebo `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="4cb35-150">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="4cb35-151">LF</span><span class="sxs-lookup"><span data-stu-id="4cb35-151">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="4cb35-152">bigint</span><span class="sxs-lookup"><span data-stu-id="4cb35-152">bigint</span></span>|<span data-ttu-id="4cb35-153">celé číslo, ne pouze 64bitové znázornění</span><span class="sxs-lookup"><span data-stu-id="4cb35-153">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="4cb35-154">I</span><span class="sxs-lookup"><span data-stu-id="4cb35-154">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="4cb35-155">decimal</span><span class="sxs-lookup"><span data-stu-id="4cb35-155">decimal</span></span>|<span data-ttu-id="4cb35-156">desetinné číslo, které jsou reprezentovány jako pevný bod nebo racionální číslo</span><span class="sxs-lookup"><span data-stu-id="4cb35-156">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="4cb35-157">M nebo m</span><span class="sxs-lookup"><span data-stu-id="4cb35-157">M or m</span></span>|<span data-ttu-id="4cb35-158">`0.7833M` Nebo `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="4cb35-158">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="4cb35-159">Char</span><span class="sxs-lookup"><span data-stu-id="4cb35-159">Char</span></span>|<span data-ttu-id="4cb35-160">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="4cb35-160">Unicode character</span></span>|<span data-ttu-id="4cb35-161">žádná</span><span class="sxs-lookup"><span data-stu-id="4cb35-161">none</span></span>|`'a'`|
|<span data-ttu-id="4cb35-162">String</span><span class="sxs-lookup"><span data-stu-id="4cb35-162">String</span></span>|<span data-ttu-id="4cb35-163">Řetězec znaků Unicode</span><span class="sxs-lookup"><span data-stu-id="4cb35-163">Unicode string</span></span>|<span data-ttu-id="4cb35-164">žádná</span><span class="sxs-lookup"><span data-stu-id="4cb35-164">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="4cb35-165">or</span><span class="sxs-lookup"><span data-stu-id="4cb35-165">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="4cb35-166">or</span><span class="sxs-lookup"><span data-stu-id="4cb35-166">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="4cb35-167">or</span><span class="sxs-lookup"><span data-stu-id="4cb35-167">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="4cb35-168">Viz také [řetězce](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="4cb35-168">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="4cb35-169">byte</span><span class="sxs-lookup"><span data-stu-id="4cb35-169">byte</span></span>|<span data-ttu-id="4cb35-170">Znak ASCII</span><span class="sxs-lookup"><span data-stu-id="4cb35-170">ASCII character</span></span>|<span data-ttu-id="4cb35-171">B</span><span class="sxs-lookup"><span data-stu-id="4cb35-171">B</span></span>|`'a'B`|
|<span data-ttu-id="4cb35-172">Byte</span><span class="sxs-lookup"><span data-stu-id="4cb35-172">byte[]</span></span>|<span data-ttu-id="4cb35-173">Řetězec ASCII</span><span class="sxs-lookup"><span data-stu-id="4cb35-173">ASCII string</span></span>|<span data-ttu-id="4cb35-174">B</span><span class="sxs-lookup"><span data-stu-id="4cb35-174">B</span></span>|`"text"B`|
|<span data-ttu-id="4cb35-175">Řetězec nebo byte]</span><span class="sxs-lookup"><span data-stu-id="4cb35-175">String or byte[]</span></span>|<span data-ttu-id="4cb35-176">řetězec verbatim</span><span class="sxs-lookup"><span data-stu-id="4cb35-176">verbatim string</span></span>|<span data-ttu-id="4cb35-177">předponu @</span><span class="sxs-lookup"><span data-stu-id="4cb35-177">@ prefix</span></span>|<span data-ttu-id="4cb35-178">`@"\\server\share"` (Unicode)</span><span class="sxs-lookup"><span data-stu-id="4cb35-178">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="4cb35-179">`@"\\server\share"B` (ASCII)</span><span class="sxs-lookup"><span data-stu-id="4cb35-179">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="remarks"></a><span data-ttu-id="4cb35-180">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4cb35-180">Remarks</span></span>

<span data-ttu-id="4cb35-181">Řetězce Unicode mohou obsahovat explicitní kódování, kterou lze zadat pomocí `\u` 16bitové šestnáctkové nebo UTF-32 kódování, kterou lze zadat pomocí `\U` za nímž následuje 32-bit šestnáctkový kód, který představuje Unicode náhradní pár.</span><span class="sxs-lookup"><span data-stu-id="4cb35-181">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents a Unicode surrogate pair.</span></span>

<span data-ttu-id="4cb35-182">Od verze F # 3.1, můžete použít `+` přihlásit ke kombinování řetězcových literálů.</span><span class="sxs-lookup"><span data-stu-id="4cb35-182">As of F# 3.1, you can use the `+` sign to combine string literals.</span></span> <span data-ttu-id="4cb35-183">Můžete také použít bitového nebo (`|||`) operátor kombinování příznaků výčtu.</span><span class="sxs-lookup"><span data-stu-id="4cb35-183">You can also use the bitwise or (`|||`) operator to combine enum flags.</span></span> <span data-ttu-id="4cb35-184">Například následující kód je platný v F # 3.1:</span><span class="sxs-lookup"><span data-stu-id="4cb35-184">For example, the following code is legal in F# 3.1:</span></span>

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

<span data-ttu-id="4cb35-185">Použití jiných operátorů bitového typu není povoleno.</span><span class="sxs-lookup"><span data-stu-id="4cb35-185">The use of other bitwise operators isn't allowed.</span></span>

## <a name="named-literals"></a><span data-ttu-id="4cb35-186">Pojmenované literály</span><span class="sxs-lookup"><span data-stu-id="4cb35-186">Named Literals</span></span>

<span data-ttu-id="4cb35-187">Hodnoty, které mají být konstantami, mohou být označeny [literálu](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) atribut.</span><span class="sxs-lookup"><span data-stu-id="4cb35-187">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="4cb35-188">Tento atribut má efekt sestavení hodnoty se zkompiluje jako konstanta.</span><span class="sxs-lookup"><span data-stu-id="4cb35-188">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="4cb35-189">Ve vzoru porovnávání výrazů identifikátory, které začínají malými písmeny, jsou vždy považovány za proměnné ke svázání, nikoli jako literály, takže obecně používejte počáteční velká písmena při definování literálů.</span><span class="sxs-lookup"><span data-stu-id="4cb35-189">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="4cb35-190">Celá čísla v jiných základů</span><span class="sxs-lookup"><span data-stu-id="4cb35-190">Integers In Other Bases</span></span>

<span data-ttu-id="4cb35-191">Je taky možné specifikovat podepsaný 32bitová celá čísla v šestnáctkové soustavě, osmičkové nebo binární pomocí `0x`, `0o` nebo `0b` předpony v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="4cb35-191">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let Numbers = (0x9F, 0o77, 0b1010)
// Result: Numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="4cb35-192">Podtržítka v numerických literálech</span><span class="sxs-lookup"><span data-stu-id="4cb35-192">Underscores in Numeric Literals</span></span>

<span data-ttu-id="4cb35-193">Od verze F # 4.1, můžete oddělit číslic znakem podtržítka (`_`).</span><span class="sxs-lookup"><span data-stu-id="4cb35-193">Starting with F# 4.1, you can separate digits with the underscore character (`_`).</span></span>

```fsharp
let DeadBeef = 0xDEAD_BEEF

let DeadBeefAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let ExampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="4cb35-194">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4cb35-194">See also</span></span>

- [<span data-ttu-id="4cb35-195">Core.literalattribute – třída</span><span class="sxs-lookup"><span data-stu-id="4cb35-195">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
