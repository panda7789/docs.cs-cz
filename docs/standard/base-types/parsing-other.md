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
ms.openlocfilehash: 08e891501bbefcf8b32eff10dd7294af9d81adac
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127576"
---
# <a name="parsing-other-strings-in-net"></a><span data-ttu-id="6abd8-102">Analýza jiných řetězců v .NET</span><span class="sxs-lookup"><span data-stu-id="6abd8-102">Parsing Other Strings in .NET</span></span>
<span data-ttu-id="6abd8-103">Kromě číselných a <xref:System.DateTime> řetězců můžete také analyzovat řetězce, které reprezentují typy <xref:System.Char>, <xref:System.Boolean>a <xref:System.Enum> do datových typů.</span><span class="sxs-lookup"><span data-stu-id="6abd8-103">In addition to numeric and <xref:System.DateTime> strings, you can also parse strings that represent the types <xref:System.Char>, <xref:System.Boolean>, and <xref:System.Enum> into data types.</span></span>  
  
## <a name="char"></a><span data-ttu-id="6abd8-104">Char</span><span class="sxs-lookup"><span data-stu-id="6abd8-104">Char</span></span>  
 <span data-ttu-id="6abd8-105">Statická metoda Parse spojená s datovým typem **char** je užitečná pro převod řetězce, který obsahuje jeden znak na jeho hodnotu Unicode.</span><span class="sxs-lookup"><span data-stu-id="6abd8-105">The static parse method associated with the **Char** data type is useful for converting a string that contains a single character into its Unicode value.</span></span> <span data-ttu-id="6abd8-106">Následující příklad kódu analyzuje řetězec na znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="6abd8-106">The following code example parses a string into a Unicode character.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a><span data-ttu-id="6abd8-107">Boolean</span><span class="sxs-lookup"><span data-stu-id="6abd8-107">Boolean</span></span>  
 <span data-ttu-id="6abd8-108">Datový typ **Boolean** obsahuje metodu **Parse** , kterou můžete použít k převodu řetězce reprezentujícího logickou hodnotu na skutečný typ **Boolean** .</span><span class="sxs-lookup"><span data-stu-id="6abd8-108">The **Boolean** data type contains a **Parse** method that you can use to convert a string that represents a Boolean value into an actual **Boolean** type.</span></span> <span data-ttu-id="6abd8-109">Tato metoda nerozlišuje velká a malá písmena a může úspěšně analyzovat řetězec obsahující "true" nebo "false".</span><span class="sxs-lookup"><span data-stu-id="6abd8-109">This method is not case-sensitive and can successfully parse a string containing "True" or "False."</span></span> <span data-ttu-id="6abd8-110">Metoda **Parse** přidružená k typu **Boolean** může také analyzovat řetězce, které jsou obklopeny prázdnými znaky.</span><span class="sxs-lookup"><span data-stu-id="6abd8-110">The **Parse** method associated with the **Boolean** type can also parse strings that are surrounded by white spaces.</span></span> <span data-ttu-id="6abd8-111">Pokud je předán jakýkoli jiný řetězec, je vyvolána <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="6abd8-111">If any other string is passed, a <xref:System.FormatException> is thrown.</span></span>  
  
 <span data-ttu-id="6abd8-112">Následující příklad kódu používá metodu **Parse** pro převod řetězce na logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6abd8-112">The following code example uses the **Parse** method to convert a string into a Boolean value.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a><span data-ttu-id="6abd8-113">Výčet</span><span class="sxs-lookup"><span data-stu-id="6abd8-113">Enumeration</span></span>  
 <span data-ttu-id="6abd8-114">Metodu statické **analýzy** lze použít k inicializaci typu výčtu na hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="6abd8-114">You can use the static **Parse** method to initialize an enumeration type to the value of a string.</span></span> <span data-ttu-id="6abd8-115">Tato metoda přijímá typ výčtu, který analyzujete, řetězec k analýze a volitelný logický příznak označující, zda se při analýze rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="6abd8-115">This method accepts the enumeration type you are parsing, the string to parse, and an optional Boolean flag indicating whether or not the parse is case-sensitive.</span></span> <span data-ttu-id="6abd8-116">Řetězec, který analyzujete, může obsahovat několik hodnot oddělených čárkami, které mohou být uvozeny nebo následovány jedním nebo více prázdnými mezerami (označují se také jako prázdné znaky).</span><span class="sxs-lookup"><span data-stu-id="6abd8-116">The string you are parsing can contain several values separated by commas, which can be preceded or followed by one or more empty spaces (also called white spaces).</span></span> <span data-ttu-id="6abd8-117">Pokud řetězec obsahuje více hodnot, hodnota vráceného objektu je hodnota všech zadaných hodnot v kombinaci s bitovou operací nebo.</span><span class="sxs-lookup"><span data-stu-id="6abd8-117">When the string contains multiple values, the value of the returned object is the value of all specified values combined with a bitwise OR operation.</span></span>  
  
 <span data-ttu-id="6abd8-118">Následující příklad používá metodu **Parse** pro převod řetězcové reprezentace na hodnotu výčtu.</span><span class="sxs-lookup"><span data-stu-id="6abd8-118">The following example uses the **Parse** method to convert a string representation into an enumeration value.</span></span> <span data-ttu-id="6abd8-119">Výčet <xref:System.DayOfWeek> je inicializován pro **čtvrtek** z řetězce.</span><span class="sxs-lookup"><span data-stu-id="6abd8-119">The <xref:System.DayOfWeek> enumeration is initialized to **Thursday** from a string.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="6abd8-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6abd8-120">See also</span></span>

- [<span data-ttu-id="6abd8-121">Analýza řetězců</span><span class="sxs-lookup"><span data-stu-id="6abd8-121">Parsing Strings</span></span>](../../../docs/standard/base-types/parsing-strings.md)
- [<span data-ttu-id="6abd8-122">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="6abd8-122">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)
- [<span data-ttu-id="6abd8-123">Převod typu v .NET</span><span class="sxs-lookup"><span data-stu-id="6abd8-123">Type Conversion in the .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)
