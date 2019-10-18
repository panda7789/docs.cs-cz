---
title: <example> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- example XML tag
- <example> XML tag
ms.assetid: 90eeda1c-3fc4-427c-879c-5046d265a97c
ms.openlocfilehash: 8f28dbf19bc03cb9d91323e9fa43a7081c1990db
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524015"
---
# <a name="example-visual-basic"></a>\<example > (Visual Basic)
Určuje příklad člena.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<example>description</example>  
```  
  
## <a name="parameters"></a>Parametry  
 `description`  
 Popis ukázky kódu.  
  
## <a name="remarks"></a>Poznámky  
 Značka `<example>` umožňuje zadat příklad použití metody nebo jiného člena knihovny. To běžně zahrnuje použití značky [\<code >](../../../visual-basic/language-reference/xmldoc/code.md) .  
  
 Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá značka `<example>` k zahrnutí příkladu pro použití pole `ID`.  
  
 [!code-vb[VbVbcnXmlDocComments#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
