---
title: "Výraz Nothing a řetězce v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6ce9f81f23f50e38f6b1ad5e638e8c6ac026e992
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="nothing-and-strings-in-visual-basic"></a>Výraz Nothing a řetězce v jazyce Visual Basic
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Runtime a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] vyhodnotit `Nothing` odlišně při rozhodování o řetězce.  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Modul Runtime jazyka Visual Basic a .NET Framework  
 Podívejte se na následující příklad:  
  
 [!code-vb[VbVbalrStrings#47](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/nothing-and-strings_1.vb)]  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Runtime obvykle vyhodnotí `Nothing` jako prázdný řetězec (""). [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Neexistuje, ale a vyvolá výjimku, vždy, když je proveden pokus o provedení operace řetězec na `Nothing`.  
  
## <a name="see-also"></a>Viz také  
 [Představení řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
