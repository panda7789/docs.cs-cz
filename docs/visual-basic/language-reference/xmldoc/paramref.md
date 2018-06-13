---
title: '&lt;paramref&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 763e311dfb46ceeed358c3b3bebd6212d3e2489c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33598659"
---
# <a name="ltparamrefgt-visual-basic"></a>&lt;paramref&gt; (Visual Basic)
Formátuje slovo jako parametr.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Název parametru, který bude odkazovat na. Uzavřete název do dvojitých uvozovek nahoře ("").  
  
## <a name="remarks"></a>Poznámky  
 `<paramref>` Značky poskytuje způsob, jak znamenat, že slovo parametr. Soubor XML lze zpracovat formátování tento parametr nějakým způsobem distinct.  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<paramref>` značky k odkazování na `id` parametr.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
