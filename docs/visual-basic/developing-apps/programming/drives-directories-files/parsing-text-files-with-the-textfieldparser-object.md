---
title: Analýza textových souborů pomocí objektu TextFieldParser (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, using
- I/O [Visual Basic], parsing files
- files [Visual Basic], parsing
ms.assetid: fc31d6e6-af0c-403f-8a00-d556b2c57567
ms.openlocfilehash: 520121ba549532c5ce73810347025949eee5a077
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587303"
---
# <a name="parsing-text-files-with-the-textfieldparser-object-visual-basic"></a><span data-ttu-id="26b05-102">Analýza textových souborů pomocí objektu TextFieldParser (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26b05-102">Parsing text files with the TextFieldParser object (Visual Basic)</span></span>
<span data-ttu-id="26b05-103">`TextFieldParser` Objektu umožňuje analyzovat a zpracovat velmi velké soubory, které mají strukturu sloupce textu, například soubory protokolu nebo informace o starší databázi.</span><span class="sxs-lookup"><span data-stu-id="26b05-103">The `TextFieldParser` object allows you to parse and process very large file that are structured as delimited-width columns of text, such as log files or legacy database information.</span></span> <span data-ttu-id="26b05-104">Analýza textový soubor s `TextFieldParser` je podobná procházení textového souboru, metoda extrahovat textových polí je podobná metodám určený k tokenizaci řetězce s oddělovači.</span><span class="sxs-lookup"><span data-stu-id="26b05-104">Parsing a text file with `TextFieldParser` is similar to iterating over a text file, while the parse method to extract fields of text is similar to string manipulation methods used to tokenize delimited strings.</span></span>  
  
## <a name="parsing-different-types-of-text-files"></a><span data-ttu-id="26b05-105">Analýza různé typy textových souborů</span><span class="sxs-lookup"><span data-stu-id="26b05-105">Parsing different types of text files</span></span>  
 <span data-ttu-id="26b05-106">Textové soubory, může mít různou šířku, oddělená znakem například čárkou nebo tabulátorem.</span><span class="sxs-lookup"><span data-stu-id="26b05-106">Text files may have fields of various width, delimited by a character such as a comma or a tab space.</span></span> <span data-ttu-id="26b05-107">Definování `TextFieldType` a oddělovače, jako v následujícím příkladu, který používá `SetDelimiters` metoda k definování souboru text oddělený tabulátory:</span><span class="sxs-lookup"><span data-stu-id="26b05-107">Define `TextFieldType` and the delimiter, as in the following example, which uses the `SetDelimiters` method to define a tab-delimited text file:</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#21](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_1.vb)]  
  
 <span data-ttu-id="26b05-108">Další textové soubory mohou mít šířku polí, které jsou vyřešeny.</span><span class="sxs-lookup"><span data-stu-id="26b05-108">Other text files may have field widths that are fixed.</span></span> <span data-ttu-id="26b05-109">V takových případech je třeba definovat `TextFieldType` jako `FixedWidth` a určit šířku každého pole, jako v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="26b05-109">In such cases, you need to define the `TextFieldType` as `FixedWidth` and define the widths of each field, as in the following example.</span></span> <span data-ttu-id="26b05-110">Tento příklad používá `SetFieldWidths` metoda k definování sloupců textu: první sloupec je 5 znaků široký, druhý je 10, 11 je třetí a čtvrtý je proměnné šířky.</span><span class="sxs-lookup"><span data-stu-id="26b05-110">This example uses the `SetFieldWidths` method to define the columns of text: the first column is 5 characters wide, the second is 10, the third is 11, and the fourth is of variable width.</span></span>  
  
 [!code-vb[VbVbalrTextFieldParser#22](../../../../visual-basic/developing-apps/development-with-my/codesnippet/VisualBasic/parsing-text-files-with-the-textfieldparser-object_2.vb)]  
  
 <span data-ttu-id="26b05-111">Po definování formátu můžete projít soubor, pomocí `ReadFields` metoda zase zpracovávat každý řádek.</span><span class="sxs-lookup"><span data-stu-id="26b05-111">Once the format is defined, you can loop through the file, using the `ReadFields` method to process each line in turn.</span></span>  
  
 <span data-ttu-id="26b05-112">Pokud pole neodpovídá zadaném formátu, <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="26b05-112">If a field does not match the specified format, a <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> exception is thrown.</span></span> <span data-ttu-id="26b05-113">Pokud je vyvolána, `ErrorLine` a `ErrorLineNumber` vlastnosti obsahovat text, který způsobuje výjimku a číslo řádku textu.</span><span class="sxs-lookup"><span data-stu-id="26b05-113">When such exceptions are thrown, the `ErrorLine` and `ErrorLineNumber` properties hold the text causing the exception and the line number of that text.</span></span>  
  
## <a name="parsing-files-with-multiple-formats"></a><span data-ttu-id="26b05-114">Analýza souborů ve více formátech</span><span class="sxs-lookup"><span data-stu-id="26b05-114">Parsing files with multiple formats</span></span>  
 <span data-ttu-id="26b05-115">`PeekChars` Metodu `TextFieldParser` objekt lze použít ke kontrole každého pole před, čtení, který vám umožní definovat více formátů pro pole a odpovídajícím způsobem reagovat.</span><span class="sxs-lookup"><span data-stu-id="26b05-115">The `PeekChars` method of the `TextFieldParser` object can be used to check each field before reading it, allowing you to define multiple formats for the fields and react accordingly.</span></span> <span data-ttu-id="26b05-116">Další informace najdete v tématu [postupy: čtení z textových souborů s více formátů](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span><span class="sxs-lookup"><span data-stu-id="26b05-116">For more information, see [How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26b05-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="26b05-117">See also</span></span>  
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
