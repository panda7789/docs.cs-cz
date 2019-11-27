---
title: 'Postupy: čtení z textových souborů s pevnou šířkou'
ms.date: 07/20/2015
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
ms.openlocfilehash: 3cea9bfe2388f0ca510b15cb020f899b81c4603c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334628"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a><span data-ttu-id="24b96-102">Postupy: čtení z textových souborů s pevnou šířkou v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24b96-102">How to: read from fixed-width text files in Visual Basic</span></span>

<span data-ttu-id="24b96-103">Objekt `TextFieldParser` poskytuje způsob, jak snadno a efektivně analyzovat strukturované textové soubory, jako jsou protokoly.</span><span class="sxs-lookup"><span data-stu-id="24b96-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span>  
  
 <span data-ttu-id="24b96-104">Vlastnost `TextFieldType` definuje, zda je analyzovaný soubor soubor s oddělovači nebo který má pole s pevnou šířkou textu.</span><span class="sxs-lookup"><span data-stu-id="24b96-104">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span></span> <span data-ttu-id="24b96-105">V textovém souboru s pevnou šířkou může mít pole na konci proměnlivou šířku.</span><span class="sxs-lookup"><span data-stu-id="24b96-105">In a fixed-width text file, the field at the end can have a variable width.</span></span> <span data-ttu-id="24b96-106">Chcete-li určit, že pole na konci má proměnnou Width, definujte ji tak, aby měla šířku menší nebo rovna nule.</span><span class="sxs-lookup"><span data-stu-id="24b96-106">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span></span>  
  
### <a name="to-parse-a-fixed-width-text-file"></a><span data-ttu-id="24b96-107">Chcete-li analyzovat textový soubor s pevnou šířkou</span><span class="sxs-lookup"><span data-stu-id="24b96-107">To parse a fixed-width text file</span></span>  
  
1. <span data-ttu-id="24b96-108">Vytvoří nový `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="24b96-108">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="24b96-109">Následující kód vytvoří `TextFieldParser` s názvem `Reader` a otevře soubor `test.log`.</span><span class="sxs-lookup"><span data-stu-id="24b96-109">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span></span>  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. <span data-ttu-id="24b96-110">Definujte vlastnost `TextFieldType` jako `FixedWidth`a definujte šířku a formát.</span><span class="sxs-lookup"><span data-stu-id="24b96-110">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span></span> <span data-ttu-id="24b96-111">Následující kód definuje sloupce textu; první je 5 znaků široké, druhý 10, třetí 11 a čtvrtá je proměnná Width.</span><span class="sxs-lookup"><span data-stu-id="24b96-111">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span></span>  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. <span data-ttu-id="24b96-112">Projděte pole v souboru.</span><span class="sxs-lookup"><span data-stu-id="24b96-112">Loop through the fields in the file.</span></span> <span data-ttu-id="24b96-113">Pokud jsou některé řádky poškozené, nahlaste chybu a pokračujte v analýze.</span><span class="sxs-lookup"><span data-stu-id="24b96-113">If any lines are corrupted, report an error and continue parsing.</span></span>  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. <span data-ttu-id="24b96-114">Zavřete `While` a `Using` bloky pomocí `End While` a `End Using`.</span><span class="sxs-lookup"><span data-stu-id="24b96-114">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="24b96-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="24b96-115">Example</span></span>  

 <span data-ttu-id="24b96-116">Tento příklad čte ze souboru `test.log`.</span><span class="sxs-lookup"><span data-stu-id="24b96-116">This example reads from the file `test.log`.</span></span>  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a><span data-ttu-id="24b96-117">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="24b96-117">Robust programming</span></span>  

 <span data-ttu-id="24b96-118">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="24b96-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="24b96-119">Řádek nelze analyzovat pomocí zadaného formátu (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="24b96-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="24b96-120">Zpráva výjimky Určuje řádek, který způsobil výjimku, zatímco vlastnost <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> je přiřazena k textu obsaženému na řádku.</span><span class="sxs-lookup"><span data-stu-id="24b96-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
- <span data-ttu-id="24b96-121">Zadaný soubor neexistuje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="24b96-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="24b96-122">Částečně důvěryhodná situace, kdy uživatel nemá dostatečná oprávnění pro přístup k souboru.</span><span class="sxs-lookup"><span data-stu-id="24b96-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="24b96-123">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="24b96-123">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="24b96-124">Cesta je příliš dlouhá (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="24b96-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="24b96-125">Uživatel nemá dostatečná oprávnění pro přístup k souboru (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="24b96-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24b96-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="24b96-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="24b96-127">Postupy: Čtení z textových souborů s oddělovačem čárkou</span><span class="sxs-lookup"><span data-stu-id="24b96-127">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="24b96-128">Postupy: Čtení z textových souborů ve více formátech</span><span class="sxs-lookup"><span data-stu-id="24b96-128">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="24b96-129">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="24b96-129">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="24b96-130">Návod: manipulace se soubory a adresáři v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24b96-130">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="24b96-131">Řešení potíží: Čtení z textových souborů a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="24b96-131">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
