---
title: "Postupy: Přejmenování souboru v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 34316fabf63959389eee498a6063ac7c9a7b320a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-rename-a-file-in-visual-basic"></a><span data-ttu-id="f25e6-102">Postupy: Přejmenování souboru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="f25e6-102">How to: Rename a File in Visual Basic</span></span>
<span data-ttu-id="f25e6-103">Použití `RenameFile` metodu `My.Computer.FileSystem` objekt, který chcete přejmenovat soubor zadáním aktuální umístění, název souboru a nový název souboru.</span><span class="sxs-lookup"><span data-stu-id="f25e6-103">Use the `RenameFile` method of the `My.Computer.FileSystem` object to rename a file by supplying the current location, file name, and the new file name.</span></span> <span data-ttu-id="f25e6-104">Tento způsob nejde použít k přesouvání souborů. použít `MoveFile` metoda přesunout a přejmenujte soubor.</span><span class="sxs-lookup"><span data-stu-id="f25e6-104">This method cannot be used to move a file; use the `MoveFile` method to move and rename the file.</span></span>  
  
### <a name="to-rename-a-file"></a><span data-ttu-id="f25e6-105">Pokud chcete přejmenovat soubor</span><span class="sxs-lookup"><span data-stu-id="f25e6-105">To rename a file</span></span>  
  
-   <span data-ttu-id="f25e6-106">Použití `My.Computer.FileSystem.RenameFile` metoda chcete přejmenovat soubor.</span><span class="sxs-lookup"><span data-stu-id="f25e6-106">Use the `My.Computer.FileSystem.RenameFile` method to rename a file.</span></span> <span data-ttu-id="f25e6-107">Tento příklad přejmenuje soubor s názvem `Test.txt` k `SecondTest.txt`.</span><span class="sxs-lookup"><span data-stu-id="f25e6-107">This example renames the file named `Test.txt` to `SecondTest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-rename-a-file_1.vb)]  
  
 <span data-ttu-id="f25e6-108">Tento příklad kódu je také k dispozici jako IntelliSense fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="f25e6-108">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="f25e6-109">V Sběrač fragmentů kódu fragmentu nachází v **systému - zpracování jednotek, složek a souborů souborů**.</span><span class="sxs-lookup"><span data-stu-id="f25e6-109">In the code snippet picker, the snippet is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="f25e6-110">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="f25e6-110">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f25e6-111">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="f25e6-111">Robust Programming</span></span>  
 <span data-ttu-id="f25e6-112">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="f25e6-112">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="f25e6-113">Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje jenom prázdné znaky, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="f25e6-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="f25e6-114">`newName`obsahuje informace o cestě (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="f25e6-114">`newName` contains path information (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="f25e6-115">Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="f25e6-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="f25e6-116">`newName`je `Nothing` nebo prázdný řetězec (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="f25e6-116">`newName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="f25e6-117">Zdrojový soubor je neplatný nebo neexistuje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="f25e6-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="f25e6-118">Jde o existující soubor nebo adresář s názvem zadaným v `newName` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="f25e6-118">There is an existing file or directory with the name specified in `newName` (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="f25e6-119">Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="f25e6-119">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="f25e6-120">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="f25e6-120">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="f25e6-121">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="f25e6-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="f25e6-122">Uživatel nemá požadované oprávnění (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="f25e6-122">The user does not have the required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f25e6-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="f25e6-123">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>  
 [<span data-ttu-id="f25e6-124">Postupy: přesunutí souboru</span><span class="sxs-lookup"><span data-stu-id="f25e6-124">How to: Move a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)  
 [<span data-ttu-id="f25e6-125">Vytváření, odstraňování a přesouvání souborů a adresářů</span><span class="sxs-lookup"><span data-stu-id="f25e6-125">Creating, Deleting, and Moving Files and Directories</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)  
 [<span data-ttu-id="f25e6-126">Postupy: vytvoření kopie souboru ve stejném adresáři</span><span class="sxs-lookup"><span data-stu-id="f25e6-126">How to: Create a Copy of a File in the Same Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)  
 [<span data-ttu-id="f25e6-127">Postupy: vytvoření kopie souboru v jiném adresáři</span><span class="sxs-lookup"><span data-stu-id="f25e6-127">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
