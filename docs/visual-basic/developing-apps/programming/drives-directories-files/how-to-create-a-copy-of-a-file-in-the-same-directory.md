---
title: 'Postupy: Vytvoření kopie souboru ve stejném adresáři'
ms.date: 07/20/2015
f1_keywords:
- File.Copy
helpviewer_keywords:
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files [Visual Basic], copying
- CopyFile method [Visual Basic], copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
ms.openlocfilehash: 33a4f5424ac50de7b5dc988034ca15127dc1ed02
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348825"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a><span data-ttu-id="b637a-102">Postupy: Vytvoření kopie souboru ve stejném adresáři v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b637a-102">How to: Create a Copy of a File in the Same Directory in Visual Basic</span></span>

<span data-ttu-id="b637a-103">Pomocí `My.Computer.FileSystem.CopyFile` této metody zkopírujte soubory.</span><span class="sxs-lookup"><span data-stu-id="b637a-103">Use the `My.Computer.FileSystem.CopyFile` method to copy files.</span></span> <span data-ttu-id="b637a-104">Parametry umožňují přepsat existující soubory, přejmenovat soubor, zobrazit průběh operace a umožnit uživateli operaci zrušit.</span><span class="sxs-lookup"><span data-stu-id="b637a-104">The parameters allow you to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a><span data-ttu-id="b637a-105">Vytvoření kopie souboru ve stejné složce</span><span class="sxs-lookup"><span data-stu-id="b637a-105">To create a copy of a file in the same folder</span></span>  
  
- <span data-ttu-id="b637a-106">Použijte `CopyFile` metodu, zadání cílového souboru a umístění.</span><span class="sxs-lookup"><span data-stu-id="b637a-106">Use the `CopyFile` method, supplying the target file and the location.</span></span> <span data-ttu-id="b637a-107">Následující příklad vytvoří `test.txt` kopii `test2.txt`s názvem .</span><span class="sxs-lookup"><span data-stu-id="b637a-107">The following example creates a copy of `test.txt` called `test2.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a><span data-ttu-id="b637a-108">Chcete-li vytvořit kopii souboru ve stejné složce, přepsání existujících souborů</span><span class="sxs-lookup"><span data-stu-id="b637a-108">To create a copy of a file in the same folder, overwriting existing files</span></span>  
  
- <span data-ttu-id="b637a-109">Použijte `CopyFile` metodu, zadání cílového souboru `overwrite` a `True`umístění a nastavení .</span><span class="sxs-lookup"><span data-stu-id="b637a-109">Use the `CopyFile` method, supplying the target file and location, and setting `overwrite` to `True`.</span></span> <span data-ttu-id="b637a-110">Následující příklad vytvoří `test.txt` kopii `test2.txt` volané a přepíše všechny existující soubory tímto názvem.</span><span class="sxs-lookup"><span data-stu-id="b637a-110">The following example creates a copy of `test.txt` called `test2.txt` and overwrites any existing files by that name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
## <a name="robust-programming"></a><span data-ttu-id="b637a-111">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="b637a-111">Robust Programming</span></span>  

 <span data-ttu-id="b637a-112">Následující podmínky mohou způsobit, že bude vyvolána výjimka:</span><span class="sxs-lookup"><span data-stu-id="b637a-112">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="b637a-113">Cesta není platná z jednoho z následujících důvodů: jedná se o řetězec nulové délky, obsahuje pouze prázdné znaky, \\ \\\\obsahuje neplatné znaky nebo se jedná o cestu zařízení (začíná na . ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="b637a-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="b637a-114">Systém nemohl načíst absolutní<xref:System.ArgumentException>cestu ( ).</span><span class="sxs-lookup"><span data-stu-id="b637a-114">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="b637a-115">Cesta není platná, protože `Nothing` <xref:System.ArgumentNullException>je ( ).</span><span class="sxs-lookup"><span data-stu-id="b637a-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="b637a-116">Zdrojový soubor není platný nebo neexistuje<xref:System.IO.FileNotFoundException>( ).</span><span class="sxs-lookup"><span data-stu-id="b637a-116">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="b637a-117">Kombinovaná cesta odkazuje na existující<xref:System.IO.IOException>adresář ( ).</span><span class="sxs-lookup"><span data-stu-id="b637a-117">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="b637a-118">Cílový soubor existuje `overwrite` a je `False` <xref:System.IO.IOException>nastaven na ( ).</span><span class="sxs-lookup"><span data-stu-id="b637a-118">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="b637a-119">Uživatel nemá dostatečná oprávnění pro přístup<xref:System.IO.IOException>k souboru ( ).</span><span class="sxs-lookup"><span data-stu-id="b637a-119">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="b637a-120">Soubor v cílové složce se stejným názvem<xref:System.IO.IOException>se používá ( ).</span><span class="sxs-lookup"><span data-stu-id="b637a-120">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="b637a-121">Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="b637a-121">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="b637a-122">`ShowUI`je `True`nastavena `onUserCancel` na `ThrowException`, je nastavena na ,<xref:System.OperationCanceledException>a uživatel zrušil operaci ( ).</span><span class="sxs-lookup"><span data-stu-id="b637a-122">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="b637a-123">`ShowUI`je `True`nastavena `onUserCancel` na `ThrowException`, je nastavena na , a<xref:System.OperationCanceledException>dojde k nespecifikované chybě vstupně-out ( ).</span><span class="sxs-lookup"><span data-stu-id="b637a-123">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="b637a-124">Cesta překračuje maximální délku definovanou<xref:System.IO.PathTooLongException>systémem ( ).</span><span class="sxs-lookup"><span data-stu-id="b637a-124">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="b637a-125">Uživatel nemá požadované oprávnění<xref:System.UnauthorizedAccessException>( ).</span><span class="sxs-lookup"><span data-stu-id="b637a-125">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="b637a-126">Uživatel nemá potřebná oprávnění k<xref:System.Security.SecurityException>zobrazení cesty ( ).</span><span class="sxs-lookup"><span data-stu-id="b637a-126">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b637a-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="b637a-127">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="b637a-128">Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře</span><span class="sxs-lookup"><span data-stu-id="b637a-128">How to: Copy Files with a Specific Pattern to a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="b637a-129">Postupy: Vytvoření kopie souboru v jiném adresáři</span><span class="sxs-lookup"><span data-stu-id="b637a-129">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="b637a-130">Postupy: Zkopírování adresáře do jiného adresáře</span><span class="sxs-lookup"><span data-stu-id="b637a-130">How to: Copy a Directory to Another Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="b637a-131">Postupy: Přejmenování souboru</span><span class="sxs-lookup"><span data-stu-id="b637a-131">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
