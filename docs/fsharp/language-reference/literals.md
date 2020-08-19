---
title: Literály
description: 'Seznamte se s typy literálů v programovacím jazyce F #.'
ms.date: 08/15/2020
ms.openlocfilehash: 15f73db3c36f7c60ab1eeba96c63a28ebc6d7f01
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559151"
---
# <a name="literals"></a><span data-ttu-id="2ce06-103">Literály</span><span class="sxs-lookup"><span data-stu-id="2ce06-103">Literals</span></span>

<span data-ttu-id="2ce06-104">Tento článek obsahuje tabulku, která ukazuje, jak zadat typ literálu v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="2ce06-104">This article provides a table that shows how to specify the type of a literal in F#.</span></span>

## <a name="literal-types"></a><span data-ttu-id="2ce06-105">Typy literálů</span><span class="sxs-lookup"><span data-stu-id="2ce06-105">Literal types</span></span>

<span data-ttu-id="2ce06-106">V následující tabulce jsou uvedeny typy literálů v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="2ce06-106">The following table shows the literal types in F#.</span></span> <span data-ttu-id="2ce06-107">Znaky, které představují číslice v šestnáctkovém zápisu, nerozlišují velká a malá písmena; znaky, které identifikují typ, rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="2ce06-107">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="2ce06-108">Typ</span><span class="sxs-lookup"><span data-stu-id="2ce06-108">Type</span></span>|<span data-ttu-id="2ce06-109">Popis</span><span class="sxs-lookup"><span data-stu-id="2ce06-109">Description</span></span>|<span data-ttu-id="2ce06-110">Přípona nebo předpona</span><span class="sxs-lookup"><span data-stu-id="2ce06-110">Suffix or prefix</span></span>|<span data-ttu-id="2ce06-111">Příklady</span><span class="sxs-lookup"><span data-stu-id="2ce06-111">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="2ce06-112">sbyte</span><span class="sxs-lookup"><span data-stu-id="2ce06-112">sbyte</span></span>|<span data-ttu-id="2ce06-113">8bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="2ce06-113">signed 8-bit integer</span></span>|<span data-ttu-id="2ce06-114">y</span><span class="sxs-lookup"><span data-stu-id="2ce06-114">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="2ce06-115">byte</span><span class="sxs-lookup"><span data-stu-id="2ce06-115">byte</span></span>|<span data-ttu-id="2ce06-116">8bitové přirozené číslo bez znaménka</span><span class="sxs-lookup"><span data-stu-id="2ce06-116">unsigned 8-bit natural number</span></span>|<span data-ttu-id="2ce06-117">uy</span><span class="sxs-lookup"><span data-stu-id="2ce06-117">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="2ce06-118">Int16</span><span class="sxs-lookup"><span data-stu-id="2ce06-118">int16</span></span>|<span data-ttu-id="2ce06-119">16bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="2ce06-119">signed 16-bit integer</span></span>|<span data-ttu-id="2ce06-120">s</span><span class="sxs-lookup"><span data-stu-id="2ce06-120">s</span></span>|`86s`|
|<span data-ttu-id="2ce06-121">UInt16</span><span class="sxs-lookup"><span data-stu-id="2ce06-121">uint16</span></span>|<span data-ttu-id="2ce06-122">16bitové přirozené číslo bez znaménka</span><span class="sxs-lookup"><span data-stu-id="2ce06-122">unsigned 16-bit natural number</span></span>|<span data-ttu-id="2ce06-123">vylepšení</span><span class="sxs-lookup"><span data-stu-id="2ce06-123">us</span></span>|`86us`|
|<span data-ttu-id="2ce06-124">int</span><span class="sxs-lookup"><span data-stu-id="2ce06-124">int</span></span><br /><br /><span data-ttu-id="2ce06-125">uvedena</span><span class="sxs-lookup"><span data-stu-id="2ce06-125">int32</span></span>|<span data-ttu-id="2ce06-126">podepsané 32 – celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="2ce06-126">signed 32-bit integer</span></span>|<span data-ttu-id="2ce06-127">l nebo None</span><span class="sxs-lookup"><span data-stu-id="2ce06-127">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="2ce06-128">uint</span><span class="sxs-lookup"><span data-stu-id="2ce06-128">uint</span></span><br /><br /><span data-ttu-id="2ce06-129">UInt32</span><span class="sxs-lookup"><span data-stu-id="2ce06-129">uint32</span></span>|<span data-ttu-id="2ce06-130">nepodepsané 32 – přirozené číslo v bitech</span><span class="sxs-lookup"><span data-stu-id="2ce06-130">unsigned 32-bit natural number</span></span>|<span data-ttu-id="2ce06-131">u nebo ul</span><span class="sxs-lookup"><span data-stu-id="2ce06-131">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="2ce06-132">nativeint –</span><span class="sxs-lookup"><span data-stu-id="2ce06-132">nativeint</span></span>|<span data-ttu-id="2ce06-133">nativní ukazatel na podepsané přirozené číslo</span><span class="sxs-lookup"><span data-stu-id="2ce06-133">native pointer to a signed natural number</span></span>|<span data-ttu-id="2ce06-134">n</span><span class="sxs-lookup"><span data-stu-id="2ce06-134">n</span></span>|`123n`|
|<span data-ttu-id="2ce06-135">unativeint –</span><span class="sxs-lookup"><span data-stu-id="2ce06-135">unativeint</span></span>|<span data-ttu-id="2ce06-136">nativní ukazatel jako přirozené číslo bez znaménka</span><span class="sxs-lookup"><span data-stu-id="2ce06-136">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="2ce06-137">instalován</span><span class="sxs-lookup"><span data-stu-id="2ce06-137">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="2ce06-138">Int64</span><span class="sxs-lookup"><span data-stu-id="2ce06-138">int64</span></span>|<span data-ttu-id="2ce06-139">podepsané 64 – celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="2ce06-139">signed 64-bit integer</span></span>|<span data-ttu-id="2ce06-140">L</span><span class="sxs-lookup"><span data-stu-id="2ce06-140">L</span></span>|`86L`|
|<span data-ttu-id="2ce06-141">UInt64</span><span class="sxs-lookup"><span data-stu-id="2ce06-141">uint64</span></span>|<span data-ttu-id="2ce06-142">nepodepsané 64 – přirozené číslo v bitech</span><span class="sxs-lookup"><span data-stu-id="2ce06-142">unsigned 64-bit natural number</span></span>|<span data-ttu-id="2ce06-143">UL</span><span class="sxs-lookup"><span data-stu-id="2ce06-143">UL</span></span>|`86UL`|
|<span data-ttu-id="2ce06-144">Single, float32</span><span class="sxs-lookup"><span data-stu-id="2ce06-144">single, float32</span></span>|<span data-ttu-id="2ce06-145">32-bitové číslo s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="2ce06-145">32-bit floating point number</span></span>|<span data-ttu-id="2ce06-146">F nebo f</span><span class="sxs-lookup"><span data-stu-id="2ce06-146">F or f</span></span>|<span data-ttu-id="2ce06-147">`4.14F` nebo `4.14f`</span><span class="sxs-lookup"><span data-stu-id="2ce06-147">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="2ce06-148">znaky</span><span class="sxs-lookup"><span data-stu-id="2ce06-148">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="2ce06-149">Plovák klepat</span><span class="sxs-lookup"><span data-stu-id="2ce06-149">float; double</span></span>|<span data-ttu-id="2ce06-150">64-bitové číslo s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="2ce06-150">64-bit floating point number</span></span>|<span data-ttu-id="2ce06-151">žádné</span><span class="sxs-lookup"><span data-stu-id="2ce06-151">none</span></span>|<span data-ttu-id="2ce06-152">`4.14` nebo `2.3E+32` nebo `2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="2ce06-152">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="2ce06-153">ZNAKY</span><span class="sxs-lookup"><span data-stu-id="2ce06-153">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="2ce06-154">bigint</span><span class="sxs-lookup"><span data-stu-id="2ce06-154">bigint</span></span>|<span data-ttu-id="2ce06-155">celé číslo není omezeno na 64-bitovou reprezentaci</span><span class="sxs-lookup"><span data-stu-id="2ce06-155">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="2ce06-156">I</span><span class="sxs-lookup"><span data-stu-id="2ce06-156">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="2ce06-157">decimal</span><span class="sxs-lookup"><span data-stu-id="2ce06-157">decimal</span></span>|<span data-ttu-id="2ce06-158">desetinné číslo reprezentované jako pevný bod nebo racionální číslo</span><span class="sxs-lookup"><span data-stu-id="2ce06-158">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="2ce06-159">M nebo m</span><span class="sxs-lookup"><span data-stu-id="2ce06-159">M or m</span></span>|<span data-ttu-id="2ce06-160">`0.7833M` nebo `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="2ce06-160">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="2ce06-161">Char</span><span class="sxs-lookup"><span data-stu-id="2ce06-161">Char</span></span>|<span data-ttu-id="2ce06-162">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="2ce06-162">Unicode character</span></span>|<span data-ttu-id="2ce06-163">žádné</span><span class="sxs-lookup"><span data-stu-id="2ce06-163">none</span></span>|<span data-ttu-id="2ce06-164">`'a'` nebo `'\u0061'`</span><span class="sxs-lookup"><span data-stu-id="2ce06-164">`'a'` or `'\u0061'`</span></span>|
|<span data-ttu-id="2ce06-165">Řetězec</span><span class="sxs-lookup"><span data-stu-id="2ce06-165">String</span></span>|<span data-ttu-id="2ce06-166">Řetězec Unicode</span><span class="sxs-lookup"><span data-stu-id="2ce06-166">Unicode string</span></span>|<span data-ttu-id="2ce06-167">žádné</span><span class="sxs-lookup"><span data-stu-id="2ce06-167">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="2ce06-168">nebo</span><span class="sxs-lookup"><span data-stu-id="2ce06-168">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="2ce06-169">nebo</span><span class="sxs-lookup"><span data-stu-id="2ce06-169">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="2ce06-170">nebo</span><span class="sxs-lookup"><span data-stu-id="2ce06-170">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="2ce06-171">Viz také [řetězce](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="2ce06-171">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="2ce06-172">byte</span><span class="sxs-lookup"><span data-stu-id="2ce06-172">byte</span></span>|<span data-ttu-id="2ce06-173">Znak ASCII</span><span class="sxs-lookup"><span data-stu-id="2ce06-173">ASCII character</span></span>|<span data-ttu-id="2ce06-174">B</span><span class="sxs-lookup"><span data-stu-id="2ce06-174">B</span></span>|`'a'B`|
|<span data-ttu-id="2ce06-175">Byte []</span><span class="sxs-lookup"><span data-stu-id="2ce06-175">byte[]</span></span>|<span data-ttu-id="2ce06-176">Řetězec ASCII</span><span class="sxs-lookup"><span data-stu-id="2ce06-176">ASCII string</span></span>|<span data-ttu-id="2ce06-177">B</span><span class="sxs-lookup"><span data-stu-id="2ce06-177">B</span></span>|`"text"B`|
|<span data-ttu-id="2ce06-178">Řetězec nebo Byte []</span><span class="sxs-lookup"><span data-stu-id="2ce06-178">String or byte[]</span></span>|<span data-ttu-id="2ce06-179">řetězec doslovného řetězce</span><span class="sxs-lookup"><span data-stu-id="2ce06-179">verbatim string</span></span>|<span data-ttu-id="2ce06-180">@ prefix</span><span class="sxs-lookup"><span data-stu-id="2ce06-180">@ prefix</span></span>|<span data-ttu-id="2ce06-181">`@"\\server\share"` Sady</span><span class="sxs-lookup"><span data-stu-id="2ce06-181">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="2ce06-182">`@"\\server\share"B` Abecední</span><span class="sxs-lookup"><span data-stu-id="2ce06-182">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="named-literals"></a><span data-ttu-id="2ce06-183">Pojmenované literály</span><span class="sxs-lookup"><span data-stu-id="2ce06-183">Named literals</span></span>

<span data-ttu-id="2ce06-184">Hodnoty, které mají být konstanty, mohou být označeny atributem [Literal](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-literalattribute.html) .</span><span class="sxs-lookup"><span data-stu-id="2ce06-184">Values that are intended to be constants can be marked with the [Literal](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-core-literalattribute.html) attribute.</span></span> <span data-ttu-id="2ce06-185">Tento atribut má vliv, který způsobí, že se hodnota zkompiluje jako konstanta.</span><span class="sxs-lookup"><span data-stu-id="2ce06-185">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="2ce06-186">V výrazech porovnávání se vzorem se identifikátory začínající malým písmenem vždy považují za proměnné, které mají být vázány, nikoli jako literály, takže při definování literálů byste obecně měli použít počáteční velká písmena.</span><span class="sxs-lookup"><span data-stu-id="2ce06-186">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="2ce06-187">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ce06-187">Remarks</span></span>

<span data-ttu-id="2ce06-188">Řetězce v kódování Unicode mohou obsahovat explicitní kódování, která lze zadat pomocí `\u` 16bitového šestnáctkového kódu (0000-FFFF), nebo kódování UTF-32, které lze zadat pomocí `\U` kódu a 32 hexadecimálního kódu, který představuje libovolný bod kódu Unicode (00000000-0010FFFF).</span><span class="sxs-lookup"><span data-stu-id="2ce06-188">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code (0000 - FFFF), or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents any Unicode code point (00000000 - 0010FFFF).</span></span>

<span data-ttu-id="2ce06-189">Použití jiných bitových operátorů kromě `|||` není povoleno.</span><span class="sxs-lookup"><span data-stu-id="2ce06-189">The use of other bitwise operators other than `|||` isn't allowed.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="2ce06-190">Celá čísla v jiných základech</span><span class="sxs-lookup"><span data-stu-id="2ce06-190">Integers in other bases</span></span>

<span data-ttu-id="2ce06-191">Podepsaná 32 celočíselná celá čísla lze také zadat v šestnáctkovém, osmičkovém nebo binárním formátu `0x` pomocí `0o` `0b` předpony nebo v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="2ce06-191">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="2ce06-192">Podtržítka v numerických literálech</span><span class="sxs-lookup"><span data-stu-id="2ce06-192">Underscores in numeric literals</span></span>

<span data-ttu-id="2ce06-193">Můžete oddělit číslice znakem podtržítka ( `_` ).</span><span class="sxs-lookup"><span data-stu-id="2ce06-193">You can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```
