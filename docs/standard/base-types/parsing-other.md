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
ms.openlocfilehash: a3503e0e499c6010fcc3d8669fa5c1eaf2dbf570
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84277541"
---
# <a name="parsing-other-strings-in-net"></a><span data-ttu-id="d2042-102">Analýza jiných řetězců v .NET</span><span class="sxs-lookup"><span data-stu-id="d2042-102">Parsing Other Strings in .NET</span></span>
<span data-ttu-id="d2042-103">Kromě čísel a <xref:System.DateTime> řetězců můžete také analyzovat řetězce, které reprezentují typy <xref:System.Char> , <xref:System.Boolean> a <xref:System.Enum> do datových typů.</span><span class="sxs-lookup"><span data-stu-id="d2042-103">In addition to numeric and <xref:System.DateTime> strings, you can also parse strings that represent the types <xref:System.Char>, <xref:System.Boolean>, and <xref:System.Enum> into data types.</span></span>  
  
## <a name="char"></a><span data-ttu-id="d2042-104">Char</span><span class="sxs-lookup"><span data-stu-id="d2042-104">Char</span></span>  
 <span data-ttu-id="d2042-105">Statická metoda Parse spojená s datovým typem **char** je užitečná pro převod řetězce, který obsahuje jeden znak na jeho hodnotu Unicode.</span><span class="sxs-lookup"><span data-stu-id="d2042-105">The static parse method associated with the **Char** data type is useful for converting a string that contains a single character into its Unicode value.</span></span> <span data-ttu-id="d2042-106">Následující příklad kódu analyzuje řetězec na znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="d2042-106">The following code example parses a string into a Unicode character.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#2)]
 [!code-csharp[Conceptual.String.Parse#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#2)]
 [!code-vb[Conceptual.String.Parse#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#2)]  
  
## <a name="boolean"></a><span data-ttu-id="d2042-107">Logická hodnota</span><span class="sxs-lookup"><span data-stu-id="d2042-107">Boolean</span></span>  
 <span data-ttu-id="d2042-108">Datový typ **Boolean** obsahuje metodu **Parse** , kterou můžete použít k převodu řetězce reprezentujícího logickou hodnotu na skutečný typ **Boolean** .</span><span class="sxs-lookup"><span data-stu-id="d2042-108">The **Boolean** data type contains a **Parse** method that you can use to convert a string that represents a Boolean value into an actual **Boolean** type.</span></span> <span data-ttu-id="d2042-109">Tato metoda nerozlišuje velká a malá písmena a může úspěšně analyzovat řetězec obsahující "true" nebo "false".</span><span class="sxs-lookup"><span data-stu-id="d2042-109">This method is not case-sensitive and can successfully parse a string containing "True" or "False."</span></span> <span data-ttu-id="d2042-110">Metoda **Parse** přidružená k typu **Boolean** může také analyzovat řetězce, které jsou obklopeny prázdnými znaky.</span><span class="sxs-lookup"><span data-stu-id="d2042-110">The **Parse** method associated with the **Boolean** type can also parse strings that are surrounded by white spaces.</span></span> <span data-ttu-id="d2042-111">Pokud je předán jakýkoli jiný řetězec, <xref:System.FormatException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="d2042-111">If any other string is passed, a <xref:System.FormatException> is thrown.</span></span>  
  
 <span data-ttu-id="d2042-112">Následující příklad kódu používá metodu **Parse** pro převod řetězce na logickou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d2042-112">The following code example uses the **Parse** method to convert a string into a Boolean value.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#3)]
 [!code-csharp[Conceptual.String.Parse#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#3)]
 [!code-vb[Conceptual.String.Parse#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#3)]  
  
## <a name="enumeration"></a><span data-ttu-id="d2042-113">Výčet</span><span class="sxs-lookup"><span data-stu-id="d2042-113">Enumeration</span></span>  
 <span data-ttu-id="d2042-114">Metodu statické **analýzy** lze použít k inicializaci typu výčtu na hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="d2042-114">You can use the static **Parse** method to initialize an enumeration type to the value of a string.</span></span> <span data-ttu-id="d2042-115">Tato metoda přijímá typ výčtu, který analyzujete, řetězec k analýze a volitelný logický příznak označující, zda se při analýze rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="d2042-115">This method accepts the enumeration type you are parsing, the string to parse, and an optional Boolean flag indicating whether or not the parse is case-sensitive.</span></span> <span data-ttu-id="d2042-116">Řetězec, který analyzujete, může obsahovat několik hodnot oddělených čárkami, které mohou být uvozeny nebo následovány jedním nebo více prázdnými mezerami (označují se také jako prázdné znaky).</span><span class="sxs-lookup"><span data-stu-id="d2042-116">The string you are parsing can contain several values separated by commas, which can be preceded or followed by one or more empty spaces (also called white spaces).</span></span> <span data-ttu-id="d2042-117">Pokud řetězec obsahuje více hodnot, hodnota vráceného objektu je hodnota všech zadaných hodnot v kombinaci s bitovou operací nebo.</span><span class="sxs-lookup"><span data-stu-id="d2042-117">When the string contains multiple values, the value of the returned object is the value of all specified values combined with a bitwise OR operation.</span></span>  
  
 <span data-ttu-id="d2042-118">Následující příklad používá metodu **Parse** pro převod řetězcové reprezentace na hodnotu výčtu.</span><span class="sxs-lookup"><span data-stu-id="d2042-118">The following example uses the **Parse** method to convert a string representation into an enumeration value.</span></span> <span data-ttu-id="d2042-119"><xref:System.DayOfWeek>Výčet je inicializován pro **čtvrtek** z řetězce.</span><span class="sxs-lookup"><span data-stu-id="d2042-119">The <xref:System.DayOfWeek> enumeration is initialized to **Thursday** from a string.</span></span>  
  
 [!code-cpp[Conceptual.String.Parse#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.parse/cpp/parse.cpp#4)]
 [!code-csharp[Conceptual.String.Parse#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.parse/cs/parse.cs#4)]
 [!code-vb[Conceptual.String.Parse#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.parse/vb/parse.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="d2042-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2042-120">See also</span></span>

- [<span data-ttu-id="d2042-121">Analýza řetězců</span><span class="sxs-lookup"><span data-stu-id="d2042-121">Parsing Strings</span></span>](parsing-strings.md)
- [<span data-ttu-id="d2042-122">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="d2042-122">Formatting Types</span></span>](formatting-types.md)
- [<span data-ttu-id="d2042-123">Převod typu v .NET</span><span class="sxs-lookup"><span data-stu-id="d2042-123">Type Conversion in the .NET</span></span>](type-conversion.md)
