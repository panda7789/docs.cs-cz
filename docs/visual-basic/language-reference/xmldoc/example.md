---
title: '&lt;Příklad&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: cd5ec21001263d7484500ab7680e6e36270e8768
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54670510"
---
# <a name="ltexamplegt-visual-basic"></a>&lt;Příklad&gt; (Visual Basic)
Příklad určuje pro člena.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<example>description</example>  
```  
  
#### <a name="parameters"></a>Parametry  
 `description`  
 Popis ukázky kódu.  
  
## <a name="remarks"></a>Poznámky  
 `<example>` Značky vám umožní určit příklad použití metody nebo jiný člen knihovny. To obvykle zahrnuje použití [ \<kód >](../../../visual-basic/language-reference/xmldoc/code.md) značky.  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `<example>` značka, které zahrnují příkladu pro použití `ID` pole.  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/example_1.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
