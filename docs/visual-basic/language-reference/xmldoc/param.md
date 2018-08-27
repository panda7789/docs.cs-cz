---
title: '&lt;Param&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- param XML tag
- <param> XML tag
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
ms.openlocfilehash: 4cb3de06d574f8b9abb3e3e11641a6ada750b56a
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42935755"
---
# <a name="ltparamgt-visual-basic"></a>&lt;Param&gt; (Visual Basic)
Definuje parametr název a popis.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<param name="name">description</param>  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Název parametru metody. Název uzavřete do dvojitých uvozovek ("").  
  
 `description`  
 Popis pro parametr.  
  
## <a name="remarks"></a>Poznámky  
 `<param>` Značky byste měli použít ve komentář pro deklaraci metody, popisující jeden z parametrů pro metodu.  
  
 Text `<param>` značky se objeví v následujících umístěních:  
  
-   Informace o parametru technologie IntelliSense. Další informace najdete v tématu [pomocí technologie IntelliSense](/visualstudio/ide/using-intellisense).  
  
-   Prohlížeč objektů. Další informace najdete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `<param>` značka, které popisují `id` parametru.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
