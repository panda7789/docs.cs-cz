---
title: <exception> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- <exception> XML tag
- exception XML tag
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
ms.openlocfilehash: 157287ce5c85ec51f1711934cf9a5e4f568957ef
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977175"
---
# <a name="exception-visual-basic"></a>\<exception> (Visual Basic)
Určuje, jaké výjimky mohou být vyvolány.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<exception cref="member">description</exception>  
```  
  
#### <a name="parameters"></a>Parametry  
 `member`  
 Odkaz na výjimku, která je k dispozici z prostředí aktuální kompilace. Kompilátor kontroluje, zda existuje výjimka a přeloží `member` k názvu canonical prvku ve výstupním souboru XML. `member` musí být uvedena v uvozovkách ("").  
  
 `description`  
 Popis.  
  
## <a name="remarks"></a>Poznámky  
 Použití `<exception>` značku k určení, jaké výjimky mohou být vyvolány. Tato značka se použije k definici metody.  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<exception>` značka, které popisují výjimku, která `IntDivide` funkce může vyvolat.  
  
 [!code-vb[VbVbcnXmlDocComments#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Viz také:
- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
