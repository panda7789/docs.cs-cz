---
title: <summary>
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 893ed299b46bd6255ca0e87d008ac53265698614
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411496"
---
# <a name="summary-visual-basic"></a>\<summary> (Visual Basic)
Určuje souhrn člena.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<summary>description</summary>  
```  
  
## <a name="parameters"></a>Parametry  
 `description`  
 Souhrn objektu.  
  
## <a name="remarks"></a>Poznámky  
 Použijte `<summary>` značku k popisu typu nebo člena typu. Slouží [\<remarks>](remarks.md) k přidání doplňujících informací k popisu typu.  
  
 Text `<summary>` značky je jediným zdrojem informací o typu v technologii IntelliSense a je také zobrazen v prohlížeč objektů. Informace o Prohlížeč objektů naleznete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<summary>` značku k popisu `ResetCounter` metody a `Counter` Vlastnosti.  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [Značky pro komentáře XML](index.md)
