---
title: '&lt;Příklad&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 8c09ab934ee7457fdff39a63c58f2546cda4d643
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ltexamplegt-visual-basic"></a>&lt;Příklad&gt; (Visual Basic)
Určuje příklad člena.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<example>description</example>  
```  
  
#### <a name="parameters"></a>Parametry  
 `description`  
 Popis ukázka kódu.  
  
## <a name="remarks"></a>Poznámky  
 `<example>` Značka umožňuje určit příklad použití metody nebo jiné knihovny člen. To obvykle zahrnuje použití [ \<kód >](../../../visual-basic/language-reference/xmldoc/code.md) značky.  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<example>` značka, které zahrnují příklad pro použití `ID` pole.  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/example_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
