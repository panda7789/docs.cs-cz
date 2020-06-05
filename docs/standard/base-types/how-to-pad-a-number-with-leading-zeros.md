---
title: 'Postupy: Vyplnění čísla úvodními nulami'
description: Naučte se číslo doplnit počátečními nulami. Přidejte počáteční nuly do celých čísel nebo číselných hodnot na konkrétní celkovou délku nebo konkrétní počet počátečních nul.
ms.date: 02/25/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- numbers [.NET Framework], format strings
ms.assetid: 0b2c2cb5-c580-4891-8d81-cb632f5ec384
ms.openlocfilehash: 6ef0ddb37f1bc73254aa639d7c018ec6a01abd9b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447183"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a><span data-ttu-id="fc1b8-104">Postupy: Vyplnění čísla úvodními nulami</span><span class="sxs-lookup"><span data-stu-id="fc1b8-104">How to: Pad a Number with Leading Zeros</span></span>

<span data-ttu-id="fc1b8-105">Můžete přidat počáteční nuly k celému číslu pomocí [standardního číselného formátovacího řetězce](standard-numeric-format-strings.md) "D" se specifikátorem přesnosti.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-105">You can add leading zeros to an integer by using the "D" [standard numeric format string](standard-numeric-format-strings.md) with a precision specifier.</span></span> <span data-ttu-id="fc1b8-106">Pomocí [vlastního řetězce číselného formátu](custom-numeric-format-strings.md)lze přidat úvodní nuly k číslům Integer i s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-106">You can add leading zeros to both integer and floating-point numbers by using a [custom numeric format string](custom-numeric-format-strings.md).</span></span> <span data-ttu-id="fc1b8-107">Tento článek ukazuje, jak použít obě metody k vyplnění čísla počátečními nulami.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-107">This article shows how to use both methods to pad a number with leading zeros.</span></span>

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="fc1b8-108">Vyplnění celého čísla počátečními nulami na určitou délku</span><span class="sxs-lookup"><span data-stu-id="fc1b8-108">To pad an integer with leading zeros to a specific length</span></span>

1. <span data-ttu-id="fc1b8-109">Určete minimální počet číslic, které mají být zobrazeny v celočíselné hodnotě.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-109">Determine the minimum number of digits you want the integer value to display.</span></span> <span data-ttu-id="fc1b8-110">V tomto čísle uveďte všechny úvodní číslice.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-110">Include any leading digits in this number.</span></span>

1. <span data-ttu-id="fc1b8-111">Určete, zda chcete zobrazit celé číslo jako desítkovou hodnotu nebo hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-111">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="fc1b8-112">Chcete-li zobrazit celé číslo jako desítkovou hodnotu, zavolejte svou `ToString(String)` metodu a předejte řetězec "D*n*" jako hodnotu `format` parametru, kde *n* představuje minimální délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-112">To display the integer as a decimal value, call its `ToString(String)` method, and pass the string "D*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>

    - <span data-ttu-id="fc1b8-113">Chcete-li zobrazit celé číslo jako šestnáctkovou hodnotu, zavolejte svou `ToString(String)` metodu a předejte řetězec "X*n*" jako hodnotu parametru Format, kde *n* představuje minimální délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-113">To display the integer as a hexadecimal value, call its `ToString(String)` method and pass the string "X*n*" as the value of the format parameter, where *n* represents the minimum length of the string.</span></span>

<span data-ttu-id="fc1b8-114">Řetězec formátu lze použít také v řetězci v [jazyce C#](../../csharp/language-reference/tokens/interpolated.md) i [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), nebo můžete zavolat metodu, například <xref:System.String.Format%2A?displayProperty=nameWithType> nebo <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> , která používá [složené formátování](composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="fc1b8-114">You can also use the format string in an interpolated string in both [C#](../../csharp/language-reference/tokens/interpolated.md) and [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), or you can call a method, such as <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, that uses [composite formatting](composite-formatting.md).</span></span>

<span data-ttu-id="fc1b8-115">Následující příklad formátuje několik celočíselných hodnot s počátečními nulami tak, aby celková délka formátovaného čísla byla alespoň osm znaků.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-115">The following example formats several integer values with leading zeros so that the total length of the formatted number is at least eight characters.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
[!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="fc1b8-116">Chcete-li doplnit celé číslo s určitým počtem počátečních nul</span><span class="sxs-lookup"><span data-stu-id="fc1b8-116">To pad an integer with a specific number of leading zeros</span></span>

1. <span data-ttu-id="fc1b8-117">Určete, kolik počátečních nul má být celočíselná hodnota zobrazena.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-117">Determine how many leading zeros you want the integer value to display.</span></span>

1. <span data-ttu-id="fc1b8-118">Určete, zda chcete zobrazit celé číslo jako desítkovou hodnotu nebo hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-118">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="fc1b8-119">Formátování jako Desítková hodnota vyžaduje použití specifikátoru standardního formátu "D".</span><span class="sxs-lookup"><span data-stu-id="fc1b8-119">Formatting it as a decimal value requires that you use the "D" standard format specifier.</span></span>

    - <span data-ttu-id="fc1b8-120">Formátování jako hexadecimální hodnota vyžaduje použití specifikátoru standardního formátu "X".</span><span class="sxs-lookup"><span data-stu-id="fc1b8-120">Formatting it as a hexadecimal value requires that you use the "X" standard format specifier.</span></span>

1. <span data-ttu-id="fc1b8-121">Určete délku nedoplněného číselného řetězce voláním celočíselné hodnoty `ToString("D").Length` nebo `ToString("X").Length` metody.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-121">Determine the length of the unpadded numeric string by calling the integer value's `ToString("D").Length` or `ToString("X").Length` method.</span></span>

1. <span data-ttu-id="fc1b8-122">Přidejte počet počátečních nul, které chcete zahrnout do formátovaného řetězce, na délku nedoplněného číselného řetězce.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-122">Add the number of leading zeros that you want to include in the formatted string to the length of the unpadded numeric string.</span></span> <span data-ttu-id="fc1b8-123">Přidání počtu počátečních nul definuje celkovou délku čalouněného řetězce.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-123">Adding the number of leading zeros defines the total length of the padded string.</span></span>

1. <span data-ttu-id="fc1b8-124">Zavolejte metodu celočíselné hodnoty `ToString(String)` a předejte řetězec "D*n*" pro desítkové řetězce a "X*n*" pro šestnáctkové řetězce, kde *n* představuje celkovou délku čalouněného řetězce.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-124">Call the integer value's `ToString(String)` method, and pass the string "D*n*" for decimal strings and "X*n*" for hexadecimal strings, where *n* represents the total length of the padded string.</span></span> <span data-ttu-id="fc1b8-125">Můžete také použít formátovací řetězec "D*n*" nebo "X*n*" v metodě, která podporuje složené formátování.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-125">You can also use the "D*n*" or "X*n*" format string in a method that supports composite formatting.</span></span>

<span data-ttu-id="fc1b8-126">V následujícím příkladu je celočíselná hodnota s pěti počátečními nulami.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-126">The following example pads an integer value with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
[!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="fc1b8-127">Vyplnění číselné hodnoty počátečními nulami na určitou délku</span><span class="sxs-lookup"><span data-stu-id="fc1b8-127">To pad a numeric value with leading zeros to a specific length</span></span>

1. <span data-ttu-id="fc1b8-128">Určete, kolik číslic nalevo od desetinné čárky má mít řetězcové vyjádření čísla.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-128">Determine how many digits to the left of the decimal you want the string representation of the number to have.</span></span> <span data-ttu-id="fc1b8-129">V tomto celkovém počtu číslic uveďte všechny úvodní nuly.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-129">Include any leading zeros in this total number of digits.</span></span>

1. <span data-ttu-id="fc1b8-130">Definujte vlastní řetězec číselného formátu, který používá nulový zástupný symbol "0" k vyjádření minimálního počtu nul.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-130">Define a custom numeric format string that uses the zero placeholder "0" to represent the minimum number of zeros.</span></span>

1. <span data-ttu-id="fc1b8-131">Zavolejte `ToString(String)` metodu Number a předejte jí vlastní formátovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-131">Call the number's `ToString(String)` method and pass it the custom format string.</span></span> <span data-ttu-id="fc1b8-132">Můžete také použít vlastní řetězec formátu s interpolací řetězce nebo metodou, která podporuje složené formátování.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-132">You can also use the custom format string with string interpolation or with a method that supports composite formatting.</span></span>

<span data-ttu-id="fc1b8-133">Následující příklad formátuje několik číselných hodnot s počátečními nulami.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-133">The following example formats several numeric values with leading zeros.</span></span> <span data-ttu-id="fc1b8-134">V důsledku toho je celková délka formátovaného čísla aspoň osm číslic nalevo od desetinné čárky.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-134">As a result, the total length of the formatted number is at least eight digits to the left of the decimal.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
[!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="fc1b8-135">Vyplnění číselné hodnoty určitým počtem počátečních nul</span><span class="sxs-lookup"><span data-stu-id="fc1b8-135">To pad a numeric value with a specific number of leading zeros</span></span>

1. <span data-ttu-id="fc1b8-136">Určete, kolik počátečních nul má číselná hodnota.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-136">Determine how many leading zeros you want the numeric value to have.</span></span>

1. <span data-ttu-id="fc1b8-137">Určuje počet číslic nalevo od desetinné čárky v nedoplněném číselném řetězci:</span><span class="sxs-lookup"><span data-stu-id="fc1b8-137">Determine the number of digits to the left of the decimal in the unpadded numeric string:</span></span>

    1. <span data-ttu-id="fc1b8-138">Určí, zda řetězcové vyjádření čísla obsahuje symbol desetinné čárky.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-138">Determine whether the string representation of a number includes a decimal point symbol.</span></span>

    1. <span data-ttu-id="fc1b8-139">Pokud obsahuje symbol desetinné čárky, určete počet znaků vlevo od desetinné čárky.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-139">If it does include a decimal point symbol, determine the number of characters to the left of the decimal point.</span></span>

         <span data-ttu-id="fc1b8-140">-nebo-</span><span class="sxs-lookup"><span data-stu-id="fc1b8-140">-or-</span></span>

         <span data-ttu-id="fc1b8-141">Pokud neobsahuje symbol desetinné čárky, určete délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-141">If it doesn't include a decimal point symbol, determine the string's length.</span></span>

1. <span data-ttu-id="fc1b8-142">Vytvořte vlastní řetězec formátu, který používá:</span><span class="sxs-lookup"><span data-stu-id="fc1b8-142">Create a custom format string that uses:</span></span>

    - <span data-ttu-id="fc1b8-143">Nulový zástupný symbol "0" pro každou počáteční nuly, která se má objevit v řetězci.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-143">The zero placeholder "0" for each of the leading zeros to appear in the string.</span></span>

    - <span data-ttu-id="fc1b8-144">Zástupný symbol nula nebo zástupný symbol číslice "#" pro reprezentaci každé číslice ve výchozím řetězci.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-144">Either the zero placeholder or the digit placeholder "#" to represent each digit in the default string.</span></span>

1. <span data-ttu-id="fc1b8-145">Zadejte řetězec vlastního formátu jako parametr buď do metody Number, `ToString(String)` nebo do metody, která podporuje složené formátování.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-145">Supply the custom format string as a parameter either to the number's `ToString(String)` method or to a method that supports composite formatting.</span></span>

<span data-ttu-id="fc1b8-146">Následující příklad <xref:System.Double> doplní dvě hodnoty pěti počátečními nulami.</span><span class="sxs-lookup"><span data-stu-id="fc1b8-146">The following example pads two <xref:System.Double> values with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
[!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="fc1b8-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="fc1b8-147">See also</span></span>

- [<span data-ttu-id="fc1b8-148">Vlastní řetězce číselného formátu</span><span class="sxs-lookup"><span data-stu-id="fc1b8-148">Custom Numeric Format Strings</span></span>](custom-numeric-format-strings.md)
- [<span data-ttu-id="fc1b8-149">Řetězce standardního číselného formátu</span><span class="sxs-lookup"><span data-stu-id="fc1b8-149">Standard Numeric Format Strings</span></span>](standard-numeric-format-strings.md)
- [<span data-ttu-id="fc1b8-150">Složené formátování</span><span class="sxs-lookup"><span data-stu-id="fc1b8-150">Composite Formatting</span></span>](composite-formatting.md)
