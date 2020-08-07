---
title: Literály
description: 'Seznamte se s typy literálů v programovacím jazyce F #.'
ms.date: 06/28/2019
ms.openlocfilehash: 98d609a1cf0beb00c0dd4d45ea343aaa2280b62e
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855020"
---
# <a name="literals"></a><span data-ttu-id="9703e-103">Literály</span><span class="sxs-lookup"><span data-stu-id="9703e-103">Literals</span></span>

<span data-ttu-id="9703e-104">Tento článek obsahuje tabulku, která ukazuje, jak zadat typ literálu v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="9703e-104">This article provides a table that shows how to specify the type of a literal in F#.</span></span>

> [!NOTE]
> <span data-ttu-id="9703e-105">Reference k rozhraní docs.microsoft.com API pro F # není dokončená.</span><span class="sxs-lookup"><span data-stu-id="9703e-105">The docs.microsoft.com API reference for F# is not complete.</span></span> <span data-ttu-id="9703e-106">Pokud narazíte na nefunkční odkazy, místo toho použijte [dokumentaci základní knihovny F #](https://fsharp.github.io/fsharp-core-docs/) .</span><span class="sxs-lookup"><span data-stu-id="9703e-106">If you encounter any broken links, reference [F# Core Library Documentation](https://fsharp.github.io/fsharp-core-docs/) instead.</span></span>

## <a name="literal-types"></a><span data-ttu-id="9703e-107">Typy literálů</span><span class="sxs-lookup"><span data-stu-id="9703e-107">Literal types</span></span>

<span data-ttu-id="9703e-108">V následující tabulce jsou uvedeny typy literálů v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="9703e-108">The following table shows the literal types in F#.</span></span> <span data-ttu-id="9703e-109">Znaky, které představují číslice v šestnáctkovém zápisu, nerozlišují velká a malá písmena; znaky, které identifikují typ, rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="9703e-109">Characters that represent digits in hexadecimal notation are not case-sensitive; characters that identify the type are case-sensitive.</span></span>

|<span data-ttu-id="9703e-110">Typ</span><span class="sxs-lookup"><span data-stu-id="9703e-110">Type</span></span>|<span data-ttu-id="9703e-111">Popis</span><span class="sxs-lookup"><span data-stu-id="9703e-111">Description</span></span>|<span data-ttu-id="9703e-112">Přípona nebo předpona</span><span class="sxs-lookup"><span data-stu-id="9703e-112">Suffix or prefix</span></span>|<span data-ttu-id="9703e-113">Příklady</span><span class="sxs-lookup"><span data-stu-id="9703e-113">Examples</span></span>|
|----|-----------|----------------|--------|
|<span data-ttu-id="9703e-114">sbyte</span><span class="sxs-lookup"><span data-stu-id="9703e-114">sbyte</span></span>|<span data-ttu-id="9703e-115">8bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="9703e-115">signed 8-bit integer</span></span>|<span data-ttu-id="9703e-116">y</span><span class="sxs-lookup"><span data-stu-id="9703e-116">y</span></span>|`86y`<br /><br />`0b00000101y`|
|<span data-ttu-id="9703e-117">byte</span><span class="sxs-lookup"><span data-stu-id="9703e-117">byte</span></span>|<span data-ttu-id="9703e-118">8bitové přirozené číslo bez znaménka</span><span class="sxs-lookup"><span data-stu-id="9703e-118">unsigned 8-bit natural number</span></span>|<span data-ttu-id="9703e-119">uy</span><span class="sxs-lookup"><span data-stu-id="9703e-119">uy</span></span>|`86uy`<br /><br />`0b00000101uy`|
|<span data-ttu-id="9703e-120">Int16</span><span class="sxs-lookup"><span data-stu-id="9703e-120">int16</span></span>|<span data-ttu-id="9703e-121">16bitové celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="9703e-121">signed 16-bit integer</span></span>|<span data-ttu-id="9703e-122">s</span><span class="sxs-lookup"><span data-stu-id="9703e-122">s</span></span>|`86s`|
|<span data-ttu-id="9703e-123">UInt16</span><span class="sxs-lookup"><span data-stu-id="9703e-123">uint16</span></span>|<span data-ttu-id="9703e-124">16bitové přirozené číslo bez znaménka</span><span class="sxs-lookup"><span data-stu-id="9703e-124">unsigned 16-bit natural number</span></span>|<span data-ttu-id="9703e-125">vylepšení</span><span class="sxs-lookup"><span data-stu-id="9703e-125">us</span></span>|`86us`|
|<span data-ttu-id="9703e-126">int</span><span class="sxs-lookup"><span data-stu-id="9703e-126">int</span></span><br /><br /><span data-ttu-id="9703e-127">uvedena</span><span class="sxs-lookup"><span data-stu-id="9703e-127">int32</span></span>|<span data-ttu-id="9703e-128">podepsané 32 – celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="9703e-128">signed 32-bit integer</span></span>|<span data-ttu-id="9703e-129">l nebo None</span><span class="sxs-lookup"><span data-stu-id="9703e-129">l or none</span></span>|`86`<br /><br />`86l`|
|<span data-ttu-id="9703e-130">uint</span><span class="sxs-lookup"><span data-stu-id="9703e-130">uint</span></span><br /><br /><span data-ttu-id="9703e-131">UInt32</span><span class="sxs-lookup"><span data-stu-id="9703e-131">uint32</span></span>|<span data-ttu-id="9703e-132">nepodepsané 32 – přirozené číslo v bitech</span><span class="sxs-lookup"><span data-stu-id="9703e-132">unsigned 32-bit natural number</span></span>|<span data-ttu-id="9703e-133">u nebo ul</span><span class="sxs-lookup"><span data-stu-id="9703e-133">u or ul</span></span>|`86u`<br /><br />`86ul`|
|<span data-ttu-id="9703e-134">nativeint –</span><span class="sxs-lookup"><span data-stu-id="9703e-134">nativeint</span></span>|<span data-ttu-id="9703e-135">nativní ukazatel na podepsané přirozené číslo</span><span class="sxs-lookup"><span data-stu-id="9703e-135">native pointer to a signed natural number</span></span>|<span data-ttu-id="9703e-136">n</span><span class="sxs-lookup"><span data-stu-id="9703e-136">n</span></span>|`123n`|
|<span data-ttu-id="9703e-137">unativeint –</span><span class="sxs-lookup"><span data-stu-id="9703e-137">unativeint</span></span>|<span data-ttu-id="9703e-138">nativní ukazatel jako přirozené číslo bez znaménka</span><span class="sxs-lookup"><span data-stu-id="9703e-138">native pointer as an unsigned natural number</span></span>|<span data-ttu-id="9703e-139">instalován</span><span class="sxs-lookup"><span data-stu-id="9703e-139">un</span></span>|`0x00002D3Fun`|
|<span data-ttu-id="9703e-140">Int64</span><span class="sxs-lookup"><span data-stu-id="9703e-140">int64</span></span>|<span data-ttu-id="9703e-141">podepsané 64 – celé číslo se znaménkem</span><span class="sxs-lookup"><span data-stu-id="9703e-141">signed 64-bit integer</span></span>|<span data-ttu-id="9703e-142">L</span><span class="sxs-lookup"><span data-stu-id="9703e-142">L</span></span>|`86L`|
|<span data-ttu-id="9703e-143">UInt64</span><span class="sxs-lookup"><span data-stu-id="9703e-143">uint64</span></span>|<span data-ttu-id="9703e-144">nepodepsané 64 – přirozené číslo v bitech</span><span class="sxs-lookup"><span data-stu-id="9703e-144">unsigned 64-bit natural number</span></span>|<span data-ttu-id="9703e-145">UL</span><span class="sxs-lookup"><span data-stu-id="9703e-145">UL</span></span>|`86UL`|
|<span data-ttu-id="9703e-146">Single, float32</span><span class="sxs-lookup"><span data-stu-id="9703e-146">single, float32</span></span>|<span data-ttu-id="9703e-147">32-bitové číslo s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="9703e-147">32-bit floating point number</span></span>|<span data-ttu-id="9703e-148">F nebo f</span><span class="sxs-lookup"><span data-stu-id="9703e-148">F or f</span></span>|<span data-ttu-id="9703e-149">`4.14F` nebo `4.14f`</span><span class="sxs-lookup"><span data-stu-id="9703e-149">`4.14F` or `4.14f`</span></span>|
|||<span data-ttu-id="9703e-150">znaky</span><span class="sxs-lookup"><span data-stu-id="9703e-150">lf</span></span>|`0x00000000lf`|
|<span data-ttu-id="9703e-151">Plovák klepat</span><span class="sxs-lookup"><span data-stu-id="9703e-151">float; double</span></span>|<span data-ttu-id="9703e-152">64-bitové číslo s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="9703e-152">64-bit floating point number</span></span>|<span data-ttu-id="9703e-153">žádné</span><span class="sxs-lookup"><span data-stu-id="9703e-153">none</span></span>|<span data-ttu-id="9703e-154">`4.14`nebo `2.3E+32` nebo`2.3e+32`</span><span class="sxs-lookup"><span data-stu-id="9703e-154">`4.14` or `2.3E+32` or `2.3e+32`</span></span>|
|||<span data-ttu-id="9703e-155">ZNAKY</span><span class="sxs-lookup"><span data-stu-id="9703e-155">LF</span></span>|`0x0000000000000000LF`|
|<span data-ttu-id="9703e-156">bigint</span><span class="sxs-lookup"><span data-stu-id="9703e-156">bigint</span></span>|<span data-ttu-id="9703e-157">celé číslo není omezeno na 64-bitovou reprezentaci</span><span class="sxs-lookup"><span data-stu-id="9703e-157">integer not limited to 64-bit representation</span></span>|<span data-ttu-id="9703e-158">I</span><span class="sxs-lookup"><span data-stu-id="9703e-158">I</span></span>|`9999999999999999999999999999I`|
|<span data-ttu-id="9703e-159">decimal</span><span class="sxs-lookup"><span data-stu-id="9703e-159">decimal</span></span>|<span data-ttu-id="9703e-160">desetinné číslo reprezentované jako pevný bod nebo racionální číslo</span><span class="sxs-lookup"><span data-stu-id="9703e-160">fractional number represented as a fixed point or rational number</span></span>|<span data-ttu-id="9703e-161">M nebo m</span><span class="sxs-lookup"><span data-stu-id="9703e-161">M or m</span></span>|<span data-ttu-id="9703e-162">`0.7833M` nebo `0.7833m`</span><span class="sxs-lookup"><span data-stu-id="9703e-162">`0.7833M` or `0.7833m`</span></span>|
|<span data-ttu-id="9703e-163">Char</span><span class="sxs-lookup"><span data-stu-id="9703e-163">Char</span></span>|<span data-ttu-id="9703e-164">znak Unicode</span><span class="sxs-lookup"><span data-stu-id="9703e-164">Unicode character</span></span>|<span data-ttu-id="9703e-165">žádné</span><span class="sxs-lookup"><span data-stu-id="9703e-165">none</span></span>|<span data-ttu-id="9703e-166">`'a'` nebo `'\u0061'`</span><span class="sxs-lookup"><span data-stu-id="9703e-166">`'a'` or `'\u0061'`</span></span>|
|<span data-ttu-id="9703e-167">Řetězec</span><span class="sxs-lookup"><span data-stu-id="9703e-167">String</span></span>|<span data-ttu-id="9703e-168">Řetězec Unicode</span><span class="sxs-lookup"><span data-stu-id="9703e-168">Unicode string</span></span>|<span data-ttu-id="9703e-169">žádné</span><span class="sxs-lookup"><span data-stu-id="9703e-169">none</span></span>|`"text\n"`<br /><br /><span data-ttu-id="9703e-170">– nebo –</span><span class="sxs-lookup"><span data-stu-id="9703e-170">or</span></span><br /><br />`@"c:\filename"`<br /><br /><span data-ttu-id="9703e-171">– nebo –</span><span class="sxs-lookup"><span data-stu-id="9703e-171">or</span></span><br /><br />`"""<book title="Paradise Lost">"""`<br /><br /><span data-ttu-id="9703e-172">– nebo –</span><span class="sxs-lookup"><span data-stu-id="9703e-172">or</span></span><br /><br />`"string1" + "string2"`<br /><br /><span data-ttu-id="9703e-173">Viz také [řetězce](Strings.md).</span><span class="sxs-lookup"><span data-stu-id="9703e-173">See also [Strings](Strings.md).</span></span>|
|<span data-ttu-id="9703e-174">byte</span><span class="sxs-lookup"><span data-stu-id="9703e-174">byte</span></span>|<span data-ttu-id="9703e-175">Znak ASCII</span><span class="sxs-lookup"><span data-stu-id="9703e-175">ASCII character</span></span>|<span data-ttu-id="9703e-176">B</span><span class="sxs-lookup"><span data-stu-id="9703e-176">B</span></span>|`'a'B`|
|<span data-ttu-id="9703e-177">Byte []</span><span class="sxs-lookup"><span data-stu-id="9703e-177">byte[]</span></span>|<span data-ttu-id="9703e-178">Řetězec ASCII</span><span class="sxs-lookup"><span data-stu-id="9703e-178">ASCII string</span></span>|<span data-ttu-id="9703e-179">B</span><span class="sxs-lookup"><span data-stu-id="9703e-179">B</span></span>|`"text"B`|
|<span data-ttu-id="9703e-180">Řetězec nebo Byte []</span><span class="sxs-lookup"><span data-stu-id="9703e-180">String or byte[]</span></span>|<span data-ttu-id="9703e-181">řetězec doslovného řetězce</span><span class="sxs-lookup"><span data-stu-id="9703e-181">verbatim string</span></span>|<span data-ttu-id="9703e-182">@ prefix</span><span class="sxs-lookup"><span data-stu-id="9703e-182">@ prefix</span></span>|<span data-ttu-id="9703e-183">`@"\\server\share"`Sady</span><span class="sxs-lookup"><span data-stu-id="9703e-183">`@"\\server\share"` (Unicode)</span></span><br /><br /><span data-ttu-id="9703e-184">`@"\\server\share"B`Abecední</span><span class="sxs-lookup"><span data-stu-id="9703e-184">`@"\\server\share"B` (ASCII)</span></span>|

## <a name="named-literals"></a><span data-ttu-id="9703e-185">Pojmenované literály</span><span class="sxs-lookup"><span data-stu-id="9703e-185">Named literals</span></span>

<span data-ttu-id="9703e-186">Hodnoty, které mají být konstanty, mohou být označeny atributem [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) .</span><span class="sxs-lookup"><span data-stu-id="9703e-186">Values that are intended to be constants can be marked with the [Literal](https://msdn.microsoft.com/library/465f36ce-d146-41c0-b425-679c509cd285) attribute.</span></span> <span data-ttu-id="9703e-187">Tento atribut má vliv, který způsobí, že se hodnota zkompiluje jako konstanta.</span><span class="sxs-lookup"><span data-stu-id="9703e-187">This attribute has the effect of causing a value to be compiled as a constant.</span></span>

<span data-ttu-id="9703e-188">V výrazech porovnávání se vzorem se identifikátory začínající malým písmenem vždy považují za proměnné, které mají být vázány, nikoli jako literály, takže při definování literálů byste obecně měli použít počáteční velká písmena.</span><span class="sxs-lookup"><span data-stu-id="9703e-188">In pattern matching expressions, identifiers that begin with lowercase characters are always treated as variables to be bound, rather than as literals, so you should generally use initial capitals when you define literals.</span></span>

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

## <a name="remarks"></a><span data-ttu-id="9703e-189">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9703e-189">Remarks</span></span>

<span data-ttu-id="9703e-190">Řetězce v kódování Unicode mohou obsahovat explicitní kódování, která lze zadat pomocí `\u` 16bitového šestnáctkového kódu (0000-FFFF), nebo kódování UTF-32, které lze zadat pomocí `\U` kódu a 32 hexadecimálního kódu, který představuje libovolný bod kódu Unicode (00000000-0010FFFF).</span><span class="sxs-lookup"><span data-stu-id="9703e-190">Unicode strings can contain explicit encodings that you can specify by using `\u` followed by a 16-bit hexadecimal code (0000 - FFFF), or UTF-32 encodings that you can specify by using `\U` followed by a 32-bit hexadecimal code that represents any Unicode code point (00000000 - 0010FFFF).</span></span>

<span data-ttu-id="9703e-191">Použití jiných bitových operátorů kromě `|||` není povoleno.</span><span class="sxs-lookup"><span data-stu-id="9703e-191">The use of other bitwise operators other than `|||` isn't allowed.</span></span>

## <a name="integers-in-other-bases"></a><span data-ttu-id="9703e-192">Celá čísla v jiných základech</span><span class="sxs-lookup"><span data-stu-id="9703e-192">Integers in other bases</span></span>

<span data-ttu-id="9703e-193">Podepsaná 32 celočíselná celá čísla lze také zadat v šestnáctkovém, osmičkovém nebo binárním formátu `0x` pomocí `0o` `0b` předpony nebo v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="9703e-193">Signed 32-bit integers can also be specified in hexadecimal, octal, or binary using a `0x`, `0o` or `0b` prefix respectively.</span></span>

```fsharp
let numbers = (0x9F, 0o77, 0b1010)
// Result: numbers : int * int * int = (159, 63, 10)
```

## <a name="underscores-in-numeric-literals"></a><span data-ttu-id="9703e-194">Podtržítka v numerických literálech</span><span class="sxs-lookup"><span data-stu-id="9703e-194">Underscores in numeric literals</span></span>

<span data-ttu-id="9703e-195">Můžete oddělit číslice znakem podtržítka ( `_` ).</span><span class="sxs-lookup"><span data-stu-id="9703e-195">You can separate digits with the underscore character (`_`).</span></span>

```fsharp
let value = 0xDEAD_BEEF

let valueAsBits = 0b1101_1110_1010_1101_1011_1110_1110_1111

let exampleSSN = 123_456_7890
```

## <a name="see-also"></a><span data-ttu-id="9703e-196">Viz také</span><span class="sxs-lookup"><span data-stu-id="9703e-196">See also</span></span>

- [<span data-ttu-id="9703e-197">Core. LiteralAttribute – – třída</span><span class="sxs-lookup"><span data-stu-id="9703e-197">Core.LiteralAttribute Class</span></span>](https://msdn.microsoft.com/visualfsharpdocs/conceptual/core.literalattribute-class-%5bfsharp%5d)
