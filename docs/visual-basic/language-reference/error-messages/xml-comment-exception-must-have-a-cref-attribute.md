---
title: Výjimka komentáře XML musí mít &#39;cref&#39; atribut
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: abe9fe0f6216f81fa223fe83a122b580577e1c32
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43255642"
---
# <a name="xml-comment-exception-must-have-a-39cref39-attribute"></a>Výjimka komentáře XML musí mít &#39;cref&#39; atribut
\<Výjimky > značky poskytuje způsob, jak dokumentovat výjimky, které mohou být vyvolány metodou. Požadované `cref` atribut určuje název člena, který je zaškrtnuté políčko generátorem dokumentaci. Pokud existuje člen je přeložit název canonical elementu v souboru dokumentace.  
  
 **ID chyby:** BC42319  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přidat `cref` atribut na výjimku následujícím způsobem:  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a>Viz také  
 [\<výjimky >](../../../visual-basic/language-reference/xmldoc/exception.md)  
 [Postupy: Vytvoření dokumentace XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)  
 [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
