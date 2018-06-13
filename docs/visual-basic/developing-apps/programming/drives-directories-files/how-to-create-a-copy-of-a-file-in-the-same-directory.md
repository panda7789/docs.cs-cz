---
title: 'Postupy: Vytvoření kopie souboru ve stejném adresáři v jazyce Visual Basic'
ms.date: 07/20/2015
f1_keywords:
- File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
ms.openlocfilehash: 1147e89292181060589b38be2972e2ff1a3e386c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588931"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a><span data-ttu-id="19c17-102">Postupy: Vytvoření kopie souboru ve stejném adresáři v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="19c17-102">How to: Create a Copy of a File in the Same Directory in Visual Basic</span></span>
<span data-ttu-id="19c17-103">Použití `My.Computer.FileSystem.CopyFile` metoda kopírování souborů.</span><span class="sxs-lookup"><span data-stu-id="19c17-103">Use the `My.Computer.FileSystem.CopyFile` method to copy files.</span></span> <span data-ttu-id="19c17-104">Parametry umožňují přepsat existující soubory, přejmenujte soubor, zobrazit průběh operace a umožní uživateli na tlačítko Storno.</span><span class="sxs-lookup"><span data-stu-id="19c17-104">The parameters allow you to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a><span data-ttu-id="19c17-105">Vytvoření kopie souboru ve stejné složce</span><span class="sxs-lookup"><span data-stu-id="19c17-105">To create a copy of a file in the same folder</span></span>  
  
-   <span data-ttu-id="19c17-106">Použití `CopyFile` metoda, poskytuje cílový soubor a umístění.</span><span class="sxs-lookup"><span data-stu-id="19c17-106">Use the `CopyFile` method, supplying the target file and the location.</span></span> <span data-ttu-id="19c17-107">Následující příklad vytvoří kopii `test.txt` názvem `test2.txt`.</span><span class="sxs-lookup"><span data-stu-id="19c17-107">The following example creates a copy of `test.txt` called `test2.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#51](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_1.vb)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a><span data-ttu-id="19c17-108">Vytvoření kopie souboru ve stejné složce, přepíše existující soubory</span><span class="sxs-lookup"><span data-stu-id="19c17-108">To create a copy of a file in the same folder, overwriting existing files</span></span>  
  
-   <span data-ttu-id="19c17-109">Použití `CopyFile` metoda, poskytuje cílový soubor a umístění a nastavení `overwrite` k `True`.</span><span class="sxs-lookup"><span data-stu-id="19c17-109">Use the `CopyFile` method, supplying the target file and location, and setting `overwrite` to `True`.</span></span> <span data-ttu-id="19c17-110">Následující příklad vytvoří kopii `test.txt` názvem `test2.txt` a přepíše všechny existující soubory s tímto názvem.</span><span class="sxs-lookup"><span data-stu-id="19c17-110">The following example creates a copy of `test.txt` called `test2.txt` and overwrites any existing files by that name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#52](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_2.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="19c17-111">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="19c17-111">Robust Programming</span></span>  
 <span data-ttu-id="19c17-112">Vyvolání výjimky může způsobit následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="19c17-112">The following conditions may cause an exception to be thrown:</span></span>  
  
-   <span data-ttu-id="19c17-113">Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje jenom prázdné znaky, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="19c17-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="19c17-114">Systém nemohl načíst absolutní cestu (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="19c17-114">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="19c17-115">Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="19c17-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="19c17-116">Zdrojový soubor je neplatný nebo neexistuje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="19c17-116">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="19c17-117">Kombinované cesta odkazuje na existující adresář (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="19c17-117">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="19c17-118">Cílový soubor existuje a `overwrite` je nastaven na `False` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="19c17-118">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="19c17-119">Uživatel nemá dostatečná oprávnění k přístupu k souboru (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="19c17-119">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="19c17-120">Soubor v cílové složce se stejným názvem je používán (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="19c17-120">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="19c17-121">Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="19c17-121">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="19c17-122">`ShowUI` je nastavena na `True`, `onUserCancel` je nastaven na `ThrowException`, a uživatel zrušil operaci (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="19c17-122">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="19c17-123">`ShowUI` je nastavena na `True`, `onUserCancel` je nastaven na `ThrowException`, a dojde k nespecifikované chybě vstupně-výstupní operace (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="19c17-123">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="19c17-124">Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="19c17-124">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="19c17-125">Uživatel nemá požadované oprávnění (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="19c17-125">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="19c17-126">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="19c17-126">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19c17-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="19c17-127">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>  
 [<span data-ttu-id="19c17-128">Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře</span><span class="sxs-lookup"><span data-stu-id="19c17-128">How to: Copy Files with a Specific Pattern to a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)  
 [<span data-ttu-id="19c17-129">Postupy: Vytvoření kopie souboru v jiném adresáři</span><span class="sxs-lookup"><span data-stu-id="19c17-129">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)  
 [<span data-ttu-id="19c17-130">Postupy: Zkopírování adresáře do jiného adresáře</span><span class="sxs-lookup"><span data-stu-id="19c17-130">How to: Copy a Directory to Another Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)  
 [<span data-ttu-id="19c17-131">Postupy: Přejmenování souboru</span><span class="sxs-lookup"><span data-stu-id="19c17-131">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
