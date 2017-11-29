---
title: "&lt;Vrátí&gt; (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6130a6fabe450900fe19ef4d361654508f907ea
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="ltreturnsgt-visual-basic"></a>&lt;Vrátí&gt; (Visual Basic)
Určuje vrácenou hodnotu vlastnosti nebo funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a>Parametry  
 `description`  
 Popis návratovou hodnotu.  
  
## <a name="remarks"></a>Poznámky  
 Použití `<returns>` značku komentář pro deklaraci metody k popisu návratovou hodnotu.  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<returns>` značka, které popisují, co `DoesRecordExist` funkce vrátí.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/returns_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
