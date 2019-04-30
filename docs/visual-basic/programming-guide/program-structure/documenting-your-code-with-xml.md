---
title: Dokumentace kódu s XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: 6b9fe9994b7bdf2259dcdb1ecef906e0f9955c8f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61785499"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a>Dokumentace kódu s XML (Visual Basic)

V jazyce Visual Basic můžete dokumentaci kódu pomocí XML

## <a name="xml-documentation-comments"></a>Dokumentační komentáře XML

Visual Basic poskytuje snadný způsob, jak automaticky vytvořit dokumentaci XML pro projekty. Můžete automaticky generovat skeleton XML pro typy a členy a pak zadejte souhrny, popisný dokumentace pro každého parametru a další poznámky. S odpovídající instalační program je automaticky vygenerován dokumentace XML do souboru XML se stejným názvem jako váš projekt a příponu .xml. Další informace najdete v tématu [/doc](../../../visual-basic/reference/command-line-compiler/doc.md).

Soubor XML můžete využívat nebo jinak zpracovávají jako XML. Tento soubor je umístěn ve stejném adresáři jako soubor .exe nebo .dll výstup projektu.

Dokumentace XML začíná `'''`. Zpracování tyto poznámky platí některá omezení:

- V dokumentaci k musí být ve správném formátu XML. Pokud není správně vytvořený kód XML, je vygenerováno upozornění a soubor dokumentace obsahuje komentář informacemi o tom, že došlo k chybě.

- Vývojáři jsou zdarma vytvořit vlastní sadu značek. Je doporučená sada značky (viz "Související oddíly" v tomto tématu). Některé doporučené značky mají zvláštní význam:

  - \<Param > Značka se používá k popisu parametrů. Pokud použijete, kompilátor ověří, že parametr existuje a že všechny parametry jsou popsané v dokumentaci. Pokud se ověření nezdaří, kompilátor vyvolá upozornění.

  - `cref` Atribut lze připojit ke každé značce poskytnout odkaz na prvek kódu. Kompilátor ověří, zda tento prvek kódu existuje. Pokud se ověření nezdaří, kompilátor vyvolá upozornění. Kompilátor respektuje také některé `Imports` příkazy při hledání typu je popsáno v `cref` atribut.

  - \<Summary > Značka se používá technologie IntelliSense v sadě Visual Studio zobrazíte další informace o typu nebo členu.

## <a name="related-sections"></a>Související oddíly

Podrobné informace o vytváření souboru XML s komentáře k dokumentaci naleznete v následujících tématech:

- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)

- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)

- [Zpracování souboru XML](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)

- [Postupy: Vytvoření dokumentace XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)

- [Nástroje XML v sadě Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a>Viz také:

- [Vývoj aplikací v jazyce Visual Basic](../../../visual-basic/developing-apps/index.md)
- [Průvodce programováním v jazyce Visual Basic](../../../visual-basic/programming-guide/index.md)
