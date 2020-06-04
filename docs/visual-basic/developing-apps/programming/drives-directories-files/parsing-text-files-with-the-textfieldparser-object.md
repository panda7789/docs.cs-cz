---
title: Analýza textových souborů pomocí objektu TextFieldParser
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files [Visual Basic], parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
ms.openlocfilehash: 7b2cb0dd39d14dd94db661cc9cbacf99edf0e778
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406674"
---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a><span data-ttu-id="ce9e0-102">Analýza textových souborů pomocí objektu TextFieldParser (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ce9e0-102">Parsing text files with the TextFieldParser object (Visual Basic)</span></span>

<span data-ttu-id="ce9e0-103">`TextFieldParser`Objekt umožňuje analyzovat a zpracovat velmi velký soubor, který je strukturovaný jako sloupec s oddělovači, například soubory protokolu nebo starší informace databáze.</span><span class="sxs-lookup"><span data-stu-id="ce9e0-103">The `TextFieldParser` object allows you to parse and process very large file that are structured as delimited-width columns of text, such as log files or legacy database information.</span></span> <span data-ttu-id="ce9e0-104">Analýza textového souboru pomocí `TextFieldParser` je podobná iteraci přes textový soubor, zatímco metoda Parse pro extrakci polí textu je podobná metodám manipulace s řetězci, které slouží k tokenizovat řetězců s oddělovači.</span><span class="sxs-lookup"><span data-stu-id="ce9e0-104">Parsing a text file with `TextFieldParser` is similar to iterating over a text file, while the parse method to extract fields of text is similar to string manipulation methods used to tokenize delimited strings.</span></span>  
  
## <a name="parsing-different-types-of-text-files"></a><span data-ttu-id="ce9e0-105">Analýza různých typů textových souborů</span><span class="sxs-lookup"><span data-stu-id="ce9e0-105">Parsing different types of text files</span></span>  

 <span data-ttu-id="ce9e0-106">Textové soubory mohou obsahovat pole s různou šířkou, oddělené znakem, jako je čárka nebo mezera tabulátoru.</span><span class="sxs-lookup"><span data-stu-id="ce9e0-106">Text files may have fields of various width, delimited by a character such as a comma or a tab space.</span></span> <span data-ttu-id="ce9e0-107">Definujte `TextFieldType` a oddělovač, jak je uvedeno v následujícím příkladu, který používá `SetDelimiters` metodu k definování textového souboru s oddělovači tabulátoru:</span><span class="sxs-lookup"><span data-stu-id="ce9e0-107">Define `TextFieldType` and the delimiter, as in the following example, which uses the `SetDelimiters` method to define a tab-delimited text file:</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#21)]  
  
 <span data-ttu-id="ce9e0-108">Jiné textové soubory mohou mít pevné šířky polí.</span><span class="sxs-lookup"><span data-stu-id="ce9e0-108">Other text files may have field widths that are fixed.</span></span> <span data-ttu-id="ce9e0-109">V takových případech je nutné definovat `TextFieldType` jako `FixedWidth` a definovat šířku každého pole, jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="ce9e0-109">In such cases, you need to define the `TextFieldType` as `FixedWidth` and define the widths of each field, as in the following example.</span></span> <span data-ttu-id="ce9e0-110">V tomto příkladu se používá `SetFieldWidths` Metoda k definování sloupců textu: první sloupec má šířku 5 znaků, druhá je 10, třetí je 11 a čtvrtá je proměnná šířka.</span><span class="sxs-lookup"><span data-stu-id="ce9e0-110">This example uses the `SetFieldWidths` method to define the columns of text: the first column is 5 characters wide, the second is 10, the third is 11, and the fourth is of variable width.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#22)]  
  
 <span data-ttu-id="ce9e0-111">Po definování formátu můžete projít soubor pomocí `ReadFields` metody pro zpracování každého řádku.</span><span class="sxs-lookup"><span data-stu-id="ce9e0-111">Once the format is defined, you can loop through the file, using the `ReadFields` method to process each line in turn.</span></span>  
  
 <span data-ttu-id="ce9e0-112">Pokud se pole neshoduje se zadaným formátem, <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="ce9e0-112">If a field does not match the specified format, a <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> exception is thrown.</span></span> <span data-ttu-id="ce9e0-113">Pokud jsou takové výjimky vyvolány `ErrorLine` , `ErrorLineNumber` vlastnosti a uchovávají text, který způsobuje výjimku, a číslo řádku tohoto textu.</span><span class="sxs-lookup"><span data-stu-id="ce9e0-113">When such exceptions are thrown, the `ErrorLine` and `ErrorLineNumber` properties hold the text causing the exception and the line number of that text.</span></span>  
  
## <a name="parsing-files-with-multiple-formats"></a><span data-ttu-id="ce9e0-114">Analýza souborů s více formáty</span><span class="sxs-lookup"><span data-stu-id="ce9e0-114">Parsing files with multiple formats</span></span>  

 <span data-ttu-id="ce9e0-115">`PeekChars`Metodu `TextFieldParser` objektu lze použít ke kontrole každého pole před jeho čtením, což vám umožní definovat více formátů pro pole a odpovídajícím způsobem reagovat.</span><span class="sxs-lookup"><span data-stu-id="ce9e0-115">The `PeekChars` method of the `TextFieldParser` object can be used to check each field before reading it, allowing you to define multiple formats for the fields and react accordingly.</span></span> <span data-ttu-id="ce9e0-116">Další informace najdete v tématu [Postupy: čtení z textových souborů s více formáty](how-to-read-from-text-files-with-multiple-formats.md).</span><span class="sxs-lookup"><span data-stu-id="ce9e0-116">For more information, see [How to: Read From Text Files with Multiple Formats](how-to-read-from-text-files-with-multiple-formats.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce9e0-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="ce9e0-117">See also</span></span>

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
