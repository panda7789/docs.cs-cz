---
title: Nothing a řetězce
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: 392de45b0ee1688224f3e8170b0144f1acdb0912
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360563"
---
# <a name="nothing-and-strings-in-visual-basic"></a><span data-ttu-id="8f5ac-102">Výraz Nothing a řetězce v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8f5ac-102">Nothing and Strings in Visual Basic</span></span>
<span data-ttu-id="8f5ac-103">Modul runtime Visual Basic a .NET Framework vyhodnocuje `Nothing` jinak, když do řetězců přijdou.</span><span class="sxs-lookup"><span data-stu-id="8f5ac-103">The Visual Basic runtime and the .NET Framework evaluate `Nothing` differently when it comes to strings.</span></span>  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a><span data-ttu-id="8f5ac-104">Visual Basic runtime a .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8f5ac-104">Visual Basic Runtime and the .NET Framework</span></span>  
 <span data-ttu-id="8f5ac-105">Uvažujte následující příklad:</span><span class="sxs-lookup"><span data-stu-id="8f5ac-105">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 <span data-ttu-id="8f5ac-106">Modul runtime Visual Basic obvykle vyhodnocuje `Nothing` jako prázdný řetězec ("").</span><span class="sxs-lookup"><span data-stu-id="8f5ac-106">The Visual Basic runtime usually evaluates `Nothing` as an empty string ("").</span></span> <span data-ttu-id="8f5ac-107">.NET Framework však a vyvolá výjimku při každém pokusu o provedení operace s řetězcem `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="8f5ac-107">The .NET Framework does not, however, and throws an exception whenever an attempt is made to perform a string operation on `Nothing`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f5ac-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f5ac-108">See also</span></span>

- [<span data-ttu-id="8f5ac-109">Představení řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8f5ac-109">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
