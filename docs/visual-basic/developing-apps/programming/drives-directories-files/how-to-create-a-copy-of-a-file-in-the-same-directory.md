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
ms.openlocfilehash: 741f0c80ba268369ebdd598460e9d5fa13d09571
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401677"
---
# <a name="how-to-create-a-copy-of-a-file-in-the-same-directory-in-visual-basic"></a><span data-ttu-id="132d2-102">Postupy: Vytvoření kopie souboru ve stejném adresáři v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="132d2-102">How to: Create a Copy of a File in the Same Directory in Visual Basic</span></span>

<span data-ttu-id="132d2-103">`My.Computer.FileSystem.CopyFile`K kopírování souborů použijte metodu.</span><span class="sxs-lookup"><span data-stu-id="132d2-103">Use the `My.Computer.FileSystem.CopyFile` method to copy files.</span></span> <span data-ttu-id="132d2-104">Parametry umožňují přepsat existující soubory, přejmenovat soubor, zobrazit průběh operace a nechat uživatele operaci zrušit.</span><span class="sxs-lookup"><span data-stu-id="132d2-104">The parameters allow you to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder"></a><span data-ttu-id="132d2-105">Vytvoření kopie souboru ve stejné složce</span><span class="sxs-lookup"><span data-stu-id="132d2-105">To create a copy of a file in the same folder</span></span>  
  
- <span data-ttu-id="132d2-106">Použijte `CopyFile` metodu, zadejte cílový soubor a umístění.</span><span class="sxs-lookup"><span data-stu-id="132d2-106">Use the `CopyFile` method, supplying the target file and the location.</span></span> <span data-ttu-id="132d2-107">Následující příklad vytvoří kopii s `test.txt` názvem `test2.txt` .</span><span class="sxs-lookup"><span data-stu-id="132d2-107">The following example creates a copy of `test.txt` called `test2.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#51](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#51)]  
  
### <a name="to-create-a-copy-of-a-file-in-the-same-folder-overwriting-existing-files"></a><span data-ttu-id="132d2-108">Vytvoření kopie souboru ve stejné složce, při které se přepíší stávající soubory</span><span class="sxs-lookup"><span data-stu-id="132d2-108">To create a copy of a file in the same folder, overwriting existing files</span></span>  
  
- <span data-ttu-id="132d2-109">Použijte `CopyFile` metodu, zadejte cílový soubor a umístění a nastavení `overwrite` na `True` .</span><span class="sxs-lookup"><span data-stu-id="132d2-109">Use the `CopyFile` method, supplying the target file and location, and setting `overwrite` to `True`.</span></span> <span data-ttu-id="132d2-110">Následující příklad vytvoří kopii s `test.txt` názvem `test2.txt` a přepíše všechny existující soubory s tímto názvem.</span><span class="sxs-lookup"><span data-stu-id="132d2-110">The following example creates a copy of `test.txt` called `test2.txt` and overwrites any existing files by that name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#52](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#52)]  
  
## <a name="robust-programming"></a><span data-ttu-id="132d2-111">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="132d2-111">Robust Programming</span></span>  

 <span data-ttu-id="132d2-112">Následující podmínky mohou způsobit vyvolání výjimky:</span><span class="sxs-lookup"><span data-stu-id="132d2-112">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="132d2-113">Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="132d2-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="132d2-114">Systém nemůže načíst absolutní cestu ( <xref:System.ArgumentException> ).</span><span class="sxs-lookup"><span data-stu-id="132d2-114">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="132d2-115">Cesta není platná, protože je `Nothing` ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="132d2-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="132d2-116">Zdrojový soubor není platný nebo neexistuje ( <xref:System.IO.FileNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="132d2-116">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="132d2-117">Kombinovaná cesta odkazuje na existující adresář ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="132d2-117">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="132d2-118">Cílový soubor existuje a `overwrite` je nastaven na hodnotu `False` ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="132d2-118">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="132d2-119">Uživatel nemá dostatečná oprávnění pro přístup k souboru ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="132d2-119">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="132d2-120">Soubor v cílové složce se stejným názvem se používá ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="132d2-120">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="132d2-121">Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu Format ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="132d2-121">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="132d2-122">`ShowUI`je nastaven na `True` , `onUserCancel` je nastaven na `ThrowException` a uživatel zrušil operaci ( <xref:System.OperationCanceledException> ).</span><span class="sxs-lookup"><span data-stu-id="132d2-122">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="132d2-123">`ShowUI`je nastaven na `True` , `onUserCancel` je nastaven na `ThrowException` a dojde k nespecifikované vstupně-výstupní chybě ( <xref:System.OperationCanceledException> ).</span><span class="sxs-lookup"><span data-stu-id="132d2-123">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="132d2-124">Cesta přesahuje maximální povolenou délku () definovanou systémem <xref:System.IO.PathTooLongException> .</span><span class="sxs-lookup"><span data-stu-id="132d2-124">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="132d2-125">Uživatel nemá požadovaná oprávnění ( <xref:System.UnauthorizedAccessException> ).</span><span class="sxs-lookup"><span data-stu-id="132d2-125">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="132d2-126">Uživatel nemá potřebná oprávnění k zobrazení cesty ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="132d2-126">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="132d2-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="132d2-127">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="132d2-128">Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře</span><span class="sxs-lookup"><span data-stu-id="132d2-128">How to: Copy Files with a Specific Pattern to a Directory</span></span>](how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="132d2-129">Postupy: Vytvoření kopie souboru v jiném adresáři</span><span class="sxs-lookup"><span data-stu-id="132d2-129">How to: Create a Copy of a File in a Different Directory</span></span>](how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="132d2-130">Postupy: Zkopírování adresáře do jiného adresáře</span><span class="sxs-lookup"><span data-stu-id="132d2-130">How to: Copy a Directory to Another Directory</span></span>](how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="132d2-131">Postupy: Přejmenování souboru</span><span class="sxs-lookup"><span data-stu-id="132d2-131">How to: Rename a File</span></span>](how-to-rename-a-file.md)
