---
title: 'Postupy: Vytvoření kopie souboru v jiném adresáři v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
ms.openlocfilehash: f14658cedd18aa22f354c0b7d9cca08960cd7690
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722119"
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a><span data-ttu-id="e27e4-102">Postupy: Vytvoření kopie souboru v jiném adresáři v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e27e4-102">How to: Create a Copy of a File in a Different Directory in Visual Basic</span></span>
<span data-ttu-id="e27e4-103">`My.Computer.FileSystem.CopyFile` Metody můžete zkopírovat soubory.</span><span class="sxs-lookup"><span data-stu-id="e27e4-103">The `My.Computer.FileSystem.CopyFile` method allows you to copy files.</span></span> <span data-ttu-id="e27e4-104">Parametry poskytují možnost přepsat existující soubory, přejmenujte soubor, zobrazí průběh operace a umožní uživateli na zrušení operace.</span><span class="sxs-lookup"><span data-stu-id="e27e4-104">Its parameters provide the ability to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-copy-a-text-file-to-another-folder"></a><span data-ttu-id="e27e4-105">Zkopírujte do textového souboru do jiné složky</span><span class="sxs-lookup"><span data-stu-id="e27e4-105">To copy a text file to another folder</span></span>  
  
-   <span data-ttu-id="e27e4-106">Použití `CopyFile` metoda kopírování souboru, soubor zdrojového a cílového adresáře.</span><span class="sxs-lookup"><span data-stu-id="e27e4-106">Use the `CopyFile` method to copy a file, specifying a source file and the target directory.</span></span> <span data-ttu-id="e27e4-107">`overwrite` Parametr umožňuje určit, jestli chcete přepsat existující soubory.</span><span class="sxs-lookup"><span data-stu-id="e27e4-107">The `overwrite` parameter allows you to specify whether or not to overwrite existing files.</span></span> <span data-ttu-id="e27e4-108">Následující příklady kódu ukazují, jak používat `CopyFile`.</span><span class="sxs-lookup"><span data-stu-id="e27e4-108">The following code examples demonstrate how to use `CopyFile`.</span></span>  
  
     [!code-vb[VbFileIOMisc#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-a-different-directory_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="e27e4-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="e27e4-109">Robust Programming</span></span>  
 <span data-ttu-id="e27e4-110">Následující podmínky mohou způsobit výjimku, která je vyvolána:</span><span class="sxs-lookup"><span data-stu-id="e27e4-110">The following conditions may cause an exception to be thrown:</span></span>  
  
-   <span data-ttu-id="e27e4-111">Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje pouze mezeru, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="e27e4-111">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="e27e4-112">Systém nemohl načíst absolutní cesta (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="e27e4-112">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="e27e4-113">Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="e27e4-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="e27e4-114">Zdrojový soubor je neplatný nebo neexistuje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="e27e4-114">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="e27e4-115">Kombinované cesta odkazuje na existující adresář (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="e27e4-115">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="e27e4-116">Cílový soubor existuje a `overwrite` je nastavena na `False` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="e27e4-116">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="e27e4-117">Uživatel nemá dostatečná oprávnění pro přístup k souboru (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="e27e4-117">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="e27e4-118">Soubor v cílové složce se stejným názvem se používá (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="e27e4-118">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="e27e4-119">Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="e27e4-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="e27e4-120">`ShowUI` je nastavena na `True`, `onUserCancel` je nastavena na `ThrowException`, a uživatel zrušil operaci (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="e27e4-120">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="e27e4-121">`ShowUI` je nastavena na `True`, `onUserCancel` je nastavena na `ThrowException`, a dojde k nespecifikované chybě vstupně-výstupních operací (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="e27e4-121">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="e27e4-122">Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="e27e4-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="e27e4-123">Uživatel nemá požadovaná oprávnění (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="e27e4-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="e27e4-124">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="e27e4-124">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e27e4-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e27e4-125">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="e27e4-126">Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře</span><span class="sxs-lookup"><span data-stu-id="e27e4-126">How to: Copy Files with a Specific Pattern to a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="e27e4-127">Postupy: Vytvoření kopie souboru ve stejném adresáři</span><span class="sxs-lookup"><span data-stu-id="e27e4-127">How to: Create a Copy of a File in the Same Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [<span data-ttu-id="e27e4-128">Postupy: Zkopírování adresáře do jiného adresáře</span><span class="sxs-lookup"><span data-stu-id="e27e4-128">How to: Copy a Directory to Another Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="e27e4-129">Postupy: Přejmenovat soubor</span><span class="sxs-lookup"><span data-stu-id="e27e4-129">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
