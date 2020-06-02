---
title: 'Postupy: Vyplnění čísla úvodními nulami'
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
ms.openlocfilehash: ef18fb1bb7b1592a4e92866028868bf1cf793bbf
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290458"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a><span data-ttu-id="c0a2b-102">Postupy: Vyplnění čísla úvodními nulami</span><span class="sxs-lookup"><span data-stu-id="c0a2b-102">How to: Pad a Number with Leading Zeros</span></span>

<span data-ttu-id="c0a2b-103">Můžete přidat počáteční nuly k celému číslu pomocí [standardního číselného formátovacího řetězce](standard-numeric-format-strings.md) "D" se specifikátorem přesnosti.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-103">You can add leading zeros to an integer by using the "D" [standard numeric format string](standard-numeric-format-strings.md) with a precision specifier.</span></span> <span data-ttu-id="c0a2b-104">Pomocí [vlastního řetězce číselného formátu](custom-numeric-format-strings.md)lze přidat úvodní nuly k číslům Integer i s plovoucí desetinnou čárkou.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-104">You can add leading zeros to both integer and floating-point numbers by using a [custom numeric format string](custom-numeric-format-strings.md).</span></span> <span data-ttu-id="c0a2b-105">Tento článek ukazuje, jak použít obě metody k vyplnění čísla počátečními nulami.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-105">This article shows how to use both methods to pad a number with leading zeros.</span></span>

## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="c0a2b-106">Vyplnění celého čísla počátečními nulami na určitou délku</span><span class="sxs-lookup"><span data-stu-id="c0a2b-106">To pad an integer with leading zeros to a specific length</span></span>

1. <span data-ttu-id="c0a2b-107">Určete minimální počet číslic, které mají být zobrazeny v celočíselné hodnotě.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-107">Determine the minimum number of digits you want the integer value to display.</span></span> <span data-ttu-id="c0a2b-108">V tomto čísle uveďte všechny úvodní číslice.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-108">Include any leading digits in this number.</span></span>

1. <span data-ttu-id="c0a2b-109">Určete, zda chcete zobrazit celé číslo jako desítkovou hodnotu nebo hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-109">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="c0a2b-110">Chcete-li zobrazit celé číslo jako desítkovou hodnotu, zavolejte svou `ToString(String)` metodu a předejte řetězec "D*n*" jako hodnotu `format` parametru, kde *n* představuje minimální délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-110">To display the integer as a decimal value, call its `ToString(String)` method, and pass the string "D*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>

    - <span data-ttu-id="c0a2b-111">Chcete-li zobrazit celé číslo jako šestnáctkovou hodnotu, zavolejte svou `ToString(String)` metodu a předejte řetězec "X*n*" jako hodnotu parametru Format, kde *n* představuje minimální délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-111">To display the integer as a hexadecimal value, call its `ToString(String)` method and pass the string "X*n*" as the value of the format parameter, where *n* represents the minimum length of the string.</span></span>

<span data-ttu-id="c0a2b-112">Řetězec formátu lze použít také v řetězci v [jazyce C#](../../csharp/language-reference/tokens/interpolated.md) i [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), nebo můžete zavolat metodu, například <xref:System.String.Format%2A?displayProperty=nameWithType> nebo <xref:System.Console.WriteLine%2A?displayProperty=nameWithType> , která používá [složené formátování](composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="c0a2b-112">You can also use the format string in an interpolated string in both [C#](../../csharp/language-reference/tokens/interpolated.md) and [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), or you can call a method, such as <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, that uses [composite formatting](composite-formatting.md).</span></span>

<span data-ttu-id="c0a2b-113">Následující příklad formátuje několik celočíselných hodnot s počátečními nulami tak, aby celková délka formátovaného čísla byla alespoň osm znaků.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-113">The following example formats several integer values with leading zeros so that the total length of the formatted number is at least eight characters.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
[!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]

## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="c0a2b-114">Chcete-li doplnit celé číslo s určitým počtem počátečních nul</span><span class="sxs-lookup"><span data-stu-id="c0a2b-114">To pad an integer with a specific number of leading zeros</span></span>

1. <span data-ttu-id="c0a2b-115">Určete, kolik počátečních nul má být celočíselná hodnota zobrazena.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-115">Determine how many leading zeros you want the integer value to display.</span></span>

1. <span data-ttu-id="c0a2b-116">Určete, zda chcete zobrazit celé číslo jako desítkovou hodnotu nebo hexadecimální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-116">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="c0a2b-117">Formátování jako Desítková hodnota vyžaduje použití specifikátoru standardního formátu "D".</span><span class="sxs-lookup"><span data-stu-id="c0a2b-117">Formatting it as a decimal value requires that you use the "D" standard format specifier.</span></span>

    - <span data-ttu-id="c0a2b-118">Formátování jako hexadecimální hodnota vyžaduje použití specifikátoru standardního formátu "X".</span><span class="sxs-lookup"><span data-stu-id="c0a2b-118">Formatting it as a hexadecimal value requires that you use the "X" standard format specifier.</span></span>

1. <span data-ttu-id="c0a2b-119">Určete délku nedoplněného číselného řetězce voláním celočíselné hodnoty `ToString("D").Length` nebo `ToString("X").Length` metody.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-119">Determine the length of the unpadded numeric string by calling the integer value's `ToString("D").Length` or `ToString("X").Length` method.</span></span>

1. <span data-ttu-id="c0a2b-120">Přidejte počet počátečních nul, které chcete zahrnout do formátovaného řetězce, na délku nedoplněného číselného řetězce.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-120">Add the number of leading zeros that you want to include in the formatted string to the length of the unpadded numeric string.</span></span> <span data-ttu-id="c0a2b-121">Přidání počtu počátečních nul definuje celkovou délku čalouněného řetězce.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-121">Adding the number of leading zeros defines the total length of the padded string.</span></span>

1. <span data-ttu-id="c0a2b-122">Zavolejte metodu celočíselné hodnoty `ToString(String)` a předejte řetězec "D*n*" pro desítkové řetězce a "X*n*" pro šestnáctkové řetězce, kde *n* představuje celkovou délku čalouněného řetězce.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-122">Call the integer value's `ToString(String)` method, and pass the string "D*n*" for decimal strings and "X*n*" for hexadecimal strings, where *n* represents the total length of the padded string.</span></span> <span data-ttu-id="c0a2b-123">Můžete také použít formátovací řetězec "D*n*" nebo "X*n*" v metodě, která podporuje složené formátování.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-123">You can also use the "D*n*" or "X*n*" format string in a method that supports composite formatting.</span></span>

<span data-ttu-id="c0a2b-124">V následujícím příkladu je celočíselná hodnota s pěti počátečními nulami.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-124">The following example pads an integer value with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
[!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]

## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="c0a2b-125">Vyplnění číselné hodnoty počátečními nulami na určitou délku</span><span class="sxs-lookup"><span data-stu-id="c0a2b-125">To pad a numeric value with leading zeros to a specific length</span></span>

1. <span data-ttu-id="c0a2b-126">Určete, kolik číslic nalevo od desetinné čárky má mít řetězcové vyjádření čísla.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-126">Determine how many digits to the left of the decimal you want the string representation of the number to have.</span></span> <span data-ttu-id="c0a2b-127">V tomto celkovém počtu číslic uveďte všechny úvodní nuly.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-127">Include any leading zeros in this total number of digits.</span></span>

1. <span data-ttu-id="c0a2b-128">Definujte vlastní řetězec číselného formátu, který používá nulový zástupný symbol "0" k vyjádření minimálního počtu nul.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-128">Define a custom numeric format string that uses the zero placeholder "0" to represent the minimum number of zeros.</span></span>

1. <span data-ttu-id="c0a2b-129">Zavolejte `ToString(String)` metodu Number a předejte jí vlastní formátovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-129">Call the number's `ToString(String)` method and pass it the custom format string.</span></span> <span data-ttu-id="c0a2b-130">Můžete také použít vlastní řetězec formátu s interpolací řetězce nebo metodou, která podporuje složené formátování.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-130">You can also use the custom format string with string interpolation or with a method that supports composite formatting.</span></span>

<span data-ttu-id="c0a2b-131">Následující příklad formátuje několik číselných hodnot s počátečními nulami.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-131">The following example formats several numeric values with leading zeros.</span></span> <span data-ttu-id="c0a2b-132">V důsledku toho je celková délka formátovaného čísla aspoň osm číslic nalevo od desetinné čárky.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-132">As a result, the total length of the formatted number is at least eight digits to the left of the decimal.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
[!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]

## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="c0a2b-133">Vyplnění číselné hodnoty určitým počtem počátečních nul</span><span class="sxs-lookup"><span data-stu-id="c0a2b-133">To pad a numeric value with a specific number of leading zeros</span></span>

1. <span data-ttu-id="c0a2b-134">Určete, kolik počátečních nul má číselná hodnota.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-134">Determine how many leading zeros you want the numeric value to have.</span></span>

1. <span data-ttu-id="c0a2b-135">Určuje počet číslic nalevo od desetinné čárky v nedoplněném číselném řetězci:</span><span class="sxs-lookup"><span data-stu-id="c0a2b-135">Determine the number of digits to the left of the decimal in the unpadded numeric string:</span></span>

    1. <span data-ttu-id="c0a2b-136">Určí, zda řetězcové vyjádření čísla obsahuje symbol desetinné čárky.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-136">Determine whether the string representation of a number includes a decimal point symbol.</span></span>

    1. <span data-ttu-id="c0a2b-137">Pokud obsahuje symbol desetinné čárky, určete počet znaků vlevo od desetinné čárky.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-137">If it does include a decimal point symbol, determine the number of characters to the left of the decimal point.</span></span>

         <span data-ttu-id="c0a2b-138">-nebo-</span><span class="sxs-lookup"><span data-stu-id="c0a2b-138">-or-</span></span>

         <span data-ttu-id="c0a2b-139">Pokud neobsahuje symbol desetinné čárky, určete délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-139">If it doesn't include a decimal point symbol, determine the string's length.</span></span>

1. <span data-ttu-id="c0a2b-140">Vytvořte vlastní řetězec formátu, který používá:</span><span class="sxs-lookup"><span data-stu-id="c0a2b-140">Create a custom format string that uses:</span></span>

    - <span data-ttu-id="c0a2b-141">Nulový zástupný symbol "0" pro každou počáteční nuly, která se má objevit v řetězci.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-141">The zero placeholder "0" for each of the leading zeros to appear in the string.</span></span>

    - <span data-ttu-id="c0a2b-142">Zástupný symbol nula nebo zástupný symbol číslice "#" pro reprezentaci každé číslice ve výchozím řetězci.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-142">Either the zero placeholder or the digit placeholder "#" to represent each digit in the default string.</span></span>

1. <span data-ttu-id="c0a2b-143">Zadejte řetězec vlastního formátu jako parametr buď do metody Number, `ToString(String)` nebo do metody, která podporuje složené formátování.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-143">Supply the custom format string as a parameter either to the number's `ToString(String)` method or to a method that supports composite formatting.</span></span>

<span data-ttu-id="c0a2b-144">Následující příklad <xref:System.Double> doplní dvě hodnoty pěti počátečními nulami.</span><span class="sxs-lookup"><span data-stu-id="c0a2b-144">The following example pads two <xref:System.Double> values with five leading zeros.</span></span>

[!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
[!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]

## <a name="see-also"></a><span data-ttu-id="c0a2b-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="c0a2b-145">See also</span></span>

- [<span data-ttu-id="c0a2b-146">Vlastní řetězce číselného formátu</span><span class="sxs-lookup"><span data-stu-id="c0a2b-146">Custom Numeric Format Strings</span></span>](custom-numeric-format-strings.md)
- [<span data-ttu-id="c0a2b-147">Řetězce standardního číselného formátu</span><span class="sxs-lookup"><span data-stu-id="c0a2b-147">Standard Numeric Format Strings</span></span>](standard-numeric-format-strings.md)
- [<span data-ttu-id="c0a2b-148">Složené formátování</span><span class="sxs-lookup"><span data-stu-id="c0a2b-148">Composite Formatting</span></span>](composite-formatting.md)
