---
title: '&lt;kód&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
ms.openlocfilehash: 8a4708a7b50b0e221c1ebe7f95d4f8ff80cd1ebe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54566304"
---
# <a name="ltcodegt-visual-basic"></a>&lt;kód&gt; (Visual Basic)
Označuje, že text je více řádků kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<code>content</code>  
```  
  
#### <a name="parameters"></a>Parametry  
 `content`  
 Text k označení jako kódu.  
  
## <a name="remarks"></a>Poznámky  
 Použití `<code>` značky k označení jako kódu více řádků. Použití [ \<c >](../../../visual-basic/language-reference/xmldoc/c.md) k označení, že text v popisu musí být označené jako kód.  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu \<kód > značka, které zahrnují ukázkový kód pro použití `ID` pole.  
  
 [!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
