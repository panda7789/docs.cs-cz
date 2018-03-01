---
title: "Postupy: Kopírování, odstraňování a přesouvání souborů a složek (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 56383873674998fc0d6417a2abf4fa72e498f08f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="817c1-102">Postupy: Kopírování, odstraňování a přesouvání souborů a složek (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="817c1-102">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>
<span data-ttu-id="817c1-103">Následující příklady ukazují, jak kopírovat, přesunout a odstranit soubory a složky synchronním způsobem pomocí <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, a <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> třídy z <xref:System.IO?displayProperty=nameWithType> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="817c1-103">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="817c1-104">Tyto příklady neposkytují indikátor průběhu nebo jiné uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="817c1-104">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="817c1-105">Pokud byste chtěli poskytnout dialogového okna průběhu standardní, přečtěte si téma [postupy: poskytnutí dialogového okna průběhu pro operace se soubory](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span><span class="sxs-lookup"><span data-stu-id="817c1-105">If you want to provide a standard progress dialog box, see [How to: Provide a Progress Dialog Box for File Operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="817c1-106">Použití <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> zajistit události, které vám umožní vypočítat průběh při fungování na několik souborů.</span><span class="sxs-lookup"><span data-stu-id="817c1-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="817c1-107">Další možností je použít platformy vyvolání pro volání metody příslušné soubory v prostředí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="817c1-107">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="817c1-108">Informace o tom, jak provést tyto operace se soubory asynchronně najdete v tématu [asynchronní vstup-výstup souboru](https://msdn.microsoft.com/library/kztecsys).</span><span class="sxs-lookup"><span data-stu-id="817c1-108">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](https://msdn.microsoft.com/library/kztecsys).</span></span>  
  
## <a name="example"></a><span data-ttu-id="817c1-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="817c1-109">Example</span></span>  
 <span data-ttu-id="817c1-110">Následující příklad ukazuje postup kopírování souborů a adresářů.</span><span class="sxs-lookup"><span data-stu-id="817c1-110">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="817c1-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="817c1-111">Example</span></span>  
 <span data-ttu-id="817c1-112">Následující příklad ukazuje, jak k přesouvání souborů a adresářů.</span><span class="sxs-lookup"><span data-stu-id="817c1-112">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="817c1-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="817c1-113">Example</span></span>  
 <span data-ttu-id="817c1-114">Následující příklad ukazuje, jak k odstraňování souborů a adresářů.</span><span class="sxs-lookup"><span data-stu-id="817c1-114">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](../../../csharp/programming-guide/file-system/codesnippet/CSharp/how-to-copy-delete-and-move-files-and-folders_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="817c1-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="817c1-115">See Also</span></span>  
 <xref:System.IO?displayProperty=nameWithType>  
 [<span data-ttu-id="817c1-116">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="817c1-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="817c1-117">Systém souborů a registr (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="817c1-117">File System and the Registry (C# Programming Guide)</span></span>](index.md)  
 [<span data-ttu-id="817c1-118">Postupy: poskytnutí dialogového okna průběhu pro operace se soubory</span><span class="sxs-lookup"><span data-stu-id="817c1-118">How to: Provide a Progress Dialog Box for File Operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)  
 [<span data-ttu-id="817c1-119">Vstupně-výstupních souborů a proudů</span><span class="sxs-lookup"><span data-stu-id="817c1-119">File and Stream I/O</span></span>](https://msdn.microsoft.com/library/k3352a4t)  
 [<span data-ttu-id="817c1-120">Běžné vstupně-výstupní úlohy</span><span class="sxs-lookup"><span data-stu-id="817c1-120">Common I/O Tasks</span></span>](https://msdn.microsoft.com/library/ms404278)
