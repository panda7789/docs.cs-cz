---
title: Výjimka komentáře XML musí mít atribut 'cref'.
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 2e57dc63cb7ad8b2e061296a082d6fa79b464f08
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592029"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>Výjimka komentáře XML musí mít atribut 'cref'.
Značka > \<exception poskytuje způsob, jak zdokumentovat výjimky, které mohou být vyvolány metodou. Požadovaný atribut `cref` určuje název členu, který je kontrolován generátorem dokumentace. Pokud člen existuje, je přeložen na kanonický název elementu v souboru dokumentace.  
  
 **ID chyby:** BC42319  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přidejte atribut `cref` pro výjimku následujícím způsobem:  
  
    xml  
    <exception cref="member">Popis</exception>  
    ```  
  
## See also

- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/index.md)
