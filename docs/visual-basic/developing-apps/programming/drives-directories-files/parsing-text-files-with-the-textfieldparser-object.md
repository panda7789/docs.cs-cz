---
title: Analýza textových souborů pomocí objektu TextFieldParser
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files [Visual Basic], parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
ms.openlocfilehash: f3239184beb58312a8e3598545fc37423ff85287
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333849"
---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a><span data-ttu-id="eab2e-102">Analýza textových souborů pomocí objektu TextFieldParser (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eab2e-102">Parsing text files with the TextFieldParser object (Visual Basic)</span></span>

<span data-ttu-id="eab2e-103">Objekt `TextFieldParser` umožňuje analyzovat a zpracovávat velmi velký soubor, který je strukturovaný jako sloupec textu s oddělovači, jako jsou například soubory protokolu nebo starší informace o databázi.</span><span class="sxs-lookup"><span data-stu-id="eab2e-103">The `TextFieldParser` object allows you to parse and process very large file that are structured as delimited-width columns of text, such as log files or legacy database information.</span></span> <span data-ttu-id="eab2e-104">Analýza textového souboru pomocí `TextFieldParser` je podobná iteraci přes textový soubor, zatímco metoda Parse pro extrakci polí textu je podobná metodám manipulace s řetězci, které slouží k tokenizovat řetězců s oddělovači.</span><span class="sxs-lookup"><span data-stu-id="eab2e-104">Parsing a text file with `TextFieldParser` is similar to iterating over a text file, while the parse method to extract fields of text is similar to string manipulation methods used to tokenize delimited strings.</span></span>  
  
## <a name="parsing-different-types-of-text-files"></a><span data-ttu-id="eab2e-105">Analýza různých typů textových souborů</span><span class="sxs-lookup"><span data-stu-id="eab2e-105">Parsing different types of text files</span></span>  

 <span data-ttu-id="eab2e-106">Textové soubory mohou obsahovat pole s různou šířkou, oddělené znakem, jako je čárka nebo mezera tabulátoru.</span><span class="sxs-lookup"><span data-stu-id="eab2e-106">Text files may have fields of various width, delimited by a character such as a comma or a tab space.</span></span> <span data-ttu-id="eab2e-107">Definujte `TextFieldType` a oddělovač, jak je znázorněno v následujícím příkladu, který používá metodu `SetDelimiters` k definování textového souboru s oddělovači tabulátoru:</span><span class="sxs-lookup"><span data-stu-id="eab2e-107">Define `TextFieldType` and the delimiter, as in the following example, which uses the `SetDelimiters` method to define a tab-delimited text file:</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#21)]  
  
 <span data-ttu-id="eab2e-108">Jiné textové soubory mohou mít pevné šířky polí.</span><span class="sxs-lookup"><span data-stu-id="eab2e-108">Other text files may have field widths that are fixed.</span></span> <span data-ttu-id="eab2e-109">V takových případech je nutné definovat `TextFieldType` jako `FixedWidth` a definovat šířky jednotlivých polí, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="eab2e-109">In such cases, you need to define the `TextFieldType` as `FixedWidth` and define the widths of each field, as in the following example.</span></span> <span data-ttu-id="eab2e-110">V tomto příkladu se používá metoda `SetFieldWidths` k definování sloupců textu: první sloupec má šířku 5 znaků, druhá je 10, třetí je 11 a čtvrtá je proměnná Width.</span><span class="sxs-lookup"><span data-stu-id="eab2e-110">This example uses the `SetFieldWidths` method to define the columns of text: the first column is 5 characters wide, the second is 10, the third is 11, and the fourth is of variable width.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrTextFieldParser/VB/Class1.vb#22)]  
  
 <span data-ttu-id="eab2e-111">Po definování formátu můžete projít soubor pomocí metody `ReadFields` pro zpracování každého řádku.</span><span class="sxs-lookup"><span data-stu-id="eab2e-111">Once the format is defined, you can loop through the file, using the `ReadFields` method to process each line in turn.</span></span>  
  
 <span data-ttu-id="eab2e-112">Pokud se pole neshoduje se zadaným formátem, je vyvolána výjimka <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>.</span><span class="sxs-lookup"><span data-stu-id="eab2e-112">If a field does not match the specified format, a <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> exception is thrown.</span></span> <span data-ttu-id="eab2e-113">Pokud jsou takové výjimky vyvolány, vlastnosti `ErrorLine` a `ErrorLineNumber` uchovávají text, který způsobil výjimku, a číslo řádku tohoto textu.</span><span class="sxs-lookup"><span data-stu-id="eab2e-113">When such exceptions are thrown, the `ErrorLine` and `ErrorLineNumber` properties hold the text causing the exception and the line number of that text.</span></span>  
  
## <a name="parsing-files-with-multiple-formats"></a><span data-ttu-id="eab2e-114">Analýza souborů s více formáty</span><span class="sxs-lookup"><span data-stu-id="eab2e-114">Parsing files with multiple formats</span></span>  

 <span data-ttu-id="eab2e-115">Metodu `PeekChars` objektu `TextFieldParser` lze použít ke kontrole každého pole před jeho čtením, což vám umožní definovat více formátů pro pole a odpovídajícím způsobem reagovat.</span><span class="sxs-lookup"><span data-stu-id="eab2e-115">The `PeekChars` method of the `TextFieldParser` object can be used to check each field before reading it, allowing you to define multiple formats for the fields and react accordingly.</span></span> <span data-ttu-id="eab2e-116">Další informace najdete v tématu [Postupy: čtení z textových souborů s více formáty](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span><span class="sxs-lookup"><span data-stu-id="eab2e-116">For more information, see [How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eab2e-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="eab2e-117">See also</span></span>

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
