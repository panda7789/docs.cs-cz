---
title: Char – datový typ (Visual Basic)
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
ms.openlocfilehash: 8313c2282a3b4b7b035f9f3b685a786c4471f53a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630151"
---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="46b89-102">Char – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="46b89-102">Char Data Type (Visual Basic)</span></span>

<span data-ttu-id="46b89-103">Obsahuje nepodepsaný 16bitový (2 bajt) body kódu v rozsahu od 0 do 65535.</span><span class="sxs-lookup"><span data-stu-id="46b89-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="46b89-104">Každý *bod kódu*nebo kód znaku představuje jeden znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="46b89-104">Each *code point*, or character code, represents a single Unicode character.</span></span>

## <a name="remarks"></a><span data-ttu-id="46b89-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="46b89-105">Remarks</span></span>

<span data-ttu-id="46b89-106">Datový typ `Char` použijte v případě, že potřebujete držet jenom jeden znak a nemusíte mít `String`režii.</span><span class="sxs-lookup"><span data-stu-id="46b89-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="46b89-107">V některých případech můžete použít `Char()` `Char` pole prvků pro uložení více znaků.</span><span class="sxs-lookup"><span data-stu-id="46b89-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>

<span data-ttu-id="46b89-108">Výchozí hodnota `Char` je znak s bodem kódu 0.</span><span class="sxs-lookup"><span data-stu-id="46b89-108">The default value of `Char` is the character with a code point of 0.</span></span>

## <a name="unicode-characters"></a><span data-ttu-id="46b89-109">Znaky Unicode</span><span class="sxs-lookup"><span data-stu-id="46b89-109">Unicode Characters</span></span>

<span data-ttu-id="46b89-110">Prvních 128 kódových bodů (0 – 127) Unicode odpovídá písmenům a symbolům na standardní americké klávesnici.</span><span class="sxs-lookup"><span data-stu-id="46b89-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="46b89-111">Tyto první body kódu 128 jsou stejné jako ty, které definuje znaková sada ASCII.</span><span class="sxs-lookup"><span data-stu-id="46b89-111">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="46b89-112">Druhý bod kódu 128 (128 – 255) představuje speciální znaky, jako jsou písmena abecedy založená na latince, zvýraznění, symboly měn a zlomky.</span><span class="sxs-lookup"><span data-stu-id="46b89-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="46b89-113">Kódování Unicode používá zbývající body kódu (256-65535) pro širokou škálu symbolů, včetně celosvětových textových znaků, diakritických znamének a matematických a technických symbolů.</span><span class="sxs-lookup"><span data-stu-id="46b89-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>

<span data-ttu-id="46b89-114">K určení klasifikace Unicode můžete <xref:System.Char.IsDigit%2A> použít <xref:System.Char.IsPunctuation%2A> metody jako `Char` a na proměnné.</span><span class="sxs-lookup"><span data-stu-id="46b89-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>

## <a name="type-conversions"></a><span data-ttu-id="46b89-115">Převody typu</span><span class="sxs-lookup"><span data-stu-id="46b89-115">Type Conversions</span></span>

<span data-ttu-id="46b89-116">Visual Basic nepřevádí přímo mezi `Char` a číselnými typy.</span><span class="sxs-lookup"><span data-stu-id="46b89-116">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="46b89-117">Můžete použít <xref:Microsoft.VisualBasic.Strings.Asc%2A> funkci nebo <xref:Microsoft.VisualBasic.Strings.AscW%2A> `Char` pro`Integer` převod hodnoty na, která představuje jeho bod kódu.</span><span class="sxs-lookup"><span data-stu-id="46b89-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="46b89-118">Můžete použít <xref:Microsoft.VisualBasic.Strings.Chr%2A> funkci nebo <xref:Microsoft.VisualBasic.Strings.ChrW%2A> `Integer` pro`Char` převod hodnoty na, která má tento kódový bod.</span><span class="sxs-lookup"><span data-stu-id="46b89-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>

<span data-ttu-id="46b89-119">Pokud je přepínač pro kontrolu typu ( [příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)) zapnutý, je nutné připojit znak literálového typu k řetězcovému literálu s jedním znakem a identifikovat ho `Char` jako datový typ.</span><span class="sxs-lookup"><span data-stu-id="46b89-119">If the type checking switch (the [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="46b89-120">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="46b89-120">The following example illustrates this.</span></span> <span data-ttu-id="46b89-121">První přiřazení k `charVar` proměnné generuje chybu kompilátoru [BC30512](../../misc/bc30512.md) , protože `Option Strict` je zapnuto.</span><span class="sxs-lookup"><span data-stu-id="46b89-121">The first assignment to the `charVar` variable generates compiler error [BC30512](../../misc/bc30512.md) because `Option Strict` is on.</span></span> <span data-ttu-id="46b89-122">Druhé kompilování bylo úspěšné, protože `c` literální znak literálu identifikuje literál `Char` jako hodnotu.</span><span class="sxs-lookup"><span data-stu-id="46b89-122">The second compiles successfully because the `c` literal type character identifies the literal as a `Char` value.</span></span>

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

## <a name="programming-tips"></a><span data-ttu-id="46b89-123">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="46b89-123">Programming Tips</span></span>

- <span data-ttu-id="46b89-124">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="46b89-124">**Negative Numbers.**</span></span> <span data-ttu-id="46b89-125">`Char`je typ bez znaménka a nemůže představovat zápornou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="46b89-125">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="46b89-126">V žádném případě byste neměli používat `Char` k ukládání číselných hodnot.</span><span class="sxs-lookup"><span data-stu-id="46b89-126">In any case, you should not use `Char` to hold numeric values.</span></span>

- <span data-ttu-id="46b89-127">**Problematika spolupráce.**</span><span class="sxs-lookup"><span data-stu-id="46b89-127">**Interop Considerations.**</span></span> <span data-ttu-id="46b89-128">Pokud rozhraní s komponentami, které nejsou zapsány pro .NET Framework, například automatizace nebo objekty COM, pamatujte, že typy znaků mají v jiných prostředích jinou šířku dat (8 bitů).</span><span class="sxs-lookup"><span data-stu-id="46b89-128">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="46b89-129">Pokud předáte 8bitovému argumentu takové součásti, deklarujte ji jako `Byte` `Char` místo v novém Visual Basic kódu.</span><span class="sxs-lookup"><span data-stu-id="46b89-129">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>

- <span data-ttu-id="46b89-130">**Rozšiřující.**</span><span class="sxs-lookup"><span data-stu-id="46b89-130">**Widening.**</span></span> <span data-ttu-id="46b89-131">Datový typ se rozšíří na `String`. `Char`</span><span class="sxs-lookup"><span data-stu-id="46b89-131">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="46b89-132">To znamená, že můžete `Char` převést `String` na a nemůžete <xref:System.OverflowException?displayProperty=nameWithType>se setkat s.</span><span class="sxs-lookup"><span data-stu-id="46b89-132">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="46b89-133">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="46b89-133">**Type Characters.**</span></span> <span data-ttu-id="46b89-134">Připojení znaku `C` literálového typu k řetězcovému literálu s jedním znakem vynutí `Char` datový typ.</span><span class="sxs-lookup"><span data-stu-id="46b89-134">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="46b89-135">`Char`nemá žádný znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="46b89-135">`Char` has no identifier type character.</span></span>

- <span data-ttu-id="46b89-136">**Typ rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="46b89-136">**Framework Type.**</span></span> <span data-ttu-id="46b89-137">Odpovídající typ v .NET Framework je <xref:System.Char?displayProperty=nameWithType> struktura.</span><span class="sxs-lookup"><span data-stu-id="46b89-137">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=nameWithType> structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="46b89-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46b89-138">See also</span></span>

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="46b89-139">Datové typy</span><span class="sxs-lookup"><span data-stu-id="46b89-139">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="46b89-140">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="46b89-140">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="46b89-141">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="46b89-141">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="46b89-142">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="46b89-142">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="46b89-143">Postupy: Volání funkce Windows, která přebírá typy bez znaménka</span><span class="sxs-lookup"><span data-stu-id="46b89-143">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="46b89-144">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="46b89-144">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
