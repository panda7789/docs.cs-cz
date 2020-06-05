---
title: Ořezávání a odstraňování znaků z řetězců v .NET
description: Naučte se oříznout prázdné mezery na začátku nebo konci řetězce nebo odebrat libovolný počet mezer nebo znaků ze zadané pozice v řetězci v rozhraní .NET.
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: 630fe6b51d151d1f1384f2e3cde62750c303d883
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446890"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a><span data-ttu-id="8331f-103">Ořezávání a odstraňování znaků z řetězců v .NET</span><span class="sxs-lookup"><span data-stu-id="8331f-103">Trimming and Removing Characters from Strings in .NET</span></span>
<span data-ttu-id="8331f-104">Pokud analyzujete větu na jednotlivá slova, může se stát, že se na konci slova dokončí slova, která obsahují prázdné mezery (označované také jako prázdné znaky).</span><span class="sxs-lookup"><span data-stu-id="8331f-104">If you are parsing a sentence into individual words, you might end up with words that have blank spaces (also called white spaces) on either end of the word.</span></span> <span data-ttu-id="8331f-105">V této situaci můžete použít jednu z metod Trim třídy **System. String** k odebrání libovolného počtu mezer nebo jiných znaků ze zadané pozice v řetězci.</span><span class="sxs-lookup"><span data-stu-id="8331f-105">In this situation, you can use one of the trim methods in the **System.String** class to remove any number of spaces or other characters from a specified position in the string.</span></span> <span data-ttu-id="8331f-106">Následující tabulka popisuje dostupné metody Trim.</span><span class="sxs-lookup"><span data-stu-id="8331f-106">The following table describes the available trim methods.</span></span>  
  
|<span data-ttu-id="8331f-107">Název metody</span><span class="sxs-lookup"><span data-stu-id="8331f-107">Method name</span></span>|<span data-ttu-id="8331f-108">Použití</span><span class="sxs-lookup"><span data-stu-id="8331f-108">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|<span data-ttu-id="8331f-109">Odstraní prázdné znaky nebo znaky zadané v poli znaků od začátku a konce řetězce.</span><span class="sxs-lookup"><span data-stu-id="8331f-109">Removes white spaces or characters specified in an array of characters from the beginning and end of a string.</span></span>|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|<span data-ttu-id="8331f-110">Odebere znaky zadané v poli znaků z konce řetězce.</span><span class="sxs-lookup"><span data-stu-id="8331f-110">Removes characters specified in an array of characters from the end of a string.</span></span>|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|<span data-ttu-id="8331f-111">Odebere znaky zadané v poli znaků od začátku řetězce.</span><span class="sxs-lookup"><span data-stu-id="8331f-111">Removes characters specified in an array of characters from the beginning of a string.</span></span>|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="8331f-112">Odebere zadaný počet znaků ze zadané pozice indexu v řetězci.</span><span class="sxs-lookup"><span data-stu-id="8331f-112">Removes a specified number of characters from a specified index position in a string.</span></span>|  
  
## <a name="trim"></a><span data-ttu-id="8331f-113">Trim</span><span class="sxs-lookup"><span data-stu-id="8331f-113">Trim</span></span>

 <span data-ttu-id="8331f-114">Pomocí metody lze snadno odebrat prázdné znaky z obou konců řetězce <xref:System.String.Trim%2A?displayProperty=nameWithType> , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8331f-114">You can easily remove white spaces from both ends of a string by using the <xref:System.String.Trim%2A?displayProperty=nameWithType> method, as shown in the following example.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 <span data-ttu-id="8331f-115">Můžete také odebrat znaky, které zadáte v poli znaků od začátku a konce řetězce.</span><span class="sxs-lookup"><span data-stu-id="8331f-115">You can also remove characters that you specify in a character array from the beginning and end of a string.</span></span> <span data-ttu-id="8331f-116">Následující příklad odebere prázdné znaky, tečky a hvězdičky.</span><span class="sxs-lookup"><span data-stu-id="8331f-116">The following example removes white-space characters, periods, and asterisks.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a><span data-ttu-id="8331f-117">TrimEnd</span><span class="sxs-lookup"><span data-stu-id="8331f-117">TrimEnd</span></span>

 <span data-ttu-id="8331f-118">Metoda **String. TrimEnd** odstraní znaky z konce řetězce a vytvoří nový objekt řetězce.</span><span class="sxs-lookup"><span data-stu-id="8331f-118">The **String.TrimEnd** method removes characters from the end of a string, creating a new string object.</span></span> <span data-ttu-id="8331f-119">Pole znaků je předáno této metodě pro určení znaků, které mají být odebrány.</span><span class="sxs-lookup"><span data-stu-id="8331f-119">An array of characters is passed to this method to specify the characters to be removed.</span></span> <span data-ttu-id="8331f-120">Pořadí prvků v poli znaků nemá vliv na operaci ořezávání.</span><span class="sxs-lookup"><span data-stu-id="8331f-120">The order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="8331f-121">Ořezávání se zastaví, když se najde znak, který není zadaný v poli.</span><span class="sxs-lookup"><span data-stu-id="8331f-121">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="8331f-122">Následující příklad odebere poslední písmena řetězce pomocí metody **trimEnd** .</span><span class="sxs-lookup"><span data-stu-id="8331f-122">The following example removes the last letters of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="8331f-123">V tomto příkladu je pozice `'r'` znaku a `'W'` znaku obrácena k ilustraci, že pořadí znaků v poli nezáleží.</span><span class="sxs-lookup"><span data-stu-id="8331f-123">In this example, the position of the `'r'` character and the `'W'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span> <span data-ttu-id="8331f-124">Všimněte si, že tento kód odstraní poslední slovo `MyString` a část první.</span><span class="sxs-lookup"><span data-stu-id="8331f-124">Notice that this code removes the last word of `MyString` plus part of the first.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 <span data-ttu-id="8331f-125">Tento kód `He` se zobrazí v konzole nástroje.</span><span class="sxs-lookup"><span data-stu-id="8331f-125">This code displays `He` to the console.</span></span>  
  
 <span data-ttu-id="8331f-126">Následující příklad odebere poslední slovo řetězce pomocí metody **trimEnd** .</span><span class="sxs-lookup"><span data-stu-id="8331f-126">The following example removes the last word of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="8331f-127">V tomto kódu čárka následuje za slovem `Hello` a, protože čárka není určena v poli znaků, které mají být oříznuty, ořezávání končí čárkou.</span><span class="sxs-lookup"><span data-stu-id="8331f-127">In this code, a comma follows the word `Hello` and, because the comma is not specified in the array of characters to trim, the trim ends at the comma.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 <span data-ttu-id="8331f-128">Tento kód `Hello,` se zobrazí v konzole nástroje.</span><span class="sxs-lookup"><span data-stu-id="8331f-128">This code displays `Hello,` to the console.</span></span>  
  
## <a name="trimstart"></a><span data-ttu-id="8331f-129">TrimStart</span><span class="sxs-lookup"><span data-stu-id="8331f-129">TrimStart</span></span>

 <span data-ttu-id="8331f-130">Metoda **String. TrimStart** je podobná metodě **String. TrimEnd** s tím rozdílem, že vytvoří nový řetězec odebráním znaků ze začátku existujícího objektu řetězce.</span><span class="sxs-lookup"><span data-stu-id="8331f-130">The **String.TrimStart** method is similar to the **String.TrimEnd** method except that it creates a new string by removing characters from the beginning of an existing string object.</span></span> <span data-ttu-id="8331f-131">Pole znaků je předáno metodě **trimStart** pro určení znaků, které mají být odebrány.</span><span class="sxs-lookup"><span data-stu-id="8331f-131">An array of characters is passed to the **TrimStart** method to specify the characters to be removed.</span></span> <span data-ttu-id="8331f-132">Stejně jako u metody **trimEnd** nemá pořadí prvků v poli znaků vliv na operaci ořezávání.</span><span class="sxs-lookup"><span data-stu-id="8331f-132">As with the **TrimEnd** method, the order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="8331f-133">Ořezávání se zastaví, když se najde znak, který není zadaný v poli.</span><span class="sxs-lookup"><span data-stu-id="8331f-133">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="8331f-134">Následující příklad odebere první slovo řetězce.</span><span class="sxs-lookup"><span data-stu-id="8331f-134">The following example removes the first word of a string.</span></span> <span data-ttu-id="8331f-135">V tomto příkladu je pozice `'l'` znaku a `'H'` znaku obrácena k ilustraci, že pořadí znaků v poli nezáleží.</span><span class="sxs-lookup"><span data-stu-id="8331f-135">In this example, the position of the `'l'` character and the `'H'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 <span data-ttu-id="8331f-136">Tento kód `World!` se zobrazí v konzole nástroje.</span><span class="sxs-lookup"><span data-stu-id="8331f-136">This code displays `World!` to the console.</span></span>  
  
## <a name="remove"></a><span data-ttu-id="8331f-137">Odebrat</span><span class="sxs-lookup"><span data-stu-id="8331f-137">Remove</span></span>

 <span data-ttu-id="8331f-138"><xref:System.String.Remove%2A?displayProperty=nameWithType>Metoda odstraní zadaný počet znaků, který začíná na zadané pozici v existujícím řetězci.</span><span class="sxs-lookup"><span data-stu-id="8331f-138">The <xref:System.String.Remove%2A?displayProperty=nameWithType> method removes a specified number of characters that begin at a specified position in an existing string.</span></span> <span data-ttu-id="8331f-139">Tato metoda předpokládá index založený na nule.</span><span class="sxs-lookup"><span data-stu-id="8331f-139">This method assumes a zero-based index.</span></span>  
  
 <span data-ttu-id="8331f-140">Následující příklad odebere deset znaků z řetězce, který začíná na pozici pět nul indexu řetězce.</span><span class="sxs-lookup"><span data-stu-id="8331f-140">The following example removes ten characters from a string beginning at position five of a zero-based index of the string.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
## <a name="replace"></a><span data-ttu-id="8331f-141">Nahradit</span><span class="sxs-lookup"><span data-stu-id="8331f-141">Replace</span></span>

 <span data-ttu-id="8331f-142">Můžete také odebrat zadaný znak nebo podřetězec z řetězce voláním <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> metody a zadáním prázdného řetězce ( <xref:System.String.Empty?displayProperty=nameWithType> ) jako náhrady.</span><span class="sxs-lookup"><span data-stu-id="8331f-142">You can also remove a specified character or substring from a string by calling the <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> method and specifying an empty string (<xref:System.String.Empty?displayProperty=nameWithType>) as the replacement.</span></span> <span data-ttu-id="8331f-143">Následující příklad odebere všechny čárky z řetězce.</span><span class="sxs-lookup"><span data-stu-id="8331f-143">The following example removes all commas from a string.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="8331f-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="8331f-144">See also</span></span>

- [<span data-ttu-id="8331f-145">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="8331f-145">Basic String Operations</span></span>](basic-string-operations.md)
