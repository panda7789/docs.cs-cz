---
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 2f2bebfd06d4614f05cb66834cc5bef40524ce3b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348464"
---
# <a name="include-visual-basic"></a>\<include > (Visual Basic)
Odkazuje na jiný soubor, který popisuje typy a členy ve zdrojovém kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a>Parametry  
 `filename`  
 Požadováno. Název souboru, který obsahuje dokumentaci. Název souboru může být kvalifikován cestou. Uzavřete `filename` do uvozovek ("").  
  
 `tagpath`  
 Požadováno. Cesta značek v `filename`, které vedou k `name`značky Uzavřete cestu do uvozovek ("").  
  
 `name`  
 Požadováno. Specifikátor názvu ve značce, který předchází komentář. `Name` bude mít `id`.  
  
 `id`  
 Požadováno. ID značky, která předchází komentář. Uveďte ID v jednoduchých uvozovkách (' ').  
  
## <a name="remarks"></a>Poznámky  
 Pomocí značky `<include>` můžete odkazovat na komentáře v jiném souboru, které popisují typy a členy ve zdrojovém kódu. Toto je alternativa k umístění dokumentačních komentářů přímo do souboru zdrojového kódu.  
  
 Značka `<include>` používá doporučení jazyka W3C XML Path (XPath) verze 1,0. Další informace o způsobech přizpůsobení `<include>` použití naleznete v tématu <https://www.w3.org/TR/xpath>.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá značka `<include>` pro import dokumentačních komentářů členů ze souboru s názvem `commentFile.xml`.  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
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
  
## <a name="see-also"></a>Viz také:

- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
