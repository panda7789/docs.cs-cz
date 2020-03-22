---
title: Analýza textových souborů s objektem TextFieldParser
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files [Visual Basic], parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
ms.openlocfilehash: f3239184beb58312a8e3598545fc37423ff85287
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74333849"
---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a>Analýza textových souborů s objektem TextFieldParser (Visual Basic)

Objekt `TextFieldParser` umožňuje analyzovat a zpracovávat velmi velký soubor, které jsou strukturovány jako sloupce s omezenou šířkou textu, jako jsou například soubory protokolu nebo starší informace o databázi. Analýza textového souboru `TextFieldParser` s je podobná iterace přes textový soubor, zatímco metoda analýzy extrahovat pole textu je podobná metody manipulace s řetězci používané k tokenizaci oddělených řetězců.  
  
## <a name="parsing-different-types-of-text-files"></a>Analýza různých typů textových souborů  

 Textové soubory mohou mít pole různé šířky, ohraničené znakem, například čárkou nebo mezerou na tabulátorech. Definujte `TextFieldType` a oddělovač, jako v následujícím `SetDelimiters` příkladu, který používá metodu k definování textového souboru odděleného tabulátorem:  
  
 [!code-vb[VbVbalrTextFieldParser#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#21)]  
  
 Ostatní textové soubory mohou mít pevné šířky polí. V takových případech je třeba `TextFieldType` `FixedWidth` definovat as a definovat šířky každého pole, jako v následujícím příkladu. Tento příklad `SetFieldWidths` používá metodu k definování sloupců textu: první sloupec je široký 5 znaků, druhý je 10, třetí je 11 a čtvrtý má proměnnou šířku.  
  
 [!code-vb[VbVbalrTextFieldParser#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#22)]  
  
 Jakmile je formát definován, můžete procházet soubor, pomocí `ReadFields` metody ke zpracování každého řádku v pořadí.  
  
 Pokud pole neodpovídá zadanému formátu, je vyvolána <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> výjimka. Při vyvolání těchto výjimek `ErrorLine` `ErrorLineNumber` vlastnosti a obsahovat text způsobuje výjimku a číslo řádku tohoto textu.  
  
## <a name="parsing-files-with-multiple-formats"></a>Analýza souborů s více formáty  

 Metodu `PeekChars` objektu `TextFieldParser` lze použít ke kontrole každého pole před jeho přečtením, což umožňuje definovat více formátů polí a odpovídajícím způsobem reagovat. Další informace naleznete v [tématu How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFieldParser%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ReadFields%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLineNumber%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.HasFieldsEnclosedInQuotes%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.LineNumber%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TrimWhiteSpace%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A>
