---
title: Char – datový typ
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: 3dbbf9f6a2c4079775e05f5d2dcd8704c1ec4259
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387475"
---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="3a581-102">Char – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a581-102">Char Data Type (Visual Basic)</span></span>

<span data-ttu-id="3a581-103">Obsahuje nepodepsaný 16bitový (2 bajt) body kódu v rozsahu od 0 do 65535.</span><span class="sxs-lookup"><span data-stu-id="3a581-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="3a581-104">Každý *bod kódu*nebo kód znaku představuje jeden znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="3a581-104">Each *code point*, or character code, represents a single Unicode character.</span></span>

## <a name="remarks"></a><span data-ttu-id="3a581-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3a581-105">Remarks</span></span>

<span data-ttu-id="3a581-106">`Char`Datový typ použijte v případě, že potřebujete držet jenom jeden znak a nemusíte mít režii `String` .</span><span class="sxs-lookup"><span data-stu-id="3a581-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="3a581-107">V některých případech můžete použít `Char()` pole `Char` prvků pro uložení více znaků.</span><span class="sxs-lookup"><span data-stu-id="3a581-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>

<span data-ttu-id="3a581-108">Výchozí hodnota `Char` je znak s bodem kódu 0.</span><span class="sxs-lookup"><span data-stu-id="3a581-108">The default value of `Char` is the character with a code point of 0.</span></span>

## <a name="unicode-characters"></a><span data-ttu-id="3a581-109">Znaky Unicode</span><span class="sxs-lookup"><span data-stu-id="3a581-109">Unicode Characters</span></span>

<span data-ttu-id="3a581-110">Prvních 128 kódových bodů (0 – 127) Unicode odpovídá písmenům a symbolům na standardní americké klávesnici.</span><span class="sxs-lookup"><span data-stu-id="3a581-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="3a581-111">Tyto první body kódu 128 jsou stejné jako ty, které definuje znaková sada ASCII.</span><span class="sxs-lookup"><span data-stu-id="3a581-111">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="3a581-112">Druhý bod kódu 128 (128 – 255) představuje speciální znaky, jako jsou písmena abecedy založená na latince, zvýraznění, symboly měn a zlomky.</span><span class="sxs-lookup"><span data-stu-id="3a581-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="3a581-113">Kódování Unicode používá zbývající body kódu (256-65535) pro širokou škálu symbolů, včetně celosvětových textových znaků, diakritických znamének a matematických a technických symbolů.</span><span class="sxs-lookup"><span data-stu-id="3a581-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>

<span data-ttu-id="3a581-114"><xref:System.Char.IsDigit%2A>K určení klasifikace Unicode můžete použít metody jako a <xref:System.Char.IsPunctuation%2A> na `Char` proměnné.</span><span class="sxs-lookup"><span data-stu-id="3a581-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>

## <a name="type-conversions"></a><span data-ttu-id="3a581-115">Převody typu</span><span class="sxs-lookup"><span data-stu-id="3a581-115">Type Conversions</span></span>

<span data-ttu-id="3a581-116">Visual Basic nepřevádí přímo mezi `Char` a číselnými typy.</span><span class="sxs-lookup"><span data-stu-id="3a581-116">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="3a581-117">Můžete použít <xref:Microsoft.VisualBasic.Strings.Asc%2A> <xref:Microsoft.VisualBasic.Strings.AscW%2A> funkci nebo pro převod `Char` hodnoty na `Integer` , která představuje jeho bod kódu.</span><span class="sxs-lookup"><span data-stu-id="3a581-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="3a581-118">Můžete použít <xref:Microsoft.VisualBasic.Strings.Chr%2A> <xref:Microsoft.VisualBasic.Strings.ChrW%2A> funkci nebo pro převod `Integer` hodnoty na `Char` , která má tento kódový bod.</span><span class="sxs-lookup"><span data-stu-id="3a581-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>

<span data-ttu-id="3a581-119">Pokud je přepínač pro kontrolu typu ( [příkaz Option Strict](../statements/option-strict-statement.md)) zapnutý, je nutné připojit znak literálového typu k řetězcovému literálu s jedním znakem a identifikovat ho jako `Char` datový typ.</span><span class="sxs-lookup"><span data-stu-id="3a581-119">If the type checking switch (the [Option Strict Statement](../statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="3a581-120">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="3a581-120">The following example illustrates this.</span></span> <span data-ttu-id="3a581-121">První přiřazení k `charVar` proměnné generuje chybu kompilátoru [BC30512](../../misc/bc30512.md) `Option Strict` , protože je zapnuto.</span><span class="sxs-lookup"><span data-stu-id="3a581-121">The first assignment to the `charVar` variable generates compiler error [BC30512](../../misc/bc30512.md) because `Option Strict` is on.</span></span> <span data-ttu-id="3a581-122">Druhé kompilování bylo úspěšné, protože `c` literální znak literálu identifikuje literál jako `Char` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3a581-122">The second compiles successfully because the `c` literal type character identifies the literal as a `Char` value.</span></span>

```vb
Option Strict On

Module CharType
    Public Sub Main()
        Dim charVar As Char

        ' This statement generates compiler error BC30512 because Option Strict is On.  
        charVar = "Z"  

        ' The following statement succeeds because it specifies a Char literal.  
        charVar = "Z"c
    End Sub
End Module
```

## <a name="programming-tips"></a><span data-ttu-id="3a581-123">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="3a581-123">Programming Tips</span></span>

- <span data-ttu-id="3a581-124">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="3a581-124">**Negative Numbers.**</span></span> <span data-ttu-id="3a581-125">`Char`je typ bez znaménka a nemůže představovat zápornou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3a581-125">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="3a581-126">V žádném případě byste neměli používat `Char` k ukládání číselných hodnot.</span><span class="sxs-lookup"><span data-stu-id="3a581-126">In any case, you should not use `Char` to hold numeric values.</span></span>

- <span data-ttu-id="3a581-127">**Problematika spolupráce.**</span><span class="sxs-lookup"><span data-stu-id="3a581-127">**Interop Considerations.**</span></span> <span data-ttu-id="3a581-128">Pokud rozhraní s komponentami, které nejsou zapsány pro .NET Framework, například automatizace nebo objekty COM, pamatujte, že typy znaků mají v jiných prostředích jinou šířku dat (8 bitů).</span><span class="sxs-lookup"><span data-stu-id="3a581-128">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="3a581-129">Pokud předáte 8bitovému argumentu takové součásti, deklarujte ji jako `Byte` místo `Char` v novém Visual Basic kódu.</span><span class="sxs-lookup"><span data-stu-id="3a581-129">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>

- <span data-ttu-id="3a581-130">**Rozšiřující.**</span><span class="sxs-lookup"><span data-stu-id="3a581-130">**Widening.**</span></span> <span data-ttu-id="3a581-131">`Char`Datový typ se rozšíří na `String` .</span><span class="sxs-lookup"><span data-stu-id="3a581-131">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="3a581-132">To znamená, že můžete převést na a nemůžete se `Char` `String` setkat s <xref:System.OverflowException?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="3a581-132">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="3a581-133">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="3a581-133">**Type Characters.**</span></span> <span data-ttu-id="3a581-134">Připojení znaku literálového typu `C` k řetězcovému literálu s jedním znakem vynutí `Char` datový typ.</span><span class="sxs-lookup"><span data-stu-id="3a581-134">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="3a581-135">`Char`nemá žádný znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="3a581-135">`Char` has no identifier type character.</span></span>

- <span data-ttu-id="3a581-136">**Typ rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="3a581-136">**Framework Type.**</span></span> <span data-ttu-id="3a581-137">Odpovídající typ v .NET Framework je <xref:System.Char?displayProperty=nameWithType> Struktura.</span><span class="sxs-lookup"><span data-stu-id="3a581-137">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="3a581-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a581-138">See also</span></span>

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="3a581-139">Datové typy</span><span class="sxs-lookup"><span data-stu-id="3a581-139">Data Types</span></span>](index.md)
- [<span data-ttu-id="3a581-140">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="3a581-140">String Data Type</span></span>](string-data-type.md)
- [<span data-ttu-id="3a581-141">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="3a581-141">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="3a581-142">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="3a581-142">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="3a581-143">Postupy: Volání funkce Windows, která přebírá typy bez znaménka</span><span class="sxs-lookup"><span data-stu-id="3a581-143">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="3a581-144">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="3a581-144">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
