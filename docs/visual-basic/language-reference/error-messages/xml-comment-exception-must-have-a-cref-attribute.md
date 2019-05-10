---
title: Výjimka komentáře XML musí mít atribut 'cref'.
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 91bde92e2184c90b14838a09a89a6d261447f139
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662614"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>Výjimka komentáře XML musí mít atribut 'cref'.
\<Výjimky > značky poskytuje způsob, jak dokumentovat výjimky, které mohou být vyvolány metodou. Požadované `cref` atribut určuje název člena, který je zaškrtnuté políčko generátorem dokumentaci. Pokud existuje člen je přeložit název canonical elementu v souboru dokumentace.  
  
 **ID chyby:** BC42319  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přidat `cref` atribut na výjimku následujícím způsobem:  
  
    ```  
    '''<exception cref="member">description</exception>  
    ```  
  
## <a name="see-also"></a>Viz také:

- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [Postupy: Vytvoření dokumentace XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
