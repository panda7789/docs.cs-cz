---
title: '&lt;Souhrn&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 5ef9b7a98503ff36174de4418ca7d599c365f5aa
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43784579"
---
# <a name="ltsummarygt-visual-basic"></a>&lt;Souhrn&gt; (Visual Basic)
Určuje souhrn člena.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a>Parametry  
 `description`  
 Přehled objektu.  
  
## <a name="remarks"></a>Poznámky  
 Použití `<summary>` značka, které popisují typ nebo člen typu. Použití [ \<remarks >](../../../visual-basic/language-reference/xmldoc/remarks.md) přidat doplňující informace pro popis typu.  
  
 Text `<summary>` značka je jediný zdroj informací o typu v IntelliSense a také se zobrazí v prohlížeči objektů. Informace o prohlížeči objektů najdete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `<summary>` značka, které popisují `ResetCounter` metoda a `Counter` vlastnost.  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
