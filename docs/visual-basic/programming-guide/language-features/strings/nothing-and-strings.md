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
# <a name="nothing-and-strings-in-visual-basic"></a>Výraz Nothing a řetězce v jazyce Visual Basic
Modul runtime Visual Basic a .NET Framework vyhodnocuje `Nothing` jinak, když do řetězců přijdou.  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Visual Basic runtime a .NET Framework  
 Uvažujte následující příklad:  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 Modul runtime Visual Basic obvykle vyhodnocuje `Nothing` jako prázdný řetězec (""). .NET Framework však a vyvolá výjimku při každém pokusu o provedení operace s řetězcem `Nothing` .  
  
## <a name="see-also"></a>Viz také

- [Představení řetězců v jazyce Visual Basic](introduction-to-strings.md)
