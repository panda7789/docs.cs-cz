---
title: 'Postupy: Převod mezi hexadecimálními řetězci a číselnými C# typy – Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: a7109945192fe1577cd1b96c8b4d6c05270d54e8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588382"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="ba56e-102">Postupy: Převod mezi hexadecimálními řetězci a číselnýmiC# typy (Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="ba56e-102">How to: Convert Between Hexadecimal Strings and Numeric Types (C# Programming Guide)</span></span>
<span data-ttu-id="ba56e-103">Tyto příklady vám ukážou, jak provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="ba56e-103">These examples show you how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="ba56e-104">Získá hexadecimální hodnotu každého znaku v [řetězci](../../language-reference/keywords/string.md).</span><span class="sxs-lookup"><span data-stu-id="ba56e-104">Obtain the hexadecimal value of each character in a [string](../../language-reference/keywords/string.md).</span></span>  
  
- <span data-ttu-id="ba56e-105">Získejte [znak](../../language-reference/keywords/char.md) , který odpovídá každé hodnotě v šestnáctkovém řetězci.</span><span class="sxs-lookup"><span data-stu-id="ba56e-105">Obtain the [char](../../language-reference/keywords/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
- <span data-ttu-id="ba56e-106">Převod šestnáctkového `string` čísla na [int](../../language-reference/builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="ba56e-106">Convert a hexadecimal `string` to an [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
- <span data-ttu-id="ba56e-107">Převod šestnáctkové `string` hodnoty na [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="ba56e-107">Convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>  
  
- <span data-ttu-id="ba56e-108">Převeďte pole [bajtů](../../language-reference/builtin-types/integral-numeric-types.md) na hexadecimální `string`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ba56e-108">Convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba56e-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="ba56e-109">Example</span></span>  
 <span data-ttu-id="ba56e-110">Tento příklad vytvoří výstup hexadecimální hodnoty každého znaku v `string`.</span><span class="sxs-lookup"><span data-stu-id="ba56e-110">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="ba56e-111">Nejprve analyzuje `string` pole znaků.</span><span class="sxs-lookup"><span data-stu-id="ba56e-111">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="ba56e-112">Pak volá <xref:System.Convert.ToInt32%28System.Char%29> každý znak a získá tak číselnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ba56e-112">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="ba56e-113">Nakonec formátuje číslo jako šestnáctkové vyjádření v `string`.</span><span class="sxs-lookup"><span data-stu-id="ba56e-113">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a><span data-ttu-id="ba56e-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="ba56e-114">Example</span></span>  
 <span data-ttu-id="ba56e-115">Tento příklad analyzuje `string` šestnáctkové hodnoty a vypíše znak odpovídající každé hexadecimální hodnotě.</span><span class="sxs-lookup"><span data-stu-id="ba56e-115">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="ba56e-116">Nejprve zavolá metodu [Split (Char\[\])](xref:System.String.Split(System.Char[])) pro získání každé hexadecimální hodnoty jako jednotlivce `string` v poli.</span><span class="sxs-lookup"><span data-stu-id="ba56e-116">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="ba56e-117">Poté volá <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> k převedení hexadecimální hodnoty na desítkovou hodnotu reprezentovanou jako [int](../../language-reference/builtin-types/integral-numeric-types.md). Zobrazuje dva různé způsoby získání znaku odpovídajícího kódu znaku.</span><span class="sxs-lookup"><span data-stu-id="ba56e-117">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../language-reference/builtin-types/integral-numeric-types.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="ba56e-118">První technika používá <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, která vrací znak odpovídající celočíselnému argumentu `string`jako.</span><span class="sxs-lookup"><span data-stu-id="ba56e-118">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="ba56e-119">Druhá technika je explicitně přetypování `int` na typ [char](../../language-reference/keywords/char.md).</span><span class="sxs-lookup"><span data-stu-id="ba56e-119">The second technique explicitly casts the `int` to a [char](../../language-reference/keywords/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a><span data-ttu-id="ba56e-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="ba56e-120">Example</span></span>  
 <span data-ttu-id="ba56e-121">Tento příklad ukazuje jiný způsob, jak převést šestnáctkové `string` hodnoty na celé číslo, <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> voláním metody.</span><span class="sxs-lookup"><span data-stu-id="ba56e-121">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="ba56e-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="ba56e-122">Example</span></span>  
 <span data-ttu-id="ba56e-123">Následující příklad ukazuje `string` , jak převést šestnáctkovou hodnotu na [float](../../language-reference/builtin-types/floating-point-numeric-types.md) <xref:System.BitConverter?displayProperty=nameWithType> pomocí třídy a <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ba56e-123">The following example shows how to convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a><span data-ttu-id="ba56e-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="ba56e-124">Example</span></span>  
 <span data-ttu-id="ba56e-125">Následující příklad ukazuje, jak převést pole [bajtů](../../language-reference/builtin-types/integral-numeric-types.md) na šestnáctkový řetězec pomocí <xref:System.BitConverter?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="ba56e-125">The following example shows how to convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="ba56e-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba56e-126">See also</span></span>

- [<span data-ttu-id="ba56e-127">Standardní řetězce číselného formátu</span><span class="sxs-lookup"><span data-stu-id="ba56e-127">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="ba56e-128">Typy</span><span class="sxs-lookup"><span data-stu-id="ba56e-128">Types</span></span>](./index.md)
- [<span data-ttu-id="ba56e-129">Postupy: Určení, zda řetězec představuje číselnou hodnotu</span><span class="sxs-lookup"><span data-stu-id="ba56e-129">How to: Determine Whether a String Represents a Numeric Value</span></span>](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
