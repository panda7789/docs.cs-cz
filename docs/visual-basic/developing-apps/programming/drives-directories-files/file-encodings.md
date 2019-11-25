---
title: Kódování souborů
ms.date: 07/20/2015
helpviewer_keywords:
- character encodings
- files [Visual Basic], encoding
- Unicode, file encoding
- file encoding
ms.assetid: ea2c5f5f-bbb1-4150-9928-b9951fa6bc57
ms.openlocfilehash: 52770187568d0ba0f54ec36ee2c3d754a9b4d9a8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348882"
---
# <a name="file-encodings-visual-basic"></a>Kódování souborů (Visual Basic)

File encodings, also known as character encodings, specify how to represent characters when text processing. One encoding may be preferable over another in terms of which language characters it can or cannot handle, although Unicode is usually preferred.

When reading from or writing to files, improperly matching file encodings may result in exceptions or incorrect results.

## <a name="types-of-encodings"></a>Types of Encodings

Unicode is the preferred encoding when working with files. Unicode is a worldwide character-encoding standard that uses 16-bit code values to represent all the characters used in modern computing, including technical symbols and special characters used in publishing.

Previous character-encoding standards consisted of traditional character sets, such as the Windows ANSI character set that uses 8-bit code values, or combinations of 8-bit values, to represent the characters used in a specific language or geographical region.

## <a name="encoding-class"></a>Encoding Class

The <xref:System.Text.Encoding> class represents a character encoding. This table lists the type of encodings available and describes each.

|Name|Popis|
|---|---|
|<xref:System.Text.ASCIIEncoding>|Represents an ASCII character encoding of Unicode characters.|
|<xref:System.Text.UnicodeEncoding>|Represents a UTF-16 encoding of Unicode characters.|
|<xref:System.Text.UTF32Encoding>|Represents a UTF-32 encoding of Unicode characters.|
|<xref:System.Text.UTF7Encoding>|Represents a UTF-7 encoding of Unicode characters.|
|<xref:System.Text.UTF8Encoding>|Represents a UTF-8 encoding of Unicode characters.|

## <a name="see-also"></a>Viz také:

- [Čtení ze souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [Zápis do souborů](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
