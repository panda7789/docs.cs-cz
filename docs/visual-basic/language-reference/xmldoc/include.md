---
title: '&lt;zahrnout&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 1cd992ae12e21b3d7fe29aff5a15b280c663d13b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54693065"
---
# <a name="ltincludegt-visual-basic"></a>&lt;zahrnout&gt; (Visual Basic)
Odkazuje na jiný soubor, který popisuje typy a členy ve zdrojovém kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
#### <a name="parameters"></a>Parametry  
 `filename`  
 Povinný parametr. Název souboru, který obsahuje dokumentaci. Název souboru může být kvalifikovány s cestou. Uzavřete `filename` do dvojitých uvozovek ("").  
  
 `tagpath`  
 Povinný parametr. Cesta klíčových slov do `filename` , který vede ke značce `name`. Vložte cestu do dvojitých uvozovek ("").  
  
 `name`  
 Povinný parametr. Specifikátor názvem ve značce, který předchází komentáře. `Name` bude mít `id`.  
  
 `id`  
 Povinný parametr. ID značky, které předchází komentáře. ID uzavřete do jednoduchých uvozovek ("").  
  
## <a name="remarks"></a>Poznámky  
 Použití `<include>` značka, které odkazují na komentáře do jiného souboru, které popisují typy a členy ve zdrojovém kódu. Jedná se o alternativu k uvedení dokumentační komentáře přímo v souboru zdrojového kódu.  
  
 `<include>` Značky používá doporučení W3C jazyk XML Path (XPath) verze 1.0. Další informace o tom, jak přizpůsobit vaší `<include>` , najdete v tématu <https://www.w3.org/TR/xpath>.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `<include>` značka Import ze souboru s názvem člena dokumentační komentáře `commentFile.xml`.  
  
 [!code-vb[VbVbcnXmlDocComments#4](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/include_1.vb)]  
  
 Formát `commentFile.xml` vypadá takto.  
  
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
  
## <a name="see-also"></a>Viz také:
- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
