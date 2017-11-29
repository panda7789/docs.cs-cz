---
title: "&lt;výjimka&gt; (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8d718a7c2213a61f7f60ed80a04f9bd03f6c770a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltexceptiongt-visual-basic"></a>&lt;výjimka&gt; (Visual Basic)
Určuje, výjimek, které může být vyvolána.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a>Parametry  
 `member`  
 Odkaz na výjimku, která je k dispozici z aktuální prostředí kompilace. Kompilátor kontroluje, zda výjimka existuje a překládá `member` na element kanonický název ve výstupu XML. `member`musí být v rámci dvojitých uvozovek nahoře ("").  
  
 `description`  
 Popis.  
  
## <a name="remarks"></a>Poznámky  
 Použití `<exception>` značky k určení výjimek, které může být vyvolána. Tato značka se použije k definici metody.  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<exception>` značka, které popisují výjimku, `IntDivide` funkce můžete vyvolat.  
  
 [!code-vb[VbVbcnXmlDocComments#3](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/exception_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
