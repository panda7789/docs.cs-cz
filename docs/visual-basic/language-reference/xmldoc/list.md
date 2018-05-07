---
title: '&lt;seznam&gt; (Visual Basic)'
ms.date: 07/20/2015
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
ms.openlocfilehash: f03924217393e1e909b086b282f1c62ddb471522
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
