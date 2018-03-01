---
title: "Výjimka komentáře XML musí mít & č. 39; cref & č. 39; atribut"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0c22c9cd9415faf17d027c3751d166662a92b50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a>Výjimka komentáře XML musí mít & č. 39; cref & č. 39; atribut
\<Výjimka > Značka poskytuje způsob, jak dokumentu výjimky, které mohou být vyvolány metodou. Požadované `cref` atribut určuje název člena, který je zaškrtnuta možnost generátorem dokumentaci. Pokud existuje člena, je přeložit název kanonický elementu v dokumentaci k souboru.  
  
 **ID chyby:** BC42319  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přidat `cref` atribut výjimka následujícím způsobem:  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a>Viz také  
 [\<Výjimka >](../../../visual-basic/language-reference/xmldoc/exception.md)  
 [Postupy: vytvoření dokumentace XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
