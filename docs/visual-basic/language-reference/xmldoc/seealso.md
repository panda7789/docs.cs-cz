---
title: '&lt;Viz také&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 8a7b663368cab917cbabfc5ca089b266c47c5ee8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662371"
---
# <a name="ltseealsogt-visual-basic"></a>&lt;Viz také&gt; (Visual Basic)
Určuje odkaz, který se zobrazí v části Viz také.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a>Parametry  
 `member`  
 Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor kontroluje, zda daný prvek kódu existuje a předá `member` do názvu prvku ve výstupním souboru XML. `member` musí být uvedena v uvozovkách ("").  
  
## <a name="remarks"></a>Poznámky  
 Použití `<seealso>` značka, které určuje text, který se má zobrazit v části Viz také. Použití [ \<naleznete v tématu >](../../../visual-basic/language-reference/xmldoc/see.md) zadat odkaz v rámci textu.  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `<seealso>` značku `DoesRecordExist` poznámky část neodkazuje na `UpdateRecord` metoda.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/seealso_1.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
