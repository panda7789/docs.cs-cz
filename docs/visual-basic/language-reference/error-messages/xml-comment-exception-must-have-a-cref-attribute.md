---
title: Výjimka komentáře XML musí mít atribut 'cref'.
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: a11bfe261ffb8ded95f2e513aaddf00aa00f702e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55266634"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>Výjimka komentáře XML musí mít atribut 'cref'.
\<Výjimky > značky poskytuje způsob, jak dokumentovat výjimky, které mohou být vyvolány metodou. Požadované `cref` atribut určuje název člena, který je zaškrtnuté políčko generátorem dokumentaci. Pokud existuje člen je přeložit název canonical elementu v souboru dokumentace.  
  
 **ID chyby:** BC42319  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přidat `cref` atribut na výjimku následujícím způsobem:  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a>Viz také:
- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [Postupy: Vytvoření dokumentace XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
