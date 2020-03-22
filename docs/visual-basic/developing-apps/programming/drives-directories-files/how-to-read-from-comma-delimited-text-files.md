---
title: 'Postup: čtení z textových souborů oddělených čárkami'
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
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a><span data-ttu-id="63634-102">Postup: čtení z textových souborů oddělených čárkami v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="63634-102">How to: read from comma-delimited text files in Visual Basic</span></span>

<span data-ttu-id="63634-103">Objekt `TextFieldParser` poskytuje způsob, jak snadno a efektivně analyzovat strukturované textové soubory, jako jsou například protokoly.</span><span class="sxs-lookup"><span data-stu-id="63634-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="63634-104">Vlastnost `TextFieldType` definuje, zda se jedná o soubor s oddělovačem nebo o soubor s poli textu s pevnou šířkou.</span><span class="sxs-lookup"><span data-stu-id="63634-104">The `TextFieldType` property defines whether it is a delimited file or one with fixed-width fields of text.</span></span>  
  
### <a name="to-parse-a-comma-delimited-text-file"></a><span data-ttu-id="63634-105">Analýza textového souboru odděleného čárkami</span><span class="sxs-lookup"><span data-stu-id="63634-105">To parse a comma delimited text file</span></span>  
  
1. <span data-ttu-id="63634-106">Vytvořte `TextFieldParser`nový .</span><span class="sxs-lookup"><span data-stu-id="63634-106">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="63634-107">Následující kód vytvoří `TextFieldParser` `MyReader` pojmenovaný a `test.txt`otevře soubor .</span><span class="sxs-lookup"><span data-stu-id="63634-107">The following code creates the `TextFieldParser` named `MyReader` and opens the file `test.txt`.</span></span>  
  
     [!code-vb[VbFileIORead#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#15)]  
  
2. <span data-ttu-id="63634-108">Definujte `TextField` typ a oddělovač.</span><span class="sxs-lookup"><span data-stu-id="63634-108">Define the `TextField` type and delimiter.</span></span> <span data-ttu-id="63634-109">Následující kód definuje `TextFieldType` vlastnost `Delimited` jako a oddělovač jako ",".</span><span class="sxs-lookup"><span data-stu-id="63634-109">The following code defines the `TextFieldType` property as `Delimited` and the delimiter as ",".</span></span>  
  
     [!code-vb[VbFileIORead#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#16)]  
  
3. <span data-ttu-id="63634-110">Smyčka procházet pole v souboru.</span><span class="sxs-lookup"><span data-stu-id="63634-110">Loop through the fields in the file.</span></span> <span data-ttu-id="63634-111">Pokud jsou některé řádky poškozeny, nahlaste chybu a pokračujte v provádění analýzy.</span><span class="sxs-lookup"><span data-stu-id="63634-111">If any lines are corrupt, report an error and continue parsing.</span></span> <span data-ttu-id="63634-112">Následující kód prochází souborem, zobrazuje každé pole a hlásí všechna pole, která jsou nesprávně formátována.</span><span class="sxs-lookup"><span data-stu-id="63634-112">The following code loops through the file, displaying each field in turn and reporting any fields that are formatted incorrectly.</span></span>  
  
     [!code-vb[VbFileIORead#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#17)]  
  
4. <span data-ttu-id="63634-113">Zavřete `While` `Using` bloky `End While` a `End Using`s a .</span><span class="sxs-lookup"><span data-stu-id="63634-113">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#18)]  
  
## <a name="example"></a><span data-ttu-id="63634-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="63634-114">Example</span></span>  

 <span data-ttu-id="63634-115">Tento příklad čte `test.txt`ze souboru .</span><span class="sxs-lookup"><span data-stu-id="63634-115">This example reads from the file `test.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a><span data-ttu-id="63634-116">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="63634-116">Robust programming</span></span>  

 <span data-ttu-id="63634-117">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="63634-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="63634-118">Řádek nelze analyzovat pomocí zadaného formátu<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>( ).</span><span class="sxs-lookup"><span data-stu-id="63634-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="63634-119">Zpráva o výjimce určuje řádek způsobující <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> výjimku, zatímco vlastnosti je přiřazen text obsažený v řádku.</span><span class="sxs-lookup"><span data-stu-id="63634-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned the text contained in the line.</span></span>  
  
- <span data-ttu-id="63634-120">Zadaný soubor neexistuje<xref:System.IO.FileNotFoundException>( ).</span><span class="sxs-lookup"><span data-stu-id="63634-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="63634-121">Situace částečné důvěryhodnosti, ve které uživatel nemá dostatečná oprávnění pro přístup k souboru.</span><span class="sxs-lookup"><span data-stu-id="63634-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="63634-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="63634-122">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="63634-123">Cesta je příliš<xref:System.IO.PathTooLongException>dlouhá ( ).</span><span class="sxs-lookup"><span data-stu-id="63634-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="63634-124">Uživatel nemá dostatečná oprávnění pro přístup<xref:System.UnauthorizedAccessException>k souboru ( ).</span><span class="sxs-lookup"><span data-stu-id="63634-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63634-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="63634-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="63634-126">Postupy: Čtení z textových souborů s pevnou šířkou</span><span class="sxs-lookup"><span data-stu-id="63634-126">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="63634-127">Postupy: Čtení z textových souborů ve více formátech</span><span class="sxs-lookup"><span data-stu-id="63634-127">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="63634-128">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="63634-128">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="63634-129">Návod: Práce se soubory a adresáři v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="63634-129">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="63634-130">Řešení potíží: Čtení z textových souborů a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="63634-130">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
