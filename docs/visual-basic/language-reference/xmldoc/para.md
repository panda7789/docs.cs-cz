---
title: '&lt;para&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
ms.openlocfilehash: cb80f4b39bee128790b311732adf1202dbbc6993
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601722"
---
# <a name="ltparagt-visual-basic"></a>&lt;para&gt; (Visual Basic)
Určuje, že obsah je formátován jako odstavec.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<para>content</para>  
```  
  
#### <a name="parameters"></a>Parametry  
 `content`  
 Text odstavce.  
  
## <a name="remarks"></a>Poznámky  
 `<para>` Značka je pro použití uvnitř značky, jako například [ \<souhrnné >](../../../visual-basic/language-reference/xmldoc/summary.md), [ \<Poznámky >](../../../visual-basic/language-reference/xmldoc/remarks.md), nebo [ \<vrátí >](../../../visual-basic/language-reference/xmldoc/returns.md), a umožňuje přidat struktura na text.  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<para>` značka oddílu poznámky pro rozdělení `UpdateRecord` metoda do dva odstavce.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/para_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
