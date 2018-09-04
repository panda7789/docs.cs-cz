---
title: '&lt;c&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 06c6899895f278fdf652725a05ecc7229805f4d4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43563869"
---
# <a name="ltcgt-visual-basic"></a>&lt;c&gt; (Visual Basic)
Označuje, že je text v rámci popis kódu.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---|---|  
|`text`|Text, který chcete označit jako kód.|  
  
## <a name="remarks"></a>Poznámky  
 `<c>` Značky poskytuje způsob, jak určit, že text v popisu musí být označené jako kód. Použití [ \<kód >](../../../visual-basic/language-reference/xmldoc/code.md) k označení jako kódu více řádků.  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `<c>` značky v souhrnné části, která označuje, že `Counter` je kód.  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/c_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
