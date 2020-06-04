---
title: 'Postupy: Přejmenování souboru'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: 3de41ee6627315f0e26964b75f564ff98fe472ec
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411587"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a><span data-ttu-id="126f6-102">Postupy: Přejmenování souboru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="126f6-102">How to: Rename a File in Visual Basic</span></span>

<span data-ttu-id="126f6-103">Použijte `RenameFile` metodu `My.Computer.FileSystem` objektu k přejmenování souboru zadáním aktuálního umístění, názvu souboru a nového názvu souboru.</span><span class="sxs-lookup"><span data-stu-id="126f6-103">Use the `RenameFile` method of the `My.Computer.FileSystem` object to rename a file by supplying the current location, file name, and the new file name.</span></span> <span data-ttu-id="126f6-104">Tuto metodu nelze použít k přesunutí souboru. `MoveFile`k přesunutí a přejmenování souboru použijte metodu.</span><span class="sxs-lookup"><span data-stu-id="126f6-104">This method cannot be used to move a file; use the `MoveFile` method to move and rename the file.</span></span>  
  
### <a name="to-rename-a-file"></a><span data-ttu-id="126f6-105">Přejmenování souboru</span><span class="sxs-lookup"><span data-stu-id="126f6-105">To rename a file</span></span>  
  
- <span data-ttu-id="126f6-106">`My.Computer.FileSystem.RenameFile`K přejmenování souboru použijte metodu.</span><span class="sxs-lookup"><span data-stu-id="126f6-106">Use the `My.Computer.FileSystem.RenameFile` method to rename a file.</span></span> <span data-ttu-id="126f6-107">Tento příklad přejmenuje soubor s názvem `Test.txt` na `SecondTest.txt` .</span><span class="sxs-lookup"><span data-stu-id="126f6-107">This example renames the file named `Test.txt` to `SecondTest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#9)]  
  
 <span data-ttu-id="126f6-108">Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="126f6-108">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="126f6-109">Ve výběru fragmentu kódu je fragment kódu umístěný v **systému souborů, ve kterém se zpracovávají jednotky, složky a soubory**.</span><span class="sxs-lookup"><span data-stu-id="126f6-109">In the code snippet picker, the snippet is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="126f6-110">Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="126f6-110">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="126f6-111">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="126f6-111">Robust Programming</span></span>  

 <span data-ttu-id="126f6-112">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="126f6-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="126f6-113">Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="126f6-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="126f6-114">`newName`obsahuje informace o cestě ( <xref:System.ArgumentException> ).</span><span class="sxs-lookup"><span data-stu-id="126f6-114">`newName` contains path information (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="126f6-115">Cesta není platná, protože je `Nothing` ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="126f6-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="126f6-116">`newName`je `Nothing` nebo prázdný řetězec ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="126f6-116">`newName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="126f6-117">Zdrojový soubor není platný nebo neexistuje ( <xref:System.IO.FileNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="126f6-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="126f6-118">Existuje existující soubor nebo adresář s názvem zadaným v `newName` ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="126f6-118">There is an existing file or directory with the name specified in `newName` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="126f6-119">Cesta přesahuje maximální povolenou délku () definovanou systémem <xref:System.IO.PathTooLongException> .</span><span class="sxs-lookup"><span data-stu-id="126f6-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="126f6-120">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu Format ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="126f6-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="126f6-121">Uživatel nemá potřebná oprávnění k zobrazení cesty ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="126f6-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="126f6-122">Uživatel nemá požadovaná oprávnění ( <xref:System.UnauthorizedAccessException> ).</span><span class="sxs-lookup"><span data-stu-id="126f6-122">The user does not have the required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="126f6-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="126f6-123">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [<span data-ttu-id="126f6-124">Postupy: Přesunutí souboru</span><span class="sxs-lookup"><span data-stu-id="126f6-124">How to: Move a File</span></span>](how-to-move-a-file.md)
- [<span data-ttu-id="126f6-125">Vytváření, odstraňování a přesouvání souborů a adresářů</span><span class="sxs-lookup"><span data-stu-id="126f6-125">Creating, Deleting, and Moving Files and Directories</span></span>](creating-deleting-and-moving-files-and-directories.md)
- [<span data-ttu-id="126f6-126">Postupy: Vytvoření kopie souboru ve stejném adresáři</span><span class="sxs-lookup"><span data-stu-id="126f6-126">How to: Create a Copy of a File in the Same Directory</span></span>](how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [<span data-ttu-id="126f6-127">Postupy: Vytvoření kopie souboru v jiném adresáři</span><span class="sxs-lookup"><span data-stu-id="126f6-127">How to: Create a Copy of a File in a Different Directory</span></span>](how-to-create-a-copy-of-a-file-in-a-different-directory.md)
