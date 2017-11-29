---
title: '&lt;Souhrn&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2a3008d1393c44aa0ec2398a2bd6afa079013e7e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltsummarygt-visual-basic"></a>&lt;Souhrn&gt; (Visual Basic)
Určuje souhrn člena.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a>Parametry  
 `description`  
 Souhrn objektu.  
  
## <a name="remarks"></a>Poznámky  
 Použití `<summary>` značka, které popisují typ nebo člen typu. Použití [ \<Poznámky >](../../../visual-basic/language-reference/xmldoc/remarks.md) přidat další informace o popis typu.  
  
 Text pro `<summary>` značky je jediný zdroj informací o typu v IntelliSense a zobrazuje se v prohlížeči objektů. Informace o prohlížeči objektů najdete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<summary>` značka, které popisují `ResetCounter` metoda a `Counter` vlastnost.  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
