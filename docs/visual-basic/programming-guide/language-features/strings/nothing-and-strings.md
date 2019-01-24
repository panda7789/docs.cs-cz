---
title: Výraz Nothing a řetězce v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: 65a69861c2a74a3191a45eb782a97f289b0c0726
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574167"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="4c863-102">Výraz Nothing a řetězce v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4c863-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="4c863-103">Modul runtime jazyka Visual Basic a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] vyhodnotit `Nothing` jinak pokud jde o řetězce.</span><span class="sxs-lookup"><span data-stu-id="4c863-103">The Visual Basic runtime and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="4c863-104">Modul Runtime jazyka Visual Basic a rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4c863-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="4c863-105">Vezměte v úvahu v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="4c863-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/nothing-and-strings_1.vb)]  
  
 <span data-ttu-id="4c863-106">Modul runtime jazyka Visual Basic obvykle vyhodnocuje `Nothing` jako prázdný řetězec ("").</span><span class="sxs-lookup"><span data-stu-id="4c863-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="4c863-107">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Tak není, ale a vyvolá výjimku, pokaždé, když je proveden pokus o provedení operace řetězec s `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="4c863-107">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c863-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c863-108">See also</span></span>
- [<span data-ttu-id="4c863-109">Úvod do řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4c863-109">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
