---
title: <include>
ms.date: 07/20/2015
helpviewer_keywords:
- include XML tag
- <include> XML tag
ms.assetid: ba8e9173-82cd-460b-8938-a075a2dfb36d
ms.openlocfilehash: 78a10624107cea349b01f484c641190a945dbd7e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400108"
---
# <a name="include-visual-basic"></a>\<include> (Visual Basic)
Odkazuje na jiný soubor, který popisuje typy a členy ve zdrojovém kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<include file="filename" path="tagpath[@name='id']" />  
```  
  
## <a name="parameters"></a>Parametry  
 `filename`  
 Povinná hodnota. Název souboru, který obsahuje dokumentaci. Název souboru může být kvalifikován cestou. Uzavřete `filename` do dvojitých uvozovek ("").  
  
 `tagpath`  
 Povinná hodnota. Cesta značek v `filename` , která vede k označení `name` . Uzavřete cestu do uvozovek ("").  
  
 `name`  
 Povinná hodnota. Specifikátor názvu ve značce, který předchází komentář. `Name`bude mít `id` .  
  
 `id`  
 Povinná hodnota. ID značky, která předchází komentář. Uveďte ID v jednoduchých uvozovkách (' ').  
  
## <a name="remarks"></a>Poznámky  
 Použijte `<include>` značku pro odkazování na komentáře v jiném souboru, které popisují typy a členy ve zdrojovém kódu. Toto je alternativa k umístění dokumentačních komentářů přímo do souboru zdrojového kódu.  
  
 `<include>`Značka používá doporučení jazyka W3C XML Path (XPath) verze 1,0. Další informace o způsobech přizpůsobení `<include>` použití naleznete v tématu <https://www.w3.org/TR/xpath> .  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<include>` značku k importu komentářů k dokumentaci členů ze souboru s názvem `commentFile.xml` .  
  
 [!code-vb[VbVbcnXmlDocComments#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#4)]  
  
 Formát `commentFile.xml` je následující:  
  
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

- [Značky pro komentáře XML](index.md)
