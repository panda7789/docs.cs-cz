---
title: Příkazy 'Line' již nejsou podporovány (chyba kompilátoru jazyka Visual Basic).
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: 17025e9a3c87d84a10ddaa7aeef616d985143879
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283206"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a>Příkazy 'Line' již nejsou podporovány (chyba kompilátoru jazyka Visual Basic).
Příkazy řádek již nejsou podporovány. I/O soubor funkce je dostupná jako `Microsoft.VisualBasic.FileSystem.LineInput` a grafické funkce jsou k dispozici jako `System.Drawing.Graphics.DrawLine`.  
  
 **ID chyby:** BC30830  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Pokud provádíte přístup k souborům, použijte `Microsoft.VisualBasic.FileSystem.LineInput`.  
  
2.  Pokud provádíte grafiky, použijte `System.Drawing.Graphics.Drawline`.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.IO>
- <xref:System.Drawing>
- [Přístup k souborům v jazyce Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
