---
title: Dokumentace kódu s XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML [Visual Basic], documenting code
- XML comments, Visual Basic
- Visual Basic code, documenting with XML
ms.assetid: a0d35dc7-c5f9-4d74-92ff-a1c6f28d5235
ms.openlocfilehash: 324519248b90d4f61e67803a10b3cd6c566a2a04
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404859"
---
# <a name="documenting-your-code-with-xml-visual-basic"></a>Dokumentace kódu s XML (Visual Basic)

V Visual Basic můžete svůj kód zdokumentovat pomocí XML

## <a name="xml-documentation-comments"></a>Dokumentační komentáře XML

Visual Basic poskytuje snadný způsob, jak automaticky vytvořit dokumentaci XML pro projekty. Můžete automaticky vygenerovat kostru XML pro vaše typy a členy a pak poskytnout souhrny, popisnou dokumentaci pro každý parametr a další poznámky. S příslušným nastavením se dokumentace XML automaticky generuje do souboru XML se stejným názvem, jaký má váš projekt a příponu. XML. Další informace najdete v [dokumentu-doc](../../reference/command-line-compiler/doc.md).

Soubor XML lze spotřebovat nebo jinak manipulovat jako XML. Tento soubor je umístěn ve stejném adresáři jako výstupní soubor. exe nebo. dll vašeho projektu.

Dokumentace XML začíná na `'''` . Zpracování těchto komentářů má určitá omezení:

- Dokumentace musí být ve správném formátu XML. Pokud XML není ve správném formátu, je vygenerováno upozornění a soubor dokumentace obsahuje komentář, který říká, že došlo k chybě.

- Vývojářům je zdarma vytvořit vlastní sadu značek. Je doporučená sada značek (viz část související části v tomto tématu). Některé z doporučených značek mají zvláštní význam:

  - Tato \<param> značka se používá k popisu parametrů. Pokud je použit, kompilátor ověří, zda existuje parametr a zda jsou všechny parametry popsány v dokumentaci. Pokud se ověření nepovede, kompilátor vydá upozornění.

  - `cref`Atribut lze připojit k libovolné značce k poskytnutí odkazu na prvek kódu. Kompilátor ověřuje, zda tento prvek kódu existuje. Pokud se ověření nepovede, kompilátor vydá upozornění. Kompilátor také respektuje všechny `Imports` příkazy při hledání typu, který je popsán v `cref` atributu.

  - \<summary>Značka je používána technologií IntelliSense v aplikaci Visual Studio k zobrazení dalších informací o typu nebo členu.

## <a name="related-sections"></a>Související oddíly

Podrobné informace o vytvoření souboru XML s dokumentačními komentáři naleznete v následujících tématech:

- [-doc](../../reference/command-line-compiler/doc.md)

- [Značky pro komentáře XML](../../language-reference/xmldoc/index.md)

- [Zpracování souboru XML](processing-the-xml-file.md)

- [Postupy: Vytvoření dokumentace XML](how-to-create-xml-documentation.md)

- [Nástroje XML v aplikaci Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a>Viz také

- [Vývoj aplikací pomocí jazyka Visual Basic](../../developing-apps/index.md)
- [Příručka k programování v jazyce Visual Basic](../index.md)
