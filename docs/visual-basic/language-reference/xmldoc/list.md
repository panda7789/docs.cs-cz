---
title: <list> (Visual Basic)
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
ms.openlocfilehash: 522450e4efcecaf74968ddb492b536aa98dc0b13
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260285"
---
# <a name="list-visual-basic"></a>\<list> (Visual Basic)
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
 Typ seznamu. Pro seznam s odrážkami, "number" číslovaný seznam nebo "table" pro dva sloupce tabulky musí být "bullet".  
  
 `term`  
 Použije se pouze při `type` je "table". Termín, který chcete definovat, která je definována v popisu značky.  
  
 `description`  
 Když `type` "bullet" nebo "number" `description` je položka v seznamu při `type` je "table" `description` je definice `term`.  
  
## <a name="remarks"></a>Poznámky  
 `<listheader>` Bloku definuje záhlaví tabulky nebo definice seznamu. Při definování tabulku, stačí jenom zadat položku pro `term` v záhlaví.  
  
 Každá položka v seznamu není zadán s `<item>` bloku. Při vytváření definice seznamu, musíte zadat oba `term` a `description`. Ale pro tabulku, seznam s odrážkami nebo číslovaného seznamu, stačí jenom zadat položku pro `description`.  
  
 Seznam nebo tabulku můžete mít kolik `<item>` blokuje podle potřeby.  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `<list>` značka, které definují seznam s odrážkami v části poznámky.  
  
 [!code-vb[VbVbcnXmlDocComments#5](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
