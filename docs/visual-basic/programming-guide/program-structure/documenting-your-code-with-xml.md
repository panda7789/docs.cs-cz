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

In Visual Basic, you can document your code using XML

## <a name="xml-documentation-comments"></a>Dokumentační komentáře XML

Visual Basic provides an easy way to automatically create XML documentation for projects. You can automatically generate an XML skeleton for your types and members, and then provide summaries, descriptive documentation for each parameter, and other remarks. With the appropriate setup, the XML documentation is automatically emitted into an XML file with the same name as your project and the .xml extension. For more information, see [-doc](../../../visual-basic/reference/command-line-compiler/doc.md).

The XML file can be consumed or otherwise manipulated as XML. This file is located in the same directory as the output .exe or .dll file of your project.

XML documentation starts with `'''`. The processing of these comments has some restrictions:

- The documentation must be well-formed XML. If the XML is not well formed, a warning is generated and the documentation file contains a comment saying that an error was encountered.

- Developers are free to create their own set of tags. There is a recommended set of tags (see "Related Sections" in this topic). Some of the recommended tags have special meanings:

  - The \<param> tag is used to describe parameters. If used, the compiler will verify that the parameter exists and that all parameters are described in the documentation. If the verification fails, the compiler issues a warning.

  - The `cref` attribute can be attached to any tag to provide a reference to a code element. The compiler verifies that this code element exists. If the verification fails, the compiler issues a warning. The compiler also respects any `Imports` statements when looking for a type described in the `cref` attribute.

  - The \<summary> tag is used by IntelliSense in Visual Studio to display additional information about a type or member.

## <a name="related-sections"></a>Související oddíly

For details on creating an XML file with documentation comments, see the following topics:

- [-doc](../../../visual-basic/reference/command-line-compiler/doc.md)

- [Značky pro komentáře XML](../../../visual-basic/language-reference/xmldoc/index.md)

- [Zpracování souboru XML](../../../visual-basic/programming-guide/program-structure/processing-the-xml-file.md)

- [Postupy: Vytvoření dokumentace XML](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)

- [Nástroje XML v sadě Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)

## <a name="see-also"></a>Viz také:

- [Developing Applications with Visual Basic](../../../visual-basic/developing-apps/index.md)
- [Visual Basic Programming Guide](../../../visual-basic/programming-guide/index.md)
