---
title: '&lt;paramref&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- paramref XML tag
- <paramref> XML tag
ms.assetid: 8979d53b-beb1-41b7-b41e-6bbea1c17a03
ms.openlocfilehash: 153f5ddeeb7d09159049af4d466b0695f5cb6f23
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43393442"
---
# <a name="ltparamrefgt-visual-basic"></a>&lt;paramref&gt; (Visual Basic)
Formátuje slova jako parametr.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<paramref name="name"/>  
```  
  
#### <a name="parameters"></a>Parametry  
 `name`  
 Název parametru jako reference. Název uzavřete do dvojitých uvozovek ("").  
  
## <a name="remarks"></a>Poznámky  
 `<paramref>` Značky poskytuje způsob, jak určit, že je slovo parametru. Soubor XML mohou být zpracovány k nějakým způsobem odlišné formátování tento parametr.  
  
 Kompilovat s [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) pro zpracování dokumentačních komentářů do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<paramref>` značku k odkazování `id` parametr.  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/paramref_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
