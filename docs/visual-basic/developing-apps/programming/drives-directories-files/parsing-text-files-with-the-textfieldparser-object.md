---
title: Analýza textových souborů pomocí objektu TextFieldParser
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
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a>Analýza textových souborů pomocí objektu TextFieldParser (Visual Basic)

`TextFieldParser` Objekt umožňuje analyzovat a zpracovat velmi velký soubor, který je strukturovaný jako sloupec s oddělovači, například soubory protokolu nebo starší informace databáze. Analýza textového souboru pomocí `TextFieldParser` je podobná iteraci přes textový soubor, zatímco metoda Parse pro extrakci polí textu je podobná metodám manipulace s řetězci, které slouží k tokenizovat řetězců s oddělovači.  
  
## <a name="parsing-different-types-of-text-files"></a>Analýza různých typů textových souborů  

 Textové soubory mohou obsahovat pole s různou šířkou, oddělené znakem, jako je čárka nebo mezera tabulátoru. Definujte `TextFieldType` a oddělovač, jak je uvedeno v následujícím příkladu, který používá `SetDelimiters` metodu k definování textového souboru s oddělovači tabulátoru:  
  
 [!code-vb[VbVbalrTextFieldParser#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#21)]  
  
 Jiné textové soubory mohou mít pevné šířky polí. V takových případech je nutné definovat `TextFieldType` jako `FixedWidth` a definovat šířku každého pole, jak je uvedeno v následujícím příkladu. V tomto příkladu se `SetFieldWidths` používá metoda k definování sloupců textu: první sloupec má šířku 5 znaků, druhá je 10, třetí je 11 a čtvrtá je proměnná šířka.  
  
 [!code-vb[VbVbalrTextFieldParser#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#22)]  
  
 Po definování formátu můžete projít soubor pomocí `ReadFields` metody pro zpracování každého řádku.  
  
 Pokud se pole neshoduje se zadaným formátem, <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> je vyvolána výjimka. Pokud jsou takové výjimky vyvolány `ErrorLine` , `ErrorLineNumber` vlastnosti a uchovávají text, který způsobuje výjimku, a číslo řádku tohoto textu.  
  
## <a name="parsing-files-with-multiple-formats"></a>Analýza souborů s více formáty  

 `PeekChars` Metodu `TextFieldParser` objektu lze použít ke kontrole každého pole před jeho čtením, což vám umožní definovat více formátů pro pole a odpovídajícím způsobem reagovat. Další informace najdete v tématu [Postupy: čtení z textových souborů s více formáty](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).  
  
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
