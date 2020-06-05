---
title: Přístup k řetězci založený na nule vs. One
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: ce2fcb2610c09a9591a5fd79da4baa74cc533c99
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363653"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="d3068-102">Přístup k řetězci v jazyce Visual Basic počítaný od nuly vs. počítaný od hodnoty jedna</span><span class="sxs-lookup"><span data-stu-id="d3068-102">Zero-based vs. One-based String Access in Visual Basic</span></span>
<span data-ttu-id="d3068-103">Toto téma porovnává, jak Visual Basic a .NET Framework poskytují přístup ke znakům v řetězci.</span><span class="sxs-lookup"><span data-stu-id="d3068-103">This topic compares how Visual Basic and the .NET Framework provide access to the characters in a string.</span></span> <span data-ttu-id="d3068-104">.NET Framework vždy poskytuje přístup založený na nule ke znakům v řetězci, zatímco Visual Basic poskytuje přístup založený na nule a jednom v závislosti na funkci.</span><span class="sxs-lookup"><span data-stu-id="d3068-104">The .NET Framework always provides zero-based access to the characters in a string, whereas Visual Basic provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="d3068-105">Založený na jednom</span><span class="sxs-lookup"><span data-stu-id="d3068-105">One-Based</span></span>  
 <span data-ttu-id="d3068-106">Pro příklad funkce Visual Basic založené na jedné, zvažte `Mid` funkci.</span><span class="sxs-lookup"><span data-stu-id="d3068-106">For an example of a one-based Visual Basic function, consider the `Mid` function.</span></span> <span data-ttu-id="d3068-107">Přebírá argument, který označuje pozici znaku, na které se dílčí řetězec spustí, počínaje pozicí 1.</span><span class="sxs-lookup"><span data-stu-id="d3068-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="d3068-108">Metoda .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> přebírá index znaku v řetězci, na kterém je dílčí řetězec spuštěn, počínaje pozicí 0.</span><span class="sxs-lookup"><span data-stu-id="d3068-108">The .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="d3068-109">Proto pokud máte řetězec "ABCDE", jednotlivé znaky jsou očíslovány 1, 2, 3, 4, 5 pro použití s `Mid` funkcí, ale 0, 1, 2, 3, 4 pro použití s <xref:System.String.Substring%2A?displayProperty=nameWithType> metodou.</span><span class="sxs-lookup"><span data-stu-id="d3068-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="d3068-110">Založený na nule</span><span class="sxs-lookup"><span data-stu-id="d3068-110">Zero-Based</span></span>  
 <span data-ttu-id="d3068-111">Příklad funkce Visual Basic založené na nule, je třeba vzít v úvahu `Split` funkci.</span><span class="sxs-lookup"><span data-stu-id="d3068-111">For an example of a zero-based Visual Basic function, consider the `Split` function.</span></span> <span data-ttu-id="d3068-112">Rozdělí řetězec a vrátí pole obsahující podřetězce.</span><span class="sxs-lookup"><span data-stu-id="d3068-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="d3068-113">Metoda .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> také rozdělí řetězec a vrátí pole obsahující podřetězce.</span><span class="sxs-lookup"><span data-stu-id="d3068-113">The .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="d3068-114">Vzhledem k tomu `Split` , že funkce a <xref:System.String.Split%2A> metoda vrací .NET Framework pole, musí být počítány od nuly.</span><span class="sxs-lookup"><span data-stu-id="d3068-114">Because the `Split` function and <xref:System.String.Split%2A> method return .NET Framework arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3068-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3068-115">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [<span data-ttu-id="d3068-116">Představení řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d3068-116">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
