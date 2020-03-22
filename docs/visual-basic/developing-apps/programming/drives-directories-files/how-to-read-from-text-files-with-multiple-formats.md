---
title: 'Postup: Čtení z textových souborů s více formáty'
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
ms.openlocfilehash: b36c781d5f8333749d346bb8f19540f0d1bd1692
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334575"
---
# <a name="how-to-read-from-fext-files-with-multiple-formats-in-visual-basic"></a><span data-ttu-id="9f002-102">Postup: Čtení ze souborů fext s více formáty v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9f002-102">How to: Read from fext files with multiple formats in Visual Basic</span></span>

<span data-ttu-id="9f002-103">Objekt <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> poskytuje způsob, jak snadno a efektivně analyzovat strukturované textové soubory, jako jsou například protokoly.</span><span class="sxs-lookup"><span data-stu-id="9f002-103">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="9f002-104">Soubor s více formáty můžete zpracovat pomocí `PeekChars` metody k určení formátu každého řádku při analýzě souboru.</span><span class="sxs-lookup"><span data-stu-id="9f002-104">You can process a file with multiple formats by using the `PeekChars` method to determine the format of each line as you parse through the file.</span></span>
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a><span data-ttu-id="9f002-105">Analýza textového souboru s více formáty</span><span class="sxs-lookup"><span data-stu-id="9f002-105">To parse a text file with multiple formats</span></span>

1. <span data-ttu-id="9f002-106">Přidejte do projektu textový soubor s názvem *testfile.txt.*</span><span class="sxs-lookup"><span data-stu-id="9f002-106">Add a text file named *testfile.txt* to your project.</span></span> <span data-ttu-id="9f002-107">Do textového souboru přidejte následující obsah:</span><span class="sxs-lookup"><span data-stu-id="9f002-107">Add the following content to the text file:</span></span>

    ```text
    Err  1001 Cannot access resource.
    Err  2014 Resource not found.
    Acc  10/03/2009User1      Administrator.
    Err  0323 Warning: Invalid access attempt.
    Acc  10/03/2009User2      Standard user.
    Acc  10/04/2009User2      Standard user.
    ```

2. <span data-ttu-id="9f002-108">Definujte očekávaný formát a formát použitý při nakazení chyby.</span><span class="sxs-lookup"><span data-stu-id="9f002-108">Define the expected format and the format used when an error is reported.</span></span> <span data-ttu-id="9f002-109">Poslední položka v každém poli je -1, proto se předpokládá, že poslední pole má proměnnou šířku.</span><span class="sxs-lookup"><span data-stu-id="9f002-109">The last entry in each array is -1, therefore the last field is assumed to be of variable width.</span></span> <span data-ttu-id="9f002-110">K tomu dochází, když poslední položka v poli je menší nebo rovna 0.</span><span class="sxs-lookup"><span data-stu-id="9f002-110">This occurs when the last entry in the array is less than or equal to 0.</span></span>

     [!code-vb[VbFileIORead#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#4)]

3. <span data-ttu-id="9f002-111">Vytvořte <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> nový objekt, který definuje šířku a formát.</span><span class="sxs-lookup"><span data-stu-id="9f002-111">Create a new <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object, defining the width and format.</span></span>

     [!code-vb[VbFileIORead#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#5)]

4. <span data-ttu-id="9f002-112">Smyčka přes řádky, testování formátu před čtením.</span><span class="sxs-lookup"><span data-stu-id="9f002-112">Loop through the rows, testing for format before reading.</span></span>

     [!code-vb[VbFileIORead#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#6)]

5. <span data-ttu-id="9f002-113">Zápis chyb do konzoly.</span><span class="sxs-lookup"><span data-stu-id="9f002-113">Write errors to the console.</span></span>

     [!code-vb[VbFileIORead#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#7)]

## <a name="example"></a><span data-ttu-id="9f002-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f002-114">Example</span></span>

<span data-ttu-id="9f002-115">Následuje úplný příklad, který čte `testfile.txt`ze souboru :</span><span class="sxs-lookup"><span data-stu-id="9f002-115">The following is the complete example that reads from the file `testfile.txt`:</span></span>

 [!code-vb[VbFileIORead#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#8)]

## <a name="robust-programming"></a><span data-ttu-id="9f002-116">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="9f002-116">Robust programming</span></span>

<span data-ttu-id="9f002-117">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="9f002-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="9f002-118">Řádek nelze analyzovat pomocí zadaného formátu<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>( ).</span><span class="sxs-lookup"><span data-stu-id="9f002-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="9f002-119">Zpráva o výjimce určuje řádek způsobující <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> výjimku, zatímco vlastnost je přiřazena k textu obsaženému v řádku.</span><span class="sxs-lookup"><span data-stu-id="9f002-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>
- <span data-ttu-id="9f002-120">Zadaný soubor neexistuje<xref:System.IO.FileNotFoundException>( ).</span><span class="sxs-lookup"><span data-stu-id="9f002-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>
- <span data-ttu-id="9f002-121">Situace částečné důvěryhodnosti, ve které uživatel nemá dostatečná oprávnění pro přístup k souboru.</span><span class="sxs-lookup"><span data-stu-id="9f002-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="9f002-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="9f002-122">(<xref:System.Security.SecurityException>).</span></span>
- <span data-ttu-id="9f002-123">Cesta je příliš<xref:System.IO.PathTooLongException>dlouhá ( ).</span><span class="sxs-lookup"><span data-stu-id="9f002-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>
- <span data-ttu-id="9f002-124">Uživatel nemá dostatečná oprávnění pro přístup<xref:System.UnauthorizedAccessException>k souboru ( ).</span><span class="sxs-lookup"><span data-stu-id="9f002-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="9f002-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f002-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- [<span data-ttu-id="9f002-126">Postupy: Čtení z textových souborů s oddělovači</span><span class="sxs-lookup"><span data-stu-id="9f002-126">How to: Read From Comma-Delimited Text Files</span></span>](how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="9f002-127">Postupy: Čtení z textových souborů s pevnou šířkou</span><span class="sxs-lookup"><span data-stu-id="9f002-127">How to: Read From Fixed-width Text Files</span></span>](how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="9f002-128">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="9f002-128">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
