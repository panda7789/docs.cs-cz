---
title: Postup kopírování, odstraňování a přesouvání souborů a složek – Průvodce programováním v C#
description: Naučte se kopírovat, odstraňovat a přesouvat soubory a složky pomocí tříd File, Directory, FileInfo a DirectoryInfo.
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 208502651080f4fd614e34d1bf5b088dfb1207a6
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303358"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="27255-103">Postup kopírování, odstraňování a přesouvání souborů a složek (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="27255-103">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>
<span data-ttu-id="27255-104">Následující příklady ukazují, jak kopírovat, přesunout a odstraňovat soubory a složky synchronním způsobem pomocí <xref:System.IO.File?displayProperty=nameWithType> <xref:System.IO.Directory?displayProperty=nameWithType> tříd,, a <xref:System.IO.FileInfo?displayProperty=nameWithType> <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> z <xref:System.IO?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="27255-104">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="27255-105">Tyto příklady neposkytují indikátor průběhu ani žádné jiné uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="27255-105">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="27255-106">Pokud chcete zadat standardní dialogové okno průběhu, přečtěte si téma [jak poskytnout dialogové okno průběhu pro operace se soubory](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span><span class="sxs-lookup"><span data-stu-id="27255-106">If you want to provide a standard progress dialog box, see [How to provide a progress dialog box for file operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="27255-107">Slouží <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> k poskytnutí událostí, které vám umožní vypočítat průběh při práci na více souborech.</span><span class="sxs-lookup"><span data-stu-id="27255-107">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="27255-108">Další možností je použít vyvolání platformy pro volání relevantních metod, které se týkají souborů v prostředí Windows Shell.</span><span class="sxs-lookup"><span data-stu-id="27255-108">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="27255-109">Informace o asynchronním provádění těchto operací se soubory najdete v tématu [asynchronní vstupně-výstupní](../../../standard/io/asynchronous-file-i-o.md)operace se soubory.</span><span class="sxs-lookup"><span data-stu-id="27255-109">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](../../../standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="27255-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="27255-110">Example</span></span>  
 <span data-ttu-id="27255-111">Následující příklad ukazuje, jak kopírovat soubory a adresáře.</span><span class="sxs-lookup"><span data-stu-id="27255-111">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a><span data-ttu-id="27255-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="27255-112">Example</span></span>  
 <span data-ttu-id="27255-113">Následující příklad ukazuje, jak přesunout soubory a adresáře.</span><span class="sxs-lookup"><span data-stu-id="27255-113">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a><span data-ttu-id="27255-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="27255-114">Example</span></span>  
 <span data-ttu-id="27255-115">Následující příklad ukazuje, jak odstranit soubory a adresáře.</span><span class="sxs-lookup"><span data-stu-id="27255-115">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="27255-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="27255-116">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="27255-117">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="27255-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="27255-118">Systém souborů a registr (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="27255-118">File System and the Registry (C# Programming Guide)</span></span>](index.md)
- [<span data-ttu-id="27255-119">Jak zobrazit dialogové okno průběhu pro operace se soubory</span><span class="sxs-lookup"><span data-stu-id="27255-119">How to provide a progress dialog box for file operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [<span data-ttu-id="27255-120">Vstupně-výstupní operace se soubory a datovým proudem</span><span class="sxs-lookup"><span data-stu-id="27255-120">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="27255-121">Běžné vstupně-výstupní úlohy</span><span class="sxs-lookup"><span data-stu-id="27255-121">Common I/O Tasks</span></span>](../../../standard/io/common-i-o-tasks.md)
