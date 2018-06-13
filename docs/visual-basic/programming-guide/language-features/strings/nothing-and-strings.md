---
title: Výraz Nothing a řetězce v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: d03781209f0f9b021d540bd251c6c6025ad21422
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647170"
---
# <a name="nothing-and-strings-in-visual-basic"></a>Výraz Nothing a řetězce v jazyce Visual Basic
Modul runtime jazyka Visual Basic a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] vyhodnotit `Nothing` odlišně při rozhodování o řetězce.  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Modul Runtime jazyka Visual Basic a .NET Framework  
 Podívejte se na následující příklad:  
  
 [!code-vb[VbVbalrStrings#47](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/nothing-and-strings_1.vb)]  
  
 Modul runtime jazyka Visual Basic obvykle vyhodnocuje `Nothing` jako prázdný řetězec (""). [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Neexistuje, ale a vyvolá výjimku, vždy, když je proveden pokus o provedení operace řetězec na `Nothing`.  
  
## <a name="see-also"></a>Viz také  
 [Představení řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
