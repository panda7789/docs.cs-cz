---
title: Přístup k řetězci se základem 0 vs. Přístup k řetězci základem 1 v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: cc8f286de41d7e44225e889e73ff3c7b1fdbd881
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591744"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="515d4-102">Přístup k řetězci se základem 0 vs. Přístup k řetězci základem 1 v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="515d4-102">Zero-based vs. One-based String Access in Visual Basic</span></span>
<span data-ttu-id="515d4-103">Toto téma srovnává, jak Visual Basic a rozhraní .NET Framework poskytují přístup ke znakům v řetězci.</span><span class="sxs-lookup"><span data-stu-id="515d4-103">This topic compares how Visual Basic and the .NET Framework provide access to the characters in a string.</span></span> <span data-ttu-id="515d4-104">Rozhraní .NET Framework vždy poskytuje založený na nule přístup ke znakům v řetězci, zatímco Visual Basic poskytuje přístup založený na nule a založen na jedničce, v závislosti na funkci.</span><span class="sxs-lookup"><span data-stu-id="515d4-104">The .NET Framework always provides zero-based access to the characters in a string, whereas Visual Basic provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="515d4-105">Základem 1</span><span class="sxs-lookup"><span data-stu-id="515d4-105">One-Based</span></span>  
 <span data-ttu-id="515d4-106">Příklad funkce jazyka Visual Basic založen na jedničce, vezměte v úvahu `Mid` funkce.</span><span class="sxs-lookup"><span data-stu-id="515d4-106">For an example of a one-based Visual Basic function, consider the `Mid` function.</span></span> <span data-ttu-id="515d4-107">To přebírá argument, který označuje znak na pozici, na které se spustí dílčí řetězec, počínaje pozice 1.</span><span class="sxs-lookup"><span data-stu-id="515d4-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="515d4-108">Rozhraní .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> metoda má index znaku v řetězci, na které má spustit, podřetězec počínaje pozice 0.</span><span class="sxs-lookup"><span data-stu-id="515d4-108">The .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="515d4-109">Pokud máte řetězec "ABCDE", proto jsou jednotlivé znaky číslované 1,2,3,4,5 pro použití s `Mid` funkce, ale 0,1,2,3,4 pro použití se službou <xref:System.String.Substring%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="515d4-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="515d4-110">Od nuly</span><span class="sxs-lookup"><span data-stu-id="515d4-110">Zero-Based</span></span>  
 <span data-ttu-id="515d4-111">Příklad založený na nule funkce jazyka Visual Basic, vezměte v úvahu `Split` funkce.</span><span class="sxs-lookup"><span data-stu-id="515d4-111">For an example of a zero-based Visual Basic function, consider the `Split` function.</span></span> <span data-ttu-id="515d4-112">Rozdělí řetězec a vrátí pole obsahující podřetězce.</span><span class="sxs-lookup"><span data-stu-id="515d4-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="515d4-113">Rozhraní .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> metoda také rozdělí řetězec a vrátí pole obsahující podřetězce.</span><span class="sxs-lookup"><span data-stu-id="515d4-113">The .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="515d4-114">Vzhledem k tomu, `Split` funkce a <xref:System.String.Split%2A> metoda vrátit pole rozhraní .NET Framework, musí být založený na nule.</span><span class="sxs-lookup"><span data-stu-id="515d4-114">Because the `Split` function and <xref:System.String.Split%2A> method return .NET Framework arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="515d4-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="515d4-115">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [<span data-ttu-id="515d4-116">Úvod do řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="515d4-116">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
