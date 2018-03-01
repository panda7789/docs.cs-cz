---
title: "& č. 39; Řádek & č. 39; příkazy již nejsou podporovány (Chyba kompilátoru jazyka Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30830
- vbc30830
helpviewer_keywords:
- BC30830
ms.assetid: 4734bc1d-882e-4555-b498-1f1ec0399d16
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9d2db5dc786749360dfcf6789f12b5659d5713fc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="39line39-statements-are-no-longer-supported-visual-basic-compiler-error"></a>& č. 39; Řádek & č. 39; příkazy již nejsou podporovány (Chyba kompilátoru jazyka Visual Basic)
Příkazy řádku již nejsou podporovány. Vstupně-výstupní funkce je k dispozici jako `Microsoft.VisualBasic.FileSystem.LineInput` a grafické funkce je k dispozici jako `System.Drawing.Graphics.DrawLine`.  
  
 **ID chyby:** BC30830  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Pokud se provádí přístup k souborům, použijte `Microsoft.VisualBasic.FileSystem.LineInput`.  
  
2.  Pokud budete provádět grafiky, použijte `System.Drawing.Graphics.Drawline`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IO>  
 <xref:System.Drawing>  
 [Přístup k souborům v jazyce Visual Basic](../../../visual-basic/developing-apps/programming/drives-directories-files/file-access.md)
