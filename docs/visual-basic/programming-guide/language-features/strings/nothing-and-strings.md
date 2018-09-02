---
title: Výraz Nothing a řetězce v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: d03781209f0f9b021d540bd251c6c6025ad21422
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43425208"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="b96c6-102">Výraz Nothing a řetězce v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b96c6-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="b96c6-103">Modul runtime jazyka Visual Basic a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] vyhodnotit `Nothing` jinak pokud jde o řetězce.</span><span class="sxs-lookup"><span data-stu-id="b96c6-103">The Visual Basic runtime and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="b96c6-104">Modul Runtime jazyka Visual Basic a rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="b96c6-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="b96c6-105">Vezměte v úvahu v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b96c6-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/nothing-and-strings_1.vb)]  
  
 <span data-ttu-id="b96c6-106">Modul runtime jazyka Visual Basic obvykle vyhodnocuje `Nothing` jako prázdný řetězec ("").</span><span class="sxs-lookup"><span data-stu-id="b96c6-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="b96c6-107">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Tak není, ale a vyvolá výjimku, pokaždé, když je proveden pokus o provedení operace řetězec s `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="b96c6-107">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b96c6-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="b96c6-108">See Also</span></span>  
 [<span data-ttu-id="b96c6-109">Úvod do řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b96c6-109">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
