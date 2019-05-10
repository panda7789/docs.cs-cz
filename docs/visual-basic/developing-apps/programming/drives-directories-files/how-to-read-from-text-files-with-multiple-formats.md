---
title: 'Postupy: Čtení z textových souborů ve více formátech v jazyce Visual Basic'
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
ms.openlocfilehash: 9fa484f0a74d900bd6f0365f2ce71fd32e1422db
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623184"
---
# <a name="how-to-read-from-text-files-with-multiple-formats-in-visual-basic"></a><span data-ttu-id="64b8c-102">Postupy: Čtení z textových souborů ve více formátech v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="64b8c-102">How to: Read From Text Files with Multiple Formats in Visual Basic</span></span>
<span data-ttu-id="64b8c-103"><xref:Microsoft.VisualBasic.FileIO.TextFieldParser> Objekt poskytuje způsob, jak snadno a efektivně analýza strukturovaných textových souborů, jako jsou protokoly.</span><span class="sxs-lookup"><span data-stu-id="64b8c-103">The <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="64b8c-104">Můžete zpracovat soubor ve více formátech s použitím `PeekChars` metoda určit formát každý řádek v souboru.</span><span class="sxs-lookup"><span data-stu-id="64b8c-104">You can process a file with multiple formats by using the `PeekChars` method to determine the format of each line as you parse through the file.</span></span>  
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a><span data-ttu-id="64b8c-105">Analyzovat textového souboru ve více formátech</span><span class="sxs-lookup"><span data-stu-id="64b8c-105">To parse a text file with multiple formats</span></span>  
  
1. <span data-ttu-id="64b8c-106">Přidání textového souboru s názvem testfile.txt do vašeho projektu.</span><span class="sxs-lookup"><span data-stu-id="64b8c-106">Add a text file named testfile.txt to your project.</span></span> <span data-ttu-id="64b8c-107">Do textového souboru přidejte následující obsah.</span><span class="sxs-lookup"><span data-stu-id="64b8c-107">Add the following content to the text file.</span></span>  
  
    ```  
    Err  1001 Cannot access resource.  
    Err  2014 Resource not found.  
    Acc  10/03/2009User1      Administrator.  
    Err  0323 Warning: Invalid access attempt.  
    Acc  10/03/2009User2      Standard user.  
    Acc  10/04/2009User2      Standard user.  
    ```  
  
2. <span data-ttu-id="64b8c-108">Definování očekávaný formát a použít, když dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="64b8c-108">Define the expected format and the format used when an error is reported.</span></span> <span data-ttu-id="64b8c-109">Poslední položka v každé pole je -1, proto poslední pole je předpokládá se, že proměnné šířky.</span><span class="sxs-lookup"><span data-stu-id="64b8c-109">The last entry in each array is -1, therefore the last field is assumed to be of variable width.</span></span> <span data-ttu-id="64b8c-110">K tomu dojde, když poslední položky v poli je menší než nebo rovna 0.</span><span class="sxs-lookup"><span data-stu-id="64b8c-110">This occurs when the last entry in the array is less than or equal to 0.</span></span>  
  
     [!code-vb[VbFileIORead#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#4)]  
  
3. <span data-ttu-id="64b8c-111">Vytvořte nový <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> objekt definováním šířku a formátu.</span><span class="sxs-lookup"><span data-stu-id="64b8c-111">Create a new <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> object, defining the width and format.</span></span>  
  
     [!code-vb[VbFileIORead#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#5)]  
  
4. <span data-ttu-id="64b8c-112">Projít řádky testování formát před čtením.</span><span class="sxs-lookup"><span data-stu-id="64b8c-112">Loop through the rows, testing for format before reading.</span></span>  
  
     [!code-vb[VbFileIORead#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#6)]  
  
5. <span data-ttu-id="64b8c-113">Chyby zápisu do konzoly.</span><span class="sxs-lookup"><span data-stu-id="64b8c-113">Write errors to the console.</span></span>  
  
     [!code-vb[VbFileIORead#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#7)]  
  
## <a name="example"></a><span data-ttu-id="64b8c-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="64b8c-114">Example</span></span>  
 <span data-ttu-id="64b8c-115">Následuje Úplný příklad, který čte ze souboru `testfile.txt`.</span><span class="sxs-lookup"><span data-stu-id="64b8c-115">Following is the complete example that reads from the file `testfile.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="64b8c-116">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="64b8c-116">Robust Programming</span></span>  
 <span data-ttu-id="64b8c-117">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="64b8c-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="64b8c-118">Řádek nelze analyzovat pomocí určeného formátu (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="64b8c-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="64b8c-119">Zpráva o výjimce určuje řádek, který způsobil výjimku, a <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> vlastnost je přiřazena k obsažené v řádku textu.</span><span class="sxs-lookup"><span data-stu-id="64b8c-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
- <span data-ttu-id="64b8c-120">Zadaný soubor neexistuje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="64b8c-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="64b8c-121">Stav částečným vztahem důvěryhodnosti, ve kterém uživatel nemá dostatečná oprávnění pro přístup k souboru.</span><span class="sxs-lookup"><span data-stu-id="64b8c-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="64b8c-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="64b8c-122">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="64b8c-123">Cesta je příliš dlouhá (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="64b8c-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="64b8c-124">Uživatel nemá dostatečná oprávnění pro přístup k souboru (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="64b8c-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64b8c-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64b8c-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- [<span data-ttu-id="64b8c-126">Postupy: Čtení z textových souborů s oddělovačem čárkou</span><span class="sxs-lookup"><span data-stu-id="64b8c-126">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="64b8c-127">Postupy: Čtení z souborů s pevnou šířkou</span><span class="sxs-lookup"><span data-stu-id="64b8c-127">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="64b8c-128">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="64b8c-128">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
