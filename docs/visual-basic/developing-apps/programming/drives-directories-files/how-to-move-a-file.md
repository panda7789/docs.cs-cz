---
title: 'Postupy: Přesunutí souboru'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
ms.openlocfilehash: 29c64a7a81028d47bf489212e6d8faec5e8dda75
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74335356"
---
# <a name="how-to-move-a-file-in-visual-basic"></a><span data-ttu-id="448c1-102">Postupy: Přesunutí souboru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="448c1-102">How to: Move a File in Visual Basic</span></span>

<span data-ttu-id="448c1-103">`My.Computer.FileSystem.MoveFile` Metodu lze použít k přesunutí souboru do jiné složky.</span><span class="sxs-lookup"><span data-stu-id="448c1-103">The `My.Computer.FileSystem.MoveFile` method can be used to move a file to another folder.</span></span> <span data-ttu-id="448c1-104">Pokud cílová struktura neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="448c1-104">If the target structure does not exist, it will be created.</span></span>  
  
### <a name="to-move-a-file"></a><span data-ttu-id="448c1-105">Přesunutí souboru</span><span class="sxs-lookup"><span data-stu-id="448c1-105">To move a file</span></span>  
  
- <span data-ttu-id="448c1-106">Použijte `MoveFile` metodu k přesunutí souboru, zadáním názvu a umístění souboru pro zdrojový soubor a cílový soubor.</span><span class="sxs-lookup"><span data-stu-id="448c1-106">Use the `MoveFile` method to move the file, specifying the file name and location for both the source file and the target file.</span></span> <span data-ttu-id="448c1-107">Tento příklad přesune soubor s názvem `test.txt` z `TestDir1` do `TestDir2`.</span><span class="sxs-lookup"><span data-stu-id="448c1-107">This example moves the file named `test.txt` from `TestDir1` to `TestDir2`.</span></span> <span data-ttu-id="448c1-108">Všimněte si, že název cílového souboru je zadán, i když je stejný jako název zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="448c1-108">Note that the target file name is specified even though it is the same as the source file name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#24)]  
  
### <a name="to-move-a-file-and-rename-it"></a><span data-ttu-id="448c1-109">Přesunutí souboru a jeho přejmenování</span><span class="sxs-lookup"><span data-stu-id="448c1-109">To move a file and rename it</span></span>  
  
- <span data-ttu-id="448c1-110">Použijte `MoveFile` metodu pro přesunutí souboru, zadání názvu a umístění zdrojového souboru, cílového umístění a nového názvu v cílovém umístění.</span><span class="sxs-lookup"><span data-stu-id="448c1-110">Use the `MoveFile` method to move the file, specifying the source file name and location, the target location, and the new name at the target location.</span></span> <span data-ttu-id="448c1-111">Tento příklad přesune soubor s názvem `test.txt` z `TestDir1` na `TestDir2` a přejmenuje ho `nexttest.txt`.</span><span class="sxs-lookup"><span data-stu-id="448c1-111">This example moves the file named `test.txt` from `TestDir1` to `TestDir2` and renames it `nexttest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#25)]  
  
## <a name="robust-programming"></a><span data-ttu-id="448c1-112">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="448c1-112">Robust Programming</span></span>  

 <span data-ttu-id="448c1-113">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="448c1-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="448c1-114">Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná \\ \\na.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="448c1-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="448c1-115">Cesta není platná, protože je `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="448c1-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="448c1-116">`destinationFileName`je `Nothing` nebo prázdný řetězec (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="448c1-116">`destinationFileName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="448c1-117">Zdrojový soubor není platný nebo neexistuje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="448c1-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="448c1-118">Kombinovaná cesta odkazuje na existující adresář, cílový soubor existuje a `overwrite` je nastaven na `False`, je používán soubor v cílovém adresáři se stejným názvem nebo uživatel nemá dostatečná oprávnění pro přístup k souboru (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="448c1-118">The combined path points to an existing directory, the destination file exists and `overwrite` is set to `False`, a file in the target directory with the same name is in use, or the user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="448c1-119">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu format<xref:System.NotSupportedException>().</span><span class="sxs-lookup"><span data-stu-id="448c1-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="448c1-120">`showUI`je nastaven na `True`, `onUserCancel` je nastaven na `ThrowException`a buď uživatel zrušil operaci, nebo dojde k nespecifikované vstupně-výstupní chybě (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="448c1-120">`showUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and either the user has cancelled the operation or an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="448c1-121">Cesta přesahuje maximální povolenou délku (<xref:System.IO.PathTooLongException>) definovanou systémem.</span><span class="sxs-lookup"><span data-stu-id="448c1-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="448c1-122">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="448c1-122">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="448c1-123">Uživatel nemá požadovaná oprávnění (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="448c1-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="448c1-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="448c1-124">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>
- [<span data-ttu-id="448c1-125">Postupy: Přejmenování souboru</span><span class="sxs-lookup"><span data-stu-id="448c1-125">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
- [<span data-ttu-id="448c1-126">Postupy: Vytvoření kopie souboru v jiném adresáři</span><span class="sxs-lookup"><span data-stu-id="448c1-126">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="448c1-127">Postupy: Analýza cest k souborům</span><span class="sxs-lookup"><span data-stu-id="448c1-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
