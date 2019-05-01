---
title: Přístup k řetězci se základem 0 vs. Přístup k řetězci základem 1 v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: a6ceb10d4a3cb9463551d8c85375ddbbb607ffdc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024453"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="d54d3-102">Přístup k řetězci se základem 0 vs. Přístup k řetězci základem 1 v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d54d3-102">Zero-based vs. One-based String Access in Visual Basic</span></span>
<span data-ttu-id="d54d3-103">Toto téma srovnává způsobu, jakým Visual Basic a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] poskytují přístup ke znakům v řetězci.</span><span class="sxs-lookup"><span data-stu-id="d54d3-103">This topic compares how Visual Basic and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provide access to the characters in a string.</span></span> <span data-ttu-id="d54d3-104">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Vždy poskytuje založený na nule přístup ke znakům v řetězci, zatímco Visual Basic poskytuje přístup založený na nule a založen na jedničce, v závislosti na funkci.</span><span class="sxs-lookup"><span data-stu-id="d54d3-104">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] always provides zero-based access to the characters in a string, whereas Visual Basic provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="d54d3-105">Základem 1</span><span class="sxs-lookup"><span data-stu-id="d54d3-105">One-Based</span></span>  
 <span data-ttu-id="d54d3-106">Příklad funkce jazyka Visual Basic založen na jedničce, vezměte v úvahu `Mid` funkce.</span><span class="sxs-lookup"><span data-stu-id="d54d3-106">For an example of a one-based Visual Basic function, consider the `Mid` function.</span></span> <span data-ttu-id="d54d3-107">To přebírá argument, který označuje znak na pozici, na které se spustí dílčí řetězec, počínaje pozice 1.</span><span class="sxs-lookup"><span data-stu-id="d54d3-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="d54d3-108">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> Metoda má index znaku v řetězci, na které má spustit, podřetězec počínaje pozice 0.</span><span class="sxs-lookup"><span data-stu-id="d54d3-108">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="d54d3-109">Pokud máte řetězec "ABCDE", proto jsou jednotlivé znaky číslované 1,2,3,4,5 pro použití s `Mid` funkce, ale 0,1,2,3,4 pro použití se službou <xref:System.String.Substring%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="d54d3-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="d54d3-110">Od nuly</span><span class="sxs-lookup"><span data-stu-id="d54d3-110">Zero-Based</span></span>  
 <span data-ttu-id="d54d3-111">Příklad založený na nule funkce jazyka Visual Basic, vezměte v úvahu `Split` funkce.</span><span class="sxs-lookup"><span data-stu-id="d54d3-111">For an example of a zero-based Visual Basic function, consider the `Split` function.</span></span> <span data-ttu-id="d54d3-112">Rozdělí řetězec a vrátí pole obsahující podřetězce.</span><span class="sxs-lookup"><span data-stu-id="d54d3-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="d54d3-113">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> Metoda také rozdělí řetězec a vrátí pole obsahující podřetězce.</span><span class="sxs-lookup"><span data-stu-id="d54d3-113">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="d54d3-114">Protože `Split` funkce a <xref:System.String.Split%2A> metoda návratový [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pole, musí být založený na nule.</span><span class="sxs-lookup"><span data-stu-id="d54d3-114">Because the `Split` function and <xref:System.String.Split%2A> method return [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d54d3-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d54d3-115">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [<span data-ttu-id="d54d3-116">Úvod do řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d54d3-116">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
