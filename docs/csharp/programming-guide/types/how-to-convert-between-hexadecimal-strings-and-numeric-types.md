---
title: Převod mezi šestnáctkovými řetězci a číselnými typy – Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: 0e1f6ad2606b367d369c1c644c947831b2aa8289
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75698518"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="53abb-102">Převod mezi šestnáctkovými řetězci a číselnými typy (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="53abb-102">How to convert between hexadecimal strings and numeric types (C# Programming Guide)</span></span>
<span data-ttu-id="53abb-103">Tyto příklady ukazují, jak provádět následující úkoly:</span><span class="sxs-lookup"><span data-stu-id="53abb-103">These examples show you how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="53abb-104">Získejte šestnáctkovou hodnotu každého znaku v [řetězci](../../language-reference/builtin-types/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="53abb-104">Obtain the hexadecimal value of each character in a [string](../../language-reference/builtin-types/reference-types.md).</span></span>  
  
- <span data-ttu-id="53abb-105">Získejte [znak,](../../language-reference/builtin-types/char.md) který odpovídá každé hodnotě v šestnáctkovém řetězci.</span><span class="sxs-lookup"><span data-stu-id="53abb-105">Obtain the [char](../../language-reference/builtin-types/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
- <span data-ttu-id="53abb-106">Převeďte šestnáctkový `string` na [int](../../language-reference/builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="53abb-106">Convert a hexadecimal `string` to an [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
- <span data-ttu-id="53abb-107">Převeďte šestnáctkový `string` převodník na [plovák](../../language-reference/builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="53abb-107">Convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md).</span></span>  
  
- <span data-ttu-id="53abb-108">Převeďte [bajtové](../../language-reference/builtin-types/integral-numeric-types.md) pole na šestnáctkové `string`pole .</span><span class="sxs-lookup"><span data-stu-id="53abb-108">Convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53abb-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="53abb-109">Example</span></span>  
 <span data-ttu-id="53abb-110">Tento příklad vyvodí šestnáctkovou hodnotu `string`každého znaku v .</span><span class="sxs-lookup"><span data-stu-id="53abb-110">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="53abb-111">Nejprve analyzuje `string` pole znaků.</span><span class="sxs-lookup"><span data-stu-id="53abb-111">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="53abb-112">Potom volá <xref:System.Convert.ToInt32%28System.Char%29> každý znak získat jeho číselnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="53abb-112">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="53abb-113">Nakonec zformátuje číslo jako jeho šestnáctkové znázornění `string`v .</span><span class="sxs-lookup"><span data-stu-id="53abb-113">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a><span data-ttu-id="53abb-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="53abb-114">Example</span></span>  
 <span data-ttu-id="53abb-115">Tento příklad analyzuje `string` šestnáctkové hodnoty a výstupy znak odpovídající každé šestnáctkové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="53abb-115">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="53abb-116">Nejprve volá [Split(Char\[\])](xref:System.String.Split(System.Char[])) metoda získat každou šestnáctkovou hodnotu jako jednotlivec `string` v poli.</span><span class="sxs-lookup"><span data-stu-id="53abb-116">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="53abb-117">Pak volá <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> převést šestnáctkovou hodnotu na desetinnou hodnotu reprezentovanou jako [int](../../language-reference/builtin-types/integral-numeric-types.md). Zobrazuje dva různé způsoby, jak získat znak odpovídající tomuto kódu znaku.</span><span class="sxs-lookup"><span data-stu-id="53abb-117">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../language-reference/builtin-types/integral-numeric-types.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="53abb-118">Používá první <xref:System.Char.ConvertFromUtf32%28System.Int32%29>technika , která vrátí znak odpovídající argumentu `string`celé číslo jako .</span><span class="sxs-lookup"><span data-stu-id="53abb-118">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="53abb-119">Druhá technika explicitně `int` vrhá char [.](../../language-reference/builtin-types/char.md)</span><span class="sxs-lookup"><span data-stu-id="53abb-119">The second technique explicitly casts the `int` to a [char](../../language-reference/builtin-types/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a><span data-ttu-id="53abb-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="53abb-120">Example</span></span>  
 <span data-ttu-id="53abb-121">Tento příklad ukazuje jiný způsob, jak převést šestnáctkové `string` na celé <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> číslo voláním metody.</span><span class="sxs-lookup"><span data-stu-id="53abb-121">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="53abb-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="53abb-122">Example</span></span>  
 <span data-ttu-id="53abb-123">Následující příklad ukazuje, jak převést šestnáctkové `string` na [float](../../language-reference/builtin-types/floating-point-numeric-types.md) pomocí <xref:System.BitConverter?displayProperty=nameWithType> třídy <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> a metody.</span><span class="sxs-lookup"><span data-stu-id="53abb-123">The following example shows how to convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a><span data-ttu-id="53abb-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="53abb-124">Example</span></span>  
 <span data-ttu-id="53abb-125">Následující příklad ukazuje, jak převést [bajtové](../../language-reference/builtin-types/integral-numeric-types.md) pole na šestnáctkový <xref:System.BitConverter?displayProperty=nameWithType> řetězec pomocí třídy.</span><span class="sxs-lookup"><span data-stu-id="53abb-125">The following example shows how to convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="53abb-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="53abb-126">See also</span></span>

- [<span data-ttu-id="53abb-127">Standardní řetězce číselného formátu</span><span class="sxs-lookup"><span data-stu-id="53abb-127">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="53abb-128">Typy</span><span class="sxs-lookup"><span data-stu-id="53abb-128">Types</span></span>](./index.md)
- [<span data-ttu-id="53abb-129">Jak určit, jestli řetězec představuje číselnou hodnotu</span><span class="sxs-lookup"><span data-stu-id="53abb-129">How to determine whether a string represents a numeric value</span></span>](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
