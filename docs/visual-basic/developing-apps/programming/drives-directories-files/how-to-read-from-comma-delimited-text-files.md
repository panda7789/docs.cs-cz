---
title: 'Postupy: čtení z textových souborů s hodnotami oddělenými čárkou'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
ms.openlocfilehash: ba62a0226a1a83326cbc7ab393d135763a7c7cb2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411639"
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a><span data-ttu-id="1b7a5-102">Postupy: čtení z textových souborů s oddělovači ve formátu čárky v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1b7a5-102">How to: read from comma-delimited text files in Visual Basic</span></span>

<span data-ttu-id="1b7a5-103">`TextFieldParser`Objekt poskytuje způsob, jak snadno a efektivně analyzovat strukturované textové soubory, jako jsou protokoly.</span><span class="sxs-lookup"><span data-stu-id="1b7a5-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="1b7a5-104">`TextFieldType`Vlastnost určuje, zda se jedná o soubor s oddělovači, nebo o pole s pevnou šířkou textu.</span><span class="sxs-lookup"><span data-stu-id="1b7a5-104">The `TextFieldType` property defines whether it is a delimited file or one with fixed-width fields of text.</span></span>  
  
### <a name="to-parse-a-comma-delimited-text-file"></a><span data-ttu-id="1b7a5-105">Jak analyzovat textový soubor s oddělovači</span><span class="sxs-lookup"><span data-stu-id="1b7a5-105">To parse a comma delimited text file</span></span>  
  
1. <span data-ttu-id="1b7a5-106">Vytvořte nový `TextFieldParser` .</span><span class="sxs-lookup"><span data-stu-id="1b7a5-106">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="1b7a5-107">Následující kód vytvoří `TextFieldParser` pojmenované `MyReader` a otevře soubor `test.txt` .</span><span class="sxs-lookup"><span data-stu-id="1b7a5-107">The following code creates the `TextFieldParser` named `MyReader` and opens the file `test.txt`.</span></span>  
  
     [!code-vb[VbFileIORead#15](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#15)]  
  
2. <span data-ttu-id="1b7a5-108">Definujte `TextField` typ a oddělovač.</span><span class="sxs-lookup"><span data-stu-id="1b7a5-108">Define the `TextField` type and delimiter.</span></span> <span data-ttu-id="1b7a5-109">Následující kód definuje `TextFieldType` vlastnost jako `Delimited` a oddělovač jako ",".</span><span class="sxs-lookup"><span data-stu-id="1b7a5-109">The following code defines the `TextFieldType` property as `Delimited` and the delimiter as ",".</span></span>  
  
     [!code-vb[VbFileIORead#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#16)]  
  
3. <span data-ttu-id="1b7a5-110">Projděte pole v souboru.</span><span class="sxs-lookup"><span data-stu-id="1b7a5-110">Loop through the fields in the file.</span></span> <span data-ttu-id="1b7a5-111">Pokud jsou některé řádky poškozené, nahlaste chybu a pokračujte v analýze.</span><span class="sxs-lookup"><span data-stu-id="1b7a5-111">If any lines are corrupt, report an error and continue parsing.</span></span> <span data-ttu-id="1b7a5-112">Následující kód prochází souborem, zobrazením jednotlivých polí a vytvářením sestav pro všechna pole, která jsou formátována nesprávně.</span><span class="sxs-lookup"><span data-stu-id="1b7a5-112">The following code loops through the file, displaying each field in turn and reporting any fields that are formatted incorrectly.</span></span>  
  
     [!code-vb[VbFileIORead#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#17)]  
  
4. <span data-ttu-id="1b7a5-113">Zavřete `While` bloky a v `Using` nástroji `End While` a `End Using` .</span><span class="sxs-lookup"><span data-stu-id="1b7a5-113">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#18)]  
  
## <a name="example"></a><span data-ttu-id="1b7a5-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="1b7a5-114">Example</span></span>  

 <span data-ttu-id="1b7a5-115">Tento příklad čte ze souboru `test.txt` .</span><span class="sxs-lookup"><span data-stu-id="1b7a5-115">This example reads from the file `test.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#19)]  
  
## <a name="robust-programming"></a><span data-ttu-id="1b7a5-116">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="1b7a5-116">Robust programming</span></span>  

 <span data-ttu-id="1b7a5-117">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="1b7a5-117">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="1b7a5-118">Řádek nelze analyzovat pomocí zadaného formátu ( <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> ).</span><span class="sxs-lookup"><span data-stu-id="1b7a5-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="1b7a5-119">Zpráva o výjimce Určuje řádek, který způsobil výjimku, zatímco <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> vlastnost je přiřazena k textu obsaženému na řádku.</span><span class="sxs-lookup"><span data-stu-id="1b7a5-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned the text contained in the line.</span></span>  
  
- <span data-ttu-id="1b7a5-120">Zadaný soubor neexistuje ( <xref:System.IO.FileNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="1b7a5-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="1b7a5-121">Částečně důvěryhodná situace, kdy uživatel nemá dostatečná oprávnění pro přístup k souboru.</span><span class="sxs-lookup"><span data-stu-id="1b7a5-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="1b7a5-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="1b7a5-122">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="1b7a5-123">Cesta je příliš dlouhá ( <xref:System.IO.PathTooLongException> ).</span><span class="sxs-lookup"><span data-stu-id="1b7a5-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="1b7a5-124">Uživatel nemá dostatečná oprávnění pro přístup k souboru ( <xref:System.UnauthorizedAccessException> ).</span><span class="sxs-lookup"><span data-stu-id="1b7a5-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b7a5-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="1b7a5-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="1b7a5-126">Postupy: Čtení z textových souborů s pevnou šířkou</span><span class="sxs-lookup"><span data-stu-id="1b7a5-126">How to: Read From Fixed-width Text Files</span></span>](how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="1b7a5-127">Postupy: Čtení z textových souborů ve více formátech</span><span class="sxs-lookup"><span data-stu-id="1b7a5-127">How to: Read From Text Files with Multiple Formats</span></span>](how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="1b7a5-128">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="1b7a5-128">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="1b7a5-129">Návod: Práce se soubory a adresáři v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1b7a5-129">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="1b7a5-130">Řešení potíží: Čtení z textových souborů a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="1b7a5-130">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
