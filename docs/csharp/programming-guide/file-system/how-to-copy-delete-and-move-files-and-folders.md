---
title: 'Postupy: Kopírování, odstranění a přesunutí souborů a složek - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 3e6c08050186642ceec4e2301524919379e12aaa
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54527702"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="ce95f-102">Postupy: Kopírování, odstraňování a přesouvání souborů a složek (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="ce95f-102">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>
<span data-ttu-id="ce95f-103">Následující příklady ukazují, jak zkopírovat, přesunout a odstranit soubory a složky v synchronním způsobem pomocí <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, a <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> třídy z <xref:System.IO?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ce95f-103">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="ce95f-104">Tyto příklady neposkytují indikátor průběhu nebo jiných uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ce95f-104">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="ce95f-105">Pokud chcete poskytnout dialogového okna průběhu standardní, přečtěte si téma [jak: Poskytnutí dialogového okna průběhu pro operace se soubory](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span><span class="sxs-lookup"><span data-stu-id="ce95f-105">If you want to provide a standard progress dialog box, see [How to: Provide a Progress Dialog Box for File Operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="ce95f-106">Použití <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> poskytnout události, které vám umožní výpočtu průběhu při provozu na více souborů.</span><span class="sxs-lookup"><span data-stu-id="ce95f-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="ce95f-107">Další možností je používat platformu vyvolání pro volání metody relevantní vztahující se k souboru v prostředí Windows.</span><span class="sxs-lookup"><span data-stu-id="ce95f-107">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="ce95f-108">Informace o tom, jak provádět tyto operace se soubory asynchronně, naleznete v tématu [asynchronní vstupně-výstupní operace souboru](../../../standard/io/asynchronous-file-i-o.md).</span><span class="sxs-lookup"><span data-stu-id="ce95f-108">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](../../../standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce95f-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce95f-109">Example</span></span>  
 <span data-ttu-id="ce95f-110">Následující příklad ukazuje, jak kopírovat soubory a adresáře.</span><span class="sxs-lookup"><span data-stu-id="ce95f-110">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="ce95f-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce95f-111">Example</span></span>  
 <span data-ttu-id="ce95f-112">Následující příklad ukazuje, jak přesunout soubory a adresáře.</span><span class="sxs-lookup"><span data-stu-id="ce95f-112">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="ce95f-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce95f-113">Example</span></span>  
 <span data-ttu-id="ce95f-114">Následující příklad ukazuje, jak odstraňovat soubory a adresáře.</span><span class="sxs-lookup"><span data-stu-id="ce95f-114">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="ce95f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce95f-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="ce95f-116">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ce95f-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ce95f-117">Systém souborů a registr (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="ce95f-117">File System and the Registry (C# Programming Guide)</span></span>](index.md)
- [<span data-ttu-id="ce95f-118">Postupy: Poskytnutí dialogového okna průběhu pro operace se soubory</span><span class="sxs-lookup"><span data-stu-id="ce95f-118">How to: Provide a Progress Dialog Box for File Operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [<span data-ttu-id="ce95f-119">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="ce95f-119">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="ce95f-120">Obecné vstupně-výstupní úlohy</span><span class="sxs-lookup"><span data-stu-id="ce95f-120">Common I/O Tasks</span></span>](../../../standard/io/common-i-o-tasks.md)
