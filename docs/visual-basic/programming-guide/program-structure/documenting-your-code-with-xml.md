---
title: Dokumentace kódu s XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: bdf0da7a8acc919e4a1d66b81e30c9ed912dd321
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347445"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a>Dokumentace kódu s XML (Visual Basic)

V Visual Basic můžete svůj kód zdokumentovat pomocí XML

## <a name="xml-documentation-comments"></a>Dokumentační komentáře XML

Visual Basic poskytuje snadný způsob, jak automaticky vytvořit dokumentaci XML pro projekty. Můžete automaticky vygenerovat kostru XML pro vaše typy a členy a pak poskytnout souhrny, popisnou dokumentaci pro každý parametr a další poznámky. S příslušným nastavením se dokumentace XML automaticky generuje do souboru XML se stejným názvem, jaký má váš projekt a příponu. XML. Další informace najdete v [dokumentu-doc](../../../visual-basic/reference/command-line-compiler/doc.md).

Soubor XML lze spotřebovat nebo jinak manipulovat jako XML. Tento soubor je umístěn ve stejném adresáři jako výstupní soubor. exe nebo. dll vašeho projektu.

Dokumentace XML začíná `'''`. Zpracování těchto komentářů má určitá omezení:

- Dokumentace musí být ve správném formátu XML. Pokud XML není ve správném formátu, je vygenerováno upozornění a soubor dokumentace obsahuje komentář, který říká, že došlo k chybě.

- Vývojářům je zdarma vytvořit vlastní sadu značek. Je doporučená sada značek (viz část související části v tomto tématu). Některé z doporučených značek mají zvláštní význam:

  - K popisu parametrů se používá značka \<param >. Pokud je použit, kompilátor ověří, zda existuje parametr a zda jsou všechny parametry popsány v dokumentaci. Pokud se ověření nepovede, kompilátor vydá upozornění.

  - Atribut `cref` lze připojit k libovolné značce k poskytnutí odkazu na prvek kódu. Kompilátor ověřuje, zda tento prvek kódu existuje. Pokud se ověření nepovede, kompilátor vydá upozornění. Kompilátor také respektuje jakékoli `Imports` příkazy při hledání typu popsaného v atributu `cref`.

  - Inteligentní > Značka \<je používána technologií IntelliSense v aplikaci Visual Studio k zobrazení dalších informací o typu nebo členu.

## <a name="related-sections"></a>Související oddíly

Podrobné informace o vytvoření souboru XML s dokumentačními komentáři naleznete v následujících tématech:

- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)

- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)

- [Zpracování souboru XML](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)

- [Postupy: Vytvoření dokumentace XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)

- [Nástroje XML v sadě Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a>Viz také:

- [Vývoj aplikací pomocí Visual Basic](../../../visual-basic/developing-apps/index.md)
- [Průvodce programováním Visual Basic](../../../visual-basic/programming-guide/index.md)
