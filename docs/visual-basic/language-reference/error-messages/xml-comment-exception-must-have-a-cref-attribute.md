---
title: Výjimka komentáře XML musí mít atribut 'cref'.
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: 54965f3796b6c5ef0e387cd354abcb5740476257
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321176"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>Výjimka komentáře XML musí mít atribut 'cref'.

Značka > \<výjimka poskytuje způsob, jak zdokumentovat výjimky, které mohou být vyvolány metodou. Požadovaný atribut `cref` Určuje název členu, který je kontrolován generátorem dokumentace. Pokud člen existuje, je přeložen na kanonický název elementu v souboru dokumentace.

**ID chyby:** BC42319

## <a name="to-correct-this-error"></a>Oprava této chyby

Přidejte atribut `cref` k výjimce následujícím způsobem:

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a>Viz také:

- [\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md)
- [Postupy: Vytvoření dokumentace XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
