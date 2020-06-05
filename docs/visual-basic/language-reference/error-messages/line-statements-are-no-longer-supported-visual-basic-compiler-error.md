---
title: Příkazy 'Line' již nejsou podporovány (chyba kompilátoru jazyka Visual Basic).
ms.date: 07/20/2015
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
ms.openlocfilehash: a3d243f39f3fc45ca6b1ba0d26892d4c3db56f59
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397295"
---
# <a name="line-statements-are-no-longer-supported-visual-basic-compiler-error"></a>Příkazy 'Line' již nejsou podporovány (chyba kompilátoru jazyka Visual Basic).
Příkazy řádku již nejsou podporovány. Funkce pro vstupně-výstupní operace se soubory jsou k dispozici, protože `Microsoft.VisualBasic.FileSystem.LineInput` funkce grafiky jsou k dispozici jako `System.Drawing.Graphics.DrawLine` .  
  
 **ID chyby:** BC30830  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Při provádění přístupu k souboru použijte `Microsoft.VisualBasic.FileSystem.LineInput` .  
  
2. Při provádění grafiky použijte `System.Drawing.Graphics.Drawline` .  
  
## <a name="see-also"></a>Viz také

- <xref:System.IO>
- <xref:System.Drawing>
- [Přístup k souborům v jazyce Visual Basic](../../developing-apps/programming/drives-directories-files/file-access.md)
