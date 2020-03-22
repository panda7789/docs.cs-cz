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
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a><span data-ttu-id="f5909-102">Analýza textových souborů s objektem TextFieldParser (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5909-102">Parsing text files with the TextFieldParser object (Visual Basic)</span></span>

<span data-ttu-id="f5909-103">Objekt `TextFieldParser` umožňuje analyzovat a zpracovávat velmi velký soubor, které jsou strukturovány jako sloupce s omezenou šířkou textu, jako jsou například soubory protokolu nebo starší informace o databázi.</span><span class="sxs-lookup"><span data-stu-id="f5909-103">The `TextFieldParser` object allows you to parse and process very large file that are structured as delimited-width columns of text, such as log files or legacy database information.</span></span> <span data-ttu-id="f5909-104">Analýza textového souboru `TextFieldParser` s je podobná iterace přes textový soubor, zatímco metoda analýzy extrahovat pole textu je podobná metody manipulace s řetězci používané k tokenizaci oddělených řetězců.</span><span class="sxs-lookup"><span data-stu-id="f5909-104">Parsing a text file with `TextFieldParser` is similar to iterating over a text file, while the parse method to extract fields of text is similar to string manipulation methods used to tokenize delimited strings.</span></span>  
  
## <a name="parsing-different-types-of-text-files"></a><span data-ttu-id="f5909-105">Analýza různých typů textových souborů</span><span class="sxs-lookup"><span data-stu-id="f5909-105">Parsing different types of text files</span></span>  

 <span data-ttu-id="f5909-106">Textové soubory mohou mít pole různé šířky, ohraničené znakem, například čárkou nebo mezerou na tabulátorech.</span><span class="sxs-lookup"><span data-stu-id="f5909-106">Text files may have fields of various width, delimited by a character such as a comma or a tab space.</span></span> <span data-ttu-id="f5909-107">Definujte `TextFieldType` a oddělovač, jako v následujícím `SetDelimiters` příkladu, který používá metodu k definování textového souboru odděleného tabulátorem:</span><span class="sxs-lookup"><span data-stu-id="f5909-107">Define `TextFieldType` and the delimiter, as in the following example, which uses the `SetDelimiters` method to define a tab-delimited text file:</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#21)]  
  
 <span data-ttu-id="f5909-108">Ostatní textové soubory mohou mít pevné šířky polí.</span><span class="sxs-lookup"><span data-stu-id="f5909-108">Other text files may have field widths that are fixed.</span></span> <span data-ttu-id="f5909-109">V takových případech je třeba `TextFieldType` `FixedWidth` definovat as a definovat šířky každého pole, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f5909-109">In such cases, you need to define the `TextFieldType` as `FixedWidth` and define the widths of each field, as in the following example.</span></span> <span data-ttu-id="f5909-110">Tento příklad `SetFieldWidths` používá metodu k definování sloupců textu: první sloupec je široký 5 znaků, druhý je 10, třetí je 11 a čtvrtý má proměnnou šířku.</span><span class="sxs-lookup"><span data-stu-id="f5909-110">This example uses the `SetFieldWidths` method to define the columns of text: the first column is 5 characters wide, the second is 10, the third is 11, and the fourth is of variable width.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#22)]  
  
 <span data-ttu-id="f5909-111">Jakmile je formát definován, můžete procházet soubor, pomocí `ReadFields` metody ke zpracování každého řádku v pořadí.</span><span class="sxs-lookup"><span data-stu-id="f5909-111">Once the format is defined, you can loop through the file, using the `ReadFields` method to process each line in turn.</span></span>  
  
 <span data-ttu-id="f5909-112">Pokud pole neodpovídá zadanému formátu, je vyvolána <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> výjimka.</span><span class="sxs-lookup"><span data-stu-id="f5909-112">If a field does not match the specified format, a <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> exception is thrown.</span></span> <span data-ttu-id="f5909-113">Při vyvolání těchto výjimek `ErrorLine` `ErrorLineNumber` vlastnosti a obsahovat text způsobuje výjimku a číslo řádku tohoto textu.</span><span class="sxs-lookup"><span data-stu-id="f5909-113">When such exceptions are thrown, the `ErrorLine` and `ErrorLineNumber` properties hold the text causing the exception and the line number of that text.</span></span>  
  
## <a name="parsing-files-with-multiple-formats"></a><span data-ttu-id="f5909-114">Analýza souborů s více formáty</span><span class="sxs-lookup"><span data-stu-id="f5909-114">Parsing files with multiple formats</span></span>  

 <span data-ttu-id="f5909-115">Metodu `PeekChars` objektu `TextFieldParser` lze použít ke kontrole každého pole před jeho přečtením, což umožňuje definovat více formátů polí a odpovídajícím způsobem reagovat.</span><span class="sxs-lookup"><span data-stu-id="f5909-115">The `PeekChars` method of the `TextFieldParser` object can be used to check each field before reading it, allowing you to define multiple formats for the fields and react accordingly.</span></span> <span data-ttu-id="f5909-116">Další informace naleznete v [tématu How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span><span class="sxs-lookup"><span data-stu-id="f5909-116">For more information, see [How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5909-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5909-117">See also</span></span>

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
