---
title: Postup kopírování, odstraňování a přesouvání souborů a složek – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 662f0ab3b9e69aa8bfb0085f42f577b850029e4d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712270"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="bc6d3-102">Postup kopírování, odstraňování a přesouvání souborů a složek (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="bc6d3-102">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>
<span data-ttu-id="bc6d3-103">Následující příklady ukazují, jak kopírovat, přesunout a odstraňovat soubory a složky synchronním způsobem pomocí tříd <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>a <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> z oboru názvů <xref:System.IO?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bc6d3-103">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="bc6d3-104">Tyto příklady neposkytují indikátor průběhu ani žádné jiné uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bc6d3-104">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="bc6d3-105">Pokud chcete zadat standardní dialogové okno průběhu, přečtěte si téma [jak poskytnout dialogové okno průběhu pro operace se soubory](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span><span class="sxs-lookup"><span data-stu-id="bc6d3-105">If you want to provide a standard progress dialog box, see [How to provide a progress dialog box for file operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="bc6d3-106">Pomocí <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> můžete poskytnout události, které vám umožní vypočítat průběh při práci na více souborech.</span><span class="sxs-lookup"><span data-stu-id="bc6d3-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="bc6d3-107">Další možností je použít vyvolání platformy pro volání relevantních metod, které se týkají souborů v prostředí Windows Shell.</span><span class="sxs-lookup"><span data-stu-id="bc6d3-107">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="bc6d3-108">Informace o asynchronním provádění těchto operací se soubory najdete v tématu [asynchronní vstupně-výstupní](../../../standard/io/asynchronous-file-i-o.md)operace se soubory.</span><span class="sxs-lookup"><span data-stu-id="bc6d3-108">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](../../../standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc6d3-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc6d3-109">Example</span></span>  
 <span data-ttu-id="bc6d3-110">Následující příklad ukazuje, jak kopírovat soubory a adresáře.</span><span class="sxs-lookup"><span data-stu-id="bc6d3-110">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a><span data-ttu-id="bc6d3-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc6d3-111">Example</span></span>  
 <span data-ttu-id="bc6d3-112">Následující příklad ukazuje, jak přesunout soubory a adresáře.</span><span class="sxs-lookup"><span data-stu-id="bc6d3-112">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a><span data-ttu-id="bc6d3-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc6d3-113">Example</span></span>  
 <span data-ttu-id="bc6d3-114">Následující příklad ukazuje, jak odstranit soubory a adresáře.</span><span class="sxs-lookup"><span data-stu-id="bc6d3-114">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="bc6d3-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc6d3-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="bc6d3-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="bc6d3-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="bc6d3-117">Systém souborů a registr (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="bc6d3-117">File System and the Registry (C# Programming Guide)</span></span>](index.md)
- [<span data-ttu-id="bc6d3-118">Postup poskytnutí dialogového okna průběhu pro operace se soubory</span><span class="sxs-lookup"><span data-stu-id="bc6d3-118">How to provide a progress dialog box for file operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [<span data-ttu-id="bc6d3-119">Vstup/výstup souborů a datových proudů</span><span class="sxs-lookup"><span data-stu-id="bc6d3-119">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="bc6d3-120">Obecné vstupně-výstupní úlohy</span><span class="sxs-lookup"><span data-stu-id="bc6d3-120">Common I/O Tasks</span></span>](../../../standard/io/common-i-o-tasks.md)
