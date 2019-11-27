---
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 3bc4393d2fa14f804c6383780e238b1ac2610a94
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352204"
---
# <a name="summary-visual-basic"></a>\<souhrn > (Visual Basic)
Určuje souhrn člena.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a>Parametry  
 `description`  
 Souhrn objektu.  
  
## <a name="remarks"></a>Poznámky  
 Použijte značku `<summary>` k popisu typu nebo člena typu. Pomocí [\<poznámky >](../../../visual-basic/language-reference/xmldoc/remarks.md) přidat doplňující informace k popisu typu.  
  
 Text značky `<summary>` je jediným zdrojem informací o typu v technologii IntelliSense a je také zobrazen v Prohlížeč objektů. Informace o Prohlížeč objektů naleznete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Zkompilujte s [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá značku `<summary>` k popisu metody `ResetCounter` a `Counter` vlastnosti.  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
