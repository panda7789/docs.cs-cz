---
title: '&lt;zahrnout&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 65bc0439696612cd8331a9c0718efcfee83af574
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="ltincludegt-visual-basic"></a>&lt;zahrnout&gt; (Visual Basic)
Odkazuje na jiný soubor, který popisuje typy a členy ve zdrojovém kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Požadováno. Název souboru, který obsahuje v dokumentaci. Název souboru může být kvalifikovaný s cestou. Uzavřete `filename` v uvozovkách ("").  
  
 `tagpath`  
 Požadováno. Cesta značky v `filename` který vede ke značce `name`. Vložte cestu do dvojitých uvozovek nahoře ("").  
  
 `name`  
 Požadováno. Specifikátor název ve značce, která předchází komentáře. `Name` bude mít `id`.  
  
 `id`  
 Požadováno. ID značky, která předchází komentáře. Uzavřete ID v jednoduchých uvozovkách ("").  
  
## <a name="remarks"></a>Poznámky  
 Použití `<include>` značky k odkazování na komentáře v jiném souboru, které popisují typy a členy ve zdrojovém kódu. Jde o alternativu k uvedení dokumentační komentáře ve zdrojovém kódu souboru přímo.  
  
 `<include>` Značku používá doporučení W3C XML Path Language (XPath) verze 1.0. Další informace o tom, jak přizpůsobit vaší `<include>` použijte je k dispozici na http://www.w3.org/TR/xpath.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<include>` značka import člen dokumentační komentáře ze souboru s názvem `commentFile.xml`.  
  
 [!code-vb[VbVbcnXmlDocComments#4](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/include_1.vb)]  
  
 Formát `commentFile.xml` je následující.  
  
```xml  
<Docs>  
<Members name="Open">  
<summary>Opens a file.</summary>  
<param name="filename">File name to open.</param>  
</Members>  
<Members name="Close">  
<summary>Closes a file.</summary>  
<param name="filename">File name to close.</param>  
</Members>  
</Docs>  
```  
  
## <a name="see-also"></a>Viz také  
 [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
