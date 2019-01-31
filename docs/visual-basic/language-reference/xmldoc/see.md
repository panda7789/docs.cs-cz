---
title: <see> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 9faf1ec7211493b8c0058439e9a6e3bcb293ea99
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55289520"
---
# <a name="see-visual-basic"></a>\<Zobrazit > (Visual Basic)
Uvádí odkaz na jiný člen.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a>Parametry  
 `member`  
 Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor kontroluje, zda daný prvek kódu existuje a předá `member` do názvu prvku ve výstupním souboru XML. `member` musí být uvedena v uvozovkách ("").  
  
## <a name="remarks"></a>Poznámky  
 Použití `<see>` značka zadat odkaz v rámci textu. Použití [ \<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) označuje text, který chcete zobrazit v části "V části Viz také".  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `<see>` značku `UpdateRecord` poznámky část neodkazuje na `DoesRecordExist` metoda.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/see_1.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
