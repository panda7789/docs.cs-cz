---
title: '&lt;kód&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 9ec9d23f1f62358dc272f9764f88e3bb2ba41f78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599749"
---
# <a name="ltcodegt-visual-basic"></a>&lt;kód&gt; (Visual Basic)
Označuje, že je text více řádků kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<code>content</code>  
```  
  
#### <a name="parameters"></a>Parametry  
 `content`  
 Text k označení jako kódu.  
  
## <a name="remarks"></a>Poznámky  
 Použití `<code>` značky k označení jako kódu více řádků. Použití [ \<c >](../../../visual-basic/language-reference/xmldoc/c.md) indikující, že text v rámci popis by měl být označen jako kód.  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá \<kód > značka, které zahrnují ukázkový kód pro použití `ID` pole.  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
