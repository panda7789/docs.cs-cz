---
title: 'Postupy: Vytvoření dokumentace XML'
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments
- XML documentation [Visual Basic], creating
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
ms.openlocfilehash: 1421cc85beba42b3cf3656c34b1d02347fbaf164
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403236"
---
# <a name="how-to-create-xml-documentation-in-visual-basic"></a>Postupy: Vytvoření dokumentace XML v jazyce Visual Basic

Tento příklad ukazuje, jak přidat dokumentační komentáře XML do kódu.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-create-xml-documentation-for-a-type-or-member"></a>Vytvoření dokumentace XML pro typ nebo člen

1. V **editoru kódu**umístěte kurzor na řádek nad typ nebo člen, pro který chcete vytvořit dokumentaci.

2. Typ `'''` (tři jednoduché uvozovky).

    V **editoru kódu**se přidá kostra XML pro daný typ nebo člen.

3. Přidejte popisné informace mezi příslušné značky.

    > [!NOTE]
    > Pokud přidáte další řádky do bloku dokumentace XML, musí každý řádek začínat na `'''` .

4. Přidejte další kód, který používá typ nebo člen s novými dokumentačními komentáři XML.

    IntelliSense zobrazí text ze \<summary> značky pro daný typ nebo člen.

5. Zkompilujte kód pro vygenerování souboru XML obsahujícího dokumentační komentáře. Další informace najdete v [dokumentu-doc](../../reference/command-line-compiler/doc.md).

## <a name="see-also"></a>Viz také

- [Dokumentace kódu s XML](documenting-your-code-with-xml.md)
- [Značky pro komentáře XML](../../language-reference/xmldoc/index.md)
- [-doc](../../reference/command-line-compiler/doc.md)
