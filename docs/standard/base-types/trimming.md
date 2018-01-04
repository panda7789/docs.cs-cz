---
title: "Ořezávání a odstraňování znaků z řetězců v .NET"
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
- strings [.NET Framework], removing characters
- Remove method
- TrimEnd method
- Trim method
- trimming characters
- TrimStart method
- removing characters
ms.assetid: ab248dab-70d4-4413-81c6-542d153fd195
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: dac047c7efefcacb959401aedcb96080810f2278
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a><span data-ttu-id="f8c49-102">Ořezávání a odstraňování znaků z řetězců v .NET</span><span class="sxs-lookup"><span data-stu-id="f8c49-102">Trimming and Removing Characters from Strings in .NET</span></span>
<span data-ttu-id="f8c49-103">Pokud analyzujete věty do jednotlivých slov, budete muset zvýšit slova, která mají mezery (také nazývané mezer) na obou koncích aplikace word.</span><span class="sxs-lookup"><span data-stu-id="f8c49-103">If you are parsing a sentence into individual words, you might end up with words that have blank spaces (also called white spaces) on either end of the word.</span></span> <span data-ttu-id="f8c49-104">V takovém případě můžete použít jednu z metod trim v **System.String** třída odebrat libovolný počet mezery ani jiné znaky ze zadané pozici v řetězci.</span><span class="sxs-lookup"><span data-stu-id="f8c49-104">In this situation, you can use one of the trim methods in the **System.String** class to remove any number of spaces or other characters from a specified position in the string.</span></span> <span data-ttu-id="f8c49-105">Následující tabulka popisuje dostupné metody uvolnění dočasné paměti.</span><span class="sxs-lookup"><span data-stu-id="f8c49-105">The following table describes the available trim methods.</span></span>  
  
|<span data-ttu-id="f8c49-106">Název metody</span><span class="sxs-lookup"><span data-stu-id="f8c49-106">Method name</span></span>|<span data-ttu-id="f8c49-107">Použití</span><span class="sxs-lookup"><span data-stu-id="f8c49-107">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|<span data-ttu-id="f8c49-108">Odebere mezery nebo znaky zadané v poli znaků od začátku a konce řetězce.</span><span class="sxs-lookup"><span data-stu-id="f8c49-108">Removes white spaces or characters specified in an array of characters from the beginning and end of a string.</span></span>|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|<span data-ttu-id="f8c49-109">Odebere zadané v poli znaků od konce řetězce znaků.</span><span class="sxs-lookup"><span data-stu-id="f8c49-109">Removes characters specified in an array of characters from the end of a string.</span></span>|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|<span data-ttu-id="f8c49-110">Odebere zadané v poli znaků od začátku řetězce znaků.</span><span class="sxs-lookup"><span data-stu-id="f8c49-110">Removes characters specified in an array of characters from the beginning of a string.</span></span>|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="f8c49-111">Odebere zadaný počet znaků z pozice zadaného indexu v řetězci.</span><span class="sxs-lookup"><span data-stu-id="f8c49-111">Removes a specified number of characters from a specified index position in a string.</span></span>|  
  
## <a name="trim"></a><span data-ttu-id="f8c49-112">Uvolnění dočasné paměti</span><span class="sxs-lookup"><span data-stu-id="f8c49-112">Trim</span></span>  
 <span data-ttu-id="f8c49-113">Prázdné znaky z obou konců řetězce můžete snadno odebrat pomocí <xref:System.String.Trim%2A?displayProperty=nameWithType> metoda, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f8c49-113">You can easily remove white spaces from both ends of a string by using the <xref:System.String.Trim%2A?displayProperty=nameWithType> method, as shown in the following example.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 <span data-ttu-id="f8c49-114">Můžete také odebrat znaky, které zadáte v poli znaků od začátku a konce řetězce.</span><span class="sxs-lookup"><span data-stu-id="f8c49-114">You can also remove characters that you specify in a character array from the beginning and end of a string.</span></span> <span data-ttu-id="f8c49-115">Následující příklad odebere prázdné znaky, tečky a hvězdičky.</span><span class="sxs-lookup"><span data-stu-id="f8c49-115">The following example removes white-space characters, periods, and asterisks.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a><span data-ttu-id="f8c49-116">TrimEnd</span><span class="sxs-lookup"><span data-stu-id="f8c49-116">TrimEnd</span></span>  
 <span data-ttu-id="f8c49-117">**String.TrimEnd** metoda odebere znaků z konce řetězce a vytvoří nový objekt řetězce.</span><span class="sxs-lookup"><span data-stu-id="f8c49-117">The **String.TrimEnd** method removes characters from the end of a string, creating a new string object.</span></span> <span data-ttu-id="f8c49-118">Pole znaků je předán tuto metodu za účelem určení znaků, které mají být odebrány.</span><span class="sxs-lookup"><span data-stu-id="f8c49-118">An array of characters is passed to this method to specify the characters to be removed.</span></span> <span data-ttu-id="f8c49-119">Pořadí prvků v poli znak nemá vliv na operace uvolnění dočasné paměti.</span><span class="sxs-lookup"><span data-stu-id="f8c49-119">The order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="f8c49-120">Ořezávání zastaví, když je nalezen znak není zadaný v poli.</span><span class="sxs-lookup"><span data-stu-id="f8c49-120">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="f8c49-121">Následující příklad odebere poslední písmena řetězec pomocí **TrimEnd** metoda.</span><span class="sxs-lookup"><span data-stu-id="f8c49-121">The following example removes the last letters of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="f8c49-122">V tomto příkladu pozici `'r'` znak a `'W'` znak se vrátit k objasnění, že pořadí znaků v poli nezáleží.</span><span class="sxs-lookup"><span data-stu-id="f8c49-122">In this example, the position of the `'r'` character and the `'W'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span> <span data-ttu-id="f8c49-123">Všimněte si, že tento kód odstraní poslední slovo `MyString` plus součástí první.</span><span class="sxs-lookup"><span data-stu-id="f8c49-123">Notice that this code removes the last word of `MyString` plus part of the first.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 <span data-ttu-id="f8c49-124">Tento kód zobrazí `He` ke konzole.</span><span class="sxs-lookup"><span data-stu-id="f8c49-124">This code displays `He` to the console.</span></span>  
  
 <span data-ttu-id="f8c49-125">Následující příklad odebere poslední slovo řetězec pomocí **TrimEnd** metoda.</span><span class="sxs-lookup"><span data-stu-id="f8c49-125">The following example removes the last word of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="f8c49-126">V tomto kódu čárka následuje slovo `Hello` a protože čárkou není zadané v poli znaků, oříznout, ořezávání končí čárkou.</span><span class="sxs-lookup"><span data-stu-id="f8c49-126">In this code, a comma follows the word `Hello` and, because the comma is not specified in the array of characters to trim, the trim ends at the comma.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 <span data-ttu-id="f8c49-127">Tento kód zobrazí `Hello,` ke konzole.</span><span class="sxs-lookup"><span data-stu-id="f8c49-127">This code displays `Hello,` to the console.</span></span>  
  
## <a name="trimstart"></a><span data-ttu-id="f8c49-128">TrimStart</span><span class="sxs-lookup"><span data-stu-id="f8c49-128">TrimStart</span></span>  
 <span data-ttu-id="f8c49-129">**String.TrimStart** metoda je podobná **String.TrimEnd** metoda s výjimkou, že vytvoří nový řetězec odebráním znaků od začátku existujícího objektu řetězce.</span><span class="sxs-lookup"><span data-stu-id="f8c49-129">The **String.TrimStart** method is similar to the **String.TrimEnd** method except that it creates a new string by removing characters from the beginning of an existing string object.</span></span> <span data-ttu-id="f8c49-130">Předaný pole znaků **TrimStart** metodu za účelem určení znaků, které mají být odebrány.</span><span class="sxs-lookup"><span data-stu-id="f8c49-130">An array of characters is passed to the **TrimStart** method to specify the characters to be removed.</span></span> <span data-ttu-id="f8c49-131">Stejně jako u **TrimEnd** metoda pořadí prvků v poli znak nemá vliv na operace uvolnění dočasné paměti.</span><span class="sxs-lookup"><span data-stu-id="f8c49-131">As with the **TrimEnd** method, the order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="f8c49-132">Ořezávání zastaví, když je nalezen znak není zadaný v poli.</span><span class="sxs-lookup"><span data-stu-id="f8c49-132">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="f8c49-133">Následující příklad odebere první slovo řetězce.</span><span class="sxs-lookup"><span data-stu-id="f8c49-133">The following example removes the first word of a string.</span></span> <span data-ttu-id="f8c49-134">V tomto příkladu pozici `'l'` znak a `'H'` znak se vrátit k objasnění, že pořadí znaků v poli nezáleží.</span><span class="sxs-lookup"><span data-stu-id="f8c49-134">In this example, the position of the `'l'` character and the `'H'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 <span data-ttu-id="f8c49-135">Tento kód zobrazí `World!` ke konzole.</span><span class="sxs-lookup"><span data-stu-id="f8c49-135">This code displays `World!` to the console.</span></span>  
  
## <a name="remove"></a><span data-ttu-id="f8c49-136">Odebrat</span><span class="sxs-lookup"><span data-stu-id="f8c49-136">Remove</span></span>  
 <span data-ttu-id="f8c49-137"><xref:System.String.Remove%2A?displayProperty=nameWithType> Metoda odebere zadaný počet znaků, které začínají na zadané pozici v existujícím řetězci.</span><span class="sxs-lookup"><span data-stu-id="f8c49-137">The <xref:System.String.Remove%2A?displayProperty=nameWithType> method removes a specified number of characters that begin at a specified position in an existing string.</span></span> <span data-ttu-id="f8c49-138">Tato metoda předpokládá index počítaný od nuly.</span><span class="sxs-lookup"><span data-stu-id="f8c49-138">This method assumes a zero-based index.</span></span>  
  
 <span data-ttu-id="f8c49-139">Následující příklad odebere deset znaků z řetězce počínaje pozicí pět index počítaný od nuly řetězce.</span><span class="sxs-lookup"><span data-stu-id="f8c49-139">The following example removes ten characters from a string beginning at position five of a zero-based index of the string.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
 <span data-ttu-id="f8c49-140">Rovněž můžete odebrat zadaný znak nebo dílčí řetězec z řetězce voláním <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> metoda a zadání prázdný řetězec (<xref:System.String.Empty?displayProperty=nameWithType>) jako náhrada.</span><span class="sxs-lookup"><span data-stu-id="f8c49-140">You can also remove a specified character or substring from a string by calling the <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> method and specifying an empty string (<xref:System.String.Empty?displayProperty=nameWithType>) as the replacement.</span></span> <span data-ttu-id="f8c49-141">Následující příklad odebere všechny čárkami v řetězci.</span><span class="sxs-lookup"><span data-stu-id="f8c49-141">The following example removes all commas from a string.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="f8c49-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="f8c49-142">See Also</span></span>  
 [<span data-ttu-id="f8c49-143">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="f8c49-143">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
