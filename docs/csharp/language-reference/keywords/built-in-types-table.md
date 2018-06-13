---
title: Tabulka předdefinovaných typů (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#], built-in
- built-in C# types
ms.assetid: 54f901f2-bf2f-472c-ae8d-73e8ecfc57fe
ms.openlocfilehash: 120347e5bff7f0d6c7120af0cb250936ca39ea16
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172263"
---
# <a name="built-in-types-table-c-reference"></a><span data-ttu-id="45194-102">Tabulka předdefinovaných typů (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="45194-102">Built-In Types Table (C# Reference)</span></span>
<span data-ttu-id="45194-103">V následující tabulce jsou uvedeny klíčová slova pro vestavěné C# typy, které jsou aliasy předdefinovaných typů v <xref:System> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="45194-103">The following table shows the keywords for built-in C# types, which are aliases of predefined types in the <xref:System> namespace.</span></span>  
  
|<span data-ttu-id="45194-104">Typ jazyka C#</span><span class="sxs-lookup"><span data-stu-id="45194-104">C# Type</span></span>|<span data-ttu-id="45194-105">Typ rozhraní .NET framework</span><span class="sxs-lookup"><span data-stu-id="45194-105">.NET Framework Type</span></span>|  
|--------------|-------------------------|  
|[<span data-ttu-id="45194-106">bool</span><span class="sxs-lookup"><span data-stu-id="45194-106">bool</span></span>](../../../csharp/language-reference/keywords/bool.md)|`System.Boolean`|  
|[<span data-ttu-id="45194-107">byte</span><span class="sxs-lookup"><span data-stu-id="45194-107">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|`System.Byte`|  
|[<span data-ttu-id="45194-108">sbyte</span><span class="sxs-lookup"><span data-stu-id="45194-108">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|`System.SByte`|  
|[<span data-ttu-id="45194-109">char</span><span class="sxs-lookup"><span data-stu-id="45194-109">char</span></span>](../../../csharp/language-reference/keywords/char.md)|`System.Char`|  
|[<span data-ttu-id="45194-110">decimal</span><span class="sxs-lookup"><span data-stu-id="45194-110">decimal</span></span>](../../../csharp/language-reference/keywords/decimal.md)|`System.Decimal`|  
|[<span data-ttu-id="45194-111">double</span><span class="sxs-lookup"><span data-stu-id="45194-111">double</span></span>](../../../csharp/language-reference/keywords/double.md)|`System.Double`|  
|[<span data-ttu-id="45194-112">float</span><span class="sxs-lookup"><span data-stu-id="45194-112">float</span></span>](../../../csharp/language-reference/keywords/float.md)|`System.Single`|  
|[<span data-ttu-id="45194-113">int</span><span class="sxs-lookup"><span data-stu-id="45194-113">int</span></span>](../../../csharp/language-reference/keywords/int.md)|`System.Int32`|  
|[<span data-ttu-id="45194-114">uint</span><span class="sxs-lookup"><span data-stu-id="45194-114">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|`System.UInt32`|  
|[<span data-ttu-id="45194-115">long</span><span class="sxs-lookup"><span data-stu-id="45194-115">long</span></span>](../../../csharp/language-reference/keywords/long.md)|`System.Int64`|  
|[<span data-ttu-id="45194-116">ulong</span><span class="sxs-lookup"><span data-stu-id="45194-116">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|`System.UInt64`|  
|[<span data-ttu-id="45194-117">object</span><span class="sxs-lookup"><span data-stu-id="45194-117">object</span></span>](../../../csharp/language-reference/keywords/object.md)|`System.Object`|  
|[<span data-ttu-id="45194-118">short</span><span class="sxs-lookup"><span data-stu-id="45194-118">short</span></span>](../../../csharp/language-reference/keywords/short.md)|`System.Int16`|  
|[<span data-ttu-id="45194-119">ushort</span><span class="sxs-lookup"><span data-stu-id="45194-119">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|`System.UInt16`|  
|[<span data-ttu-id="45194-120">string</span><span class="sxs-lookup"><span data-stu-id="45194-120">string</span></span>](../../../csharp/language-reference/keywords/string.md)|`System.String`|  
  
## <a name="remarks"></a><span data-ttu-id="45194-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45194-121">Remarks</span></span>  
 <span data-ttu-id="45194-122">Všechny typy v tabulce s výjimkou `object` a `string`, se označují jako jednoduché typy.</span><span class="sxs-lookup"><span data-stu-id="45194-122">All of the types in the table, except `object` and `string`, are referred to as simple types.</span></span>  
  
 <span data-ttu-id="45194-123">Jazyce C# typ klíčová slova a jejich aliasy jsou zaměnitelné.</span><span class="sxs-lookup"><span data-stu-id="45194-123">The C# type keywords and their aliases are interchangeable.</span></span> <span data-ttu-id="45194-124">Můžou například deklarovat proměnná typu integer pomocí některé z následujících deklarace:</span><span class="sxs-lookup"><span data-stu-id="45194-124">For example, you can declare an integer variable by using either of the following declarations:</span></span>  
  
```csharp  
int x = 123;  
System.Int32 x = 123;  
```  
  
 <span data-ttu-id="45194-125">Pokud chcete zobrazit skutečný typ pro jakýkoli typ C#, použijte metodu systému `GetType()`.</span><span class="sxs-lookup"><span data-stu-id="45194-125">To display the actual type for any C# type, use the system method `GetType()`.</span></span> <span data-ttu-id="45194-126">Například následující příkaz zobrazí alias systému, který představuje typ `myVariable`:</span><span class="sxs-lookup"><span data-stu-id="45194-126">For example, the following statement displays the system alias that represents the type of `myVariable`:</span></span>  
  
```csharp  
Console.WriteLine(myVariable.GetType());  
```  
  
 <span data-ttu-id="45194-127">Můžete také [typeof](../../../csharp/language-reference/keywords/typeof.md) operátor.</span><span class="sxs-lookup"><span data-stu-id="45194-127">You can also use the [typeof](../../../csharp/language-reference/keywords/typeof.md) operator.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45194-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="45194-128">See Also</span></span>  
 [<span data-ttu-id="45194-129">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="45194-129">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="45194-130">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="45194-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="45194-131">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="45194-131">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="45194-132">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="45194-132">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="45194-133">Tabulka výchozích hodnot</span><span class="sxs-lookup"><span data-stu-id="45194-133">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
 [<span data-ttu-id="45194-134">Tabulka formátování číselných výsledků</span><span class="sxs-lookup"><span data-stu-id="45194-134">Formatting Numeric Results Table</span></span>](../../../csharp/language-reference/keywords/formatting-numeric-results-table.md)  
 [<span data-ttu-id="45194-135">dynamic</span><span class="sxs-lookup"><span data-stu-id="45194-135">dynamic</span></span>](../../../csharp/language-reference/keywords/dynamic.md)  
 [<span data-ttu-id="45194-136">Referenční tabulky pro typy</span><span class="sxs-lookup"><span data-stu-id="45194-136">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
