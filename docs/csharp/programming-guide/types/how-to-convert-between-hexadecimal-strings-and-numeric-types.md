---
title: Jak převádět mezi hexadecimálními řetězci a číselnými typy – Průvodce programováním v C#
description: Naučte se převádět mezi hexadecimálními řetězci a číselnými typy. Podívejte se na příklady kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: a49c4a9ee1fc19134d434d42b1eae59376c89fa4
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381798"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="02a14-104">Jak převádět mezi hexadecimálními řetězci a číselnými typy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="02a14-104">How to convert between hexadecimal strings and numeric types (C# Programming Guide)</span></span>
<span data-ttu-id="02a14-105">Tyto příklady vám ukážou, jak provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="02a14-105">These examples show you how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="02a14-106">Získá hexadecimální hodnotu každého znaku v [řetězci](../../language-reference/builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="02a14-106">Obtain the hexadecimal value of each character in a [string](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="02a14-107">Získejte [znak](../../language-reference/builtin-types/char.md) , který odpovídá každé hodnotě v šestnáctkovém řetězci.</span><span class="sxs-lookup"><span data-stu-id="02a14-107">Obtain the [char](../../language-reference/builtin-types/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
- <span data-ttu-id="02a14-108">Převod šestnáctkového čísla `string` na [int](../../language-reference/builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="02a14-108">Convert a hexadecimal `string` to an [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
- <span data-ttu-id="02a14-109">Převod šestnáctkové hodnoty `string` na [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="02a14-109">Convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>  
  
- <span data-ttu-id="02a14-110">Převeďte pole [bajtů](../../language-reference/builtin-types/integral-numeric-types.md) na hexadecimální hodnotu `string` .</span><span class="sxs-lookup"><span data-stu-id="02a14-110">Convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02a14-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="02a14-111">Example</span></span>  
 <span data-ttu-id="02a14-112">Tento příklad vytvoří výstup hexadecimální hodnoty každého znaku v `string` .</span><span class="sxs-lookup"><span data-stu-id="02a14-112">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="02a14-113">Nejprve analyzuje `string` pole znaků.</span><span class="sxs-lookup"><span data-stu-id="02a14-113">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="02a14-114">Pak volá <xref:System.Convert.ToInt32%28System.Char%29> každý znak a získá tak číselnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="02a14-114">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="02a14-115">Nakonec formátuje číslo jako šestnáctkové vyjádření v `string` .</span><span class="sxs-lookup"><span data-stu-id="02a14-115">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a><span data-ttu-id="02a14-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="02a14-116">Example</span></span>  
 <span data-ttu-id="02a14-117">Tento příklad analyzuje `string` šestnáctkové hodnoty a vypíše znak odpovídající každé hexadecimální hodnotě.</span><span class="sxs-lookup"><span data-stu-id="02a14-117">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="02a14-118">Nejprve zavolá metodu [Split (Char \[ \] )](xref:System.String.Split(System.Char[])) pro získání každé hexadecimální hodnoty jako jednotlivce `string` v poli.</span><span class="sxs-lookup"><span data-stu-id="02a14-118">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="02a14-119">Poté volá <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> k převedení hexadecimální hodnoty na desítkovou hodnotu reprezentovanou jako [int](../../language-reference/builtin-types/integral-numeric-types.md). Zobrazuje dva různé způsoby získání znaku odpovídajícího kódu znaku.</span><span class="sxs-lookup"><span data-stu-id="02a14-119">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../language-reference/builtin-types/integral-numeric-types.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="02a14-120">První technika používá <xref:System.Char.ConvertFromUtf32%28System.Int32%29> , která vrací znak odpovídající celočíselnému argumentu jako `string` .</span><span class="sxs-lookup"><span data-stu-id="02a14-120">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="02a14-121">Druhá technika je explicitně přetypování `int` na typ [char](../../language-reference/builtin-types/char.md).</span><span class="sxs-lookup"><span data-stu-id="02a14-121">The second technique explicitly casts the `int` to a [char](../../language-reference/builtin-types/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a><span data-ttu-id="02a14-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="02a14-122">Example</span></span>  
 <span data-ttu-id="02a14-123">Tento příklad ukazuje jiný způsob, jak převést šestnáctkové `string` hodnoty na celé číslo, voláním <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> metody.</span><span class="sxs-lookup"><span data-stu-id="02a14-123">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="02a14-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="02a14-124">Example</span></span>  
 <span data-ttu-id="02a14-125">Následující příklad ukazuje, jak převést šestnáctkovou hodnotu `string` na [float](../../language-reference/builtin-types/floating-point-numeric-types.md) pomocí <xref:System.BitConverter?displayProperty=nameWithType> třídy a <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="02a14-125">The following example shows how to convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a><span data-ttu-id="02a14-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="02a14-126">Example</span></span>  
 <span data-ttu-id="02a14-127">Následující příklad ukazuje, jak převést pole [bajtů](../../language-reference/builtin-types/integral-numeric-types.md) na šestnáctkový řetězec pomocí <xref:System.BitConverter?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="02a14-127">The following example shows how to convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="02a14-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="02a14-128">See also</span></span>

- [<span data-ttu-id="02a14-129">Standardní řetězce pro formátování čísel</span><span class="sxs-lookup"><span data-stu-id="02a14-129">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="02a14-130">Typy</span><span class="sxs-lookup"><span data-stu-id="02a14-130">Types</span></span>](./index.md)
- [<span data-ttu-id="02a14-131">Jak určit, jestli řetězec představuje číselnou hodnotu</span><span class="sxs-lookup"><span data-stu-id="02a14-131">How to determine whether a string represents a numeric value</span></span>](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
