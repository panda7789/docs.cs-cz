---
title: "Analýza textových souborů pomocí objektu TextFieldParser (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files [Visual Basic], parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 544b65a5197f6a1b68a54f12dbdc0c591bc512e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a>Analýza textových souborů pomocí objektu TextFieldParser (Visual Basic)
`TextFieldParser` Objektu umožňuje analyzovat a zpracovat velmi velké soubory, které mají strukturu sloupce textu, například soubory protokolu nebo informace o starší databázi. Analýza textový soubor s `TextFieldParser` je podobná procházení textového souboru, metoda extrahovat textových polí je podobná metodám určený k tokenizaci řetězce s oddělovači.  
  
## <a name="parsing-different-types-of-text-files"></a>Analýza různé typy textových souborů  
 Textové soubory, může mít různou šířku, oddělená znakem například čárkou nebo tabulátorem. Definování `TextFieldType` a oddělovače, jako v následujícím příkladu, který používá `SetDelimiters` metoda k definování souboru text oddělený tabulátory:  
  
 [!code-vb[VbVbalrTextFieldParser#21](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_1.vb)]  
  
 Další textové soubory mohou mít šířku polí, které jsou vyřešeny. V takových případech je třeba definovat `TextFieldType` jako `FixedWidth` a určit šířku každého pole, jako v následujícím příkladu. Tento příklad používá `SetFieldWidths` metoda k definování sloupců textu: první sloupec je 5 znaků široký, druhý je 10, 11 je třetí a čtvrtý je proměnné šířky.  
  
 [!code-vb[VbVbalrTextFieldParser#22](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_2.vb)]  
  
 Po definování formátu můžete projít soubor, pomocí `ReadFields` metoda zase zpracovávat každý řádek.  
  
 Pokud pole neodpovídá zadaném formátu, <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> je vyvolána výjimka. Pokud je vyvolána, `ErrorLine` a `ErrorLineNumber` vlastnosti obsahovat text, který způsobuje výjimku a číslo řádku textu.  
  
## <a name="parsing-files-with-multiple-formats"></a>Analýza souborů ve více formátech  
 `PeekChars` Metodu `TextFieldParser` objekt lze použít ke kontrole každého pole před, čtení, který vám umožní definovat více formátů pro pole a odpovídajícím způsobem reagovat. Další informace najdete v tématu [postupy: čtení z textových souborů s více formátů](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFieldParser%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ReadFields%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.CommentTokens%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.Delimiters%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLineNumber%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.FieldWidths%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.HasFieldsEnclosedInQuotes%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.LineNumber%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TrimWhiteSpace%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetDelimiters%2A>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.SetFieldWidths%2A>
