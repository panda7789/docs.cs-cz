---
title: <exception>
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: e1e7f2d0fb06599f83ba224ed52a10429d9b11fe
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346962"
---
# <a name="exception-visual-basic"></a>> \<výjimky (Visual Basic)
Určuje, které výjimky mohou být vyvolány.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<exception cref="member">description</exception>  
```  
  
## <a name="parameters"></a>Parametry  
 `member`  
 Odkaz na výjimku, která je k dispozici z aktuálního prostředí kompilace. Kompilátor kontroluje, zda daná výjimka existuje, a překládá `member` na název kanonického prvku ve výstupním souboru XML. `member` musí být v uvozovkách ("").  
  
 `description`  
 Popis.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí značky `<exception>` určete, které výjimky mohou být vyvolány. Tato značka se aplikuje na definici metody.  
  
 Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá značka `<exception>` k popisu výjimky, kterou může funkce `IntDivide` vyvolat.  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
