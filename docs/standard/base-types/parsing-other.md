---
title: "Analýza jiných řetězců v .NET"
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
- cpp
helpviewer_keywords:
- Char data type, parsing strings
- enumerations [.NET Framework], parsing strings
- base types, parsing strings
- parsing strings, other strings
- Boolean data type, parsing strings
ms.assetid: d139bc00-3c4e-4d78-ac9a-5c951b258d28
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: edd48993f50ec8b91ba7941a682d7de9f22aa12e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="parsing-other-strings-in-net"></a><span data-ttu-id="01518-102">Analýza jiných řetězců v .NET</span><span class="sxs-lookup"><span data-stu-id="01518-102">Parsing Other Strings in .NET</span></span>
<span data-ttu-id="01518-103">Kromě číselný a <xref:System.DateTime> řetězce, můžete také analyzovat řetězců, které představují typy <xref:System.Char>, <xref:System.Boolean>, a <xref:System.Enum> do datových typů.</span><span class="sxs-lookup"><span data-stu-id="01518-103">In addition to numeric and <xref:System.DateTime> strings, you can also parse strings that represent the types <xref:System.Char>, <xref:System.Boolean>, and <xref:System.Enum> into data types.</span></span>  
  
## <a name="char"></a><span data-ttu-id="01518-104">Char</span><span class="sxs-lookup"><span data-stu-id="01518-104">Char</span></span>  
 <span data-ttu-id="01518-105">Přidružená metoda statické analýzy **Char** datový typ je vhodný pro převod řetězce, který obsahuje jediný znak na jeho hodnotu Unicode.</span><span class="sxs-lookup"><span data-stu-id="01518-105">The static parse method associated with the **Char** data type is useful for converting a string that contains a single character into its Unicode value.</span></span> <span data-ttu-id="01518-106">Následující příklad kódu analyzuje řetězec do znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="01518-106">The following code example parses a string into a Unicode character.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a><span data-ttu-id="01518-107">Boolean</span><span class="sxs-lookup"><span data-stu-id="01518-107">Boolean</span></span>  
 <span data-ttu-id="01518-108">**Boolean** obsahuje datový typ **analyzovat** metodu, kterou můžete použít se převést řetězec, který představuje logickou hodnotu na skutečné třídě **Boolean** typu.</span><span class="sxs-lookup"><span data-stu-id="01518-108">The **Boolean** data type contains a **Parse** method that you can use to convert a string that represents a Boolean value into an actual **Boolean** type.</span></span> <span data-ttu-id="01518-109">Tato metoda není velká a malá písmena a mohou úspěšně analyzovat řetězec obsahující "True" nebo "Nepravda".</span><span class="sxs-lookup"><span data-stu-id="01518-109">This method is not case-sensitive and can successfully parse a string containing "True" or "False."</span></span> <span data-ttu-id="01518-110">**Analyzovat** přidružená metoda **Boolean** typ může také analyzovat řetězce, které jsou ohraničeny prázdnými znaky.</span><span class="sxs-lookup"><span data-stu-id="01518-110">The **Parse** method associated with the **Boolean** type can also parse strings that are surrounded by white spaces.</span></span> <span data-ttu-id="01518-111">Pokud je předán jakýkoli jiný řetězec, <xref:System.FormatException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="01518-111">If any other string is passed, a <xref:System.FormatException> is thrown.</span></span>  
  
 <span data-ttu-id="01518-112">Následující příklad kódu používá **analyzovat** metoda převést řetězec na logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="01518-112">The following code example uses the **Parse** method to convert a string into a Boolean value.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a><span data-ttu-id="01518-113">Výčet</span><span class="sxs-lookup"><span data-stu-id="01518-113">Enumeration</span></span>  
 <span data-ttu-id="01518-114">Můžete použít statickou **analyzovat** metoda pro inicializaci typ výčtu na hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="01518-114">You can use the static **Parse** method to initialize an enumeration type to the value of a string.</span></span> <span data-ttu-id="01518-115">Tato metoda přijímá typ výčtu, který analyzujete, řetězec, který má analyzovat a volitelný logický příznak, která udává, zda je analýzy malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="01518-115">This method accepts the enumeration type you are parsing, the string to parse, and an optional Boolean flag indicating whether or not the parse is case-sensitive.</span></span> <span data-ttu-id="01518-116">Řetězec, který analyzujete může obsahovat několik hodnot oddělených čárkami, které mohou být před nebo za nímž následuje jeden nebo více prázdný mezery (také nazývané prázdné znaky).</span><span class="sxs-lookup"><span data-stu-id="01518-116">The string you are parsing can contain several values separated by commas, which can be preceded or followed by one or more empty spaces (also called white spaces).</span></span> <span data-ttu-id="01518-117">Pokud řetězec obsahuje více hodnot, hodnota vráceného objektu je hodnota všech zadaných hodnot v kombinaci s bitové operace OR.</span><span class="sxs-lookup"><span data-stu-id="01518-117">When the string contains multiple values, the value of the returned object is the value of all specified values combined with a bitwise OR operation.</span></span>  
  
 <span data-ttu-id="01518-118">Následující příklad používá **analyzovat** způsobů, jak převést řetězcovou reprezentaci na hodnotu výčtu.</span><span class="sxs-lookup"><span data-stu-id="01518-118">The following example uses the **Parse** method to convert a string representation into an enumeration value.</span></span> <span data-ttu-id="01518-119"><xref:System.DayOfWeek> Výčtu je inicializováno **čtvrtek** z řetězce.</span><span class="sxs-lookup"><span data-stu-id="01518-119">The <xref:System.DayOfWeek> enumeration is initialized to **Thursday** from a string.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="01518-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="01518-120">See Also</span></span>  
 [<span data-ttu-id="01518-121">Analýza řetězců</span><span class="sxs-lookup"><span data-stu-id="01518-121">Parsing Strings</span></span>](../../../docs/standard/base-types/parsing-strings.md)  
 [<span data-ttu-id="01518-122">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="01518-122">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 [<span data-ttu-id="01518-123">Převod typů v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="01518-123">Type Conversion in the .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)
