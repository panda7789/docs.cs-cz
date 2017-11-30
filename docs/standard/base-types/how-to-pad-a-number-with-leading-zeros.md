---
title: "Postupy: Zarovnání čísla úvodními nulami"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- numeric format strings [.NET Framework]
- formatting [.NET Framework], numbers
- number formatting [.NET Framework]
- numbers [.NET Framework], format strings
ms.assetid: 0b2c2cb5-c580-4891-8d81-cb632f5ec384
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6266807a01e8119ae1410a1ba09cab55c788b4d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-pad-a-number-with-leading-zeros"></a><span data-ttu-id="ae8b8-102">Postupy: Zarovnání čísla úvodními nulami</span><span class="sxs-lookup"><span data-stu-id="ae8b8-102">How to: Pad a Number with Leading Zeros</span></span>
<span data-ttu-id="ae8b8-103">Úvodní nuly na celé číslo můžete přidat pomocí "D" [standardního řetězce formátu čísel](../../../docs/standard/base-types/standard-numeric-format-strings.md) s specifikátorem přesnosti.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-103">You can add leading zeros to an integer by using the "D" [standard numeric format string](../../../docs/standard/base-types/standard-numeric-format-strings.md) with a precision specifier.</span></span> <span data-ttu-id="ae8b8-104">Můžete přidat pomocí úvodní nuly celé číslo a čísla s plovoucí desetinnou čárkou [vlastní číselný formátovací řetězec](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span><span class="sxs-lookup"><span data-stu-id="ae8b8-104">You can add leading zeros to both integer and floating-point numbers by using a [custom numeric format string](../../../docs/standard/base-types/custom-numeric-format-strings.md).</span></span> <span data-ttu-id="ae8b8-105">Toto téma ukazuje, jak používat obě metody k zarovnání čísla úvodními nulami.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-105">This topic shows how to use both methods to pad a number with leading zeros.</span></span>  
  
### <a name="to-pad-an-integer-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="ae8b8-106">Chcete-li doplnit celé číslo s úvodními nulami na konkrétní délku</span><span class="sxs-lookup"><span data-stu-id="ae8b8-106">To pad an integer with leading zeros to a specific length</span></span>  
  
1.  <span data-ttu-id="ae8b8-107">Určete minimální počet číslic, které chcete celočíselnou hodnotu pro zobrazení.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-107">Determine the minimum number of digits you want the integer value to display.</span></span> <span data-ttu-id="ae8b8-108">Zahrňte všechny úvodní číslice toto číslo.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-108">Include any leading digits in this number.</span></span>  
  
2.  <span data-ttu-id="ae8b8-109">Určí, zda chcete zobrazit na celé číslo jako hodnotu decimal nebo šestnáctkové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-109">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span>  
  
    -   <span data-ttu-id="ae8b8-110">Chcete-li zobrazit celé číslo jako hodnotu decimal, volejte jeho `ToString(String)` metoda a předejte jí řetězec "D*n*" jako hodnotu `format` parametr, kde  *n*  představuje minimální délka řetězce.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-110">To display the integer as a decimal value, call its `ToString(String)` method, and pass the string "D*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>  
  
    -   <span data-ttu-id="ae8b8-111">Pro zobrazení na celé číslo jako šestnáctkové hodnoty, volejte jeho `ToString(String)` metoda a předejte jí řetězec "X*n*" jako hodnotu `format` parametr, kde  *n*  představuje minimální délka řetězce.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-111">To display the integer as a hexadecimal value, call its `ToString(String)` method and pass the string "X*n*" as the value of the `format` parameter, where *n* represents the minimum length of the string.</span></span>  
  
     <span data-ttu-id="ae8b8-112">Můžete také použít řetězec formátu metoda, jako například <xref:System.String.Format%2A> nebo <xref:System.Console.WriteLine%2A>, která používá [složené formátování](../../../docs/standard/base-types/composite-formatting.md).</span><span class="sxs-lookup"><span data-stu-id="ae8b8-112">You can also use the format string in a method, such as <xref:System.String.Format%2A> or <xref:System.Console.WriteLine%2A>, that uses [composite formatting](../../../docs/standard/base-types/composite-formatting.md).</span></span>  
  
 <span data-ttu-id="ae8b8-113">Následující příklad formátuje několik celočíselné hodnoty úvodními nulami tak, aby celková délka číslo naformátovaný aspoň osm znaků.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-113">The following example formats several integer values with leading zeros so that the total length of the formatted number is at least eight characters.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#1)]
 [!code-vb[Formatting.HowTo.PadNumber#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#1)]  
  
### <a name="to-pad-an-integer-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="ae8b8-114">Chcete-li doplnit celé číslo s konkrétní počet úvodní nuly</span><span class="sxs-lookup"><span data-stu-id="ae8b8-114">To pad an integer with a specific number of leading zeros</span></span>  
  
1.  <span data-ttu-id="ae8b8-115">Určete, kolik úvodní nuly chcete celočíselnou hodnotu pro zobrazení.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-115">Determine how many leading zeros you want the integer value to display.</span></span>  
  
2.  <span data-ttu-id="ae8b8-116">Určí, zda chcete zobrazit na celé číslo jako hodnotu decimal nebo šestnáctkové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-116">Determine whether you want to display the integer as a decimal value or a hexadecimal value.</span></span> <span data-ttu-id="ae8b8-117">Formátování jako desítkovou hodnotu vyžaduje, abyste používali specifikátor standardní formát "D"; formátování jako šestnáctkové hodnoty vyžaduje, že používáte specifikátor standardní formát "X".</span><span class="sxs-lookup"><span data-stu-id="ae8b8-117">Formatting it as a decimal value requires that you use the "D" standard format specifier; formatting it as a hexadecimal value requires that you use the "X" standard format specifier.</span></span>  
  
3.  <span data-ttu-id="ae8b8-118">Určete délku nedoplněného číselných řetězců voláním celočíselnou hodnotu `ToString("D").Length` nebo `ToString("X").Length` metoda.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-118">Determine the length of the unpadded numeric string by calling the integer value's `ToString("D").Length` or `ToString("X").Length` method.</span></span>  
  
4.  <span data-ttu-id="ae8b8-119">Přidáte počet úvodní nuly, které chcete zahrnout do formátovaný řetězec, který má délku nedoplněného číselných řetězců.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-119">Add the number of leading zeros that you want to include in the formatted string to the length of the unpadded numeric string.</span></span> <span data-ttu-id="ae8b8-120">Definuje celková délka doplněného řetězce.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-120">This defines the total length of the padded string.</span></span>  
  
5.  <span data-ttu-id="ae8b8-121">Volání celočíselnou hodnotu `ToString(String)` metoda a předejte jí řetězec "D*n*" pro desítkové řetězce a "X*n*" pro řetězce v šestnáctkovém, kde  *n*  představuje celková délka doplněného řetězce.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-121">Call the integer value's `ToString(String)` method, and pass the string "D*n*" for decimal strings and "X*n*" for hexadecimal strings, where *n* represents the total length of the padded string.</span></span> <span data-ttu-id="ae8b8-122">Můžete také "D*n*" nebo "X*n*" naformátovat řetězec v metodu, která podporuje složené formátování.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-122">You can also use the "D*n*" or "X*n*" format string in a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="ae8b8-123">Následující příklad doplní hodnotu celého čísla úvodními nulami pět.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-123">The following example pads an integer value with five leading zeros.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#2)]
 [!code-vb[Formatting.HowTo.PadNumber#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#2)]  
  
### <a name="to-pad-a-numeric-value-with-leading-zeros-to-a-specific-length"></a><span data-ttu-id="ae8b8-124">Chcete-li doplnit číselnou hodnotu úvodními nulami na konkrétní délku</span><span class="sxs-lookup"><span data-stu-id="ae8b8-124">To pad a numeric value with leading zeros to a specific length</span></span>  
  
1.  <span data-ttu-id="ae8b8-125">Určete, kolik číslic nalevo od desetinné čárky chcete řetězcovou reprezentaci číslo, které má mít.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-125">Determine how many digits to the left of the decimal you want the string representation of the number to have.</span></span> <span data-ttu-id="ae8b8-126">Zahrnout všechny úvodní nuly v celkový počet číslic.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-126">Include any leading zeros in this total number of digits.</span></span>  
  
2.  <span data-ttu-id="ae8b8-127">Definujte vlastní číselného formátu řetězec, který používá nulový zástupný symbol ("0"), které představují minimální počet nul.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-127">Define a custom numeric format string that uses the zero placeholder ("0") to represent the minimum number of zeros.</span></span>  
  
3.  <span data-ttu-id="ae8b8-128">Zavolat číslo `ToString(String)` metoda a předejte ji vlastní řetězec formátu.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-128">Call the number's `ToString(String)` method and pass it the custom format string.</span></span> <span data-ttu-id="ae8b8-129">Můžete také vlastní formátovací řetězec pomocí metody, která podporuje složené formátování.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-129">You can also use the custom format string with a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="ae8b8-130">Následující příklad formátuje několik číselných hodnot úvodními nulami tak, aby celková délka číslo formátovaný alespoň osm číslic nalevo od desetinné čárky.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-130">The following example formats several numeric values with leading zeros so that the total length of the formatted number is at least eight digits to the left of the decimal.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#3)]
 [!code-vb[Formatting.HowTo.PadNumber#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#3)]  
  
### <a name="to-pad-a-numeric-value-with-a-specific-number-of-leading-zeros"></a><span data-ttu-id="ae8b8-131">Chcete-li doplnit číselnou hodnotu s konkrétní počet úvodní nuly</span><span class="sxs-lookup"><span data-stu-id="ae8b8-131">To pad a numeric value with a specific number of leading zeros</span></span>  
  
1.  <span data-ttu-id="ae8b8-132">Určete, kolik úvodní nuly chcete číselná hodnota, která mají.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-132">Determine how many leading zeros you want the numeric value to have.</span></span>  
  
2.  <span data-ttu-id="ae8b8-133">Určete počet číslic nalevo od desetinné čárky v nedoplněného číselných řetězců.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-133">Determine the number of digits to the left of the decimal in the unpadded numeric string.</span></span> <span data-ttu-id="ae8b8-134">Provedete to následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ae8b8-134">To do this:</span></span>  
  
    1.  <span data-ttu-id="ae8b8-135">Určí, zda řetězcovou reprezentaci číslo obsahuje symbol desetinné čárky.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-135">Determine whether the string representation of a number includes a decimal point symbol.</span></span>  
  
    2.  <span data-ttu-id="ae8b8-136">Pokud obsahuje symbol desetinné čárky, určete počet znaků směrem doleva od desetinné čárky.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-136">If it does include a decimal point symbol, determine the number of characters to the left of the decimal point.</span></span>  
  
         <span data-ttu-id="ae8b8-137">-nebo-</span><span class="sxs-lookup"><span data-stu-id="ae8b8-137">-or-</span></span>  
  
         <span data-ttu-id="ae8b8-138">Pokud nebude obsahovat symbol desetinné čárky, zjistěte délku řetězce.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-138">If it does not include a decimal point symbol, determine the string's length.</span></span>  
  
3.  <span data-ttu-id="ae8b8-139">Vytvoření vlastní formát řetězce používající nulový zástupný symbol ("0") pro každou úvodní nuly se objeví v řetězci, který používá nulový zástupný symbol nebo zástupný symbol číslice ("#") k reprezentaci jednotlivých číslice v výchozí řetězec.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-139">Create a custom format string that uses the zero placeholder ("0") for each of the leading zeros to appear in the string, and that uses either the zero placeholder or the digit placeholder ("#") to represent each digit in the default string.</span></span>  
  
4.  <span data-ttu-id="ae8b8-140">Zadat vlastní řetězec formátu jako parametr buď na číslo `ToString(String)` metodu nebo metodu, která podporuje složené formátování.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-140">Supply the custom format string as a parameter either to the number's `ToString(String)` method or to a method that supports composite formatting.</span></span>  
  
 <span data-ttu-id="ae8b8-141">Následující příklad doplňuje dvě <xref:System.Double> hodnoty pěti úvodními nulami.</span><span class="sxs-lookup"><span data-stu-id="ae8b8-141">The following example pads two <xref:System.Double> values with five leading zeros.</span></span>  
  
 [!code-csharp[Formatting.HowTo.PadNumber#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.HowTo.PadNumber/cs/Pad1.cs#4)]
 [!code-vb[Formatting.HowTo.PadNumber#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.HowTo.PadNumber/vb/Pad1.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="ae8b8-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="ae8b8-142">See Also</span></span>  
 [<span data-ttu-id="ae8b8-143">Vlastní řetězce číselného formátu</span><span class="sxs-lookup"><span data-stu-id="ae8b8-143">Custom Numeric Format Strings</span></span>](../../../docs/standard/base-types/custom-numeric-format-strings.md)  
 [<span data-ttu-id="ae8b8-144">Standardní řetězce formátu čísla</span><span class="sxs-lookup"><span data-stu-id="ae8b8-144">Standard Numeric Format Strings</span></span>](../../../docs/standard/base-types/standard-numeric-format-strings.md)  
 [<span data-ttu-id="ae8b8-145">Složené formátování</span><span class="sxs-lookup"><span data-stu-id="ae8b8-145">Composite Formatting</span></span>](../../../docs/standard/base-types/composite-formatting.md)
