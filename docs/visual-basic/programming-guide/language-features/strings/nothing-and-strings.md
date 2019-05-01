---
title: Výraz Nothing a řetězce v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: 5fbcf86261892e3eb8e43ee8eaa3728cd8e42ced
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032276"
---
# <a name="nothing-and-strings-in-visual-basic"></a>Výraz Nothing a řetězce v jazyce Visual Basic
Modul runtime jazyka Visual Basic a [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] vyhodnotit `Nothing` jinak pokud jde o řetězce.  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Modul Runtime jazyka Visual Basic a rozhraní .NET Framework  
 Vezměte v úvahu v následujícím příkladu:  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 Modul runtime jazyka Visual Basic obvykle vyhodnocuje `Nothing` jako prázdný řetězec (""). [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Tak není, ale a vyvolá výjimku, pokaždé, když je proveden pokus o provedení operace řetězec s `Nothing`.  
  
## <a name="see-also"></a>Viz také:

- [Úvod do řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
