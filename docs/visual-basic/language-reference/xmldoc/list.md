---
title: '&lt;seznam&gt; (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- listheader XML tag
- <item> XML tag
- <list> XML tag
- <listheader> XML tag
- term XML tag
- list XML tag
- <description> XML tag
- description XML tag
- item XML tag
- <term> XML tag
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 34347df88f1bc3097db0020526ec99943c8f7bd4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltlistgt-visual-basic"></a>&lt;seznam&gt; (Visual Basic)
Definuje seznam nebo tabulku.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<list type="type">  
   <listheader>  
      <term>term</term>  
      <description>description</description>  
   </listheader>  
   <item>  
      <term>term</term>  
      <description>description</description>  
   </item>  
</list>  
```  
  
#### <a name="parameters"></a>Parametry  
 `type`  
 Typ seznamu. Musí být "bullet" pro "číslo" číslovaný seznam, nebo "tabulka" pro dva sloupce tabulky, seznamu s odrážkami.  
  
 `term`  
 Pouze použít, když `type` je "tabulky." Termín, který chcete definovat, která je definovaná ve značce popis.  
  
 `description`  
 Když `type` "bullet" nebo "number" `description` položka v seznamu je při `type` je "tabulku" `description` je definice `term`.  
  
## <a name="remarks"></a>Poznámky  
 `<listheader>` Bloku definuje záhlaví tabulky nebo definice seznamu. Při definování tabulku, stačí zadat položku pro `term` v záhlaví.  
  
 Každá položka v seznamu je definován s `<item>` bloku. Při vytváření definice seznamu, musíte zadat oba `term` a `description`. Ale pro tabulku, seznamu s odrážkami nebo číslovaný seznam, stačí zadat položku pro `description`.  
  
 Seznam nebo tabulka může mít jako mnoho `<item>` blokuje podle potřeby.  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<list>` značky k definování seznamu s odrážkami v oddílu Poznámky.  
  
 [!code-vb[VbVbcnXmlDocComments#5](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
