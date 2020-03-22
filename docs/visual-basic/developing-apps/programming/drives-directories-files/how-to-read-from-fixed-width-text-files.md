---
title: 'Postup: čtení z textu s pevnou šířkou Soubory'
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: 3cea9bfe2388f0ca510b15cb020f899b81c4603c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74334628"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a><span data-ttu-id="da41b-102">Postup: čtení z textových souborů s pevnou šířkou v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="da41b-102">How to: read from fixed-width text files in Visual Basic</span></span>

<span data-ttu-id="da41b-103">Objekt `TextFieldParser` poskytuje způsob, jak snadno a efektivně analyzovat strukturované textové soubory, jako jsou například protokoly.</span><span class="sxs-lookup"><span data-stu-id="da41b-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span>  
  
 <span data-ttu-id="da41b-104">Vlastnost `TextFieldType` definuje, zda je analyzovaný soubor soubor s oddělovačem nebo soubor, který má pole s pevnou šířkou textu.</span><span class="sxs-lookup"><span data-stu-id="da41b-104">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span></span> <span data-ttu-id="da41b-105">V textovém souboru s pevnou šířkou může mít pole na konci proměnnou šířku.</span><span class="sxs-lookup"><span data-stu-id="da41b-105">In a fixed-width text file, the field at the end can have a variable width.</span></span> <span data-ttu-id="da41b-106">Chcete-li určit, že pole na konci má proměnnou šířku, definujte ji tak, aby měla šířku menší nebo rovnou nule.</span><span class="sxs-lookup"><span data-stu-id="da41b-106">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span></span>  
  
### <a name="to-parse-a-fixed-width-text-file"></a><span data-ttu-id="da41b-107">Analýza textového souboru s pevnou šířkou</span><span class="sxs-lookup"><span data-stu-id="da41b-107">To parse a fixed-width text file</span></span>  
  
1. <span data-ttu-id="da41b-108">Vytvořte `TextFieldParser`nový .</span><span class="sxs-lookup"><span data-stu-id="da41b-108">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="da41b-109">Následující kód vytvoří `TextFieldParser` `Reader` pojmenovaný a `test.log`otevře soubor .</span><span class="sxs-lookup"><span data-stu-id="da41b-109">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span></span>  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. <span data-ttu-id="da41b-110">Definujte `TextFieldType` vlastnost `FixedWidth`jako , definování šířky a formátu.</span><span class="sxs-lookup"><span data-stu-id="da41b-110">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span></span> <span data-ttu-id="da41b-111">Následující kód definuje sloupce textu; první je 5 znaků široký, druhý 10, třetí 11 a čtvrtý má proměnnou šířku.</span><span class="sxs-lookup"><span data-stu-id="da41b-111">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span></span>  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. <span data-ttu-id="da41b-112">Smyčka procházet pole v souboru.</span><span class="sxs-lookup"><span data-stu-id="da41b-112">Loop through the fields in the file.</span></span> <span data-ttu-id="da41b-113">Pokud jsou některé řádky poškozeny, oznamte chybu a pokračujte v provádění analýzy.</span><span class="sxs-lookup"><span data-stu-id="da41b-113">If any lines are corrupted, report an error and continue parsing.</span></span>  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. <span data-ttu-id="da41b-114">Zavřete `While` `Using` bloky `End While` a `End Using`s a .</span><span class="sxs-lookup"><span data-stu-id="da41b-114">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="da41b-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="da41b-115">Example</span></span>  

 <span data-ttu-id="da41b-116">Tento příklad čte `test.log`ze souboru .</span><span class="sxs-lookup"><span data-stu-id="da41b-116">This example reads from the file `test.log`.</span></span>  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a><span data-ttu-id="da41b-117">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="da41b-117">Robust programming</span></span>  

 <span data-ttu-id="da41b-118">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="da41b-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="da41b-119">Řádek nelze analyzovat pomocí zadaného formátu<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>( ).</span><span class="sxs-lookup"><span data-stu-id="da41b-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="da41b-120">Zpráva o výjimce určuje řádek způsobující <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> výjimku, zatímco vlastnost je přiřazena k textu obsaženému v řádku.</span><span class="sxs-lookup"><span data-stu-id="da41b-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
- <span data-ttu-id="da41b-121">Zadaný soubor neexistuje<xref:System.IO.FileNotFoundException>( ).</span><span class="sxs-lookup"><span data-stu-id="da41b-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="da41b-122">Situace částečné důvěryhodnosti, ve které uživatel nemá dostatečná oprávnění pro přístup k souboru.</span><span class="sxs-lookup"><span data-stu-id="da41b-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="da41b-123">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="da41b-123">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="da41b-124">Cesta je příliš<xref:System.IO.PathTooLongException>dlouhá ( ).</span><span class="sxs-lookup"><span data-stu-id="da41b-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="da41b-125">Uživatel nemá dostatečná oprávnění pro přístup<xref:System.UnauthorizedAccessException>k souboru ( ).</span><span class="sxs-lookup"><span data-stu-id="da41b-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da41b-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="da41b-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="da41b-127">Postupy: Čtení z textových souborů s oddělovači</span><span class="sxs-lookup"><span data-stu-id="da41b-127">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="da41b-128">Postupy: Čtení z textových souborů ve více formátech</span><span class="sxs-lookup"><span data-stu-id="da41b-128">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="da41b-129">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="da41b-129">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="da41b-130">Návod: Práce se soubory a adresáři v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="da41b-130">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="da41b-131">Řešení potíží: Čtení z textových souborů a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="da41b-131">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
