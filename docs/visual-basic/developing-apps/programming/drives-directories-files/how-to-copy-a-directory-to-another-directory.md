---
title: 'Postupy: Zkopírování adresáře do jiného adresáře'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
ms.openlocfilehash: a23079f093f53ab8e20eb71c684a594dcf7f894b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348866"
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a><span data-ttu-id="2b2a8-102">Postupy: Zkopírování adresáře do jiného adresáře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2b2a8-102">How to: Copy a Directory to Another Directory in Visual Basic</span></span>

<span data-ttu-id="2b2a8-103">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> method to copy a directory to another directory.</span><span class="sxs-lookup"><span data-stu-id="2b2a8-103">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> method to copy a directory to another directory.</span></span> <span data-ttu-id="2b2a8-104">This method copies the contents of the directory as well as the directory itself.</span><span class="sxs-lookup"><span data-stu-id="2b2a8-104">This method copies the contents of the directory as well as the directory itself.</span></span> <span data-ttu-id="2b2a8-105">If the target directory does not exist, it will be created.</span><span class="sxs-lookup"><span data-stu-id="2b2a8-105">If the target directory does not exist, it will be created.</span></span> <span data-ttu-id="2b2a8-106">If a directory with the same name exists in the target location and `overwrite` is set to `False`, the contents of the two directories will be merged.</span><span class="sxs-lookup"><span data-stu-id="2b2a8-106">If a directory with the same name exists in the target location and `overwrite` is set to `False`, the contents of the two directories will be merged.</span></span> <span data-ttu-id="2b2a8-107">You can specify a new name for the directory during the operation.</span><span class="sxs-lookup"><span data-stu-id="2b2a8-107">You can specify a new name for the directory during the operation.</span></span>

<span data-ttu-id="2b2a8-108">When copying files within a directory, exceptions may be thrown that are caused by specific file, such as a file existing during a merge while `overwrite` is set to `False`.</span><span class="sxs-lookup"><span data-stu-id="2b2a8-108">When copying files within a directory, exceptions may be thrown that are caused by specific file, such as a file existing during a merge while `overwrite` is set to `False`.</span></span> <span data-ttu-id="2b2a8-109">When such exceptions are thrown, they are consolidated into a single exception, whose `Data` property holds entries in which the file or directory path is the key and the specific exception message is contained in the corresponding value.</span><span class="sxs-lookup"><span data-stu-id="2b2a8-109">When such exceptions are thrown, they are consolidated into a single exception, whose `Data` property holds entries in which the file or directory path is the key and the specific exception message is contained in the corresponding value.</span></span>

## <a name="to-copy-a-directory-to-another-directory"></a><span data-ttu-id="2b2a8-110">To copy a directory to another directory</span><span class="sxs-lookup"><span data-stu-id="2b2a8-110">To copy a directory to another directory</span></span>

- <span data-ttu-id="2b2a8-111">Use the `CopyDirectory` method, specifying source and destination directory names.</span><span class="sxs-lookup"><span data-stu-id="2b2a8-111">Use the `CopyDirectory` method, specifying source and destination directory names.</span></span> <span data-ttu-id="2b2a8-112">The following example copies the directory named `TestDirectory1` into `TestDirectory2`, overwriting existing files.</span><span class="sxs-lookup"><span data-stu-id="2b2a8-112">The following example copies the directory named `TestDirectory1` into `TestDirectory2`, overwriting existing files.</span></span>

    [!code-vb[VbVbcnMyFileSystem#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#16)]

    <span data-ttu-id="2b2a8-113">This code example is also available as an IntelliSense code snippet.</span><span class="sxs-lookup"><span data-stu-id="2b2a8-113">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="2b2a8-114">In the code snippet picker, it is located in **File system - Processing Drives, Folders, and Files**.</span><span class="sxs-lookup"><span data-stu-id="2b2a8-114">In the code snippet picker, it is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="2b2a8-115">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="2b2a8-115">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>

## <a name="robust-programming"></a><span data-ttu-id="2b2a8-116">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="2b2a8-116">Robust Programming</span></span>

<span data-ttu-id="2b2a8-117">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="2b2a8-117">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="2b2a8-118">The new name specified for the directory contains a colon (:) or slash (\ or /) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="2b2a8-118">The new name specified for the directory contains a colon (:) or slash (\ or /) (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="2b2a8-119">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="2b2a8-119">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="2b2a8-120">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="2b2a8-120">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="2b2a8-121">`destinationDirectoryName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="2b2a8-121">`destinationDirectoryName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>)</span></span>

- <span data-ttu-id="2b2a8-122">The source directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="2b2a8-122">The source directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="2b2a8-123">The source directory is a root directory (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="2b2a8-123">The source directory is a root directory (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="2b2a8-124">The combined path points to an existing file (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="2b2a8-124">The combined path points to an existing file (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="2b2a8-125">The source path and target path are the same (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="2b2a8-125">The source path and target path are the same (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="2b2a8-126">`ShowUI` is set to `UIOption.AllDialogs` and the user cancels the operation, or one or more files in the directory cannot be copied (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="2b2a8-126">`ShowUI` is set to `UIOption.AllDialogs` and the user cancels the operation, or one or more files in the directory cannot be copied (<xref:System.OperationCanceledException>).</span></span>

- <span data-ttu-id="2b2a8-127">The operation is cyclic (<xref:System.InvalidOperationException>).</span><span class="sxs-lookup"><span data-stu-id="2b2a8-127">The operation is cyclic (<xref:System.InvalidOperationException>).</span></span>

- <span data-ttu-id="2b2a8-128">The path contains a colon (:) (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="2b2a8-128">The path contains a colon (:) (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="2b2a8-129">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="2b2a8-129">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="2b2a8-130">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="2b2a8-130">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="2b2a8-131">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="2b2a8-131">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="2b2a8-132">A destination file exists but cannot be accessed (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="2b2a8-132">A destination file exists but cannot be accessed (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="2b2a8-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2b2a8-133">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>
- [<span data-ttu-id="2b2a8-134">Postupy: Hledání podadresářů pomocí specifického vzoru</span><span class="sxs-lookup"><span data-stu-id="2b2a8-134">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="2b2a8-135">Postupy: Získání kolekce souborů z adresáře</span><span class="sxs-lookup"><span data-stu-id="2b2a8-135">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
