---
title: "Postupy: čtení z oddělených čárkou textových souborů v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bd88762179d9760bcce37b4c500a2bb118e09173
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a><span data-ttu-id="08807-102">Postupy: čtení z oddělených čárkou textových souborů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="08807-102">How to: read from comma-delimited text files in Visual Basic</span></span>
<span data-ttu-id="08807-103">`TextFieldParser` Objekt poskytuje způsob, jak snadno a efektivně analýza strukturovaných textových souborů, jako jsou protokoly.</span><span class="sxs-lookup"><span data-stu-id="08807-103">The `TextFieldParser` object provides a way to easily and efficiently parse structured text files, such as logs.</span></span> <span data-ttu-id="08807-104">`TextFieldType` Vlastnost definuje, zda je soubor s oddělovači nebo s pevnou šířkou textových polí.</span><span class="sxs-lookup"><span data-stu-id="08807-104">The `TextFieldType` property defines whether it is a delimited file or one with fixed-width fields of text.</span></span>  
  
### <a name="to-parse-a-comma-delimited-text-file"></a><span data-ttu-id="08807-105">Analyzovat čárkou textový soubor s oddělovači</span><span class="sxs-lookup"><span data-stu-id="08807-105">To parse a comma delimited text file</span></span>  
  
1.  <span data-ttu-id="08807-106">Vytvořte novou `TextFieldParser`.</span><span class="sxs-lookup"><span data-stu-id="08807-106">Create a new `TextFieldParser`.</span></span> <span data-ttu-id="08807-107">Následující kód vytvoří `TextFieldParser` s názvem `MyReader` a otevře soubor `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="08807-107">The following code creates the `TextFieldParser` named `MyReader` and opens the file `test.txt`.</span></span>  
  
     [!code-vb[VbFileIORead#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_1.vb)]  
  
2.  <span data-ttu-id="08807-108">Definování `TextField` typu a oddělovač.</span><span class="sxs-lookup"><span data-stu-id="08807-108">Define the `TextField` type and delimiter.</span></span> <span data-ttu-id="08807-109">Následující kód definuje `TextFieldType` vlastnost jako `Delimited` a oddělovač jako ",".</span><span class="sxs-lookup"><span data-stu-id="08807-109">The following code defines the `TextFieldType` property as `Delimited` and the delimiter as ",".</span></span>  
  
     [!code-vb[VbFileIORead#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_2.vb)]  
  
3.  <span data-ttu-id="08807-110">Projděte všechny pole v souboru.</span><span class="sxs-lookup"><span data-stu-id="08807-110">Loop through the fields in the file.</span></span> <span data-ttu-id="08807-111">Pokud jsou řádky poškozeny, ohlaste chybu a pokračujte v analýze.</span><span class="sxs-lookup"><span data-stu-id="08807-111">If any lines are corrupt, report an error and continue parsing.</span></span> <span data-ttu-id="08807-112">Následující kód prochází soubor, pak zobrazení každé pole a vytváření sestav všechna pole, které jsou v nesprávném formátu.</span><span class="sxs-lookup"><span data-stu-id="08807-112">The following code loops through the file, displaying each field in turn and reporting any fields that are formatted incorrectly.</span></span>  
  
     [!code-vb[VbFileIORead#17](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_3.vb)]  
  
4.  <span data-ttu-id="08807-113">Zavřít `While` a `Using` zablokuje s `End While` a `End Using`.</span><span class="sxs-lookup"><span data-stu-id="08807-113">Close the `While` and `Using` blocks with `End While` and `End Using`.</span></span>  
  
     [!code-vb[VbFileIORead#18](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_4.vb)]  
  
## <a name="example"></a><span data-ttu-id="08807-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="08807-114">Example</span></span>  
 <span data-ttu-id="08807-115">Tento příklad čte ze souboru `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="08807-115">This example reads from the file `test.txt`.</span></span>  
  
 [!code-vb[VbFileIORead#19](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_5.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="08807-116">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="08807-116">Robust programming</span></span>  
 <span data-ttu-id="08807-117">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="08807-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="08807-118">Řádek nelze analyzovat pomocí zadaného formátu (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span><span class="sxs-lookup"><span data-stu-id="08807-118">A row cannot be parsed using the specified format (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>).</span></span> <span data-ttu-id="08807-119">Zpráva o výjimce určuje řádek, který způsobil výjimku a <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> vlastnost je přiřazen obsažené v řádku textu.</span><span class="sxs-lookup"><span data-stu-id="08807-119">The exception message specifies the line causing the exception, while the <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> property is assigned the text contained in the line.</span></span>  
  
-   <span data-ttu-id="08807-120">Zadaný soubor neexistuje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="08807-120">The specified file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="08807-121">Stav částečným vztahem důvěryhodnosti, ve kterém uživatel nemá dostatečná oprávnění k přístupu k souboru.</span><span class="sxs-lookup"><span data-stu-id="08807-121">A partial-trust situation in which the user does not have sufficient permissions to access the file.</span></span> <span data-ttu-id="08807-122">(<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="08807-122">(<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="08807-123">Cesta je příliš dlouhá (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="08807-123">The path is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="08807-124">Uživatel nemá dostatečná oprávnění k přístupu k souboru (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="08807-124">The user does not have sufficient permissions to access the file (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08807-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="08807-125">See also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>  
 [<span data-ttu-id="08807-126">Postupy: čtení z textových souborů s pevnou délkou</span><span class="sxs-lookup"><span data-stu-id="08807-126">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)  
 [<span data-ttu-id="08807-127">Postupy: čtení z textových souborů ve více formátech</span><span class="sxs-lookup"><span data-stu-id="08807-127">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)  
 [<span data-ttu-id="08807-128">Analýza textových souborů pomocí objektu TextFieldParser</span><span class="sxs-lookup"><span data-stu-id="08807-128">Parsing Text Files with the TextFieldParser Object</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 [<span data-ttu-id="08807-129">Návod: Manipulace se soubory a adresáře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="08807-129">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 [<span data-ttu-id="08807-130">Řešení potíží: Čtení a zápis do textových souborů</span><span class="sxs-lookup"><span data-stu-id="08807-130">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
