---
title: 'Postupy: Vytvoření kopie souboru v jiném adresáři'
ms.date: 07/20/2015
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
ms.openlocfilehash: e9a14e1f3743979548b92a3db653d09a470a1875
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348833"
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a><span data-ttu-id="95881-102">Postupy: Vytvoření kopie souboru v jiném adresáři v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="95881-102">How to: Create a Copy of a File in a Different Directory in Visual Basic</span></span>

<span data-ttu-id="95881-103">Metoda `My.Computer.FileSystem.CopyFile` umožňuje kopírovat soubory.</span><span class="sxs-lookup"><span data-stu-id="95881-103">The `My.Computer.FileSystem.CopyFile` method allows you to copy files.</span></span> <span data-ttu-id="95881-104">Jeho parametry umožňují přepsat existující soubory, přejmenovat soubor, zobrazit průběh operace a umožnit uživateli operaci zrušit.</span><span class="sxs-lookup"><span data-stu-id="95881-104">Its parameters provide the ability to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-copy-a-text-file-to-another-folder"></a><span data-ttu-id="95881-105">Kopírování textového souboru do jiné složky</span><span class="sxs-lookup"><span data-stu-id="95881-105">To copy a text file to another folder</span></span>  
  
- <span data-ttu-id="95881-106">Pomocí `CopyFile` této metody zkopírujte soubor a určete zdrojový soubor a cílový adresář.</span><span class="sxs-lookup"><span data-stu-id="95881-106">Use the `CopyFile` method to copy a file, specifying a source file and the target directory.</span></span> <span data-ttu-id="95881-107">Parametr `overwrite` umožňuje určit, zda chcete přepsat existující soubory.</span><span class="sxs-lookup"><span data-stu-id="95881-107">The `overwrite` parameter allows you to specify whether or not to overwrite existing files.</span></span> <span data-ttu-id="95881-108">Následující příklady kódu ukazují, `CopyFile`jak používat .</span><span class="sxs-lookup"><span data-stu-id="95881-108">The following code examples demonstrate how to use `CopyFile`.</span></span>  
  
     [!code-vb[VbFileIOMisc#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#24)]  
  
## <a name="robust-programming"></a><span data-ttu-id="95881-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="95881-109">Robust Programming</span></span>  

 <span data-ttu-id="95881-110">Následující podmínky mohou způsobit, že bude vyvolána výjimka:</span><span class="sxs-lookup"><span data-stu-id="95881-110">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="95881-111">Cesta není platná z jednoho z následujících důvodů: jedná se o řetězec nulové délky, obsahuje pouze prázdné znaky, \\ \\\\obsahuje neplatné znaky nebo se jedná o cestu zařízení (začíná na . ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="95881-111">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="95881-112">Systém nemohl načíst absolutní<xref:System.ArgumentException>cestu ( ).</span><span class="sxs-lookup"><span data-stu-id="95881-112">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="95881-113">Cesta není platná, protože `Nothing` <xref:System.ArgumentNullException>je ( ).</span><span class="sxs-lookup"><span data-stu-id="95881-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="95881-114">Zdrojový soubor není platný nebo neexistuje<xref:System.IO.FileNotFoundException>( ).</span><span class="sxs-lookup"><span data-stu-id="95881-114">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="95881-115">Kombinovaná cesta odkazuje na existující<xref:System.IO.IOException>adresář ( ).</span><span class="sxs-lookup"><span data-stu-id="95881-115">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="95881-116">Cílový soubor existuje `overwrite` a je `False` <xref:System.IO.IOException>nastaven na ( ).</span><span class="sxs-lookup"><span data-stu-id="95881-116">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="95881-117">Uživatel nemá dostatečná oprávnění pro přístup<xref:System.IO.IOException>k souboru ( ).</span><span class="sxs-lookup"><span data-stu-id="95881-117">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="95881-118">Soubor v cílové složce se stejným názvem<xref:System.IO.IOException>se používá ( ).</span><span class="sxs-lookup"><span data-stu-id="95881-118">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="95881-119">Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="95881-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="95881-120">`ShowUI`je `True`nastavena `onUserCancel` na `ThrowException`, je nastavena na ,<xref:System.OperationCanceledException>a uživatel zrušil operaci ( ).</span><span class="sxs-lookup"><span data-stu-id="95881-120">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="95881-121">`ShowUI`je `True`nastavena `onUserCancel` na `ThrowException`, je nastavena na , a<xref:System.OperationCanceledException>dojde k nespecifikované chybě vstupně-out ( ).</span><span class="sxs-lookup"><span data-stu-id="95881-121">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="95881-122">Cesta překračuje maximální délku definovanou<xref:System.IO.PathTooLongException>systémem ( ).</span><span class="sxs-lookup"><span data-stu-id="95881-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="95881-123">Uživatel nemá požadované oprávnění<xref:System.UnauthorizedAccessException>( ).</span><span class="sxs-lookup"><span data-stu-id="95881-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="95881-124">Uživatel nemá potřebná oprávnění k<xref:System.Security.SecurityException>zobrazení cesty ( ).</span><span class="sxs-lookup"><span data-stu-id="95881-124">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95881-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="95881-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="95881-126">Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře</span><span class="sxs-lookup"><span data-stu-id="95881-126">How to: Copy Files with a Specific Pattern to a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="95881-127">Postupy: Vytvoření kopie souboru ve stejném adresáři</span><span class="sxs-lookup"><span data-stu-id="95881-127">How to: Create a Copy of a File in the Same Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [<span data-ttu-id="95881-128">Postupy: Zkopírování adresáře do jiného adresáře</span><span class="sxs-lookup"><span data-stu-id="95881-128">How to: Copy a Directory to Another Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="95881-129">Postupy: Přejmenování souboru</span><span class="sxs-lookup"><span data-stu-id="95881-129">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
