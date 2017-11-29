---
title: "Postupy: Čtení z textových souborů v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f75d89fb4ab10a8c116d4a0ab79c17ceb3efd0ce
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a><span data-ttu-id="ad023-102">Postupy: Čtení z textových souborů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ad023-102">How to: Read From Text Files in Visual Basic</span></span>
<span data-ttu-id="ad023-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> Metodu `My.Computer.FileSystem` objekt umožňuje čtení z textového souboru.</span><span class="sxs-lookup"><span data-stu-id="ad023-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> method of the `My.Computer.FileSystem` object allows you to read from a text file.</span></span> <span data-ttu-id="ad023-104">Kódování souboru lze určit, pokud obsah tohoto souboru používá nějaké kódování, například ASCII nebo UTF-8.</span><span class="sxs-lookup"><span data-stu-id="ad023-104">The file encoding can be specified if the contents of the file use an encoding such as ASCII or UTF-8.</span></span>  
  
 <span data-ttu-id="ad023-105">Při čtení ze souboru obsahujícího znaky s diakritikou budete muset určit kódování souboru.</span><span class="sxs-lookup"><span data-stu-id="ad023-105">If you are reading from a file with extended characters, you will need to specify the file encoding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ad023-106">Pokud chcete přečíst jeden řádek textu souboru, použijte <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> metodu `My.Computer.FileSystem` objektu.</span><span class="sxs-lookup"><span data-stu-id="ad023-106">To read a file a single line of text at a time, use the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> method of the `My.Computer.FileSystem` object.</span></span> <span data-ttu-id="ad023-107">`OpenTextFileReader` Metoda vrátí <xref:System.IO.StreamReader> objektu.</span><span class="sxs-lookup"><span data-stu-id="ad023-107">The `OpenTextFileReader` method returns a <xref:System.IO.StreamReader> object.</span></span> <span data-ttu-id="ad023-108">Můžete použít <xref:System.IO.StreamReader.ReadLine%2A> metodu `StreamReader` objektu určeného ke čtení souboru jeden řádek v čase.</span><span class="sxs-lookup"><span data-stu-id="ad023-108">You can use the <xref:System.IO.StreamReader.ReadLine%2A> method of the `StreamReader` object to read a file one line at a time.</span></span> <span data-ttu-id="ad023-109">Můžete otestovat na konci souboru pomocí <xref:System.IO.StreamReader.EndOfStream%2A> metodu `StreamReader` objektu.</span><span class="sxs-lookup"><span data-stu-id="ad023-109">You can test for the end of the file using the <xref:System.IO.StreamReader.EndOfStream%2A> method of the `StreamReader` object.</span></span>  
  
### <a name="to-read-from-a-text-file"></a><span data-ttu-id="ad023-110">Čtení z textového souboru</span><span class="sxs-lookup"><span data-stu-id="ad023-110">To read from a text file</span></span>  
  
-   <span data-ttu-id="ad023-111">Použití `ReadAllText` metodu `My.Computer.FileSystem` objektu určeného ke čtení obsahu textového souboru do řetězce cesty.</span><span class="sxs-lookup"><span data-stu-id="ad023-111">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path.</span></span> <span data-ttu-id="ad023-112">Následující příklad načte obsah souboru test.txt do řetězce a pak jej zobrazí v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="ad023-112">The following example reads the contents of test.txt into a string and then displays it in a message box.</span></span>  
  
     [!code-vb[VbFileIORead#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_1.vb)]  
  
### <a name="to-read-from-a-text-file-that-is-encoded"></a><span data-ttu-id="ad023-113">Čtení z textového souboru s kódováním</span><span class="sxs-lookup"><span data-stu-id="ad023-113">To read from a text file that is encoded</span></span>  
  
-   <span data-ttu-id="ad023-114">Použití `ReadAllText` metodu `My.Computer.FileSystem` objekt k načtení obsahu textového souboru do řetězce cesty a souboru typ kódování.</span><span class="sxs-lookup"><span data-stu-id="ad023-114">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path and file encoding type.</span></span> <span data-ttu-id="ad023-115">Následující příklad načte obsah souboru test.txt s kódováním UTF32 do řetězce a pak jej zobrazí v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="ad023-115">The following example reads the contents of the UTF32 file test.txt into a string and then displays it in a message box.</span></span>  
  
     [!code-vb[VbFileIORead#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_2.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="ad023-116">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="ad023-116">Robust Programming</span></span>  
 <span data-ttu-id="ad023-117">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="ad023-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="ad023-118">Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje jenom prázdné znaky, obsahuje neplatné znaky nebo je cesta zařízení (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="ad023-118">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="ad023-119">Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="ad023-119">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="ad023-120">Soubor neexistuje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="ad023-120">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="ad023-121">Soubor je používán jiným procesem nebo dojde k chybě vstupně-výstupní operace (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="ad023-121">The file is in use by another process or an I/O error occurs (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="ad023-122">Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="ad023-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="ad023-123">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="ad023-123">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="ad023-124">Není dostatek paměti pro zápis řetězec do vyrovnávací paměti (<xref:System.OutOfMemoryException>).</span><span class="sxs-lookup"><span data-stu-id="ad023-124">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>  
  
-   <span data-ttu-id="ad023-125">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="ad023-125">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
 <span data-ttu-id="ad023-126">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="ad023-126">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="ad023-127">Například soubor Form1.vb nemusí být [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="ad023-127">For example, the file Form1.vb may not be a [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] source file.</span></span>  
  
 <span data-ttu-id="ad023-128">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="ad023-128">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="ad023-129">Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.</span><span class="sxs-lookup"><span data-stu-id="ad023-129">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad023-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad023-130">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>  
 [<span data-ttu-id="ad023-131">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="ad023-131">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [<span data-ttu-id="ad023-132">Postupy: čtení z oddělených čárkou textových souborů</span><span class="sxs-lookup"><span data-stu-id="ad023-132">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [<span data-ttu-id="ad023-133">Postupy: čtení z textových souborů s pevnou délkou</span><span class="sxs-lookup"><span data-stu-id="ad023-133">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)  
 [<span data-ttu-id="ad023-134">Postupy: čtení z textových souborů ve více formátech</span><span class="sxs-lookup"><span data-stu-id="ad023-134">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)  
 [<span data-ttu-id="ad023-135">Řešení potíží: Čtení a zápis do textových souborů</span><span class="sxs-lookup"><span data-stu-id="ad023-135">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 [<span data-ttu-id="ad023-136">Návod: Manipulace se soubory a adresáře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ad023-136">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 [<span data-ttu-id="ad023-137">Kódování souborů</span><span class="sxs-lookup"><span data-stu-id="ad023-137">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
