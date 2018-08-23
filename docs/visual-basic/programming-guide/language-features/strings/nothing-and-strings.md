---
title: Výraz Nothing a řetězce v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: d03781209f0f9b021d540bd251c6c6025ad21422
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2018
ms.locfileid: "42751903"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="7e248-102">Výraz Nothing a řetězce v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7e248-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="7e248-103">Modul runtime jazyka Visual Basic a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] vyhodnotit `Nothing` jinak pokud jde o řetězce.</span><span class="sxs-lookup"><span data-stu-id="7e248-103">The Visual Basic runtime and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="7e248-104">Modul Runtime jazyka Visual Basic a rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7e248-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="7e248-105">Vezměte v úvahu v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="7e248-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/nothing-and-strings_1.vb)]  
  
 <span data-ttu-id="7e248-106">Modul runtime jazyka Visual Basic obvykle vyhodnocuje `Nothing` jako prázdný řetězec ("").</span><span class="sxs-lookup"><span data-stu-id="7e248-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="7e248-107">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Tak není, ale a vyvolá výjimku, pokaždé, když je proveden pokus o provedení operace řetězec s `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="7e248-107">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e248-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e248-108">See Also</span></span>  
 [<span data-ttu-id="7e248-109">Úvod do řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7e248-109">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
