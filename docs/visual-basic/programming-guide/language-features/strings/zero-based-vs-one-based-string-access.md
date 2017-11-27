---
title: "Počítaný od nuly vs. Přístup na základě jedné řetězce v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 911f063d6ca9a3f5d88a1f50d9df7f908a488f66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="b9e63-102">Počítaný od nuly vs. Přístup na základě jedné řetězce v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b9e63-102">Zero-based vs. One-based String Access in Visual Basic</span></span>
<span data-ttu-id="b9e63-103">Toto téma porovnává jak [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] poskytnout přístup k znaky v řetězci.</span><span class="sxs-lookup"><span data-stu-id="b9e63-103">This topic compares how [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provide access to the characters in a string.</span></span> <span data-ttu-id="b9e63-104">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Vždy poskytuje nule přístup k znaky v řetězci, zatímco [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] poskytuje nule a na základě jedné přístup, v závislosti na funkce.</span><span class="sxs-lookup"><span data-stu-id="b9e63-104">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] always provides zero-based access to the characters in a string, whereas [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="b9e63-105">Na základě jedné</span><span class="sxs-lookup"><span data-stu-id="b9e63-105">One-Based</span></span>  
 <span data-ttu-id="b9e63-106">Příklad základem jedna [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] fungovat, vezměte v úvahu `Mid` funkce.</span><span class="sxs-lookup"><span data-stu-id="b9e63-106">For an example of a one-based [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] function, consider the `Mid` function.</span></span> <span data-ttu-id="b9e63-107">Trvá argument, který označuje znak na pozici, na které se spustí dílčí řetězec, počínaje na pozici 1.</span><span class="sxs-lookup"><span data-stu-id="b9e63-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="b9e63-108">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> Metoda přebírá index znaku v řetězci, na které má začít, dílčí řetězec začínající na pozici 0.</span><span class="sxs-lookup"><span data-stu-id="b9e63-108">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="b9e63-109">Pokud máte řetězec "ABCDE", proto jsou jednotlivé znaky číslované 1,2,3,4,5 pro použití s `Mid` funkce, ale 0,1,2,3,4 pro použití s <xref:System.String.Substring%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="b9e63-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="b9e63-110">Počítaný od nuly</span><span class="sxs-lookup"><span data-stu-id="b9e63-110">Zero-Based</span></span>  
 <span data-ttu-id="b9e63-111">Příklad nulovým základem [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] fungovat, vezměte v úvahu `Split` funkce.</span><span class="sxs-lookup"><span data-stu-id="b9e63-111">For an example of a zero-based [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] function, consider the `Split` function.</span></span> <span data-ttu-id="b9e63-112">Rozdělí řetězec a vrátí pole obsahující dílčích řetězců.</span><span class="sxs-lookup"><span data-stu-id="b9e63-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="b9e63-113">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> Metoda také rozdělí řetězec a vrátí pole obsahující dílčích řetězců.</span><span class="sxs-lookup"><span data-stu-id="b9e63-113">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="b9e63-114">Protože `Split` funkce a <xref:System.String.Split%2A> metoda návratový [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] pole, musí být od nuly.</span><span class="sxs-lookup"><span data-stu-id="b9e63-114">Because the `Split` function and <xref:System.String.Split%2A> method return [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9e63-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="b9e63-115">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>  
 <xref:Microsoft.VisualBasic.Strings.Split%2A>  
 <xref:System.String.Substring%2A>  
 <xref:System.String.Split%2A>  
 [<span data-ttu-id="b9e63-116">Představení řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b9e63-116">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
