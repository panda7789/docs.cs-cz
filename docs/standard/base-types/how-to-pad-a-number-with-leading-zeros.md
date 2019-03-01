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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bd016bcb1484f7f94e509e79dbb6b9bb982dd96a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56972537"
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a><span data-ttu-id="7bb50-102">Postupy: Zarovnání čísla úvodními nulami</span><span class="sxs-lookup"><span data-stu-id="7bb50-102">How to: Pad a Number with Leading Zeros</span></span>

<span data-ttu-id="7bb50-103">Můžete přidat počáteční nuly na celé číslo pomocí "D" [řetězec standardního číselného formátu](../../../docs/standard/base-types/standard-numeric-format-strings.md) specifikátorem přesnosti.</span><span class="sxs-lookup"><span data-stu-id="7bb50-103">You can add leading zeros to an integer by using the "D" [standard numeric format string](../../../docs/standard/base-types/standard-numeric-format-strings.md) with a precision specifier.</span></span> <span data-ttu-id="7bb50-104">Můžete přidat počáteční nuly celého čísla a čísla s plovoucí desetinnou čárkou pomocí [vlastní číselný formátovací řetězec](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="7bb50-104">You can add leading zeros to both integer and floating-point numbers by using a [custom numeric format string](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span></span> <span data-ttu-id="7bb50-105">Tento článek ukazuje, jak používat obě metody k zarovnání čísla úvodními nulami.</span><span class="sxs-lookup"><span data-stu-id="7bb50-105">This article shows how to use both methods to pad a number with leading zeros.</span></span>
  
## <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="7bb50-106">Pro vyplnění celého čísla úvodními nulami na konkrétní délku</span><span class="sxs-lookup"><span data-stu-id="7bb50-106">To pad an integer with leading zeros to a specific length</span></span>
  
1. <span data-ttu-id="7bb50-107">Určete minimální počet číslic, které chcete, aby celočíselnou hodnotu pro zobrazení.</span><span class="sxs-lookup"><span data-stu-id="7bb50-107">Determine the minimum number of digits you want the integer value to display.</span></span> <span data-ttu-id="7bb50-108">Zahrňte všechny úvodní číslice tohoto čísla.</span><span class="sxs-lookup"><span data-stu-id="7bb50-108">Include any leading digits in this number.</span></span>  
  
1. <span data-ttu-id="7bb50-109">Určete, zda chcete pro zobrazení na celé číslo jako hodnotu Desítková nebo šestnáctková hodnota.</span><span class="sxs-lookup"><span data-stu-id="7bb50-109">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>  
  
    - <span data-ttu-id="7bb50-110">Pro zobrazení na celé číslo jako hodnotu decimal, volejte jeho `ToString(String)` a předáte řetězec "D*n*" jako hodnotu `format` parametr, kde *n* představuje minimální délka řetězce.</span><span class="sxs-lookup"><span data-stu-id="7bb50-110">To display the integer as a decimal value, call its `ToString(String)` method, and pass the string "D*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>  
  
    - <span data-ttu-id="7bb50-111">Pro zobrazení na celé číslo jako šestnáctkové hodnoty, volejte jeho `ToString(String)` a předáte řetězec "X*n*" jako hodnoty parametru formátu, ve kterém *n* představuje minimální délka řetězce.</span><span class="sxs-lookup"><span data-stu-id="7bb50-111">To display the integer as a hexadecimal value, call its `ToString(String)` method and pass the string "X*n*" as the value of the format parameter, where *n* represents the minimum length of the string.</span></span>
  
<span data-ttu-id="7bb50-112">Můžete také použít řetězec formátu v interpolovaném řetězci v obou [ C# ](../../csharp/language-reference/tokens/interpolated.md) a [jazyka Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), nebo můžete volat metodu, jako například <xref:System.String.Format%2A?displayProperty=nameWithtype> nebo <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, používající [ složené formátování](../../../docs/standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="7bb50-112">You can also use the format string in an interpolated string in both [C#](../../csharp/language-reference/tokens/interpolated.md) and [Visual Basic](../../visual-basic/programming-guide/language-features/strings/interpolated-strings.md), or you can call a method, such as <xref:System.String.Format%2A?displayProperty=nameWithtype> or <xref:System.Console.WriteLine%2A?displayProperty=nameWithType>, that uses [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>  
  
 <span data-ttu-id="7bb50-113">Následující příklad formátuje několik celočíselné hodnoty počátečními nulami tak, aby celková délka naformátovaného čísla alespoň osm znaků.</span><span class="sxs-lookup"><span data-stu-id="7bb50-113">The following example formats several integer values with leading zeros so that the total length of the formatted number is at least eight characters.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
 [!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]  
  
## <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="7bb50-114">Pro vyplnění celé číslo s konkrétní počet počáteční nuly</span><span class="sxs-lookup"><span data-stu-id="7bb50-114">To pad an integer with a specific number of leading zeros</span></span>  
  
1. <span data-ttu-id="7bb50-115">Určete, kolik počátečních nul chcete celočíselnou hodnotu pro zobrazení.</span><span class="sxs-lookup"><span data-stu-id="7bb50-115">Determine how many leading zeros you want the integer value to display.</span></span>  
  
1. <span data-ttu-id="7bb50-116">Určete, zda chcete pro zobrazení na celé číslo jako hodnotu Desítková nebo šestnáctková hodnota.</span><span class="sxs-lookup"><span data-stu-id="7bb50-116">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>

    - <span data-ttu-id="7bb50-117">Formátování jako desítková hodnota vyžaduje, že používáte specifikátor standardního formátu "D".</span><span class="sxs-lookup"><span data-stu-id="7bb50-117">Formatting it as a decimal value requires that you use the "D" standard format specifier.</span></span>

    - <span data-ttu-id="7bb50-118">Formátování jako šestnáctková hodnota vyžaduje, že používáte specifikátor standardního formátu "X".</span><span class="sxs-lookup"><span data-stu-id="7bb50-118">Formatting it as a hexadecimal value requires that you use the "X" standard format specifier.</span></span>
  
1. <span data-ttu-id="7bb50-119">Určuje délku nedoplněného číselný řetězec voláním celočíselnou hodnotu `ToString("D").Length` nebo `ToString("X").Length` metody.</span><span class="sxs-lookup"><span data-stu-id="7bb50-119">Determine the length of the unpadded numeric string by calling the integer value's `ToString("D").Length` or `ToString("X").Length` method.</span></span>
  
1. <span data-ttu-id="7bb50-120">Přidáte počet počátečních nul, které chcete zahrnout do formátovaný řetězec, který má délku nedoplněného číselné řetězce.</span><span class="sxs-lookup"><span data-stu-id="7bb50-120">Add the number of leading zeros that you want to include in the formatted string to the length of the unpadded numeric string.</span></span> <span data-ttu-id="7bb50-121">Přidání čísla nulou definuje celková délka doplněného řetězce.</span><span class="sxs-lookup"><span data-stu-id="7bb50-121">Adding the number of leading zeros defines the total length of the padded string.</span></span>  
  
1. <span data-ttu-id="7bb50-122">Volání celočíselnou hodnotu `ToString(String)` a předáte řetězec "D*n*" decimal řetězců a "X*n*" pro řetězce v šestnáctkovém formátu, ve kterém *n* představuje celkový počet Délka vyplněný řetězce.</span><span class="sxs-lookup"><span data-stu-id="7bb50-122">Call the integer value's `ToString(String)` method, and pass the string "D*n*" for decimal strings and "X*n*" for hexadecimal strings, where *n* represents the total length of the padded string.</span></span> <span data-ttu-id="7bb50-123">Můžete také použít "D*n*" nebo "X*n*" formátovací řetězec v metodě, která podporuje složené formátování.</span><span class="sxs-lookup"><span data-stu-id="7bb50-123">You can also use the "D*n*" or "X*n*" format string in a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="7bb50-124">Následující příklad vyplní celočíselnou hodnotu pěti nulami.</span><span class="sxs-lookup"><span data-stu-id="7bb50-124">The following example pads an integer value with five leading zeros.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
 [!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]  
  
## <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="7bb50-125">Pro vyplnění číselnou hodnotu počátečními nulami na konkrétní délku</span><span class="sxs-lookup"><span data-stu-id="7bb50-125">To pad a numeric value with leading zeros to a specific length</span></span>  
  
1. <span data-ttu-id="7bb50-126">Určete, kolik číslic nalevo od desetinné čárky chcete řetězcové vyjádření čísla mít.</span><span class="sxs-lookup"><span data-stu-id="7bb50-126">Determine how many digits to the left of the decimal you want the string representation of the number to have.</span></span> <span data-ttu-id="7bb50-127">Zahrnout všechny úvodní nuly v tomto celkový počet číslic.</span><span class="sxs-lookup"><span data-stu-id="7bb50-127">Include any leading zeros in this total number of digits.</span></span>  
  
1. <span data-ttu-id="7bb50-128">Definujte vlastní číselný formátovací řetězec, který používá k reprezentaci minimální počet nul nulový zástupný symbol "0".</span><span class="sxs-lookup"><span data-stu-id="7bb50-128">Define a custom numeric format string that uses the zero placeholder "0" to represent the minimum number of zeros.</span></span>  
  
1. <span data-ttu-id="7bb50-129">Zavolejte na číslo `ToString(String)` metoda a předejte jí řetězec vlastního formátu.</span><span class="sxs-lookup"><span data-stu-id="7bb50-129">Call the number's `ToString(String)` method and pass it the custom format string.</span></span> <span data-ttu-id="7bb50-130">Můžete také použít řetězec vlastního formátu pomocí interpolace řetězců nebo metodou, která podporuje složené formátování.</span><span class="sxs-lookup"><span data-stu-id="7bb50-130">You can also use the custom format string with string interpolation or with a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="7bb50-131">Následující příklad formátuje několik číselných hodnot počátečními nulami.</span><span class="sxs-lookup"><span data-stu-id="7bb50-131">The following example formats several numeric values with leading zeros.</span></span> <span data-ttu-id="7bb50-132">Celková délka naformátovaného čísla v důsledku toho je nejméně osm číslic nalevo od desetinné čárky.</span><span class="sxs-lookup"><span data-stu-id="7bb50-132">As a result, the total length of the formatted number is at least eight digits to the left of the decimal.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
 [!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]  
  
## <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="7bb50-133">Pro vyplnění číselná hodnota s konkrétní počet počáteční nuly</span><span class="sxs-lookup"><span data-stu-id="7bb50-133">To pad a numeric value with a specific number of leading zeros</span></span>  
  
1. <span data-ttu-id="7bb50-134">Určete, kolik počátečních nul chcete číselná hodnota, která mají.</span><span class="sxs-lookup"><span data-stu-id="7bb50-134">Determine how many leading zeros you want the numeric value to have.</span></span>  
  
1. <span data-ttu-id="7bb50-135">Určete počet číslic nalevo od desetinné čárky v nedoplněného číselných řetězců:</span><span class="sxs-lookup"><span data-stu-id="7bb50-135">Determine the number of digits to the left of the decimal in the unpadded numeric string:</span></span>  
  
    1. <span data-ttu-id="7bb50-136">Určení, zda řetězcové vyjádření čísla zahrnuje symbol desetinné čárky.</span><span class="sxs-lookup"><span data-stu-id="7bb50-136">Determine whether the string representation of a number includes a decimal point symbol.</span></span>  
  
    1. <span data-ttu-id="7bb50-137">Pokud je symbol desetinné čárky, určete počet znaků vlevo od desetinné čárky.</span><span class="sxs-lookup"><span data-stu-id="7bb50-137">If it does include a decimal point symbol, determine the number of characters to the left of the decimal point.</span></span>  
  
         <span data-ttu-id="7bb50-138">-nebo-</span><span class="sxs-lookup"><span data-stu-id="7bb50-138">-or-</span></span>  
  
         <span data-ttu-id="7bb50-139">Pokud neobsahuje symbol desetinné čárky, určení délky řetězce.</span><span class="sxs-lookup"><span data-stu-id="7bb50-139">If it doesn't include a decimal point symbol, determine the string's length.</span></span>  
  
1. <span data-ttu-id="7bb50-140">Vytvořte vlastní formátovací řetězec, který používá:</span><span class="sxs-lookup"><span data-stu-id="7bb50-140">Create a custom format string that uses:</span></span>

    - <span data-ttu-id="7bb50-141">Nulový zástupný symbol "0" pro každou z počátečních nul se zobrazí v řetězci.</span><span class="sxs-lookup"><span data-stu-id="7bb50-141">The zero placeholder "0" for each of the leading zeros to appear in the string.</span></span>

    - <span data-ttu-id="7bb50-142">Zástupný symbol nula nebo zástupný symbol číslice "#" k reprezentaci jednotlivých číslice v řetězci výchozí.</span><span class="sxs-lookup"><span data-stu-id="7bb50-142">Either the zero placeholder or the digit placeholder "#" to represent each digit in the default string.</span></span>
  
1. <span data-ttu-id="7bb50-143">Zadat vlastní řetězec formátu jako parametr buď na číslo `ToString(String)` metodu nebo metodu, která podporuje složené formátování.</span><span class="sxs-lookup"><span data-stu-id="7bb50-143">Supply the custom format string as a parameter either to the number's `ToString(String)` method or to a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="7bb50-144">Následující příklad vyplní dvě <xref:System.Double> hodnoty pěti nulami.</span><span class="sxs-lookup"><span data-stu-id="7bb50-144">The following example pads two <xref:System.Double> values with five leading zeros.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
 [!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="7bb50-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7bb50-145">See also</span></span>

- [<span data-ttu-id="7bb50-146">Vlastní řetězce číselného formátu</span><span class="sxs-lookup"><span data-stu-id="7bb50-146">Custom Numeric Format Strings</span></span>](../../../docs/standard/base-types/custom-numeric-format-strings.md)
- [<span data-ttu-id="7bb50-147">Standardní řetězce číselného formátu</span><span class="sxs-lookup"><span data-stu-id="7bb50-147">Standard Numeric Format Strings</span></span>](../../../docs/standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="7bb50-148">Složené formátování</span><span class="sxs-lookup"><span data-stu-id="7bb50-148">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
