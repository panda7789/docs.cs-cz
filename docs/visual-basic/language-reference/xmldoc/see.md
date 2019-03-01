---
title: <see> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: c0f1293fa0161a9a11b4e80301f5c4c4ddffe7b1
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969294"
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
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Viz také:
- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
