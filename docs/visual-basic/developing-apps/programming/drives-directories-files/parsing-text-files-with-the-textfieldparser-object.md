---
title: Analýza textových souborů pomocí objektu TextFieldParser (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files [Visual Basic], parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
ms.openlocfilehash: 09821e9b1985913b7433b070ae19c4818265926e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585393"
---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a>Analýza textových souborů pomocí objektu TextFieldParser (Visual Basic)
`TextFieldParser` Objekt umožňuje analyzovat a zpracovat velké soubory, které jsou strukturované jako sloupce textu, například soubory protokolu nebo informace o starší databázi. Analýza kódu textový soubor s `TextFieldParser` je podobný iterace textového souboru s metodu parse k extrahování textových polí je podobná řetězec metodám určený k tokenizaci řetězce s oddělovači.  
  
## <a name="parsing-different-types-of-text-files"></a>Analýza kódu různé typy textových souborů  
 Textové soubory mohou mít různou šířku oddělené znakem, jako je čárka nebo tabulátorem. Definování `TextFieldType` a oddělovače, jako v následujícím příkladu, který používá `SetDelimiters` metoda k definování oddělený tabulátory textového souboru:  
  
 [!code-vb[VbVbalrTextFieldParser#21](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_1.vb)]  
  
 Jiné textové soubory mohou mít určenými šířkami polí, které jsou opraveny. V takovém případě budete muset definovat `TextFieldType` jako `FixedWidth` a definovat šířku každého pole, jako v následujícím příkladu. V tomto příkladu `SetFieldWidths` metoda k definování textových sloupců: první sloupec je 5 znaků široký, druhá je 10, třetí je 11, a čtvrtý proměnné šířky.  
  
 [!code-vb[VbVbalrTextFieldParser#22](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_2.vb)]  
  
 Po definování formátu můžete projít soubor, použití `ReadFields` metoda zase zpracovávat každý řádek.  
  
 Pokud pole zadaný formát neodpovídá <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> je vyvolána výjimka. Pokud takové výjimky jsou vyvolány, `ErrorLine` a `ErrorLineNumber` vlastnosti obsahovat text, který způsobuje výjimku a číslo řádku textu.  
  
## <a name="parsing-files-with-multiple-formats"></a>Analýza souborů ve více formátech  
 `PeekChars` Metodu `TextFieldParser` objekt lze použít ke kontrole jednotlivých polí před čtením, abyste mohli definovat více formátů pro pole a reagují odpovídajícím způsobem. Další informace najdete v tématu [jak: Čtení z textových souborů ve více formátech](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).  
  
## <a name="see-also"></a>Viz také:
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
