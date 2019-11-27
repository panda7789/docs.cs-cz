---
title: Nothing a řetězce
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: dfc43748d0754f0a6a29763c42ab82d9937f89f8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344297"
---
# <a name="nothing-and-strings-in-visual-basic"></a>Výraz Nothing a řetězce v jazyce Visual Basic
Modul runtime Visual Basic a .NET Framework vyhodnocuje `Nothing` odlišně, když k nim přijdou řetězce.  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Visual Basic runtime a .NET Framework  
 Vezměte v úvahu v následujícím příkladu:  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 Modul runtime Visual Basic obvykle vyhodnocuje `Nothing` jako prázdný řetězec (""). .NET Framework však a vyvolá výjimku, kdykoli je proveden pokus o provedení operace s řetězcem v `Nothing`.  
  
## <a name="see-also"></a>Viz také:

- [Seznámení s řetězci v Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
