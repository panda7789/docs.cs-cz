---
title: <c> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 5f07b9cc084c73a7dcaf8c4d5f631519e550781e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56979481"
---
# <a name="c-visual-basic"></a>\<c > (Visual Basic)
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
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Viz také:
- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
