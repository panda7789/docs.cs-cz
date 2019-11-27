---
title: 'Postupy: čtení z textových souborů'
ms.date: 07/20/2015
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
ms.openlocfilehash: 8af088ad269cc77bc5c83aedb86bde9af2e37a15
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334590"
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a><span data-ttu-id="c55fd-102">Postupy: Čtení z textových souborů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c55fd-102">How to: Read From Text Files in Visual Basic</span></span>

<span data-ttu-id="c55fd-103">Metoda <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> objektu `My.Computer.FileSystem` umožňuje čtení z textového souboru.</span><span class="sxs-lookup"><span data-stu-id="c55fd-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> method of the `My.Computer.FileSystem` object allows you to read from a text file.</span></span> <span data-ttu-id="c55fd-104">Kódování souboru lze určit, pokud obsah tohoto souboru používá nějaké kódování, například ASCII nebo UTF-8.</span><span class="sxs-lookup"><span data-stu-id="c55fd-104">The file encoding can be specified if the contents of the file use an encoding such as ASCII or UTF-8.</span></span>

<span data-ttu-id="c55fd-105">Při čtení ze souboru obsahujícího znaky s diakritikou budete muset určit kódování souboru.</span><span class="sxs-lookup"><span data-stu-id="c55fd-105">If you are reading from a file with extended characters, you will need to specify the file encoding.</span></span>

> [!NOTE]
> <span data-ttu-id="c55fd-106">Chcete-li číst soubor v jednom řádku textu, použijte metodu <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> objektu `My.Computer.FileSystem`.</span><span class="sxs-lookup"><span data-stu-id="c55fd-106">To read a file a single line of text at a time, use the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> method of the `My.Computer.FileSystem` object.</span></span> <span data-ttu-id="c55fd-107">Metoda `OpenTextFileReader` vrátí objekt <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="c55fd-107">The `OpenTextFileReader` method returns a <xref:System.IO.StreamReader> object.</span></span> <span data-ttu-id="c55fd-108">Můžete použít metodu <xref:System.IO.StreamReader.ReadLine%2A> objektu `StreamReader` pro čtení souboru po jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="c55fd-108">You can use the <xref:System.IO.StreamReader.ReadLine%2A> method of the `StreamReader` object to read a file one line at a time.</span></span> <span data-ttu-id="c55fd-109">Můžete otestovat na konec souboru pomocí metody <xref:System.IO.StreamReader.EndOfStream%2A> objektu `StreamReader`.</span><span class="sxs-lookup"><span data-stu-id="c55fd-109">You can test for the end of the file using the <xref:System.IO.StreamReader.EndOfStream%2A> method of the `StreamReader` object.</span></span>

## <a name="to-read-from-a-text-file"></a><span data-ttu-id="c55fd-110">Čtení z textového souboru</span><span class="sxs-lookup"><span data-stu-id="c55fd-110">To read from a text file</span></span>

<span data-ttu-id="c55fd-111">K načtení obsahu textového souboru do řetězce použijte metodu `ReadAllText` objektu `My.Computer.FileSystem` a zadejte cestu.</span><span class="sxs-lookup"><span data-stu-id="c55fd-111">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path.</span></span> <span data-ttu-id="c55fd-112">Následující příklad načte obsah souboru test.txt do řetězce a pak jej zobrazí v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="c55fd-112">The following example reads the contents of test.txt into a string and then displays it in a message box.</span></span>

[!code-vb[VbFileIORead#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#2)]

### <a name="to-read-from-a-text-file-that-is-encoded"></a><span data-ttu-id="c55fd-113">Čtení z textového souboru s kódováním</span><span class="sxs-lookup"><span data-stu-id="c55fd-113">To read from a text file that is encoded</span></span>

<span data-ttu-id="c55fd-114">Pomocí metody `ReadAllText` objektu `My.Computer.FileSystem` si můžete přečíst obsah textového souboru do řetězce a zadat cestu a typ kódování souboru.</span><span class="sxs-lookup"><span data-stu-id="c55fd-114">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path and file encoding type.</span></span> <span data-ttu-id="c55fd-115">Následující příklad načte obsah souboru test.txt s kódováním UTF32 do řetězce a pak jej zobrazí v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="c55fd-115">The following example reads the contents of the UTF32 file test.txt into a string and then displays it in a message box.</span></span>

[!code-vb[VbFileIORead#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#3)]

## <a name="robust-programming"></a><span data-ttu-id="c55fd-116">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="c55fd-116">Robust Programming</span></span>

<span data-ttu-id="c55fd-117">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="c55fd-117">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="c55fd-118">Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="c55fd-118">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="c55fd-119">Cesta není platná, protože je `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="c55fd-119">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="c55fd-120">Soubor neexistuje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="c55fd-120">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>

- <span data-ttu-id="c55fd-121">Soubor je používán jiným procesem nebo dojde k vstupně-výstupní chybě (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="c55fd-121">The file is in use by another process or an I/O error occurs (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="c55fd-122">Cesta překračuje maximální povolenou délku systému (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="c55fd-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="c55fd-123">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatný formát (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="c55fd-123">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="c55fd-124">K zápisu řetězce do vyrovnávací paměti (<xref:System.OutOfMemoryException>) není dostatek paměti.</span><span class="sxs-lookup"><span data-stu-id="c55fd-124">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>

- <span data-ttu-id="c55fd-125">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="c55fd-125">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

<span data-ttu-id="c55fd-126">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="c55fd-126">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="c55fd-127">Například soubor Form1. vb nemusí být Visual Basic zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="c55fd-127">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>

<span data-ttu-id="c55fd-128">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="c55fd-128">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="c55fd-129">Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.</span><span class="sxs-lookup"><span data-stu-id="c55fd-129">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>

## <a name="see-also"></a><span data-ttu-id="c55fd-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c55fd-130">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
- [<span data-ttu-id="c55fd-131">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="c55fd-131">Reading from Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [<span data-ttu-id="c55fd-132">Postupy: Čtení z textových souborů s oddělovačem čárkou</span><span class="sxs-lookup"><span data-stu-id="c55fd-132">How to: Read From Comma-Delimited Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="c55fd-133">Postupy: Čtení z textových souborů s pevnou šířkou</span><span class="sxs-lookup"><span data-stu-id="c55fd-133">How to: Read From Fixed-width Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="c55fd-134">Postupy: Čtení z textových souborů ve více formátech</span><span class="sxs-lookup"><span data-stu-id="c55fd-134">How to: Read From Text Files with Multiple Formats</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="c55fd-135">Řešení potíží: Čtení z textových souborů a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="c55fd-135">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="c55fd-136">Návod: manipulace se soubory a adresáři v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c55fd-136">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="c55fd-137">Kódování souborů</span><span class="sxs-lookup"><span data-stu-id="c55fd-137">File Encodings</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
