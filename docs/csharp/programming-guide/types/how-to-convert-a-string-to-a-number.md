---
title: "Postupy: Převedení řetězce na číslo (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
caps.latest.revision: "34"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3dc67bc2f25bba14df0e3ce6859bb8bc9094871c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a><span data-ttu-id="96f75-102">Postupy: Převedení řetězce na číslo (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="96f75-102">How to: Convert a String to a Number (C# Programming Guide)</span></span>
<span data-ttu-id="96f75-103">Můžete převést [řetězec](../../../csharp/language-reference/keywords/string.md) na číslo pomocí metody v <xref:System.Convert> třídy nebo pomocí `TryParse` nalezena metoda na různých číselnými typy (int, dlouhé, float, atd.).</span><span class="sxs-lookup"><span data-stu-id="96f75-103">You can convert a [string](../../../csharp/language-reference/keywords/string.md) to a number by using methods in the <xref:System.Convert> class or by using the `TryParse` method found on the various numeric types (int, long, float, etc.).</span></span>  
  
 <span data-ttu-id="96f75-104">Pokud máte řetězec, je něco víc efektivní a přímý k volání `TryParse` – metoda (například `int.TryParse("11")`).</span><span class="sxs-lookup"><span data-stu-id="96f75-104">If you have a string, it is slightly more efficient and straightforward to call a `TryParse` method (for example, `int.TryParse("11")`).</span></span>  <span data-ttu-id="96f75-105">Použití `Convert` je užitečnější pro obecné objekty, které implementují <xref:System.IConvertible>.</span><span class="sxs-lookup"><span data-stu-id="96f75-105">Using a `Convert` method is more useful for general objects that implement <xref:System.IConvertible>.</span></span>  
  
 <span data-ttu-id="96f75-106">Můžete použít `Parse` nebo `TryParse` metody na číselný typ očekáváte, že obsahuje řetězec, například <xref:System.Int32?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="96f75-106">You can use `Parse` or `TryParse` methods on the numeric type you expect the string contains, such as the <xref:System.Int32?displayProperty=nameWithType> type.</span></span>  <span data-ttu-id="96f75-107"><xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> Používá metoda <xref:System.Int32.Parse%2A> interně.</span><span class="sxs-lookup"><span data-stu-id="96f75-107">The <xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> method uses <xref:System.Int32.Parse%2A> internally.</span></span>  <span data-ttu-id="96f75-108">Pokud řetězec není v platném formátu `Parse` vyvolá výjimku, zatímco `TryParse` vrátí [false](../../../csharp/language-reference/keywords/false.md).</span><span class="sxs-lookup"><span data-stu-id="96f75-108">If the string is not in a valid format, `Parse` throws an exception whereas `TryParse` returns [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="96f75-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="96f75-109">Example</span></span>  
 <span data-ttu-id="96f75-110">`Parse` a `TryParse` metody Ignorovat prázdné znaky na začátku a na konci řetězce, ale všechny ostatní znaky musí být znaky, které tvoří příslušného číselného typu (int, long, ulong, float, decimal, atd.).</span><span class="sxs-lookup"><span data-stu-id="96f75-110">The `Parse` and `TryParse` methods ignore whitespace at the beginning and at the end of the string, but all other characters must be characters that form the appropriate numeric type (int, long, ulong, float, decimal, etc.).</span></span>  <span data-ttu-id="96f75-111">Všechny prázdné znaky v rámci znaky, které vytvářejí číslo způsobit chybu.</span><span class="sxs-lookup"><span data-stu-id="96f75-111">Any whitespace within the characters that form the number cause an error.</span></span>  <span data-ttu-id="96f75-112">Například můžete použít `decimal.TryParse` analyzovat "10", "10.3", "10", ale tuto metodu nelze použít k analýze 10 z "10 X", "1 0" (Poznámka místa), "10. 3" (Poznámka místa), "10e1" (`float.TryParse` zde funguje), a tak dále.</span><span class="sxs-lookup"><span data-stu-id="96f75-112">For example, you can use `decimal.TryParse` to parse "10", "10.3", "  10  ", but you cannot use this method to parse 10 from "10X", "1 0" (note space), "10 .3" (note space), "10e1" (`float.TryParse` works here), and so on.</span></span>  
  
 <span data-ttu-id="96f75-113">Následující příklady ukazují úspěšné i neúspěšné volání `Parse` a `TryParse`.</span><span class="sxs-lookup"><span data-stu-id="96f75-113">The examples below demonstrate both successful and unsuccessful calls to `Parse` and `TryParse`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]  
[!code-csharp[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]  
[!code-csharp[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]  
[!code-csharp[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]  
[!code-csharp[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]  
  
## <a name="example"></a><span data-ttu-id="96f75-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="96f75-114">Example</span></span>  
 <span data-ttu-id="96f75-115">Následující tabulka uvádí některé z metod z <xref:System.Convert> třídu, která můžete použít.</span><span class="sxs-lookup"><span data-stu-id="96f75-115">The following table lists some of the methods from the <xref:System.Convert> class that you can use.</span></span>  
  
|<span data-ttu-id="96f75-116">Číselný typ</span><span class="sxs-lookup"><span data-stu-id="96f75-116">Numeric Type</span></span>|<span data-ttu-id="96f75-117">Metoda</span><span class="sxs-lookup"><span data-stu-id="96f75-117">Method</span></span>|  
|------------------|------------|  
|`decimal`|<xref:System.Convert.ToDecimal%28System.String%29>|  
|`float`|<xref:System.Convert.ToSingle%28System.String%29>|  
|`double`|<xref:System.Convert.ToDouble%28System.String%29>|  
|`short`|<xref:System.Convert.ToInt16%28System.String%29>|  
|`int`|<xref:System.Convert.ToInt32%28System.String%29>|  
|`long`|<xref:System.Convert.ToInt64%28System.String%29>|  
|`ushort`|<xref:System.Convert.ToUInt16%28System.String%29>|  
|`uint`|<xref:System.Convert.ToUInt32%28System.String%29>|  
|`ulong`|<xref:System.Convert.ToUInt64%28System.String%29>|  
  
 <span data-ttu-id="96f75-118">Tento příklad volá <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> způsobů, jak převést vstup [řetězec](../../../csharp/language-reference/keywords/string.md) k [int](../../../csharp/language-reference/keywords/int.md) .</span><span class="sxs-lookup"><span data-stu-id="96f75-118">This example calls the <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> method to convert an input [string](../../../csharp/language-reference/keywords/string.md) to an [int](../../../csharp/language-reference/keywords/int.md) .</span></span> <span data-ttu-id="96f75-119">Kód zachytí dvě nejběžnější výjimky, které může být vyvolána touto metodou, <xref:System.FormatException> a <xref:System.OverflowException>.</span><span class="sxs-lookup"><span data-stu-id="96f75-119">The code catches the two most common exceptions that can be thrown by this method, <xref:System.FormatException> and <xref:System.OverflowException>.</span></span> <span data-ttu-id="96f75-120">Pokud lze číslo zvýšit bez přetečení umístění úložiště celého čísla, program přidá k výsledku hodnotu 1 a výstup vytiskne.</span><span class="sxs-lookup"><span data-stu-id="96f75-120">If the number can be incremented without overflowing the integer storage location, the program adds 1 to the result and prints the output.</span></span>  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="96f75-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="96f75-121">See Also</span></span>  
 [<span data-ttu-id="96f75-122">Typy</span><span class="sxs-lookup"><span data-stu-id="96f75-122">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="96f75-123">Postupy: určení, zda řetězec reprezentuje číselnou hodnotu</span><span class="sxs-lookup"><span data-stu-id="96f75-123">How to: Determine Whether a String Represents a Numeric Value</span></span>](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)  
 [<span data-ttu-id="96f75-124">Nástroj formátování rozhraní .NET framework 4</span><span class="sxs-lookup"><span data-stu-id="96f75-124">.NET Framework 4 Formatting Utility</span></span>](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
