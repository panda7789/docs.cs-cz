---
title: Ořezávání a odebírání znaků z řetězců v .NET
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
ms.openlocfilehash: 1d13d4e115caa636e5d760b65bc98e195490f911
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44184090"
---
# <a name="trimming-and-removing-characters-from-strings-in-net"></a><span data-ttu-id="4ba31-102">Ořezávání a odebírání znaků z řetězců v .NET</span><span class="sxs-lookup"><span data-stu-id="4ba31-102">Trimming and Removing Characters from Strings in .NET</span></span>
<span data-ttu-id="4ba31-103">Pokud analyzujete větu na jednotlivá slova, může skončit s slova, která mají mezery (také nazývané prázdné znaky) na jednom konci slovo.</span><span class="sxs-lookup"><span data-stu-id="4ba31-103">If you are parsing a sentence into individual words, you might end up with words that have blank spaces (also called white spaces) on either end of the word.</span></span> <span data-ttu-id="4ba31-104">V takovém případě můžete použít jednu z metod uvolnění dočasné paměti v **System.String** třídy odebrat libovolný počet mezery ani jiných znaků od určené pozice v řetězci.</span><span class="sxs-lookup"><span data-stu-id="4ba31-104">In this situation, you can use one of the trim methods in the **System.String** class to remove any number of spaces or other characters from a specified position in the string.</span></span> <span data-ttu-id="4ba31-105">Následující tabulka popisuje dostupné metody uvolnění dočasné paměti.</span><span class="sxs-lookup"><span data-stu-id="4ba31-105">The following table describes the available trim methods.</span></span>  
  
|<span data-ttu-id="4ba31-106">Název metody</span><span class="sxs-lookup"><span data-stu-id="4ba31-106">Method name</span></span>|<span data-ttu-id="4ba31-107">Použití</span><span class="sxs-lookup"><span data-stu-id="4ba31-107">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.Trim%2A?displayProperty=nameWithType>|<span data-ttu-id="4ba31-108">Odstraní prázdné znaky nebo znaky zadané do pole znaků ze začátku a konce řetězce.</span><span class="sxs-lookup"><span data-stu-id="4ba31-108">Removes white spaces or characters specified in an array of characters from the beginning and end of a string.</span></span>|  
|<xref:System.String.TrimEnd%2A?displayProperty=nameWithType>|<span data-ttu-id="4ba31-109">Odebere znaky zadané do pole znaků z konce řetězce.</span><span class="sxs-lookup"><span data-stu-id="4ba31-109">Removes characters specified in an array of characters from the end of a string.</span></span>|  
|<xref:System.String.TrimStart%2A?displayProperty=nameWithType>|<span data-ttu-id="4ba31-110">Odebere znaky zadané do pole znaků od začátku řetězce.</span><span class="sxs-lookup"><span data-stu-id="4ba31-110">Removes characters specified in an array of characters from the beginning of a string.</span></span>|  
|<xref:System.String.Remove%2A?displayProperty=nameWithType>|<span data-ttu-id="4ba31-111">Odebere zadaný počet znaků z pozice zadaným indexem v řetězci.</span><span class="sxs-lookup"><span data-stu-id="4ba31-111">Removes a specified number of characters from a specified index position in a string.</span></span>|  
  
## <a name="trim"></a><span data-ttu-id="4ba31-112">Trim</span><span class="sxs-lookup"><span data-stu-id="4ba31-112">Trim</span></span>  
 <span data-ttu-id="4ba31-113">Prázdné znaky z obou směru řetězce můžete snadno odebrat pomocí <xref:System.String.Trim%2A?displayProperty=nameWithType> způsob, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4ba31-113">You can easily remove white spaces from both ends of a string by using the <xref:System.String.Trim%2A?displayProperty=nameWithType> method, as shown in the following example.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#17)]
 [!code-csharp[Conceptual.String.BasicOps#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#17)]
 [!code-vb[Conceptual.String.BasicOps#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#17)]  
  
 <span data-ttu-id="4ba31-114">Můžete také odebrat znaky, které jste zadali v pole znaků ze začátku a konce řetězce.</span><span class="sxs-lookup"><span data-stu-id="4ba31-114">You can also remove characters that you specify in a character array from the beginning and end of a string.</span></span> <span data-ttu-id="4ba31-115">Následující příklad odstraní prázdné znaky, tečky a hvězdičky z obou stran.</span><span class="sxs-lookup"><span data-stu-id="4ba31-115">The following example removes white-space characters, periods, and asterisks.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#22](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trim2.cs#22)]
 [!code-vb[Conceptual.String.BasicOps#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trim2.vb#22)]  
  
## <a name="trimend"></a><span data-ttu-id="4ba31-116">TrimEnd</span><span class="sxs-lookup"><span data-stu-id="4ba31-116">TrimEnd</span></span>  
 <span data-ttu-id="4ba31-117">**String.TrimEnd** metoda odstraní znaků z konce řetězce, vytvoří nový objekt řetězce.</span><span class="sxs-lookup"><span data-stu-id="4ba31-117">The **String.TrimEnd** method removes characters from the end of a string, creating a new string object.</span></span> <span data-ttu-id="4ba31-118">Pole znaků je předat tuto metodu za účelem zadejte znaky, které mají být odebrány.</span><span class="sxs-lookup"><span data-stu-id="4ba31-118">An array of characters is passed to this method to specify the characters to be removed.</span></span> <span data-ttu-id="4ba31-119">Pořadí prvků v poli znak nemá vliv na operace uvolnění dočasné paměti.</span><span class="sxs-lookup"><span data-stu-id="4ba31-119">The order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="4ba31-120">Trim přestane při nalezení znaku není určené v poli.</span><span class="sxs-lookup"><span data-stu-id="4ba31-120">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="4ba31-121">Následující příklad odebere poslední písmena řetězce pomocí elementu **TrimEnd** metody.</span><span class="sxs-lookup"><span data-stu-id="4ba31-121">The following example removes the last letters of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="4ba31-122">V tomto příkladu pozice `'r'` znak a `'W'` přehozeny pro ilustraci, že se pořadí znaků v poli není důležitá.</span><span class="sxs-lookup"><span data-stu-id="4ba31-122">In this example, the position of the `'r'` character and the `'W'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span> <span data-ttu-id="4ba31-123">Všimněte si, že tento kód odebere poslední slovo `MyString` plus část první.</span><span class="sxs-lookup"><span data-stu-id="4ba31-123">Notice that this code removes the last word of `MyString` plus part of the first.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#18)]
 [!code-csharp[Conceptual.String.BasicOps#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#18)]
 [!code-vb[Conceptual.String.BasicOps#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#18)]  
  
 <span data-ttu-id="4ba31-124">Tento kód zobrazí `He` do konzoly.</span><span class="sxs-lookup"><span data-stu-id="4ba31-124">This code displays `He` to the console.</span></span>  
  
 <span data-ttu-id="4ba31-125">Následující příklad odebere poslední slovo řetězce pomocí elementu **TrimEnd** metody.</span><span class="sxs-lookup"><span data-stu-id="4ba31-125">The following example removes the last word of a string using the **TrimEnd** method.</span></span> <span data-ttu-id="4ba31-126">V tomto kódu, následuje čárka slovo `Hello` a, protože čárka není zadána jako pole znaků, které mají být odebrány, ořezávání končí čárka.</span><span class="sxs-lookup"><span data-stu-id="4ba31-126">In this code, a comma follows the word `Hello` and, because the comma is not specified in the array of characters to trim, the trim ends at the comma.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#19)]
 [!code-csharp[Conceptual.String.BasicOps#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#19)]
 [!code-vb[Conceptual.String.BasicOps#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#19)]  
  
 <span data-ttu-id="4ba31-127">Tento kód zobrazí `Hello,` do konzoly.</span><span class="sxs-lookup"><span data-stu-id="4ba31-127">This code displays `Hello,` to the console.</span></span>  
  
## <a name="trimstart"></a><span data-ttu-id="4ba31-128">TrimStart</span><span class="sxs-lookup"><span data-stu-id="4ba31-128">TrimStart</span></span>  
 <span data-ttu-id="4ba31-129">**String.TrimStart** metoda je podobná **String.TrimEnd** metoda s výjimkou, že vytvoří nový řetězec tak, že odeberete znaků od začátku existující objekt řetězce.</span><span class="sxs-lookup"><span data-stu-id="4ba31-129">The **String.TrimStart** method is similar to the **String.TrimEnd** method except that it creates a new string by removing characters from the beginning of an existing string object.</span></span> <span data-ttu-id="4ba31-130">Pole znaků je předán **TrimStart** metody zadejte znaky, které mají být odebrány.</span><span class="sxs-lookup"><span data-stu-id="4ba31-130">An array of characters is passed to the **TrimStart** method to specify the characters to be removed.</span></span> <span data-ttu-id="4ba31-131">Stejně jako u **TrimEnd** metoda pořadí prvků v poli znak nemá vliv na operace uvolnění dočasné paměti.</span><span class="sxs-lookup"><span data-stu-id="4ba31-131">As with the **TrimEnd** method, the order of the elements in the character array does not affect the trim operation.</span></span> <span data-ttu-id="4ba31-132">Trim přestane při nalezení znaku není určené v poli.</span><span class="sxs-lookup"><span data-stu-id="4ba31-132">The trim stops when a character not specified in the array is found.</span></span>  
  
 <span data-ttu-id="4ba31-133">Následující příklad odebere první slovo řetězce.</span><span class="sxs-lookup"><span data-stu-id="4ba31-133">The following example removes the first word of a string.</span></span> <span data-ttu-id="4ba31-134">V tomto příkladu pozice `'l'` znak a `'H'` přehozeny pro ilustraci, že se pořadí znaků v poli není důležitá.</span><span class="sxs-lookup"><span data-stu-id="4ba31-134">In this example, the position of the `'l'` character and the `'H'` character are reversed to illustrate that the order of characters in the array does not matter.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#20)]
 [!code-csharp[Conceptual.String.BasicOps#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#20)]
 [!code-vb[Conceptual.String.BasicOps#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#20)]  
  
 <span data-ttu-id="4ba31-135">Tento kód zobrazí `World!` do konzoly.</span><span class="sxs-lookup"><span data-stu-id="4ba31-135">This code displays `World!` to the console.</span></span>  
  
## <a name="remove"></a><span data-ttu-id="4ba31-136">odebrat</span><span class="sxs-lookup"><span data-stu-id="4ba31-136">Remove</span></span>  
 <span data-ttu-id="4ba31-137"><xref:System.String.Remove%2A?displayProperty=nameWithType> Metoda odstraní zadaný počet znaků, které začínají na určenou pozici do existujícího řetězce.</span><span class="sxs-lookup"><span data-stu-id="4ba31-137">The <xref:System.String.Remove%2A?displayProperty=nameWithType> method removes a specified number of characters that begin at a specified position in an existing string.</span></span> <span data-ttu-id="4ba31-138">Tato metoda předpokládá index založený na nule.</span><span class="sxs-lookup"><span data-stu-id="4ba31-138">This method assumes a zero-based index.</span></span>  
  
 <span data-ttu-id="4ba31-139">Následující příklad odebere deset znaků od začátku řetězce na pozici pět z nuly vycházející index řetězce.</span><span class="sxs-lookup"><span data-stu-id="4ba31-139">The following example removes ten characters from a string beginning at position five of a zero-based index of the string.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/trimming.cpp#21)]
 [!code-csharp[Conceptual.String.BasicOps#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/trimming.cs#21)]
 [!code-vb[Conceptual.String.BasicOps#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/trimming.vb#21)]  
  
 <span data-ttu-id="4ba31-140">Můžete také odebrat zadaný znak nebo podřetězec z řetězce pomocí volání <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> metoda a zadáte prázdný řetězec (<xref:System.String.Empty?displayProperty=nameWithType>) jako náhrada.</span><span class="sxs-lookup"><span data-stu-id="4ba31-140">You can also remove a specified character or substring from a string by calling the <xref:System.String.Replace%28System.String%2CSystem.String%29?displayProperty=nameWithType> method and specifying an empty string (<xref:System.String.Empty?displayProperty=nameWithType>) as the replacement.</span></span> <span data-ttu-id="4ba31-141">Následující příklad odebere všechny mezery v řetězci.</span><span class="sxs-lookup"><span data-stu-id="4ba31-141">The following example removes all commas from a string.</span></span>  
  
 [!code-csharp[Conceptual.String.BasicOps#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/replace1.cs#23)]
 [!code-vb[Conceptual.String.BasicOps#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/replace1.vb#23)]  
  
## <a name="see-also"></a><span data-ttu-id="4ba31-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ba31-142">See also</span></span>

- [<span data-ttu-id="4ba31-143">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="4ba31-143">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)
