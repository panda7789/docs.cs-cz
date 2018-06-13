---
title: '&lt;v tématu&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: e790f8abd216e198ff5077beab6f857e39981d2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602077"
---
# <a name="ltseegt-visual-basic"></a>&lt;v tématu&gt; (Visual Basic)
Určuje odkaz na druhý člen.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a>Parametry  
 `member`  
 Odkaz na člena nebo na pole, které lze volat z prostředí aktuální kompilace. Kompilátor ověří, že element daného kódu existuje a předá `member` k názvu elementu ve výstupu XML. `member` musí být v rámci dvojitých uvozovek nahoře ("").  
  
## <a name="remarks"></a>Poznámky  
 Použití `<see>` značku zadejte odkaz z v textu. Použití [ \<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) označíte, text, který chcete zobrazit v části "V části Viz také".  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<see>` značky v `UpdateRecord` remarks části k odkazování na `DoesRecordExist` metoda.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/see_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
