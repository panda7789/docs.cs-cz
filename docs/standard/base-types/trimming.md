---
title: Ořezávání a odstraňování znaků z řetězců v .NET
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c694a6792168f37e1f134cf965658e8a058e240a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037877"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a><span data-ttu-id="0d46a-102">Ořezávání a odstraňování znaků z řetězců v .NET</span><span class="sxs-lookup"><span data-stu-id="0d46a-102">Trimming and Removing Characters from Strings in .NET</span></span>
<span data-ttu-id="0d46a-103">Pokud analyzujete větu na jednotlivá slova, může se stát, že se na konci slova dokončí slova, která obsahují prázdné mezery (označované také jako prázdné znaky).</span><span class="sxs-lookup"><span data-stu-id="0d46a-103">If you are parsing a sentence into individual words, you might end up with words that have blank spaces (also called white spaces) on either end of the word.</span></span> <span data-ttu-id="0d46a-104">V této situaci můžete použít jednu z metod Trim třídy **System. String** k odebrání libovolného počtu mezer nebo jiných znaků ze zadané pozice v řetězci.</span><span class="sxs-lookup"><span data-stu-id="0d46a-104">In this situation, you can use one of the trim methods in the **System.String** class to remove any number of spaces or other characters from a specified position in the string.</span></span> <span data-ttu-id="0d46a-105">Následující tabulka popisuje dostupné metody Trim.</span><span class="sxs-lookup"><span data-stu-id="0d46a-105">The following table describes the available trim methods.</span></span>  
  
|<span data-ttu-id="0d46a-106">Název metody</span><span class="sxs-lookup"><span data-stu-id="0d46a-106">Method name</span></span>|<span data-ttu-id="0d46a-107">Použití</span><span class="sxs-lookup"><span data-stu-id="0d46a-107">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|<span data-ttu-id="0d46a-108">Odstraní prázdné znaky nebo znaky zadané v poli znaků od začátku a konce řetězce.</span><span class="sxs-lookup"><span data-stu-id="0d46a-108">Removes white spaces or characters specified in an array of characters from the beginning and end of a string.</span></span>|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|<span data-ttu-id="0d46a-109">Odebere znaky zadané v poli znaků z konce řetězce.</span><span class="sxs-lookup"><span data-stu-id="0d46a-109">Removes characters specified in an array of characters from the end of a string.</span></span>|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|<span data-ttu-id="0d46a-110">Odebere znaky zadané v poli znaků od začátku řetězce.</span><span class="sxs-lookup"><span data-stu-id="0d46a-110">Removes characters specified in an array of characters from the beginning of a string.</span></span>|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="0d46a-111">Odebere zadaný počet znaků ze zadané pozice indexu v řetězci.</span><span class="sxs-lookup"><span data-stu-id="0d46a-111">Removes a specified number of characters from a specified index position in a string.</span></span>|  
  
## <a name="trim"></a><span data-ttu-id="0d46a-112">Sklon</span><span class="sxs-lookup"><span data-stu-id="0d46a-112">Trim</span></span>

 <span data-ttu-id="0d46a-113">Pomocí metody <xref:System.String.Trim%2A?displayProperty=nameWithType> lze snadno odebrat prázdné znaky z obou konců řetězce, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="0d46a-113">You can easily remove white spaces from both ends of a string by using the <xref:System.String.Trim%2A?displayProperty=nameWithType> method, as shown in the following example.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 <span data-ttu-id="0d46a-114">Můžete také odebrat znaky, které zadáte v poli znaků od začátku a konce řetězce.</span><span class="sxs-lookup"><span data-stu-id="0d46a-114">You can also remove characters that you specify in a character array from the beginning and end of a string.</span></span> <span data-ttu-id="0d46a-115">Následující příklad odebere prázdné znaky, tečky a hvězdičky.</span><span class="sxs-lookup"><span data-stu-id="0d46a-115">The following example removes white-space characters, periods, and asterisks.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a><span data-ttu-id="0d46a-116">TrimEnd</span><span class="sxs-lookup"><span data-stu-id="0d46a-116">TrimEnd</span></span>

 <span data-ttu-id="0d46a-117">Metoda **String. TrimEnd** odstraní znaky z konce řetězce a vytvoří nový objekt řetězce.</span><span class="sxs-lookup"><span data-stu-id="0d46a-117">The **String.TrimEnd** method removes characters from the end of a string, creating a new string object.</span></span> <span data-ttu-id="0d46a-118">Pole znaků je předáno této metodě pro určení znaků, které mají být odebrány.</span><span class="sxs-lookup"><span data-stu-id="0d46a-118">An array of characters is passed to this method to specify the characters to be removed.</span></span> <span data-ttu-id="0d46a-119">Pořadí prvků v poli znaků nemá vliv na operaci ořezávání.</span><span class="sxs-lookup"><span data-stu-id="0d46a-119">The order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="0d46a-120">Ořezávání se zastaví, když se najde znak, který není zadaný v poli.</span><span class="sxs-lookup"><span data-stu-id="0d46a-120">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="0d46a-121">Následující příklad odebere poslední písmena řetězce pomocí metody **trimEnd** .</span><span class="sxs-lookup"><span data-stu-id="0d46a-121">The following example removes the last letters of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="0d46a-122">V tomto příkladu je pozice `'r'`ho znaku a `'W'` znak obrácena, aby se ilustraci, že pořadí znaků v poli nezáleží.</span><span class="sxs-lookup"><span data-stu-id="0d46a-122">In this example, the position of the `'r'` character and the `'W'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span> <span data-ttu-id="0d46a-123">Všimněte si, že tento kód odstraní poslední slovo `MyString` a část prvního.</span><span class="sxs-lookup"><span data-stu-id="0d46a-123">Notice that this code removes the last word of `MyString` plus part of the first.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 <span data-ttu-id="0d46a-124">Tento kód zobrazí `He` do konzoly.</span><span class="sxs-lookup"><span data-stu-id="0d46a-124">This code displays `He` to the console.</span></span>  
  
 <span data-ttu-id="0d46a-125">Následující příklad odebere poslední slovo řetězce pomocí metody **trimEnd** .</span><span class="sxs-lookup"><span data-stu-id="0d46a-125">The following example removes the last word of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="0d46a-126">V tomto kódu čárka následuje slova `Hello` a, protože čárka není určena v poli znaků, které mají být oříznuty, ořezávání končí čárkou.</span><span class="sxs-lookup"><span data-stu-id="0d46a-126">In this code, a comma follows the word `Hello` and, because the comma is not specified in the array of characters to trim, the trim ends at the comma.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 <span data-ttu-id="0d46a-127">Tento kód zobrazí `Hello,` do konzoly.</span><span class="sxs-lookup"><span data-stu-id="0d46a-127">This code displays `Hello,` to the console.</span></span>  
  
## <a name="trimstart"></a><span data-ttu-id="0d46a-128">TrimStart</span><span class="sxs-lookup"><span data-stu-id="0d46a-128">TrimStart</span></span>

 <span data-ttu-id="0d46a-129">Metoda **String. TrimStart** je podobná metodě **String. TrimEnd** s tím rozdílem, že vytvoří nový řetězec odebráním znaků ze začátku existujícího objektu řetězce.</span><span class="sxs-lookup"><span data-stu-id="0d46a-129">The **String.TrimStart** method is similar to the **String.TrimEnd** method except that it creates a new string by removing characters from the beginning of an existing string object.</span></span> <span data-ttu-id="0d46a-130">Pole znaků je předáno metodě **trimStart** pro určení znaků, které mají být odebrány.</span><span class="sxs-lookup"><span data-stu-id="0d46a-130">An array of characters is passed to the **TrimStart** method to specify the characters to be removed.</span></span> <span data-ttu-id="0d46a-131">Stejně jako u metody **trimEnd** nemá pořadí prvků v poli znaků vliv na operaci ořezávání.</span><span class="sxs-lookup"><span data-stu-id="0d46a-131">As with the **TrimEnd** method, the order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="0d46a-132">Ořezávání se zastaví, když se najde znak, který není zadaný v poli.</span><span class="sxs-lookup"><span data-stu-id="0d46a-132">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="0d46a-133">Následující příklad odebere první slovo řetězce.</span><span class="sxs-lookup"><span data-stu-id="0d46a-133">The following example removes the first word of a string.</span></span> <span data-ttu-id="0d46a-134">V tomto příkladu je pozice `'l'`ho znaku a `'H'` znak obrácena, aby se ilustraci, že pořadí znaků v poli nezáleží.</span><span class="sxs-lookup"><span data-stu-id="0d46a-134">In this example, the position of the `'l'` character and the `'H'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 <span data-ttu-id="0d46a-135">Tento kód zobrazí `World!` do konzoly.</span><span class="sxs-lookup"><span data-stu-id="0d46a-135">This code displays `World!` to the console.</span></span>  
  
## <a name="remove"></a><span data-ttu-id="0d46a-136">Odebrány</span><span class="sxs-lookup"><span data-stu-id="0d46a-136">Remove</span></span> 

 <span data-ttu-id="0d46a-137">Metoda <xref:System.String.Remove%2A?displayProperty=nameWithType> Odstraní zadaný počet znaků, který začíná na zadané pozici v existujícím řetězci.</span><span class="sxs-lookup"><span data-stu-id="0d46a-137">The <xref:System.String.Remove%2A?displayProperty=nameWithType> method removes a specified number of characters that begin at a specified position in an existing string.</span></span> <span data-ttu-id="0d46a-138">Tato metoda předpokládá index založený na nule.</span><span class="sxs-lookup"><span data-stu-id="0d46a-138">This method assumes a zero-based index.</span></span>  
  
 <span data-ttu-id="0d46a-139">Následující příklad odebere deset znaků z řetězce, který začíná na pozici pět nul indexu řetězce.</span><span class="sxs-lookup"><span data-stu-id="0d46a-139">The following example removes ten characters from a string beginning at position five of a zero-based index of the string.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
## <a name="replace"></a><span data-ttu-id="0d46a-140">náhrady</span><span class="sxs-lookup"><span data-stu-id="0d46a-140">Replace</span></span>

 <span data-ttu-id="0d46a-141">Můžete také odebrat zadaný znak nebo podřetězec z řetězce voláním metody <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> a zadáním prázdného řetězce (<xref:System.String.Empty?displayProperty=nameWithType>) jako náhrady.</span><span class="sxs-lookup"><span data-stu-id="0d46a-141">You can also remove a specified character or substring from a string by calling the <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> method and specifying an empty string (<xref:System.String.Empty?displayProperty=nameWithType>) as the replacement.</span></span> <span data-ttu-id="0d46a-142">Následující příklad odebere všechny čárky z řetězce.</span><span class="sxs-lookup"><span data-stu-id="0d46a-142">The following example removes all commas from a string.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="0d46a-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d46a-143">See also</span></span>

- [<span data-ttu-id="0d46a-144">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="0d46a-144">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
