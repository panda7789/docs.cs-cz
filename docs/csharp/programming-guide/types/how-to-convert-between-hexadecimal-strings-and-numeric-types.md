---
title: 'Postupy: převod mezi hexadecimálními řetězci a číselnými typy C# – Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: 8b72734f9b617fed2ff65977c9a0e60f46424ae8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429437"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="85ddc-102">Postupy: Převod mezi hexadecimálními řetězci a číselnými typy (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="85ddc-102">How to: Convert Between Hexadecimal Strings and Numeric Types (C# Programming Guide)</span></span>
<span data-ttu-id="85ddc-103">Tyto příklady vám ukážou, jak provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="85ddc-103">These examples show you how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="85ddc-104">Získá hexadecimální hodnotu každého znaku v [řetězci](../../language-reference/builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="85ddc-104">Obtain the hexadecimal value of each character in a [string](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="85ddc-105">Získejte [znak](../../language-reference/builtin-types/char.md) , který odpovídá každé hodnotě v šestnáctkovém řetězci.</span><span class="sxs-lookup"><span data-stu-id="85ddc-105">Obtain the [char](../../language-reference/builtin-types/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
- <span data-ttu-id="85ddc-106">Převeďte hexadecimální `string` na [int](../../language-reference/builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="85ddc-106">Convert a hexadecimal `string` to an [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
- <span data-ttu-id="85ddc-107">Převést hexadecimální `string` na typ [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="85ddc-107">Convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>  
  
- <span data-ttu-id="85ddc-108">Převeďte [bajtové](../../language-reference/builtin-types/integral-numeric-types.md) pole na hexadecimální `string`.</span><span class="sxs-lookup"><span data-stu-id="85ddc-108">Convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85ddc-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="85ddc-109">Example</span></span>  
 <span data-ttu-id="85ddc-110">Tento příklad vypíše hexadecimální hodnotu každého znaku v `string`.</span><span class="sxs-lookup"><span data-stu-id="85ddc-110">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="85ddc-111">Nejprve analyzuje `string` na pole znaků.</span><span class="sxs-lookup"><span data-stu-id="85ddc-111">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="85ddc-112">Pak volá <xref:System.Convert.ToInt32%28System.Char%29> u každého znaku a získá tak číselnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="85ddc-112">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="85ddc-113">Nakonec formátuje číslo jako šestnáctkové vyjádření v `string`.</span><span class="sxs-lookup"><span data-stu-id="85ddc-113">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a><span data-ttu-id="85ddc-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="85ddc-114">Example</span></span>  
 <span data-ttu-id="85ddc-115">Tento příklad analyzuje `string` hexadecimálních hodnot a vypíše znak odpovídající každé hexadecimální hodnotě.</span><span class="sxs-lookup"><span data-stu-id="85ddc-115">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="85ddc-116">Nejprve volá metodu [Split (Char\[\])](xref:System.String.Split(System.Char[])) k získání každé hexadecimální hodnoty jako jednotlivé `string` v poli.</span><span class="sxs-lookup"><span data-stu-id="85ddc-116">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="85ddc-117">Poté volá <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> pro převod hexadecimální hodnoty na desítkovou hodnotu reprezentovanou jako [int](../../language-reference/builtin-types/integral-numeric-types.md). Zobrazuje dva různé způsoby získání znaku odpovídajícího kódu znaku.</span><span class="sxs-lookup"><span data-stu-id="85ddc-117">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../language-reference/builtin-types/integral-numeric-types.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="85ddc-118">První technika používá <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, která vrací znak odpovídající celočíselnému argumentu jako `string`.</span><span class="sxs-lookup"><span data-stu-id="85ddc-118">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="85ddc-119">Druhá technika je explicitně přetypování `int` na [znak](../../language-reference/builtin-types/char.md).</span><span class="sxs-lookup"><span data-stu-id="85ddc-119">The second technique explicitly casts the `int` to a [char](../../language-reference/builtin-types/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a><span data-ttu-id="85ddc-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="85ddc-120">Example</span></span>  
 <span data-ttu-id="85ddc-121">Tento příklad ukazuje jiný způsob, jak převést šestnáctkovou `string` na celé číslo, voláním metody <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29>.</span><span class="sxs-lookup"><span data-stu-id="85ddc-121">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="85ddc-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="85ddc-122">Example</span></span>  
 <span data-ttu-id="85ddc-123">Následující příklad ukazuje, jak převést šestnáctkovou `string` na typ [float](../../language-reference/builtin-types/floating-point-numeric-types.md) pomocí <xref:System.BitConverter?displayProperty=nameWithType> třídy a metody <xref:System.UInt32.Parse%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="85ddc-123">The following example shows how to convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a><span data-ttu-id="85ddc-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="85ddc-124">Example</span></span>  
 <span data-ttu-id="85ddc-125">Následující příklad ukazuje, jak převést [bajtové](../../language-reference/builtin-types/integral-numeric-types.md) pole na šestnáctkový řetězec pomocí třídy <xref:System.BitConverter?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="85ddc-125">The following example shows how to convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="85ddc-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85ddc-126">See also</span></span>

- [<span data-ttu-id="85ddc-127">Standardní řetězce číselného formátu</span><span class="sxs-lookup"><span data-stu-id="85ddc-127">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="85ddc-128">Typy</span><span class="sxs-lookup"><span data-stu-id="85ddc-128">Types</span></span>](./index.md)
- [<span data-ttu-id="85ddc-129">Postupy: Určení, zda řetězec reprezentuje číselnou hodnotu</span><span class="sxs-lookup"><span data-stu-id="85ddc-129">How to: Determine Whether a String Represents a Numeric Value</span></span>](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
