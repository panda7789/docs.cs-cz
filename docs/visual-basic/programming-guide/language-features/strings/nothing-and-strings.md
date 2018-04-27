---
title: Výraz Nothing a řetězce v jazyce Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d7693e712884a500495e4573900e7d9a049c2879
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="1e824-102">Výraz Nothing a řetězce v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1e824-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="1e824-103">Modul runtime jazyka Visual Basic a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] vyhodnotit `Nothing` odlišně při rozhodování o řetězce.</span><span class="sxs-lookup"><span data-stu-id="1e824-103">The Visual Basic runtime and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="1e824-104">Modul Runtime jazyka Visual Basic a .NET Framework</span><span class="sxs-lookup"><span data-stu-id="1e824-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="1e824-105">Podívejte se na následující příklad:</span><span class="sxs-lookup"><span data-stu-id="1e824-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/nothing-and-strings_1.vb)]  
  
 <span data-ttu-id="1e824-106">Modul runtime jazyka Visual Basic obvykle vyhodnocuje `Nothing` jako prázdný řetězec ("").</span><span class="sxs-lookup"><span data-stu-id="1e824-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="1e824-107">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Neexistuje, ale a vyvolá výjimku, vždy, když je proveden pokus o provedení operace řetězec na `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="1e824-107">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e824-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e824-108">See Also</span></span>  
 [<span data-ttu-id="1e824-109">Představení řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1e824-109">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
