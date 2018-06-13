---
title: '&lt;Param&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: c992c96303eb1441eaf667693b7aefb5361b196c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602918"
---
# <a name="ltparamgt-visual-basic"></a>&lt;Param&gt; (Visual Basic)
Definuje parametr název a popis.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Název parametru metody. Uzavřete název do dvojitých uvozovek nahoře ("").  
  
 `description`  
 Popis parametru.  
  
## <a name="remarks"></a>Poznámky  
 `<param>` Značky je třeba používat v komentář pro deklaraci metody k popisu jeden z parametrů pro metodu.  
  
 Text pro `<param>` značky se zobrazí v následujících umístěních:  
  
-   Informace o parametrech technologie IntelliSense. Další informace najdete v tématu [pomocí IntelliSense](/visualstudio/ide/using-intellisense).  
  
-   Prohlížeč objektů. Další informace najdete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<param>` značka, které popisují `id` parametr.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
