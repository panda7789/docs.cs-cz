---
title: 'Postupy: Vytvoření dokumentace XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 41b7ef1f435fd0a4f20c4ca2936e2d91e155f7c5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347419"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>Postupy: Vytvoření dokumentace XML v jazyce Visual Basic

Tento příklad ukazuje, jak přidat dokumentační komentáře XML do kódu.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-xml-documentation-for-a-type-or-member"></a>Vytvoření dokumentace XML pro typ nebo člen

1. V **editoru kódu**umístěte kurzor na řádek nad typ nebo člen, pro který chcete vytvořit dokumentaci.

2. Zadejte `'''` (tři jednoduché uvozovky).

    V **editoru kódu**se přidá kostra XML pro daný typ nebo člen.

3. Přidejte popisné informace mezi příslušné značky.

    > [!NOTE]
    > Pokud přidáte další řádky do bloku dokumentace XML, musí každý řádek začínat `'''`.

4. Přidejte další kód, který používá typ nebo člen s novými dokumentačními komentáři XML.

    IntelliSense zobrazí text z > Značka \<souhrnu pro daný typ nebo člen.

5. Zkompilujte kód pro vygenerování souboru XML obsahujícího dokumentační komentáře. Další informace najdete v [dokumentu-doc](../../../visual-basic/reference/command-line-compiler/doc.md).

## <a name="see-also"></a>Viz také:

- [Dokumentace kódu s XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)
- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)
