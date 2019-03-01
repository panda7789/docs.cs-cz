---
title: Výraz Nothing a řetězce v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: 873c4e40a0b12dd657d3294785e04dd9efc23956
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967981"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="b5642-102">Výraz Nothing a řetězce v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b5642-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="b5642-103">Modul runtime jazyka Visual Basic a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] vyhodnotit `Nothing` jinak pokud jde o řetězce.</span><span class="sxs-lookup"><span data-stu-id="b5642-103">The Visual Basic runtime and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="b5642-104">Modul Runtime jazyka Visual Basic a rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b5642-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="b5642-105">Vezměte v úvahu v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b5642-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 <span data-ttu-id="b5642-106">Modul runtime jazyka Visual Basic obvykle vyhodnocuje `Nothing` jako prázdný řetězec ("").</span><span class="sxs-lookup"><span data-stu-id="b5642-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="b5642-107">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Tak není, ale a vyvolá výjimku, pokaždé, když je proveden pokus o provedení operace řetězec s `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="b5642-107">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5642-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5642-108">See also</span></span>
- [<span data-ttu-id="b5642-109">Úvod do řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b5642-109">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
