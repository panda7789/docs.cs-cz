---
title: 'Postupy: čtení z textových souborů s hodnotami oddělenými čárkou'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
ms.openlocfilehash: 9b93893e2221b156b65ce8e945089269ea28c989
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74335065"
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a><span data-ttu-id="c7a90-102">Postupy: čtení z textových souborů s oddělovači ve formátu čárky v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c7a90-102">How to: read from comma-delimited text files in Visual Basic</span></span>

<span data-ttu-id="c7a90-103">`TextFieldParser` Objekt poskytuje způsob, jak snadno a efektivně analyzovat strukturované textové soubory, jako jsou protokoly.</span><span class="sxs-lookup"><span data-stu-id="c7a90-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="c7a90-104">`TextFieldType` Vlastnost určuje, zda se jedná o soubor s oddělovači, nebo o pole s pevnou šířkou textu.</span><span class="sxs-lookup"><span data-stu-id="c7a90-104">The `TextFieldType` property defines whether it is a delimited file or one with fixed-width fields of text.</span></span>  
  
### <a name="to-parse-a-comma-delimited-text-file"></a><span data-ttu-id="c7a90-105">Jak analyzovat textový soubor s oddělovači</span><span class="sxs-lookup"><span data-stu-id="c7a90-105">To parse a comma delimited text file</span></span>  
  
1. <span data-ttu-id="c7a90-106">Vytvořte nový `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="c7a90-106">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="c7a90-107">Následující kód vytvoří `TextFieldParser` pojmenované `MyReader` a otevře soubor. `test.txt`</span><span class="sxs-lookup"><span data-stu-id="c7a90-107">The following code creates the `TextFieldParser` named `MyReader` and opens the file `test.txt`.</span></span>  
  
     [!code-vb[VbFileIORead#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#15)]  
  
2. <span data-ttu-id="c7a90-108">Definujte `TextField` typ a oddělovač.</span><span class="sxs-lookup"><span data-stu-id="c7a90-108">Define the `TextField` type and delimiter.</span></span> <span data-ttu-id="c7a90-109">Následující kód definuje `TextFieldType` vlastnost jako `Delimited` a oddělovač jako ",".</span><span class="sxs-lookup"><span data-stu-id="c7a90-109">The following code defines the `TextFieldType` property as `Delimited` and the delimiter as ",".</span></span>  
  
     [!code-vb[VbFileIORead#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#16)]  
  
3. <span data-ttu-id="c7a90-110">Projděte pole v souboru.</span><span class="sxs-lookup"><span data-stu-id="c7a90-110">Loop through the fields in the file.</span></span> <span data-ttu-id="c7a90-111">Pokud jsou některé řádky poškozené, nahlaste chybu a pokračujte v analýze.</span><span class="sxs-lookup"><span data-stu-id="c7a90-111">If any lines are corrupt, report an error and continue parsing.</span></span> <span data-ttu-id="c7a90-112">Následující kód prochází souborem, zobrazením jednotlivých polí a vytvářením sestav pro všechna pole, která jsou formátována nesprávně.</span><span class="sxs-lookup"><span data-stu-id="c7a90-112">The following code loops through the file, displaying each field in turn and reporting any fields that are formatted incorrectly.</span></span>  
  
     [!code-vb[VbFileIORead#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#17)]  
  
4. <span data-ttu-id="c7a90-113">Zavřete bloky `While` a `Using` v nástroji `End While` a `End Using`.</span><span class="sxs-lookup"><span data-stu-id="c7a90-113">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#18)]  
  
## <a name="example"></a><span data-ttu-id="c7a90-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="c7a90-114">Example</span></span>  

 <span data-ttu-id="c7a90-115">Tento příklad čte ze souboru `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="c7a90-115">This example reads from the file `test.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a><span data-ttu-id="c7a90-116">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="c7a90-116">Robust programming</span></span>  

 <span data-ttu-id="c7a90-117">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="c7a90-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="c7a90-118">Řádek nelze analyzovat pomocí zadaného formátu (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="c7a90-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="c7a90-119">Zpráva o výjimce Určuje řádek, který způsobil výjimku, zatímco <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> vlastnost je přiřazena k textu obsaženému na řádku.</span><span class="sxs-lookup"><span data-stu-id="c7a90-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned the text contained in the line.</span></span>  
  
- <span data-ttu-id="c7a90-120">Zadaný soubor neexistuje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="c7a90-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="c7a90-121">Částečně důvěryhodná situace, kdy uživatel nemá dostatečná oprávnění pro přístup k souboru.</span><span class="sxs-lookup"><span data-stu-id="c7a90-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="c7a90-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="c7a90-122">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="c7a90-123">Cesta je příliš dlouhá (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="c7a90-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="c7a90-124">Uživatel nemá dostatečná oprávnění pro přístup k souboru (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="c7a90-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7a90-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="c7a90-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="c7a90-126">Postupy: Čtení z textových souborů s pevnou šířkou</span><span class="sxs-lookup"><span data-stu-id="c7a90-126">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="c7a90-127">Postupy: Čtení z textových souborů ve více formátech</span><span class="sxs-lookup"><span data-stu-id="c7a90-127">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="c7a90-128">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="c7a90-128">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="c7a90-129">Návod: Práce se soubory a adresáři v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c7a90-129">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="c7a90-130">Řešení potíží: Čtení z textových souborů a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="c7a90-130">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
