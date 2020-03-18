---
title: 'Postupy: Zarovnání čísla úvodními nulami'
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
ms.openlocfilehash: bc3c4b75c484274c214141d8fbfcf8ac592b0b99
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73131979"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a><span data-ttu-id="3d42a-102">Postupy: Zarovnání čísla úvodními nulami</span><span class="sxs-lookup"><span data-stu-id="3d42a-102">How to: Pad a Number with Leading Zeros</span></span>

<span data-ttu-id="3d42a-103">Počáteční nuly můžete přidat k celé číslo pomocí [standardního číselného formátovacího řetězce](../../../docs/standard/base-types/standard-numeric-format-strings.md) "D" s specifikátorem přesnosti.</span><span class="sxs-lookup"><span data-stu-id="3d42a-103">You can add leading zeros to an integer by using the "D" [standard numeric format string](../../../docs/standard/base-types/standard-numeric-format-strings.md) with a precision specifier.</span></span> <span data-ttu-id="3d42a-104">Počáteční nuly můžete přidat k číslům celého čísla i čísla s plovoucí desetinnou desetinnou hodnotou pomocí [vlastního číselného formátovacího řetězce](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="3d42a-104">You can add leading zeros to both integer and floating-point numbers by using a [custom numeric format string](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span></span> <span data-ttu-id="3d42a-105">Tento článek ukazuje, jak používat obě metody k vyložce číslo s úvodními nulami.</span><span class="sxs-lookup"><span data-stu-id="3d42a-105">This article shows how to use both methods to pad a number with leading zeros.</span></span>

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="3d42a-106">Vytvoření celého čísla s počátečními nulami na určitou délku</span><span class="sxs-lookup"><span data-stu-id="3d42a-106">To pad an integer with leading zeros to a specific length</span></span>

1. <span data-ttu-id="3d42a-107">Určete minimální počet číslic, které chcete zobrazit v celé řadové hodnotě.</span><span class="sxs-lookup"><span data-stu-id="3d42a-107">Determine the minimum number of digits you want the integer value to display.</span></span> <span data-ttu-id="3d42a-108">Do tohoto čísla uveďte všechny úvodní číslice.</span><span class="sxs-lookup"><span data-stu-id="3d42a-108">Include any leading digits in this number.</span></span>

1. <span data-ttu-id="3d42a-109">Určete, zda chcete zobrazit celé číslo jako desetinnou hodnotu nebo šestnáctkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3d42a-109">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="3d42a-110">Chcete-li zobrazit celé číslo jako desítkovou `ToString(String)` hodnotu, zavolejte jeho metodu a `format` předejte řetězec "D*n*" jako hodnotu parametru, kde *n* představuje minimální délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="3d42a-110">To display the integer as a decimal value, call its `ToString(String)` method, and pass the string "D*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>

    - <span data-ttu-id="3d42a-111">Chcete-li zobrazit celé číslo jako šestnáctkovou hodnotu, zavolejte její `ToString(String)` metodu a předejte řetězec "X*n*" jako hodnotu parametru format, kde *n* představuje minimální délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="3d42a-111">To display the integer as a hexadecimal value, call its `ToString(String)` method and pass the string "X*n*" as the value of the format parameter, where *n* represents the minimum length of the string.</span></span>

<span data-ttu-id="3d42a-112">Formátovací řetězec můžete také použít v interpolovaném řetězci v [jazyce C#](../../csharp/language-reference/tokens/interpolated.md) i <xref:System.String.Format%2A?displayProperty=nameWithType> [jazyce Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md)nebo můžete volat metodu, například nebo <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, která používá složené [formátování](../../../docs/standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="3d42a-112">You can also use the format string in an interpolated string in both [C#](../../csharp/language-reference/tokens/interpolated.md) and [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), or you can call a method, such as <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, that uses [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>

<span data-ttu-id="3d42a-113">Následující příklad zformátuje několik vícečíselných hodnot s počátečními nulami tak, aby celková délka formátovaného čísla byla alespoň osm znaků.</span><span class="sxs-lookup"><span data-stu-id="3d42a-113">The following example formats several integer values with leading zeros so that the total length of the formatted number is at least eight characters.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
[!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="3d42a-114">Vytvoření celého čísla s určitým počtem počátečních nul</span><span class="sxs-lookup"><span data-stu-id="3d42a-114">To pad an integer with a specific number of leading zeros</span></span>

1. <span data-ttu-id="3d42a-115">Určete, kolik počátečních nul se má celá hodnota zobrazit.</span><span class="sxs-lookup"><span data-stu-id="3d42a-115">Determine how many leading zeros you want the integer value to display.</span></span>

1. <span data-ttu-id="3d42a-116">Určete, zda chcete zobrazit celé číslo jako desetinnou hodnotu nebo šestnáctkovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3d42a-116">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="3d42a-117">Formátování jako desetinné hodnoty vyžaduje použití standardního specifikátoru formátu D.</span><span class="sxs-lookup"><span data-stu-id="3d42a-117">Formatting it as a decimal value requires that you use the "D" standard format specifier.</span></span>

    - <span data-ttu-id="3d42a-118">Formátování jako šestnáctkové hodnoty vyžaduje použití standardního specifikátoru formátu "X".</span><span class="sxs-lookup"><span data-stu-id="3d42a-118">Formatting it as a hexadecimal value requires that you use the "X" standard format specifier.</span></span>

1. <span data-ttu-id="3d42a-119">Určete délku nepolstrovaného číselného řetězce voláním `ToString("D").Length` `ToString("X").Length` celé hodnoty nebo metody.</span><span class="sxs-lookup"><span data-stu-id="3d42a-119">Determine the length of the unpadded numeric string by calling the integer value's `ToString("D").Length` or `ToString("X").Length` method.</span></span>

1. <span data-ttu-id="3d42a-120">Přidejte počet počátečních nul, které chcete zahrnout do formátovaného řetězce, na délku nepolstrovaného číselného řetězce.</span><span class="sxs-lookup"><span data-stu-id="3d42a-120">Add the number of leading zeros that you want to include in the formatted string to the length of the unpadded numeric string.</span></span> <span data-ttu-id="3d42a-121">Přidáním počtu úvodních nul definujete celkovou délku polstrovaného řetězce.</span><span class="sxs-lookup"><span data-stu-id="3d42a-121">Adding the number of leading zeros defines the total length of the padded string.</span></span>

1. <span data-ttu-id="3d42a-122">Volat `ToString(String)` metodu hodnota celé číslo a předat řetězec "D*n*" pro desetinné řetězce a "X*n*" pro šestnáctkové řetězce, kde *n* představuje celkovou délku polstrovanéřetězce.</span><span class="sxs-lookup"><span data-stu-id="3d42a-122">Call the integer value's `ToString(String)` method, and pass the string "D*n*" for decimal strings and "X*n*" for hexadecimal strings, where *n* represents the total length of the padded string.</span></span> <span data-ttu-id="3d42a-123">Můžete také použít formátovací řetězec "D*n*" nebo "X*n*" v metodě, která podporuje složené formátování.</span><span class="sxs-lookup"><span data-stu-id="3d42a-123">You can also use the "D*n*" or "X*n*" format string in a method that supports composite formatting.</span></span>

<span data-ttu-id="3d42a-124">Následující příklad vycpává hodnotu celéčíslo s pěti počátečními nulami.</span><span class="sxs-lookup"><span data-stu-id="3d42a-124">The following example pads an integer value with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
[!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="3d42a-125">Vyřadit číselnou hodnotu s počátečními nulami na určitou délku</span><span class="sxs-lookup"><span data-stu-id="3d42a-125">To pad a numeric value with leading zeros to a specific length</span></span>

1. <span data-ttu-id="3d42a-126">Určete, kolik číslic nalevo od desetinného místa chcete mít řetězcovou reprezentaci čísla.</span><span class="sxs-lookup"><span data-stu-id="3d42a-126">Determine how many digits to the left of the decimal you want the string representation of the number to have.</span></span> <span data-ttu-id="3d42a-127">Do tohoto celkového počtu číslic zahrňte všechny počáteční nuly.</span><span class="sxs-lookup"><span data-stu-id="3d42a-127">Include any leading zeros in this total number of digits.</span></span>

1. <span data-ttu-id="3d42a-128">Definujte vlastní číselný formátovací řetězec, který používá nulový zástupný symbol "0" k reprezentaci minimálního počtu nul.</span><span class="sxs-lookup"><span data-stu-id="3d42a-128">Define a custom numeric format string that uses the zero placeholder "0" to represent the minimum number of zeros.</span></span>

1. <span data-ttu-id="3d42a-129">Zavolejte `ToString(String)` metodu čísla a předejte mu vlastní formátovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="3d42a-129">Call the number's `ToString(String)` method and pass it the custom format string.</span></span> <span data-ttu-id="3d42a-130">Můžete také použít vlastní formátovací řetězec s interpolací řetězců nebo s metodou, která podporuje složené formátování.</span><span class="sxs-lookup"><span data-stu-id="3d42a-130">You can also use the custom format string with string interpolation or with a method that supports composite formatting.</span></span>

<span data-ttu-id="3d42a-131">Následující příklad formátuje několik číselných hodnot s úvodními nulami.</span><span class="sxs-lookup"><span data-stu-id="3d42a-131">The following example formats several numeric values with leading zeros.</span></span> <span data-ttu-id="3d42a-132">V důsledku toho je celková délka formátovaného čísla nejméně osm číslic nalevo od desetinného místa.</span><span class="sxs-lookup"><span data-stu-id="3d42a-132">As a result, the total length of the formatted number is at least eight digits to the left of the decimal.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
[!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="3d42a-133">Vytvoření číselné hodnoty s určitým počtem počátečních nul</span><span class="sxs-lookup"><span data-stu-id="3d42a-133">To pad a numeric value with a specific number of leading zeros</span></span>

1. <span data-ttu-id="3d42a-134">Určete, kolik počátečních nul má číselná hodnota mít.</span><span class="sxs-lookup"><span data-stu-id="3d42a-134">Determine how many leading zeros you want the numeric value to have.</span></span>

1. <span data-ttu-id="3d42a-135">Určete počet číslic nalevo od desetinného místa v nepolstrovaném číselném řetězci:</span><span class="sxs-lookup"><span data-stu-id="3d42a-135">Determine the number of digits to the left of the decimal in the unpadded numeric string:</span></span>

    1. <span data-ttu-id="3d42a-136">Určete, zda řetězcová reprezentace čísla obsahuje symbol desetinné čárky.</span><span class="sxs-lookup"><span data-stu-id="3d42a-136">Determine whether the string representation of a number includes a decimal point symbol.</span></span>

    1. <span data-ttu-id="3d42a-137">Pokud obsahuje symbol desetinné čárky, určete počet znaků nalevo od desetinné čárky.</span><span class="sxs-lookup"><span data-stu-id="3d42a-137">If it does include a decimal point symbol, determine the number of characters to the left of the decimal point.</span></span>

         <span data-ttu-id="3d42a-138">-nebo-</span><span class="sxs-lookup"><span data-stu-id="3d42a-138">-or-</span></span>

         <span data-ttu-id="3d42a-139">Pokud neobsahuje symbol desetinné čárky, určete délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="3d42a-139">If it doesn't include a decimal point symbol, determine the string's length.</span></span>

1. <span data-ttu-id="3d42a-140">Vytvořte vlastní formátovací řetězec, který používá:</span><span class="sxs-lookup"><span data-stu-id="3d42a-140">Create a custom format string that uses:</span></span>

    - <span data-ttu-id="3d42a-141">Nulový zástupný symbol "0" pro každou z úvodních nul, která se zobrazí v řetězci.</span><span class="sxs-lookup"><span data-stu-id="3d42a-141">The zero placeholder "0" for each of the leading zeros to appear in the string.</span></span>

    - <span data-ttu-id="3d42a-142">Buď žádný zástupný symbol nebo zástupný symbol číslice "#", který představuje každou číslici ve výchozím řetězci.</span><span class="sxs-lookup"><span data-stu-id="3d42a-142">Either the zero placeholder or the digit placeholder "#" to represent each digit in the default string.</span></span>

1. <span data-ttu-id="3d42a-143">Zadejte vlastní formátovací řetězec jako parametr `ToString(String)` metodu čísla nebo metodu, která podporuje složené formátování.</span><span class="sxs-lookup"><span data-stu-id="3d42a-143">Supply the custom format string as a parameter either to the number's `ToString(String)` method or to a method that supports composite formatting.</span></span>

<span data-ttu-id="3d42a-144">Následující příklad vycpává dvě <xref:System.Double> hodnoty s pěti počátečními nulami.</span><span class="sxs-lookup"><span data-stu-id="3d42a-144">The following example pads two <xref:System.Double> values with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
[!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="3d42a-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d42a-145">See also</span></span>

- [<span data-ttu-id="3d42a-146">Vlastní řetězce číselného formátu</span><span class="sxs-lookup"><span data-stu-id="3d42a-146">Custom Numeric Format Strings</span></span>](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [<span data-ttu-id="3d42a-147">Standardní řetězce číselného formátu</span><span class="sxs-lookup"><span data-stu-id="3d42a-147">Standard Numeric Format Strings</span></span>](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="3d42a-148">Složené formátování</span><span class="sxs-lookup"><span data-stu-id="3d42a-148">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
