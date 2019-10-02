---
title: 'Postupy: čtení z textových souborů s více formáty v Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, reading from a file
- TextFieldType enumeration
- My.Computer.FileSystem.WriteAllText method, parsing structured text files
- WriteAllText method [Visual Basic], parsing structured text files
- PeekChars method [Visual Basic], determining format of text
- reading text files [Visual Basic], multiple formats
- I/O [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 8d185eb2-79ca-42cd-95a7-d3ff44a5a0f8
ms.openlocfilehash: dc726f7648c1c0a564594331023f03d20569d766
ms.sourcegitcommit: 878ca7550b653114c3968ef8906da2b3e60e3c7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2019
ms.locfileid: "71736826"
---
# <a name="how-to-read-from-fext-files-with-multiple-formats-in-visual-basic"></a><span data-ttu-id="30e5b-102">Postupy: čtení ze souborů Fext s více formáty v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="30e5b-102">How to: Read from fext files with multiple formats in Visual Basic</span></span>

<span data-ttu-id="30e5b-103">Objekt <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> poskytuje způsob, jak snadno a efektivně analyzovat strukturované textové soubory, jako jsou protokoly.</span><span class="sxs-lookup"><span data-stu-id="30e5b-103">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="30e5b-104">Můžete zpracovat soubor s více formáty pomocí metody `PeekChars` k určení formátu každého řádku při analýze souboru.</span><span class="sxs-lookup"><span data-stu-id="30e5b-104">You can process a file with multiple formats by using the `PeekChars` method to determine the format of each line as you parse through the file.</span></span>
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a><span data-ttu-id="30e5b-105">Postup analýzy textového souboru s více formáty</span><span class="sxs-lookup"><span data-stu-id="30e5b-105">To parse a text file with multiple formats</span></span>

1. <span data-ttu-id="30e5b-106">Do projektu přidejte textový soubor s názvem *Testfile. txt* .</span><span class="sxs-lookup"><span data-stu-id="30e5b-106">Add a text file named *testfile.txt* to your project.</span></span> <span data-ttu-id="30e5b-107">Do textového souboru přidejte následující obsah:</span><span class="sxs-lookup"><span data-stu-id="30e5b-107">Add the following content to the text file:</span></span>

    ```text
    Err  1001 Cannot access resource.
    Err  2014 Resource not found.
    Acc  10/03/2009User1      Administrator.
    Err  0323 Warning: Invalid access attempt.
    Acc  10/03/2009User2      Standard user.
    Acc  10/04/2009User2      Standard user.
    ```

2. <span data-ttu-id="30e5b-108">Definujte očekávaný formát a formát použitý při hlášení chyby.</span><span class="sxs-lookup"><span data-stu-id="30e5b-108">Define the expected format and the format used when an error is reported.</span></span> <span data-ttu-id="30e5b-109">Poslední položka v každém poli je-1, proto se předpokládá, že poslední pole má proměnlivou šířku.</span><span class="sxs-lookup"><span data-stu-id="30e5b-109">The last entry in each array is -1, therefore the last field is assumed to be of variable width.</span></span> <span data-ttu-id="30e5b-110">K tomu dochází, když je poslední položka v poli menší nebo rovna 0.</span><span class="sxs-lookup"><span data-stu-id="30e5b-110">This occurs when the last entry in the array is less than or equal to 0.</span></span>

     [!code-vb[VbFileIORead#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#4)]

3. <span data-ttu-id="30e5b-111">Vytvořte nový objekt @no__t 0 a definujte šířku a formát.</span><span class="sxs-lookup"><span data-stu-id="30e5b-111">Create a new <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object, defining the width and format.</span></span>

     [!code-vb[VbFileIORead#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#5)]

4. <span data-ttu-id="30e5b-112">Procházejte řádky smyčkou a před čtením proveďte testování formátu.</span><span class="sxs-lookup"><span data-stu-id="30e5b-112">Loop through the rows, testing for format before reading.</span></span>

     [!code-vb[VbFileIORead#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#6)]

5. <span data-ttu-id="30e5b-113">Zapište do konzoly chyby.</span><span class="sxs-lookup"><span data-stu-id="30e5b-113">Write errors to the console.</span></span>

     [!code-vb[VbFileIORead#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#7)]

## <a name="example"></a><span data-ttu-id="30e5b-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="30e5b-114">Example</span></span>

<span data-ttu-id="30e5b-115">Následuje kompletní příklad, který čte ze souboru `testfile.txt`:</span><span class="sxs-lookup"><span data-stu-id="30e5b-115">The following is the complete example that reads from the file `testfile.txt`:</span></span>

 [!code-vb[VbFileIORead#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#8)]

## <a name="robust-programming"></a><span data-ttu-id="30e5b-116">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="30e5b-116">Robust programming</span></span>

<span data-ttu-id="30e5b-117">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="30e5b-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="30e5b-118">Řádek nelze analyzovat v zadaném formátu (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="30e5b-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="30e5b-119">Zpráva o výjimce Určuje řádek, který způsobil výjimku, zatímco vlastnost <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> je přiřazena k textu obsaženému na řádku.</span><span class="sxs-lookup"><span data-stu-id="30e5b-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>
- <span data-ttu-id="30e5b-120">Zadaný soubor neexistuje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="30e5b-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>
- <span data-ttu-id="30e5b-121">Částečně důvěryhodná situace, kdy uživatel nemá dostatečná oprávnění pro přístup k souboru.</span><span class="sxs-lookup"><span data-stu-id="30e5b-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="30e5b-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="30e5b-122">(<xref:System.Security.SecurityException>).</span></span>
- <span data-ttu-id="30e5b-123">Cesta je příliš dlouhá (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="30e5b-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>
- <span data-ttu-id="30e5b-124">Uživatel nemá dostatečná oprávnění pro přístup k souboru (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="30e5b-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="30e5b-125">Další informace najdete v tématech</span><span class="sxs-lookup"><span data-stu-id="30e5b-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- [<span data-ttu-id="30e5b-126">Postupy: čtení z textových souborů s hodnotami oddělenými čárkou</span><span class="sxs-lookup"><span data-stu-id="30e5b-126">How to: Read From Comma-Delimited Text Files</span></span>](how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="30e5b-127">Postupy: čtení z textových souborů s pevnou šířkou</span><span class="sxs-lookup"><span data-stu-id="30e5b-127">How to: Read From Fixed-width Text Files</span></span>](how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="30e5b-128">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="30e5b-128">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
