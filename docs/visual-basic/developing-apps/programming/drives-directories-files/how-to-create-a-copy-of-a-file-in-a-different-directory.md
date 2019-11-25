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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348833"
---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a><span data-ttu-id="733f2-102">Postupy: Vytvoření kopie souboru v jiném adresáři v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="733f2-102">How to: Create a Copy of a File in a Different Directory in Visual Basic</span></span>

<span data-ttu-id="733f2-103">The `My.Computer.FileSystem.CopyFile` method allows you to copy files.</span><span class="sxs-lookup"><span data-stu-id="733f2-103">The `My.Computer.FileSystem.CopyFile` method allows you to copy files.</span></span> <span data-ttu-id="733f2-104">Its parameters provide the ability to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span><span class="sxs-lookup"><span data-stu-id="733f2-104">Its parameters provide the ability to overwrite existing files, rename the file, show the progress of the operation, and allow the user to cancel the operation.</span></span>  
  
### <a name="to-copy-a-text-file-to-another-folder"></a><span data-ttu-id="733f2-105">To copy a text file to another folder</span><span class="sxs-lookup"><span data-stu-id="733f2-105">To copy a text file to another folder</span></span>  
  
- <span data-ttu-id="733f2-106">Use the `CopyFile` method to copy a file, specifying a source file and the target directory.</span><span class="sxs-lookup"><span data-stu-id="733f2-106">Use the `CopyFile` method to copy a file, specifying a source file and the target directory.</span></span> <span data-ttu-id="733f2-107">The `overwrite` parameter allows you to specify whether or not to overwrite existing files.</span><span class="sxs-lookup"><span data-stu-id="733f2-107">The `overwrite` parameter allows you to specify whether or not to overwrite existing files.</span></span> <span data-ttu-id="733f2-108">The following code examples demonstrate how to use `CopyFile`.</span><span class="sxs-lookup"><span data-stu-id="733f2-108">The following code examples demonstrate how to use `CopyFile`.</span></span>  
  
     [!code-vb[VbFileIOMisc#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#24)]  
  
## <a name="robust-programming"></a><span data-ttu-id="733f2-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="733f2-109">Robust Programming</span></span>  

 <span data-ttu-id="733f2-110">The following conditions may cause an exception to be thrown:</span><span class="sxs-lookup"><span data-stu-id="733f2-110">The following conditions may cause an exception to be thrown:</span></span>  
  
- <span data-ttu-id="733f2-111">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="733f2-111">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="733f2-112">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="733f2-112">The system could not retrieve the absolute path (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="733f2-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="733f2-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="733f2-114">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="733f2-114">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="733f2-115">The combined path points to an existing directory (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="733f2-115">The combined path points to an existing directory (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="733f2-116">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="733f2-116">The destination file exists and `overwrite` is set to `False` (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="733f2-117">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="733f2-117">The user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="733f2-118">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="733f2-118">A file in the target folder with the same name is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="733f2-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="733f2-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="733f2-120">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="733f2-120">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and the user has cancelled the operation (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="733f2-121">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="733f2-121">`ShowUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
- <span data-ttu-id="733f2-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="733f2-122">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="733f2-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="733f2-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="733f2-124">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="733f2-124">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="733f2-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="733f2-125">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>
- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- [<span data-ttu-id="733f2-126">Postupy: Kopírování souborů vyhovujících určitému vzoru do jiného adresáře</span><span class="sxs-lookup"><span data-stu-id="733f2-126">How to: Copy Files with a Specific Pattern to a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)
- [<span data-ttu-id="733f2-127">Postupy: Vytvoření kopie souboru ve stejném adresáři</span><span class="sxs-lookup"><span data-stu-id="733f2-127">How to: Create a Copy of a File in the Same Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [<span data-ttu-id="733f2-128">Postupy: Zkopírování adresáře do jiného adresáře</span><span class="sxs-lookup"><span data-stu-id="733f2-128">How to: Copy a Directory to Another Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)
- [<span data-ttu-id="733f2-129">Postupy: Přejmenování souboru</span><span class="sxs-lookup"><span data-stu-id="733f2-129">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
