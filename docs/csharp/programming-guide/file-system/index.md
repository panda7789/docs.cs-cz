---
title: "Systém souborů a registr (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d1b4e3fa9b6c6da89abd242be855e9fb7c16dd6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="79051-102">Systém souborů a registr (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="79051-102">File System and the Registry (C# Programming Guide)</span></span>
<span data-ttu-id="79051-103">Následující témata ukazují, jak používat C# a rozhraní .NET Framework k provádění různých základních operací u souborů, složek a registru.</span><span class="sxs-lookup"><span data-stu-id="79051-103">The following topics show how to use C# and the .NET Framework to perform various basic operations on files, folders, and the Registry.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="79051-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="79051-104">In This Section</span></span>  
  
|<span data-ttu-id="79051-105">**Název**</span><span class="sxs-lookup"><span data-stu-id="79051-105">**Title**</span></span>|<span data-ttu-id="79051-106">**Popis**</span><span class="sxs-lookup"><span data-stu-id="79051-106">**Description**</span></span>|  
|---------------|---------------------|  
|[<span data-ttu-id="79051-107">Postupy: iterace v adresářovém stromě</span><span class="sxs-lookup"><span data-stu-id="79051-107">How to: Iterate Through a Directory Tree</span></span>](../../../csharp/programming-guide/file-system/how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="79051-108">Ukazuje, jak ručně iterace v adresářovém stromě.</span><span class="sxs-lookup"><span data-stu-id="79051-108">Shows how to manually iterate through a directory tree.</span></span>|  
|[<span data-ttu-id="79051-109">Postupy: získání informací o souborech, složkách a jednotkách</span><span class="sxs-lookup"><span data-stu-id="79051-109">How to: Get Information About Files, Folders, and Drives</span></span>](../../../csharp/programming-guide/file-system/how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="79051-110">Ukazuje, jak načíst informace, jako je vytváření časy a velikost, o souborech, složkách a jednotkách.</span><span class="sxs-lookup"><span data-stu-id="79051-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|  
|[<span data-ttu-id="79051-111">Postupy: vytvoření souboru nebo složky</span><span class="sxs-lookup"><span data-stu-id="79051-111">How to: Create a File or Folder</span></span>](../../../csharp/programming-guide/file-system/how-to-create-a-file-or-folder.md)|<span data-ttu-id="79051-112">Ukazuje, jak vytvořit nový soubor nebo složku.</span><span class="sxs-lookup"><span data-stu-id="79051-112">Shows how to create a new file or folder.</span></span>|  
|[<span data-ttu-id="79051-113">Postupy: kopírování, odstraňování a přesouvání souborů a složek (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="79051-113">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="79051-114">Ukazuje, jak kopírování, odstranění a přesouvání souborů a složek.</span><span class="sxs-lookup"><span data-stu-id="79051-114">Shows how to copy, delete and move files and folders.</span></span>|  
|[<span data-ttu-id="79051-115">Postupy: poskytnutí dialogového okna průběhu pro operace se soubory</span><span class="sxs-lookup"><span data-stu-id="79051-115">How to: Provide a Progress Dialog Box for File Operations</span></span>](../../../csharp/programming-guide/file-system/how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="79051-116">Ukazuje, jak zobrazit standardní dialogové okno průběhu Windows pro určité operace se soubory.</span><span class="sxs-lookup"><span data-stu-id="79051-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|  
|[<span data-ttu-id="79051-117">Postupy: zápis do textového souboru</span><span class="sxs-lookup"><span data-stu-id="79051-117">How to: Write to a Text File</span></span>](../../../csharp/programming-guide/file-system/how-to-write-to-a-text-file.md)|<span data-ttu-id="79051-118">Ukazuje, jak k zápisu do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="79051-118">Shows how to write to a text file.</span></span>|  
|[<span data-ttu-id="79051-119">Postupy: čtení z textového souboru</span><span class="sxs-lookup"><span data-stu-id="79051-119">How to: Read From a Text File</span></span>](../../../csharp/programming-guide/file-system/how-to-read-from-a-text-file.md)|<span data-ttu-id="79051-120">Ukazuje, jak číst z textového souboru.</span><span class="sxs-lookup"><span data-stu-id="79051-120">Shows how to read from a text file.</span></span>|  
|[<span data-ttu-id="79051-121">Postupy: čtení textového souboru po řádcích</span><span class="sxs-lookup"><span data-stu-id="79051-121">How to: Read a Text File One Line at a Time</span></span>](../../../csharp/programming-guide/file-system/how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="79051-122">Ukazuje, jak k načtení textu ze souborů jeden řádek v čase.</span><span class="sxs-lookup"><span data-stu-id="79051-122">Shows how to retrieve text from a file one line at a time.</span></span>|  
|[<span data-ttu-id="79051-123">Postupy: vytvoření klíče v registru</span><span class="sxs-lookup"><span data-stu-id="79051-123">How to: Create a Key In the Registry</span></span>](../../../csharp/programming-guide/file-system/how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="79051-124">Ukazuje, jak zapsat klíč do registru systému.</span><span class="sxs-lookup"><span data-stu-id="79051-124">Shows how to write a key to the system registry.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="79051-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="79051-125">Related Sections</span></span>  
 [<span data-ttu-id="79051-126">Vstupně-výstupních souborů a proudů</span><span class="sxs-lookup"><span data-stu-id="79051-126">File and Stream I/O</span></span>](https://msdn.microsoft.com/library/k3352a4t)  
  
 [<span data-ttu-id="79051-127">Postupy: kopírování, odstraňování a přesouvání souborů a složek (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="79051-127">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/how-to-copy-delete-and-move-files-and-folders.md)  
  
 [<span data-ttu-id="79051-128">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="79051-128">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
  
 [<span data-ttu-id="79051-129">Soubory, složky a disky</span><span class="sxs-lookup"><span data-stu-id="79051-129">Files, Folders and Drives</span></span>](../../../csharp/programming-guide/file-system/index.md)  
  
 <xref:System.IO?displayProperty=nameWithType>
