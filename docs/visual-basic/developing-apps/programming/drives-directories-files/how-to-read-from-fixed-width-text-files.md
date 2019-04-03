---
title: 'Postupy: čtení ze souborů s pevnou šířkou v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: 4d6019bd9f39a6ae8db4b8c580db4c5ec9d4d4b8
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816210"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a><span data-ttu-id="08c17-102">Postupy: čtení ze souborů s pevnou šířkou v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="08c17-102">How to: read from fixed-width text files in Visual Basic</span></span>
<span data-ttu-id="08c17-103">`TextFieldParser` Objekt poskytuje způsob, jak snadno a efektivně analýza strukturovaných textových souborů, jako jsou protokoly.</span><span class="sxs-lookup"><span data-stu-id="08c17-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span>  
  
 <span data-ttu-id="08c17-104">`TextFieldType` Vlastnost definuje, zda je analyzovaný soubor souboru s oddělovači nebo, pokud má pevnou délkou textových polí.</span><span class="sxs-lookup"><span data-stu-id="08c17-104">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span></span> <span data-ttu-id="08c17-105">V souboru pevnou šířkou může mít pole na konci proměnné šířky.</span><span class="sxs-lookup"><span data-stu-id="08c17-105">In a fixed-width text file, the field at the end can have a variable width.</span></span> <span data-ttu-id="08c17-106">Chcete-li určit, zda má pole na konci proměnné šířky, definujte měl šířku menší než nebo rovna nule.</span><span class="sxs-lookup"><span data-stu-id="08c17-106">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span></span>  
  
### <a name="to-parse-a-fixed-width-text-file"></a><span data-ttu-id="08c17-107">Chcete-li analyzovat soubor pevnou šířkou</span><span class="sxs-lookup"><span data-stu-id="08c17-107">To parse a fixed-width text file</span></span>  
  
1.  <span data-ttu-id="08c17-108">Vytvořte nový `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="08c17-108">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="08c17-109">Následující kód vytvoří `TextFieldParser` s názvem `Reader` a otevře soubor `test.log`.</span><span class="sxs-lookup"><span data-stu-id="08c17-109">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span></span>  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2.  <span data-ttu-id="08c17-110">Definovat `TextFieldType` vlastnost jako `FixedWidth`, nastavte šířku a formátování.</span><span class="sxs-lookup"><span data-stu-id="08c17-110">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span></span> <span data-ttu-id="08c17-111">Následující kód definuje sloupce textu. První je 5 široké znaky, druhý 10, 11 třetí a čtvrtá kategorie je proměnné šířky.</span><span class="sxs-lookup"><span data-stu-id="08c17-111">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span></span>  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3.  <span data-ttu-id="08c17-112">Projít polí v souboru.</span><span class="sxs-lookup"><span data-stu-id="08c17-112">Loop through the fields in the file.</span></span> <span data-ttu-id="08c17-113">Pokud jsou poškozeny všechny řádky, ohlaste chybu a mohlo pokračovat s analýzou.</span><span class="sxs-lookup"><span data-stu-id="08c17-113">If any lines are corrupted, report an error and continue parsing.</span></span>  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4.  <span data-ttu-id="08c17-114">Zavřít `While` a `Using` blokuje s `End While` a `End Using`.</span><span class="sxs-lookup"><span data-stu-id="08c17-114">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="08c17-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="08c17-115">Example</span></span>  
 <span data-ttu-id="08c17-116">V tomto příkladu načteme soubor `test.log`.</span><span class="sxs-lookup"><span data-stu-id="08c17-116">This example reads from the file `test.log`.</span></span>  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a><span data-ttu-id="08c17-117">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="08c17-117">Robust programming</span></span>  
 <span data-ttu-id="08c17-118">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="08c17-118">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="08c17-119">Řádek nelze analyzovat pomocí určeného formátu (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="08c17-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="08c17-120">Zpráva o výjimce určuje řádek, který způsobil výjimku, a <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> vlastnost je přiřazena k obsažené v řádku textu.</span><span class="sxs-lookup"><span data-stu-id="08c17-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
-   <span data-ttu-id="08c17-121">Zadaný soubor neexistuje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="08c17-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="08c17-122">Stav částečným vztahem důvěryhodnosti, ve kterém uživatel nemá dostatečná oprávnění pro přístup k souboru.</span><span class="sxs-lookup"><span data-stu-id="08c17-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="08c17-123">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="08c17-123">(<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="08c17-124">Cesta je příliš dlouhá (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="08c17-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="08c17-125">Uživatel nemá dostatečná oprávnění pro přístup k souboru (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="08c17-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08c17-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="08c17-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="08c17-127">Postupy: Čtení z textových souborů s oddělovačem čárkou</span><span class="sxs-lookup"><span data-stu-id="08c17-127">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="08c17-128">Postupy: Čtení z textových souborů ve více formátech</span><span class="sxs-lookup"><span data-stu-id="08c17-128">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="08c17-129">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="08c17-129">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="08c17-130">Návod: Práce se soubory a adresáře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="08c17-130">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="08c17-131">Řešení potíží: Čtení a zápis do textových souborů</span><span class="sxs-lookup"><span data-stu-id="08c17-131">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
