---
title: 'Postupy: Vytvoření kopie souboru v jiném adresáři'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
ms.openlocfilehash: 3b4b41e105d6bb6a17fbb688aa4718b33c23b9d6
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401690"
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a><span data-ttu-id="2aaf8-102">Postupy: Vytvoření kopie souboru v jiném adresáři v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2aaf8-102">How to: Create a Copy of a File in a Different Directory in Visual Basic</span></span>

<span data-ttu-id="2aaf8-103">`My.Computer.FileSystem.CopyFile`Metoda umožňuje kopírování souborů.</span><span class="sxs-lookup"><span data-stu-id="2aaf8-103">The `My.Computer.FileSystem.CopyFile` method allows you to copy files.</span></span> <span data-ttu-id="2aaf8-104">Jeho parametry poskytují možnost přepsat stávající soubory, přejmenovat soubor, zobrazit průběh operace a umožnit uživateli zrušit operaci.</span><span class="sxs-lookup"><span data-stu-id="2aaf8-104">Its parameters provide the ability to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-copy-a-text-file-to-another-folder"></a><span data-ttu-id="2aaf8-105">Zkopírování textového souboru do jiné složky</span><span class="sxs-lookup"><span data-stu-id="2aaf8-105">To copy a text file to another folder</span></span>  
  
- <span data-ttu-id="2aaf8-106">Použijte `CopyFile` metodu ke zkopírování souboru, zadání zdrojového souboru a cílového adresáře.</span><span class="sxs-lookup"><span data-stu-id="2aaf8-106">Use the `CopyFile` method to copy a file, specifying a source file and the target directory.</span></span> <span data-ttu-id="2aaf8-107">`overwrite`Parametr umožňuje určit, jestli se mají přepsat existující soubory.</span><span class="sxs-lookup"><span data-stu-id="2aaf8-107">The `overwrite` parameter allows you to specify whether or not to overwrite existing files.</span></span> <span data-ttu-id="2aaf8-108">Následující příklady kódu ukazují, jak použít `CopyFile` .</span><span class="sxs-lookup"><span data-stu-id="2aaf8-108">The following code examples demonstrate how to use `CopyFile`.</span></span>  
  
     [!code-vb[VbFileIOMisc#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#24)]  
  
## <a name="robust-programming"></a><span data-ttu-id="2aaf8-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="2aaf8-109">Robust Programming</span></span>  

 <span data-ttu-id="2aaf8-110">Následující podmínky mohou způsobit vyvolání výjimky:</span><span class="sxs-lookup"><span data-stu-id="2aaf8-110">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="2aaf8-111">Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="2aaf8-111">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="2aaf8-112">Systém nemůže načíst absolutní cestu ( <xref:System.ArgumentException> ).</span><span class="sxs-lookup"><span data-stu-id="2aaf8-112">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="2aaf8-113">Cesta není platná, protože je `Nothing` ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="2aaf8-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="2aaf8-114">Zdrojový soubor není platný nebo neexistuje ( <xref:System.IO.FileNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="2aaf8-114">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="2aaf8-115">Kombinovaná cesta odkazuje na existující adresář ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="2aaf8-115">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="2aaf8-116">Cílový soubor existuje a `overwrite` je nastaven na hodnotu `False` ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="2aaf8-116">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="2aaf8-117">Uživatel nemá dostatečná oprávnění pro přístup k souboru ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="2aaf8-117">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="2aaf8-118">Soubor v cílové složce se stejným názvem se používá ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="2aaf8-118">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="2aaf8-119">Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu Format ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="2aaf8-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="2aaf8-120">`ShowUI`je nastaven na `True` , `onUserCancel` je nastaven na `ThrowException` a uživatel zrušil operaci ( <xref:System.OperationCanceledException> ).</span><span class="sxs-lookup"><span data-stu-id="2aaf8-120">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="2aaf8-121">`ShowUI`je nastaven na `True` , `onUserCancel` je nastaven na `ThrowException` a dojde k nespecifikované vstupně-výstupní chybě ( <xref:System.OperationCanceledException> ).</span><span class="sxs-lookup"><span data-stu-id="2aaf8-121">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="2aaf8-122">Cesta přesahuje maximální povolenou délku () definovanou systémem <xref:System.IO.PathTooLongException> .</span><span class="sxs-lookup"><span data-stu-id="2aaf8-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="2aaf8-123">Uživatel nemá požadovaná oprávnění ( <xref:System.UnauthorizedAccessException> ).</span><span class="sxs-lookup"><span data-stu-id="2aaf8-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="2aaf8-124">Uživatel nemá potřebná oprávnění k zobrazení cesty ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="2aaf8-124">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2aaf8-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="2aaf8-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="2aaf8-126">Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře</span><span class="sxs-lookup"><span data-stu-id="2aaf8-126">How to: Copy Files with a Specific Pattern to a Directory</span></span>](how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="2aaf8-127">Postupy: Vytvoření kopie souboru ve stejném adresáři</span><span class="sxs-lookup"><span data-stu-id="2aaf8-127">How to: Create a Copy of a File in the Same Directory</span></span>](how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [<span data-ttu-id="2aaf8-128">Postupy: Zkopírování adresáře do jiného adresáře</span><span class="sxs-lookup"><span data-stu-id="2aaf8-128">How to: Copy a Directory to Another Directory</span></span>](how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="2aaf8-129">Postupy: Přejmenování souboru</span><span class="sxs-lookup"><span data-stu-id="2aaf8-129">How to: Rename a File</span></span>](how-to-rename-a-file.md)
