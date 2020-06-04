---
title: 'Postupy: Čtení z textových souborů'
ms.date: 07/20/2015
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
ms.openlocfilehash: 0d99209ed123686355e8d49c82ba23f94084f895
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411613"
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a><span data-ttu-id="e3304-102">Postupy: Čtení z textových souborů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e3304-102">How to: Read From Text Files in Visual Basic</span></span>

<span data-ttu-id="e3304-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A>Metoda `My.Computer.FileSystem` objektu umožňuje čtení z textového souboru.</span><span class="sxs-lookup"><span data-stu-id="e3304-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> method of the `My.Computer.FileSystem` object allows you to read from a text file.</span></span> <span data-ttu-id="e3304-104">Kódování souboru lze určit, pokud obsah tohoto souboru používá nějaké kódování, například ASCII nebo UTF-8.</span><span class="sxs-lookup"><span data-stu-id="e3304-104">The file encoding can be specified if the contents of the file use an encoding such as ASCII or UTF-8.</span></span>

<span data-ttu-id="e3304-105">Při čtení ze souboru obsahujícího znaky s diakritikou budete muset určit kódování souboru.</span><span class="sxs-lookup"><span data-stu-id="e3304-105">If you are reading from a file with extended characters, you will need to specify the file encoding.</span></span>

> [!NOTE]
> <span data-ttu-id="e3304-106">Chcete-li číst soubor v jednom řádku textu, použijte <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> metodu `My.Computer.FileSystem` objektu.</span><span class="sxs-lookup"><span data-stu-id="e3304-106">To read a file a single line of text at a time, use the <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> method of the `My.Computer.FileSystem` object.</span></span> <span data-ttu-id="e3304-107">Metoda `OpenTextFileReader` vrátí objekt <xref:System.IO.StreamReader>.</span><span class="sxs-lookup"><span data-stu-id="e3304-107">The `OpenTextFileReader` method returns a <xref:System.IO.StreamReader> object.</span></span> <span data-ttu-id="e3304-108">Můžete použít <xref:System.IO.StreamReader.ReadLine%2A> metodu `StreamReader` objektu pro čtení souboru po jednotlivých řádcích.</span><span class="sxs-lookup"><span data-stu-id="e3304-108">You can use the <xref:System.IO.StreamReader.ReadLine%2A> method of the `StreamReader` object to read a file one line at a time.</span></span> <span data-ttu-id="e3304-109">Můžete otestovat na konec souboru pomocí <xref:System.IO.StreamReader.EndOfStream%2A> metody `StreamReader` objektu.</span><span class="sxs-lookup"><span data-stu-id="e3304-109">You can test for the end of the file using the <xref:System.IO.StreamReader.EndOfStream%2A> method of the `StreamReader` object.</span></span>

## <a name="to-read-from-a-text-file"></a><span data-ttu-id="e3304-110">Čtení z textového souboru</span><span class="sxs-lookup"><span data-stu-id="e3304-110">To read from a text file</span></span>

<span data-ttu-id="e3304-111">Použijte `ReadAllText` metodu `My.Computer.FileSystem` objektu pro čtení obsahu textového souboru do řetězce a zadejte cestu.</span><span class="sxs-lookup"><span data-stu-id="e3304-111">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path.</span></span> <span data-ttu-id="e3304-112">Následující příklad načte obsah souboru test.txt do řetězce a pak jej zobrazí v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="e3304-112">The following example reads the contents of test.txt into a string and then displays it in a message box.</span></span>

[!code-vb[VbFileIORead#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#2)]

### <a name="to-read-from-a-text-file-that-is-encoded"></a><span data-ttu-id="e3304-113">Čtení z textového souboru s kódováním</span><span class="sxs-lookup"><span data-stu-id="e3304-113">To read from a text file that is encoded</span></span>

<span data-ttu-id="e3304-114">Použijte `ReadAllText` metodu `My.Computer.FileSystem` objektu pro čtení obsahu textového souboru do řetězce a zadejte cestu a typ kódování souboru.</span><span class="sxs-lookup"><span data-stu-id="e3304-114">Use the `ReadAllText` method of the `My.Computer.FileSystem` object to read the contents of a text file into a string, supplying the path and file encoding type.</span></span> <span data-ttu-id="e3304-115">Následující příklad načte obsah souboru test.txt s kódováním UTF32 do řetězce a pak jej zobrazí v okně se zprávou.</span><span class="sxs-lookup"><span data-stu-id="e3304-115">The following example reads the contents of the UTF32 file test.txt into a string and then displays it in a message box.</span></span>

[!code-vb[VbFileIORead#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#3)]

## <a name="robust-programming"></a><span data-ttu-id="e3304-116">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="e3304-116">Robust Programming</span></span>

<span data-ttu-id="e3304-117">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="e3304-117">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="e3304-118">Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení ( <xref:System.ArgumentException> ).</span><span class="sxs-lookup"><span data-stu-id="e3304-118">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="e3304-119">Cesta není platná, protože je `Nothing` ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="e3304-119">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="e3304-120">Soubor neexistuje ( <xref:System.IO.FileNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="e3304-120">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>

- <span data-ttu-id="e3304-121">Soubor je používán jiným procesem nebo dojde k vstupně-výstupní chybě ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="e3304-121">The file is in use by another process or an I/O error occurs (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="e3304-122">Cesta přesahuje maximální povolenou délku () definovanou systémem <xref:System.IO.PathTooLongException> .</span><span class="sxs-lookup"><span data-stu-id="e3304-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="e3304-123">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu Format ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="e3304-123">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="e3304-124">K zápisu řetězce do vyrovnávací paměti () není dostatek paměti <xref:System.OutOfMemoryException> .</span><span class="sxs-lookup"><span data-stu-id="e3304-124">There is not enough memory to write the string to buffer (<xref:System.OutOfMemoryException>).</span></span>

- <span data-ttu-id="e3304-125">Uživatel nemá potřebná oprávnění k zobrazení cesty ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="e3304-125">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

<span data-ttu-id="e3304-126">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="e3304-126">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="e3304-127">Například soubor Form1. vb nemusí být Visual Basic zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="e3304-127">For example, the file Form1.vb may not be a Visual Basic source file.</span></span>

<span data-ttu-id="e3304-128">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="e3304-128">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="e3304-129">Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.</span><span class="sxs-lookup"><span data-stu-id="e3304-129">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>

## <a name="see-also"></a><span data-ttu-id="e3304-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="e3304-130">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>
- [<span data-ttu-id="e3304-131">Čtení ze souborů</span><span class="sxs-lookup"><span data-stu-id="e3304-131">Reading from Files</span></span>](reading-from-files.md)
- [<span data-ttu-id="e3304-132">Postupy: Čtení z textových souborů s oddělovačem čárkou</span><span class="sxs-lookup"><span data-stu-id="e3304-132">How to: Read From Comma-Delimited Text Files</span></span>](how-to-read-from-comma-delimited-text-files.md)
- [<span data-ttu-id="e3304-133">Postupy: Čtení z textových souborů s pevnou šířkou</span><span class="sxs-lookup"><span data-stu-id="e3304-133">How to: Read From Fixed-width Text Files</span></span>](how-to-read-from-fixed-width-text-files.md)
- [<span data-ttu-id="e3304-134">Postupy: Čtení z textových souborů ve více formátech</span><span class="sxs-lookup"><span data-stu-id="e3304-134">How to: Read From Text Files with Multiple Formats</span></span>](how-to-read-from-text-files-with-multiple-formats.md)
- [<span data-ttu-id="e3304-135">Řešení potíží: Čtení z textových souborů a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="e3304-135">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="e3304-136">Návod: Práce se soubory a adresáři v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e3304-136">Walkthrough: Manipulating Files and Directories in Visual Basic</span></span>](walkthrough-manipulating-files-and-directories.md)
- [<span data-ttu-id="e3304-137">Kódování souborů</span><span class="sxs-lookup"><span data-stu-id="e3304-137">File Encodings</span></span>](file-encodings.md)
