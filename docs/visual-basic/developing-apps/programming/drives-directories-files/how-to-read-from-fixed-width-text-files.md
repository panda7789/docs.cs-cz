---
title: 'Postupy: čtení z souborů s pevnou šířkou v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: c777e54f2857e32f1f00460c17b988c597506ad3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588671"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a><span data-ttu-id="64840-102">Postupy: čtení z souborů s pevnou šířkou v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="64840-102">How to: read from fixed-width text files in Visual Basic</span></span>
<span data-ttu-id="64840-103">`TextFieldParser` Objekt poskytuje způsob, jak snadno a efektivně analýza strukturovaných textových souborů, jako jsou protokoly.</span><span class="sxs-lookup"><span data-stu-id="64840-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span>  
  
 <span data-ttu-id="64840-104">`TextFieldType` Vlastnost určuje, zda soubor Analyzovaná soubor s oddělovači nebo s pevnou šířkou textových polí.</span><span class="sxs-lookup"><span data-stu-id="64840-104">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span></span> <span data-ttu-id="64840-105">Pevná šířka textového souboru může mít na konci pole proměnné šířky.</span><span class="sxs-lookup"><span data-stu-id="64840-105">In a fixed-width text file, the field at the end can have a variable width.</span></span> <span data-ttu-id="64840-106">K určení, zda má pole na konci proměnné šířky, zadejte ji tak, aby měl šířka menší než nebo rovna nule.</span><span class="sxs-lookup"><span data-stu-id="64840-106">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span></span>  
  
### <a name="to-parse-a-fixed-width-text-file"></a><span data-ttu-id="64840-107">Chcete-li analyzovat soubor pevnou šířkou</span><span class="sxs-lookup"><span data-stu-id="64840-107">To parse a fixed-width text file</span></span>  
  
1.  <span data-ttu-id="64840-108">Vytvořte novou `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="64840-108">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="64840-109">Následující kód vytvoří `TextFieldParser` s názvem `Reader` a otevře soubor `test.log`.</span><span class="sxs-lookup"><span data-stu-id="64840-109">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span></span>  
  
     [!code-vb[VbFileIORead#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_1.vb)]  
  
2.  <span data-ttu-id="64840-110">Definování `TextFieldType` vlastnost jako `FixedWidth`, nastavte šířku a formátování.</span><span class="sxs-lookup"><span data-stu-id="64840-110">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span></span> <span data-ttu-id="64840-111">Následující kód definuje sloupce textu; První je 5 znaků široký, druhý 10, 11 třetí a čtvrtý je proměnné šířky.</span><span class="sxs-lookup"><span data-stu-id="64840-111">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span></span>  
  
     [!code-vb[VbFileIORead#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_2.vb)]  
  
3.  <span data-ttu-id="64840-112">Projděte všechny pole v souboru.</span><span class="sxs-lookup"><span data-stu-id="64840-112">Loop through the fields in the file.</span></span> <span data-ttu-id="64840-113">Pokud jsou řádky poškozeny, ohlaste chybu a pokračujte v analýze.</span><span class="sxs-lookup"><span data-stu-id="64840-113">If any lines are corrupted, report an error and continue parsing.</span></span>  
  
     [!code-vb[VbFileIORead#11](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_3.vb)]  
  
4.  <span data-ttu-id="64840-114">Zavřít `While` a `Using` zablokuje s `End While` a `End Using`.</span><span class="sxs-lookup"><span data-stu-id="64840-114">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#12](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="64840-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="64840-115">Example</span></span>  
 <span data-ttu-id="64840-116">Tento příklad čte ze souboru `test.log`.</span><span class="sxs-lookup"><span data-stu-id="64840-116">This example reads from the file `test.log`.</span></span>  
  
 [!code-vb[VbFileIORead#13](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_5.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="64840-117">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="64840-117">Robust programming</span></span>  
 <span data-ttu-id="64840-118">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="64840-118">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="64840-119">Řádek nelze analyzovat pomocí zadaného formátu (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="64840-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="64840-120">Zpráva o výjimce určuje řádek, který způsobil výjimku a <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> vlastnost je přiřazena k obsažené v řádku textu.</span><span class="sxs-lookup"><span data-stu-id="64840-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
-   <span data-ttu-id="64840-121">Zadaný soubor neexistuje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="64840-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="64840-122">Stav částečným vztahem důvěryhodnosti, ve kterém uživatel nemá dostatečná oprávnění k přístupu k souboru.</span><span class="sxs-lookup"><span data-stu-id="64840-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="64840-123">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="64840-123">(<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="64840-124">Cesta je příliš dlouhá (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="64840-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="64840-125">Uživatel nemá dostatečná oprávnění k přístupu k souboru (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="64840-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64840-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="64840-126">See also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>  
 [<span data-ttu-id="64840-127">Postupy: Čtení z textových souborů s oddělovačem čárkou</span><span class="sxs-lookup"><span data-stu-id="64840-127">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [<span data-ttu-id="64840-128">Postupy: Čtení z textových souborů ve více formátech</span><span class="sxs-lookup"><span data-stu-id="64840-128">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)  
 [<span data-ttu-id="64840-129">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="64840-129">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 [<span data-ttu-id="64840-130">Návod: Manipulace se soubory a adresáře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="64840-130">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 [<span data-ttu-id="64840-131">Řešení potíží: Čtení z textových souborů a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="64840-131">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 
