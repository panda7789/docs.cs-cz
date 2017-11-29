---
title: "Postupy: Přesunutí souboru v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 96c6d1d89c0dfe4720637202b42414047e96f146
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-move-a-file-in-visual-basic"></a><span data-ttu-id="fa9d0-102">Postupy: Přesunutí souboru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fa9d0-102">How to: Move a File in Visual Basic</span></span>
<span data-ttu-id="fa9d0-103">`My.Computer.FileSystem.MoveFile` Metoda slouží k přesunutí souboru do jiné složky.</span><span class="sxs-lookup"><span data-stu-id="fa9d0-103">The `My.Computer.FileSystem.MoveFile` method can be used to move a file to another folder.</span></span> <span data-ttu-id="fa9d0-104">Pokud cílová struktura neexistuje, bude vytvořen.</span><span class="sxs-lookup"><span data-stu-id="fa9d0-104">If the target structure does not exist, it will be created.</span></span>  
  
### <a name="to-move-a-file"></a><span data-ttu-id="fa9d0-105">Chcete-li přesunout soubor</span><span class="sxs-lookup"><span data-stu-id="fa9d0-105">To move a file</span></span>  
  
-   <span data-ttu-id="fa9d0-106">Použití `MoveFile` metoda přesunout soubor, zadáte název souboru a umístění pro cílový i zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="fa9d0-106">Use the `MoveFile` method to move the file, specifying the file name and location for both the source file and the target file.</span></span> <span data-ttu-id="fa9d0-107">Tento příklad přesune soubor s názvem `test.txt` z `TestDir1` k `TestDir2`.</span><span class="sxs-lookup"><span data-stu-id="fa9d0-107">This example moves the file named `test.txt` from `TestDir1` to `TestDir2`.</span></span> <span data-ttu-id="fa9d0-108">Všimněte si, zda je zadán název cílového souboru, i když je stejný jako název zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="fa9d0-108">Note that the target file name is specified even though it is the same as the source file name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_1.vb)]  
  
### <a name="to-move-a-file-and-rename-it"></a><span data-ttu-id="fa9d0-109">Přesunout soubor a přejmenujte ji</span><span class="sxs-lookup"><span data-stu-id="fa9d0-109">To move a file and rename it</span></span>  
  
-   <span data-ttu-id="fa9d0-110">Použití `MoveFile` metoda souboru, název zdrojového souboru a umístění, cílové umístění a název nového v cílovém umístění.</span><span class="sxs-lookup"><span data-stu-id="fa9d0-110">Use the `MoveFile` method to move the file, specifying the source file name and location, the target location, and the new name at the target location.</span></span> <span data-ttu-id="fa9d0-111">Tento příklad přesune soubor s názvem `test.txt` z `TestDir1` k `TestDir2` a přejmenuje ho `nexttest.txt`.</span><span class="sxs-lookup"><span data-stu-id="fa9d0-111">This example moves the file named `test.txt` from `TestDir1` to `TestDir2` and renames it `nexttest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#25](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-move-a-file_2.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="fa9d0-112">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="fa9d0-112">Robust Programming</span></span>  
 <span data-ttu-id="fa9d0-113">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="fa9d0-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="fa9d0-114">Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje jenom prázdné znaky, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="fa9d0-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="fa9d0-115">Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="fa9d0-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="fa9d0-116">`destinationFileName`je `Nothing` nebo prázdný řetězec (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="fa9d0-116">`destinationFileName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="fa9d0-117">Zdrojový soubor je neplatný nebo neexistuje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="fa9d0-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="fa9d0-118">Kombinovaná cesta odkazuje na existující adresář, cílový soubor existuje a `overwrite` je nastaven na `False`, nepoužívá soubor v cílovém adresáři se stejným názvem, nebo uživatel nemá dostatečná oprávnění k přístupu k souboru (<xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="fa9d0-118">The combined path points to an existing directory, the destination file exists and `overwrite` is set to `False`, a file in the target directory with the same name is in use, or the user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="fa9d0-119">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="fa9d0-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="fa9d0-120">`showUI`je nastavena na `True`, `onUserCancel` je nastaven na `ThrowException`a buď uživatel zrušil operaci nebo dojde k nespecifikované chybě vstupně-výstupní operace (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="fa9d0-120">`showUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and either the user has cancelled the operation or an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="fa9d0-121">Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="fa9d0-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="fa9d0-122">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="fa9d0-122">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="fa9d0-123">Uživatel nemá požadované oprávnění (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="fa9d0-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa9d0-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="fa9d0-124">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>  
 [<span data-ttu-id="fa9d0-125">Postupy: přejmenování souboru</span><span class="sxs-lookup"><span data-stu-id="fa9d0-125">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)  
 [<span data-ttu-id="fa9d0-126">Postupy: vytvoření kopie souboru v jiném adresáři</span><span class="sxs-lookup"><span data-stu-id="fa9d0-126">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)  
 [<span data-ttu-id="fa9d0-127">Postupy: Analýza cest k souborům</span><span class="sxs-lookup"><span data-stu-id="fa9d0-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
