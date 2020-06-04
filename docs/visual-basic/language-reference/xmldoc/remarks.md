---
title: <remarks>
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: c57ddb870192bd94301f99eb71ad29526e8efc28
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400018"
---
# <a name="remarks-visual-basic"></a>\<remarks> (Visual Basic)
Určuje oddíl poznámky pro člena.  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a>Parametry  
 `description`  
 Popis člena  
  
## <a name="remarks"></a>Poznámky  
 Pomocí `<remarks>` značky můžete přidat informace o typu a doplnit informace zadané pomocí [\<summary>](summary.md) .  
  
 Tyto informace se zobrazí v Prohlížeč objektů. Informace o Prohlížeč objektů naleznete v tématu [zobrazení struktury kódu](/visualstudio/ide/viewing-the-structure-of-code).  
  
 Zkompilujte s [-doc](../../reference/command-line-compiler/doc.md) a zpracujte komentáře k dokumentaci do souboru.  
  
## <a name="example"></a>Příklad  
 Tento příklad používá `<remarks>` značku k vysvětlení, co `UpdateRecord` metoda dělá.  
  
 [!code-vb[VbVbcnXmlDocComments#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#6)]  
  
## <a name="see-also"></a>Viz také

- [Značky pro komentáře XML](index.md)
