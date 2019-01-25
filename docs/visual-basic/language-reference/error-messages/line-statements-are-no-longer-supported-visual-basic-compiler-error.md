---
title: '&#39;Řádek&#39; příkazy již nejsou podporovány (Chyba kompilátoru jazyka Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 36226cc371ffb8a51cb8d0f918952f1c717aea10
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702966"
---
# <a name="39line39-statements-are-no-longer-supported-visual-basic-compiler-error"></a>&#39;Řádek&#39; příkazy již nejsou podporovány (Chyba kompilátoru jazyka Visual Basic)
Příkazy řádek již nejsou podporovány. I/O soubor funkce je dostupná jako `Microsoft.VisualBasic.FileSystem.LineInput` a grafické funkce jsou k dispozici jako `System.Drawing.Graphics.DrawLine`.  
  
 **ID chyby:** BC30830  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Pokud provádíte přístup k souborům, použijte `Microsoft.VisualBasic.FileSystem.LineInput`.  
  
2.  Pokud provádíte grafiky, použijte `System.Drawing.Graphics.Drawline`.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.IO>
- <xref:System.Drawing>
- [Přístup k souborům v jazyce Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
