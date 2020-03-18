---
title: Kopírování, odstraňování a přesouvání souborů a složek – Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [C#]
ms.assetid: 62e52cd7-9597-4e4a-acf9-1315f5cdbf05
ms.openlocfilehash: 662f0ab3b9e69aa8bfb0085f42f577b850029e4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712270"
---
# <a name="how-to-copy-delete-and-move-files-and-folders-c-programming-guide"></a><span data-ttu-id="4ecc8-102">Kopírování, odstraňování a přesouvání souborů a složek (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="4ecc8-102">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>
<span data-ttu-id="4ecc8-103">Následující příklady ukazují, jak kopírovat, přesouvat a odstraňovat soubory <xref:System.IO.File?displayProperty=nameWithType>a <xref:System.IO.Directory?displayProperty=nameWithType> <xref:System.IO.FileInfo?displayProperty=nameWithType>složky <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> synchronním <xref:System.IO?displayProperty=nameWithType> způsobem pomocí aplikace , , a tříd z oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4ecc8-103">The following examples show how to copy, move, and delete files and folders in a synchronous manner by using the <xref:System.IO.File?displayProperty=nameWithType>, <xref:System.IO.Directory?displayProperty=nameWithType>, <xref:System.IO.FileInfo?displayProperty=nameWithType>, and <xref:System.IO.DirectoryInfo?displayProperty=nameWithType> classes from the <xref:System.IO?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="4ecc8-104">Tyto příklady neposkytují indikátor průběhu ani jiné uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4ecc8-104">These examples do not provide a progress bar or any other user interface.</span></span> <span data-ttu-id="4ecc8-105">Pokud chcete poskytnout standardní dialogové okno průběhu, přečtěte si informace [o tom, jak poskytnout dialogové okno průběhu pro operace se soubory](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span><span class="sxs-lookup"><span data-stu-id="4ecc8-105">If you want to provide a standard progress dialog box, see [How to provide a progress dialog box for file operations](how-to-provide-a-progress-dialog-box-for-file-operations.md).</span></span>  
  
 <span data-ttu-id="4ecc8-106">Slouží <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> k poskytnutí událostí, které vám umožní vypočítat průběh při práci s více soubory.</span><span class="sxs-lookup"><span data-stu-id="4ecc8-106">Use <xref:System.IO.FileSystemWatcher?displayProperty=nameWithType> to provide events that will enable you to calculate the progress when operating on multiple files.</span></span> <span data-ttu-id="4ecc8-107">Dalším přístupem je použití platformy invoke k volání příslušných metod souvisejících se souborem v prostředí Windows.</span><span class="sxs-lookup"><span data-stu-id="4ecc8-107">Another approach is to use platform invoke to call the relevant file-related methods in the Windows Shell.</span></span> <span data-ttu-id="4ecc8-108">Informace o tom, jak provádět tyto operace se soubory asynchronně, naleznete [v tématu Asynchronní vstupně-vstupně-nevstupně-to .](../../../standard/io/asynchronous-file-i-o.md)</span><span class="sxs-lookup"><span data-stu-id="4ecc8-108">For information about how to perform these file operations asynchronously, see [Asynchronous File I/O](../../../standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ecc8-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="4ecc8-109">Example</span></span>  
 <span data-ttu-id="4ecc8-110">Následující příklad ukazuje, jak kopírovat soubory a adresáře.</span><span class="sxs-lookup"><span data-stu-id="4ecc8-110">The following example shows how to copy files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#7)]  
  
## <a name="example"></a><span data-ttu-id="4ecc8-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="4ecc8-111">Example</span></span>  
 <span data-ttu-id="4ecc8-112">Následující příklad ukazuje, jak přesunout soubory a adresáře.</span><span class="sxs-lookup"><span data-stu-id="4ecc8-112">The following example shows how to move files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#8)]  
  
## <a name="example"></a><span data-ttu-id="4ecc8-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="4ecc8-113">Example</span></span>  
 <span data-ttu-id="4ecc8-114">Následující příklad ukazuje, jak odstranit soubory a adresáře.</span><span class="sxs-lookup"><span data-stu-id="4ecc8-114">The following example shows how to delete files and directories.</span></span>  
  
 [!code-csharp[csFilesandFolders#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="4ecc8-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ecc8-115">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="4ecc8-116">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="4ecc8-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4ecc8-117">Systém souborů a registr (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="4ecc8-117">File System and the Registry (C# Programming Guide)</span></span>](index.md)
- [<span data-ttu-id="4ecc8-118">Jak zobrazit dialogové okno průběhu pro operace se soubory</span><span class="sxs-lookup"><span data-stu-id="4ecc8-118">How to provide a progress dialog box for file operations</span></span>](how-to-provide-a-progress-dialog-box-for-file-operations.md)
- [<span data-ttu-id="4ecc8-119">I/O souborů a proudů</span><span class="sxs-lookup"><span data-stu-id="4ecc8-119">File and Stream I/O</span></span>](../../../standard/io/index.md)
- [<span data-ttu-id="4ecc8-120">Obecné vstupně-výstupní úlohy</span><span class="sxs-lookup"><span data-stu-id="4ecc8-120">Common I/O Tasks</span></span>](../../../standard/io/common-i-o-tasks.md)
