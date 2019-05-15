---
title: Výraz Nothing a řetězce v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Nothing
ms.assetid: 261380af-2024-4ecf-823b-43b1034d92cd
ms.openlocfilehash: f5c1ea8cc0728b25e8e874963967aed504e466d7
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591344"
---
# <a name="nothing-and-strings-in-visual-basic"></a>Výraz Nothing a řetězce v jazyce Visual Basic
Modul runtime jazyka Visual Basic a rozhraní .NET Framework vyhodnotit `Nothing` jinak pokud jde o řetězce.  
  
## <a name="visual-basic-runtime-and-the-net-framework"></a>Modul Runtime jazyka Visual Basic a rozhraní .NET Framework  
 Vezměte v úvahu v následujícím příkladu:  
  
 [!code-vb[VbVbalrStrings#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#47)]  
  
 Modul runtime jazyka Visual Basic obvykle vyhodnocuje `Nothing` jako prázdný řetězec (""). Rozhraní .NET Framework nepodporuje, ale a vyvolá výjimku, pokaždé, když je proveden pokus o provedení operace řetězec s `Nothing`.  
  
## <a name="see-also"></a>Viz také:

- [Úvod do řetězců v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
