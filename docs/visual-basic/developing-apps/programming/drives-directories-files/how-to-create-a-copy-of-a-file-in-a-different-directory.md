---
title: 'Postupy: Vytvoření kopie souboru v jiném adresáři v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
ms.openlocfilehash: 1584e2a768562670662d3a9636d23f0ffe38547e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589470"
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a><span data-ttu-id="18d17-102">Postupy: Vytvoření kopie souboru v jiném adresáři v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="18d17-102">How to: Create a Copy of a File in a Different Directory in Visual Basic</span></span>
<span data-ttu-id="18d17-103">`My.Computer.FileSystem.CopyFile` Metoda umožňuje kopírovat soubory.</span><span class="sxs-lookup"><span data-stu-id="18d17-103">The `My.Computer.FileSystem.CopyFile` method allows you to copy files.</span></span> <span data-ttu-id="18d17-104">Jeho parametry umožňují přepsat existující soubory, přejmenujte soubor, zobrazit průběh operace a umožní uživateli na tlačítko Storno.</span><span class="sxs-lookup"><span data-stu-id="18d17-104">Its parameters provide the ability to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-copy-a-text-file-to-another-folder"></a><span data-ttu-id="18d17-105">Zkopírovat do textového souboru do jiné složky</span><span class="sxs-lookup"><span data-stu-id="18d17-105">To copy a text file to another folder</span></span>  
  
-   <span data-ttu-id="18d17-106">Použití `CopyFile` metoda zkopírovat soubor, zadáním zdrojového souboru a cílové složky.</span><span class="sxs-lookup"><span data-stu-id="18d17-106">Use the `CopyFile` method to copy a file, specifying a source file and the target directory.</span></span> <span data-ttu-id="18d17-107">`overwrite` Parametr umožňuje určit, zda chcete přepsat existující soubory.</span><span class="sxs-lookup"><span data-stu-id="18d17-107">The `overwrite` parameter allows you to specify whether or not to overwrite existing files.</span></span> <span data-ttu-id="18d17-108">Následující příklady kódu ukazují, jak používat `CopyFile`.</span><span class="sxs-lookup"><span data-stu-id="18d17-108">The following code examples demonstrate how to use `CopyFile`.</span></span>  
  
     [!code-vb[VbFileIOMisc#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-a-different-directory_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="18d17-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="18d17-109">Robust Programming</span></span>  
 <span data-ttu-id="18d17-110">Vyvolání výjimky může způsobit následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="18d17-110">The following conditions may cause an exception to be thrown:</span></span>  
  
-   <span data-ttu-id="18d17-111">Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje jenom prázdné znaky, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="18d17-111">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="18d17-112">Systém nemohl načíst absolutní cestu (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="18d17-112">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="18d17-113">Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="18d17-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="18d17-114">Zdrojový soubor je neplatný nebo neexistuje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="18d17-114">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="18d17-115">Kombinované cesta odkazuje na existující adresář (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="18d17-115">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="18d17-116">Cílový soubor existuje a `overwrite` je nastaven na `False` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="18d17-116">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="18d17-117">Uživatel nemá dostatečná oprávnění k přístupu k souboru (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="18d17-117">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="18d17-118">Soubor v cílové složce se stejným názvem je používán (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="18d17-118">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="18d17-119">Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="18d17-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="18d17-120">`ShowUI` je nastavena na `True`, `onUserCancel` je nastaven na `ThrowException`, a uživatel zrušil operaci (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="18d17-120">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="18d17-121">`ShowUI` je nastavena na `True`, `onUserCancel` je nastaven na `ThrowException`, a dojde k nespecifikované chybě vstupně-výstupní operace (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="18d17-121">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="18d17-122">Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="18d17-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="18d17-123">Uživatel nemá požadované oprávnění (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="18d17-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="18d17-124">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="18d17-124">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18d17-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="18d17-125">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>  
 [<span data-ttu-id="18d17-126">Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře</span><span class="sxs-lookup"><span data-stu-id="18d17-126">How to: Copy Files with a Specific Pattern to a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)  
 [<span data-ttu-id="18d17-127">Postupy: Vytvoření kopie souboru ve stejném adresáři</span><span class="sxs-lookup"><span data-stu-id="18d17-127">How to: Create a Copy of a File in the Same Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)  
 [<span data-ttu-id="18d17-128">Postupy: Zkopírování adresáře do jiného adresáře</span><span class="sxs-lookup"><span data-stu-id="18d17-128">How to: Copy a Directory to Another Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)  
 [<span data-ttu-id="18d17-129">Postupy: Přejmenování souboru</span><span class="sxs-lookup"><span data-stu-id="18d17-129">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
