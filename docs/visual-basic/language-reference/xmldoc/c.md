---
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: c8ba03d9cc01c4751d15c01530c6cbf7d499dc3b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400160"
---
# <a name="c-visual-basic"></a>\<c> (Visual Basic)
Označuje, že text v rámci popisu je kód.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a>Parametry  
  
|Parametr|Popis|  
|---|---|  
|`text`|Text, který chcete označit jako kód.|  
  
## <a name="remarks"></a>Poznámky  
 `<c>`Značka poskytuje způsob, jak označit, že text v rámci popisu by měl být označen jako kód. Slouží [\<code>](code.md) k označení více řádků jako kódu.  
  
 Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<c>` značku v části Summary k označení, že `Counter` se jedná o kód.  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Značky pro komentáře XML](index.md)
