---
title: '&#39;Řádek&#39; příkazy již nejsou podporovány (Chyba kompilátoru jazyka Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 06bba0ebfc2faec24f4720c45de3bdcfec993499
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="39line39-statements-are-no-longer-supported-visual-basic-compiler-error"></a>&#39;Řádek&#39; příkazy již nejsou podporovány (Chyba kompilátoru jazyka Visual Basic)
Příkazy řádku již nejsou podporovány. Vstupně-výstupní funkce je k dispozici jako `Microsoft.VisualBasic.FileSystem.LineInput` a grafické funkce je k dispozici jako `System.Drawing.Graphics.DrawLine`.  
  
 **ID chyby:** BC30830  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Pokud se provádí přístup k souborům, použijte `Microsoft.VisualBasic.FileSystem.LineInput`.  
  
2.  Pokud budete provádět grafiky, použijte `System.Drawing.Graphics.Drawline`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO>  
 <xref:System.Drawing>  
 [Přístup k souborům v jazyce Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
