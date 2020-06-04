---
title: Výjimka komentáře XML musí mít atribut 'cref'.
ms.date: 07/20/2015
f1_keywords:
- bc42319
- vbc42319
helpviewer_keywords:
- BC42319
ms.assetid: 62eeeba3-6811-48be-b1ef-c2e4feda3177
ms.openlocfilehash: c498675ab6ae616fb63d3d76ef60bcac7e247145
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406505"
---
# <a name="xml-comment-exception-must-have-a-cref-attribute"></a>Výjimka komentáře XML musí mít atribut 'cref'.

\<exception>Značka poskytuje způsob, jak zdokumentovat výjimky, které mohou být vyvolány metodou. Požadovaný `cref` atribut určuje název členu, který je kontrolován generátorem dokumentace. Pokud člen existuje, je přeložen na kanonický název elementu v souboru dokumentace.

**ID chyby:** BC42319

## <a name="to-correct-this-error"></a>Oprava této chyby

Přidejte `cref` atribut k výjimce následujícím způsobem:

```xml
<exception cref="member">description</exception>
```

## <a name="see-also"></a>Viz také

- [\<exception>](../xmldoc/exception.md)
- [Postupy: Vytvoření dokumentace XML](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
- [Značky pro komentáře XML](../xmldoc/index.md)
