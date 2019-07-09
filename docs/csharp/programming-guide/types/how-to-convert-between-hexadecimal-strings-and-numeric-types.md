---
title: 'Postupy: Převod mezi hexadecimálními řetězci a číselnými typy - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: 2b896fb645113bc33b6a320948770947adc16dab
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67661146"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a><span data-ttu-id="4d0b4-102">Postupy: Převod mezi hexadecimálními řetězci a číselnými typy (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="4d0b4-102">How to: Convert Between Hexadecimal Strings and Numeric Types (C# Programming Guide)</span></span>
<span data-ttu-id="4d0b4-103">Tyto příklady ukazují, jak provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="4d0b4-103">These examples show you how to perform the following tasks:</span></span>  
  
- <span data-ttu-id="4d0b4-104">Získat šestnáctkovou hodnotu každého znaku v [řetězec](../../../csharp/language-reference/keywords/string.md).</span><span class="sxs-lookup"><span data-stu-id="4d0b4-104">Obtain the hexadecimal value of each character in a [string](../../../csharp/language-reference/keywords/string.md).</span></span>  
  
- <span data-ttu-id="4d0b4-105">Získat [char](../../../csharp/language-reference/keywords/char.md) odpovídající každé hodnotě v je možné šestnáctkový řetězec.</span><span class="sxs-lookup"><span data-stu-id="4d0b4-105">Obtain the [char](../../../csharp/language-reference/keywords/char.md) that corresponds to each value in a hexadecimal string.</span></span>  
  
- <span data-ttu-id="4d0b4-106">Převést šestnáctkové `string` do [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="4d0b4-106">Convert a hexadecimal `string` to an [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
- <span data-ttu-id="4d0b4-107">Převést šestnáctkové `string` k [float](../../../csharp/language-reference/builtin-types/floating-point-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="4d0b4-107">Convert a hexadecimal `string` to a [float](../../../csharp/language-reference/builtin-types/floating-point-numeric-types.md).</span></span>  
  
- <span data-ttu-id="4d0b4-108">Převést [bajtů](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) pole, které chcete hexadecimální `string`.</span><span class="sxs-lookup"><span data-stu-id="4d0b4-108">Convert a [byte](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal `string`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d0b4-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d0b4-109">Example</span></span>  
 <span data-ttu-id="4d0b4-110">Šestnáctková hodnota každý znak v tomto příkladu je výstupem `string`.</span><span class="sxs-lookup"><span data-stu-id="4d0b4-110">This example outputs the hexadecimal value of each character in a `string`.</span></span> <span data-ttu-id="4d0b4-111">Nejprve analyzuje `string` na pole znaků.</span><span class="sxs-lookup"><span data-stu-id="4d0b4-111">First it parses the `string` to an array of characters.</span></span> <span data-ttu-id="4d0b4-112">Potom volá <xref:System.Convert.ToInt32%28System.Char%29> na jednotlivé znaky získat číselnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4d0b4-112">Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value.</span></span> <span data-ttu-id="4d0b4-113">A konečně, formátuje číslo jako její šestnáctkové vyjádření v `string`.</span><span class="sxs-lookup"><span data-stu-id="4d0b4-113">Finally, it formats the number as its hexadecimal representation in a `string`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a><span data-ttu-id="4d0b4-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d0b4-114">Example</span></span>  
 <span data-ttu-id="4d0b4-115">V tomto příkladu analyzuje `string` z šestnáctkové hodnoty a uloží znak, který odpovídá každé šestnáctková hodnota.</span><span class="sxs-lookup"><span data-stu-id="4d0b4-115">This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value.</span></span> <span data-ttu-id="4d0b4-116">Nejprve se volá [rozdělit (Char\[\])](xref:System.String.Split(System.Char[])) metodu k získání jednotlivých šestnáctkové hodnoty jako individuální uživatel `string` v poli.</span><span class="sxs-lookup"><span data-stu-id="4d0b4-116">First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array.</span></span> <span data-ttu-id="4d0b4-117">Potom volá <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> převést na šestnáctkovou hodnotu Desítková hodnota reprezentovaná jako [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md). Ukazuje dva různé způsoby, získat znak, který odpovídá této kód znaku.</span><span class="sxs-lookup"><span data-stu-id="4d0b4-117">Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../../csharp/language-reference/builtin-types/integral-numeric-types.md). It shows two different ways to obtain the character corresponding to that character code.</span></span> <span data-ttu-id="4d0b4-118">První způsob využívá <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, která vrací odpovídající argument typu celé číslo jako znak `string`.</span><span class="sxs-lookup"><span data-stu-id="4d0b4-118">The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`.</span></span> <span data-ttu-id="4d0b4-119">Druhý způsob spočívá explicitní přetypování `int` k [char](../../../csharp/language-reference/keywords/char.md).</span><span class="sxs-lookup"><span data-stu-id="4d0b4-119">The second technique explicitly casts the `int` to a [char](../../../csharp/language-reference/keywords/char.md).</span></span>  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a><span data-ttu-id="4d0b4-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d0b4-120">Example</span></span>  
 <span data-ttu-id="4d0b4-121">Tento příklad ukazuje další způsob, jak převést šestnáctkové `string` na celé číslo, voláním <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> metody.</span><span class="sxs-lookup"><span data-stu-id="4d0b4-121">This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a><span data-ttu-id="4d0b4-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d0b4-122">Example</span></span>  
 <span data-ttu-id="4d0b4-123">Následující příklad ukazuje, jak převést šestnáctkové `string` k [float](../../../csharp/language-reference/builtin-types/floating-point-numeric-types.md) pomocí <xref:System.BitConverter?displayProperty=nameWithType> třídy a <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="4d0b4-123">The following example shows how to convert a hexadecimal `string` to a [float](../../../csharp/language-reference/builtin-types/floating-point-numeric-types.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a><span data-ttu-id="4d0b4-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d0b4-124">Example</span></span>  
 <span data-ttu-id="4d0b4-125">Následující příklad ukazuje, jak převést [bajtů](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) pole je možné šestnáctkový řetězec s použitím <xref:System.BitConverter?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="4d0b4-125">The following example shows how to convert a [byte](../../../csharp/language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.</span></span>  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a><span data-ttu-id="4d0b4-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d0b4-126">See also</span></span>

- [<span data-ttu-id="4d0b4-127">Standardní řetězce číselného formátu</span><span class="sxs-lookup"><span data-stu-id="4d0b4-127">Standard Numeric Format Strings</span></span>](../../../standard/base-types/standard-numeric-format-strings.md)
- [<span data-ttu-id="4d0b4-128">Typy</span><span class="sxs-lookup"><span data-stu-id="4d0b4-128">Types</span></span>](../../../csharp/programming-guide/types/index.md)
- [<span data-ttu-id="4d0b4-129">Postupy: Určení, zda řetězec reprezentuje číselnou hodnotu</span><span class="sxs-lookup"><span data-stu-id="4d0b4-129">How to: Determine Whether a String Represents a Numeric Value</span></span>](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
