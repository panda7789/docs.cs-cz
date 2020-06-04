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
ms.openlocfilehash: 77b2e0a4ebe36b68501f821ef5731935ee3b16a7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411626"
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a><span data-ttu-id="07a35-102">Postupy: čtení z textových souborů s pevnou šířkou v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="07a35-102">How to: read from fixed-width text files in Visual Basic</span></span>

<span data-ttu-id="07a35-103">`TextFieldParser`Objekt poskytuje způsob, jak snadno a efektivně analyzovat strukturované textové soubory, jako jsou protokoly.</span><span class="sxs-lookup"><span data-stu-id="07a35-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span>  
  
 <span data-ttu-id="07a35-104">`TextFieldType`Vlastnost definuje, zda je analyzovaný soubor soubor s oddělovači nebo který má pole s pevnou šířkou textu.</span><span class="sxs-lookup"><span data-stu-id="07a35-104">The `TextFieldType` property defines whether the parsed file is a delimited file or one that has fixed-width fields of text.</span></span> <span data-ttu-id="07a35-105">V textovém souboru s pevnou šířkou může mít pole na konci proměnlivou šířku.</span><span class="sxs-lookup"><span data-stu-id="07a35-105">In a fixed-width text file, the field at the end can have a variable width.</span></span> <span data-ttu-id="07a35-106">Chcete-li určit, že pole na konci má proměnnou Width, definujte ji tak, aby měla šířku menší nebo rovna nule.</span><span class="sxs-lookup"><span data-stu-id="07a35-106">To specify that the field at the end has a variable width, define it to have a width less than or equal to zero.</span></span>  
  
### <a name="to-parse-a-fixed-width-text-file"></a><span data-ttu-id="07a35-107">Chcete-li analyzovat textový soubor s pevnou šířkou</span><span class="sxs-lookup"><span data-stu-id="07a35-107">To parse a fixed-width text file</span></span>  
  
1. <span data-ttu-id="07a35-108">Vytvořte nový `TextFieldParser` .</span><span class="sxs-lookup"><span data-stu-id="07a35-108">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="07a35-109">Následující kód vytvoří `TextFieldParser` pojmenované `Reader` a otevře soubor `test.log` .</span><span class="sxs-lookup"><span data-stu-id="07a35-109">The following code creates the `TextFieldParser` named `Reader` and opens the file `test.log`.</span></span>  
  
     [!code-vb[VbFileIORead#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#9)]  
  
2. <span data-ttu-id="07a35-110">Definujte `TextFieldType` vlastnost jako `FixedWidth` a definujte šířku a formát.</span><span class="sxs-lookup"><span data-stu-id="07a35-110">Define the `TextFieldType` property as `FixedWidth`, defining the width and format.</span></span> <span data-ttu-id="07a35-111">Následující kód definuje sloupce textu; první je 5 znaků široké, druhý 10, třetí 11 a čtvrtá je proměnná Width.</span><span class="sxs-lookup"><span data-stu-id="07a35-111">The following code defines the columns of text; the first is 5 characters wide, the second 10, the third 11, and the fourth is of variable width.</span></span>  
  
     [!code-vb[VbFileIORead#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#10)]  
  
3. <span data-ttu-id="07a35-112">Projděte pole v souboru.</span><span class="sxs-lookup"><span data-stu-id="07a35-112">Loop through the fields in the file.</span></span> <span data-ttu-id="07a35-113">Pokud jsou některé řádky poškozené, nahlaste chybu a pokračujte v analýze.</span><span class="sxs-lookup"><span data-stu-id="07a35-113">If any lines are corrupted, report an error and continue parsing.</span></span>  
  
     [!code-vb[VbFileIORead#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#11)]  
  
4. <span data-ttu-id="07a35-114">Zavřete `While` bloky a v `Using` nástroji `End While` a `End Using` .</span><span class="sxs-lookup"><span data-stu-id="07a35-114">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#12)]  
  
## <a name="example"></a><span data-ttu-id="07a35-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="07a35-115">Example</span></span>  

 <span data-ttu-id="07a35-116">Tento příklad čte ze souboru `test.log` .</span><span class="sxs-lookup"><span data-stu-id="07a35-116">This example reads from the file `test.log`.</span></span>  
  
 [!code-vb[VbFileIORead#13](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#13)]  
  
## <a name="robust-programming"></a><span data-ttu-id="07a35-117">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="07a35-117">Robust programming</span></span>  

 <span data-ttu-id="07a35-118">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="07a35-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="07a35-119">Řádek nelze analyzovat pomocí zadaného formátu ( <xref:Microsoft.VisualBasic.FileIO.MalformedLineException> ).</span><span class="sxs-lookup"><span data-stu-id="07a35-119">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="07a35-120">Zpráva o výjimce Určuje řádek, který způsobil výjimku, zatímco <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> vlastnost je přiřazena k textu obsaženému na řádku.</span><span class="sxs-lookup"><span data-stu-id="07a35-120">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned to the text contained in the line.</span></span>  
  
- <span data-ttu-id="07a35-121">Zadaný soubor neexistuje ( <xref:System.IO.FileNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="07a35-121">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="07a35-122">Částečně důvěryhodná situace, kdy uživatel nemá dostatečná oprávnění pro přístup k souboru.</span><span class="sxs-lookup"><span data-stu-id="07a35-122">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="07a35-123">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="07a35-123">(<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="07a35-124">Cesta je příliš dlouhá ( <xref:System.IO.PathTooLongException> ).</span><span class="sxs-lookup"><span data-stu-id="07a35-124">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="07a35-125">Uživatel nemá dostatečná oprávnění pro přístup k souboru ( <xref:System.UnauthorizedAccessException> ).</span><span class="sxs-lookup"><span data-stu-id="07a35-125">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07a35-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="07a35-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- [<span data-ttu-id="07a35-127">Postupy: Čtení z textových souborů s oddělovačem čárkou</span><span class="sxs-lookup"><span data-stu-id="07a35-127">How to: Read From Comma-Delimited Text Files</span></span>](how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="07a35-128">Postupy: Čtení z textových souborů ve více formátech</span><span class="sxs-lookup"><span data-stu-id="07a35-128">How to: Read From Text Files with Multiple Formats</span></span>](how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="07a35-129">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="07a35-129">Parsing Text Files with the TextFieldParser Object</span></span>](parsing-text-files-with-the-textfieldparser-object.md)
- [<span data-ttu-id="07a35-130">Návod: Práce se soubory a adresáři v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="07a35-130">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="07a35-131">Řešení potíží: Čtení z textových souborů a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="07a35-131">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
