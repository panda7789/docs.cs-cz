---
title: Analýza jiných řetězců v .NET
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Char data type, parsing strings
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- parsing strings, other strings
- Boolean data type, parsing strings
ms.assetid: d139bc00-3c4e-4d78-ac9a-5c951b258d28
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cf8a7b090b7a54328101478aed7edbbc5efd79ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765983"
---
# <a name="parsing-other-strings-in-net"></a><span data-ttu-id="3e5ef-102">Analýza jiných řetězců v .NET</span><span class="sxs-lookup"><span data-stu-id="3e5ef-102">Parsing Other Strings in .NET</span></span>
<span data-ttu-id="3e5ef-103">Kromě číselné a <xref:System.DateTime> řetězce, můžete také analyzovat řetězců, které představují typy <xref:System.Char>, <xref:System.Boolean>, a <xref:System.Enum> do datových typů.</span><span class="sxs-lookup"><span data-stu-id="3e5ef-103">In addition to numeric and <xref:System.DateTime> strings, you can also parse strings that represent the types <xref:System.Char>, <xref:System.Boolean>, and <xref:System.Enum> into data types.</span></span>  
  
## <a name="char"></a><span data-ttu-id="3e5ef-104">Char</span><span class="sxs-lookup"><span data-stu-id="3e5ef-104">Char</span></span>  
 <span data-ttu-id="3e5ef-105">Statické analýzy metodu spojenou s **Char** datový typ je vhodný pro převod řetězce, který obsahuje jeden znak na jeho hodnotu Unicode.</span><span class="sxs-lookup"><span data-stu-id="3e5ef-105">The static parse method associated with the **Char** data type is useful for converting a string that contains a single character into its Unicode value.</span></span> <span data-ttu-id="3e5ef-106">Následující příklad analyzuje řetězec do znaku Unicode.</span><span class="sxs-lookup"><span data-stu-id="3e5ef-106">The following code example parses a string into a Unicode character.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a><span data-ttu-id="3e5ef-107">Boolean</span><span class="sxs-lookup"><span data-stu-id="3e5ef-107">Boolean</span></span>  
 <span data-ttu-id="3e5ef-108">**Logická** obsahuje datový typ **analyzovat** metodu, která můžete použít k převodu řetězec, který představuje logickou hodnotu do skutečný **logická** typu.</span><span class="sxs-lookup"><span data-stu-id="3e5ef-108">The **Boolean** data type contains a **Parse** method that you can use to convert a string that represents a Boolean value into an actual **Boolean** type.</span></span> <span data-ttu-id="3e5ef-109">Tato metoda není velká a malá písmena a lze úspěšnou analýzu řetězce obsahující "True" nebo "False".</span><span class="sxs-lookup"><span data-stu-id="3e5ef-109">This method is not case-sensitive and can successfully parse a string containing "True" or "False."</span></span> <span data-ttu-id="3e5ef-110">**Analyzovat** metodu spojenou s **logická** typu můžete také analyzovat řetězce, které jsou uzavřeny v prázdné znaky.</span><span class="sxs-lookup"><span data-stu-id="3e5ef-110">The **Parse** method associated with the **Boolean** type can also parse strings that are surrounded by white spaces.</span></span> <span data-ttu-id="3e5ef-111">Pokud je předán jiný řetězec, <xref:System.FormatException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="3e5ef-111">If any other string is passed, a <xref:System.FormatException> is thrown.</span></span>  
  
 <span data-ttu-id="3e5ef-112">Následující příklad kódu používá **analyzovat** způsobů, jak převést řetězec na hodnotu typu Boolean.</span><span class="sxs-lookup"><span data-stu-id="3e5ef-112">The following code example uses the **Parse** method to convert a string into a Boolean value.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a><span data-ttu-id="3e5ef-113">Výčet</span><span class="sxs-lookup"><span data-stu-id="3e5ef-113">Enumeration</span></span>  
 <span data-ttu-id="3e5ef-114">Můžete použít statické **analyzovat** metody k inicializaci typu výčtu na hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="3e5ef-114">You can use the static **Parse** method to initialize an enumeration type to the value of a string.</span></span> <span data-ttu-id="3e5ef-115">Tato metoda přijímá typ výčtu, která analyzujete, řetězec určený k analýze a volitelný příznak logické hodnoty označující, jestli je parsování malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="3e5ef-115">This method accepts the enumeration type you are parsing, the string to parse, and an optional Boolean flag indicating whether or not the parse is case-sensitive.</span></span> <span data-ttu-id="3e5ef-116">Řetězec, který se analýza může obsahovat několik hodnot oddělených čárkami, které mohou být předcházen nebo následován mezerami nejmíň jeden prázdný (také nazývané prázdné znaky).</span><span class="sxs-lookup"><span data-stu-id="3e5ef-116">The string you are parsing can contain several values separated by commas, which can be preceded or followed by one or more empty spaces (also called white spaces).</span></span> <span data-ttu-id="3e5ef-117">Pokud řetězec obsahuje více hodnot, hodnota vráceného objektu je hodnota všechny zadané hodnoty v kombinaci s bitová operace OR.</span><span class="sxs-lookup"><span data-stu-id="3e5ef-117">When the string contains multiple values, the value of the returned object is the value of all specified values combined with a bitwise OR operation.</span></span>  
  
 <span data-ttu-id="3e5ef-118">V následujícím příkladu **analyzovat** způsobů, jak převést řetězcové vyjádření na hodnotu výčtu.</span><span class="sxs-lookup"><span data-stu-id="3e5ef-118">The following example uses the **Parse** method to convert a string representation into an enumeration value.</span></span> <span data-ttu-id="3e5ef-119"><xref:System.DayOfWeek> Výčtu je inicializován na **čtvrtek** z řetězce.</span><span class="sxs-lookup"><span data-stu-id="3e5ef-119">The <xref:System.DayOfWeek> enumeration is initialized to **Thursday** from a string.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="3e5ef-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e5ef-120">See also</span></span>

- [<span data-ttu-id="3e5ef-121">Analýza řetězců</span><span class="sxs-lookup"><span data-stu-id="3e5ef-121">Parsing Strings</span></span>](../../../docs/standard/base-types/parsing-strings.md)
- [<span data-ttu-id="3e5ef-122">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="3e5ef-122">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)
- [<span data-ttu-id="3e5ef-123">Převod typů v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="3e5ef-123">Type Conversion in the .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)
