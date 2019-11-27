---
title: Přístup k řetězci založený na nule vs. One
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: 97e60038bc7ec0f030939d0980b786bffebcfb9a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354290"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="7415e-102">Přístup k řetězci v jazyce Visual Basic počítaný od nuly vs. počítaný od hodnoty jedna</span><span class="sxs-lookup"><span data-stu-id="7415e-102">Zero-based vs. One-based String Access in Visual Basic</span></span>
<span data-ttu-id="7415e-103">Toto téma porovnává, jak Visual Basic a .NET Framework poskytují přístup ke znakům v řetězci.</span><span class="sxs-lookup"><span data-stu-id="7415e-103">This topic compares how Visual Basic and the .NET Framework provide access to the characters in a string.</span></span> <span data-ttu-id="7415e-104">.NET Framework vždy poskytuje přístup založený na nule ke znakům v řetězci, zatímco Visual Basic poskytuje přístup založený na nule a jednom v závislosti na funkci.</span><span class="sxs-lookup"><span data-stu-id="7415e-104">The .NET Framework always provides zero-based access to the characters in a string, whereas Visual Basic provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="7415e-105">Založený na jednom</span><span class="sxs-lookup"><span data-stu-id="7415e-105">One-Based</span></span>  
 <span data-ttu-id="7415e-106">Příklad Visual Basic funkce založené na funkci `Mid` je považovat za funkce.</span><span class="sxs-lookup"><span data-stu-id="7415e-106">For an example of a one-based Visual Basic function, consider the `Mid` function.</span></span> <span data-ttu-id="7415e-107">Přebírá argument, který označuje pozici znaku, na které se dílčí řetězec spustí, počínaje pozicí 1.</span><span class="sxs-lookup"><span data-stu-id="7415e-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="7415e-108">Metoda .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> přebírá index znaku v řetězci, na kterém je dílčí řetězec spuštěn, počínaje pozicí 0.</span><span class="sxs-lookup"><span data-stu-id="7415e-108">The .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="7415e-109">Proto pokud máte řetězec "ABCDE", jednotlivé znaky jsou očíslovány 1, 2, 3, 4, 5 pro použití s funkcí `Mid`, ale 0, 1, 2, 3, 4 pro použití s metodou <xref:System.String.Substring%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7415e-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="7415e-110">Založený na nule</span><span class="sxs-lookup"><span data-stu-id="7415e-110">Zero-Based</span></span>  
 <span data-ttu-id="7415e-111">Příklad funkce Visual Basic založené na nule, je považovat za funkci `Split`.</span><span class="sxs-lookup"><span data-stu-id="7415e-111">For an example of a zero-based Visual Basic function, consider the `Split` function.</span></span> <span data-ttu-id="7415e-112">Rozdělí řetězec a vrátí pole obsahující podřetězce.</span><span class="sxs-lookup"><span data-stu-id="7415e-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="7415e-113">Metoda .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> také rozdělí řetězec a vrátí pole obsahující podřetězce.</span><span class="sxs-lookup"><span data-stu-id="7415e-113">The .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="7415e-114">Vzhledem k tomu, že funkce `Split` a metoda <xref:System.String.Split%2A> vrací .NET Framework pole, musí být založené na nule.</span><span class="sxs-lookup"><span data-stu-id="7415e-114">Because the `Split` function and <xref:System.String.Split%2A> method return .NET Framework arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7415e-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7415e-115">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [<span data-ttu-id="7415e-116">Seznámení s řetězci v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7415e-116">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
