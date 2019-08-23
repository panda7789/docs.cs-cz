---
title: 'Postupy: Vytvoření dokumentace XML v Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 9380c23ab6cfdbecd519926229b45ed863f07f9e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947719"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>Postupy: Vytvoření dokumentace XML v Visual Basic
Tento příklad ukazuje, jak přidat dokumentační komentáře XML do kódu.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-xml-documentation-for-a-type-or-member"></a>Vytvoření dokumentace XML pro typ nebo člen  
  
1. V **editoru kódu**umístěte kurzor na řádek nad typ nebo člen, pro který chcete vytvořit dokumentaci.  
  
2. Typ `'''` (tři jednoduché uvozovky).  
  
     V **editoru kódu**se přidá kostra XML pro daný typ nebo člen.  
  
3. Přidejte popisné informace mezi příslušné značky.  
  
    > [!NOTE]
    > Pokud přidáte další řádky do bloku dokumentace XML, musí každý řádek začínat `'''`na.  
  
4. Přidejte další kód, který používá typ nebo člen s novými dokumentačními komentáři XML.  
  
     IntelliSense zobrazí text z \<značky Summary > pro daný typ nebo člen.  
  
5. Zkompilujte kód pro vygenerování souboru XML obsahujícího dokumentační komentáře. Další informace najdete v tématu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).  
  
## <a name="see-also"></a>Viz také:

- [Dokumentace kódu s XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
