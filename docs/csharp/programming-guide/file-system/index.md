---
title: Systém souborů a průvodce C# programováním v registru
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
ms.openlocfilehash: ef6c1da09ea0435643caba0f5e2819c064f8db01
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589907"
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="14444-102">Systém souborů a registr (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="14444-102">File System and the Registry (C# Programming Guide)</span></span>
<span data-ttu-id="14444-103">Následující témata ukazují, jak používat C# a .NET Framework k provádění různých základních operací se soubory, složkami a registrem.</span><span class="sxs-lookup"><span data-stu-id="14444-103">The following topics show how to use C# and the .NET Framework to perform various basic operations on files, folders, and the Registry.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="14444-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="14444-104">In This Section</span></span>  
  
|<span data-ttu-id="14444-105">**Název**</span><span class="sxs-lookup"><span data-stu-id="14444-105">**Title**</span></span>|<span data-ttu-id="14444-106">**Popis**</span><span class="sxs-lookup"><span data-stu-id="14444-106">**Description**</span></span>|  
|---------------|---------------------|  
|[<span data-ttu-id="14444-107">Postupy: Iterace prostřednictvím stromu adresářů</span><span class="sxs-lookup"><span data-stu-id="14444-107">How to: Iterate Through a Directory Tree</span></span>](./how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="14444-108">Ukazuje, jak ručně iterovat prostřednictvím stromu adresářů.</span><span class="sxs-lookup"><span data-stu-id="14444-108">Shows how to manually iterate through a directory tree.</span></span>|  
|[<span data-ttu-id="14444-109">Postupy: Získání informací o souborech, složkách a jednotkách</span><span class="sxs-lookup"><span data-stu-id="14444-109">How to: Get Information About Files, Folders, and Drives</span></span>](./how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="14444-110">Ukazuje, jak načítat informace, jako jsou časy a velikost vytvoření, informace o souborech, složkách a jednotkách.</span><span class="sxs-lookup"><span data-stu-id="14444-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|  
|[<span data-ttu-id="14444-111">Postupy: Vytvoření souboru nebo složky</span><span class="sxs-lookup"><span data-stu-id="14444-111">How to: Create a File or Folder</span></span>](./how-to-create-a-file-or-folder.md)|<span data-ttu-id="14444-112">Ukazuje, jak vytvořit nový soubor nebo složku.</span><span class="sxs-lookup"><span data-stu-id="14444-112">Shows how to create a new file or folder.</span></span>|  
|[<span data-ttu-id="14444-113">Postupy: Kopírování, odstraňování a přesouvání souborů a složek (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="14444-113">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](./how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="14444-114">Ukazuje, jak kopírovat, odstraňovat a přesouvat soubory a složky.</span><span class="sxs-lookup"><span data-stu-id="14444-114">Shows how to copy, delete and move files and folders.</span></span>|  
|[<span data-ttu-id="14444-115">Postupy: Zadání dialogového okna průběhu pro operace se soubory</span><span class="sxs-lookup"><span data-stu-id="14444-115">How to: Provide a Progress Dialog Box for File Operations</span></span>](./how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="14444-116">Ukazuje, jak zobrazit standardní dialog průběhu Windows pro určité operace se soubory.</span><span class="sxs-lookup"><span data-stu-id="14444-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|  
|[<span data-ttu-id="14444-117">Postupy: Zapsat do textového souboru</span><span class="sxs-lookup"><span data-stu-id="14444-117">How to: Write to a Text File</span></span>](./how-to-write-to-a-text-file.md)|<span data-ttu-id="14444-118">Ukazuje, jak zapisovat do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="14444-118">Shows how to write to a text file.</span></span>|  
|[<span data-ttu-id="14444-119">Postupy: Čtení z textového souboru</span><span class="sxs-lookup"><span data-stu-id="14444-119">How to: Read From a Text File</span></span>](./how-to-read-from-a-text-file.md)|<span data-ttu-id="14444-120">Ukazuje, jak číst z textového souboru.</span><span class="sxs-lookup"><span data-stu-id="14444-120">Shows how to read from a text file.</span></span>|  
|[<span data-ttu-id="14444-121">Postupy: Číst textový soubor po jednotlivých řádcích</span><span class="sxs-lookup"><span data-stu-id="14444-121">How to: Read a Text File One Line at a Time</span></span>](./how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="14444-122">Ukazuje, jak načíst text ze souboru po jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="14444-122">Shows how to retrieve text from a file one line at a time.</span></span>|  
|[<span data-ttu-id="14444-123">Postupy: Vytvoření klíče v registru</span><span class="sxs-lookup"><span data-stu-id="14444-123">How to: Create a Key In the Registry</span></span>](./how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="14444-124">Ukazuje, jak zapsat klíč do systémového registru.</span><span class="sxs-lookup"><span data-stu-id="14444-124">Shows how to write a key to the system registry.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="14444-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="14444-125">Related Sections</span></span>  
 [<span data-ttu-id="14444-126">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="14444-126">File and Stream I/O</span></span>](../../../standard/io/index.md)  
  
 [<span data-ttu-id="14444-127">Postupy: Kopírování, odstraňování a přesouvání souborů a složek (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="14444-127">How to: Copy, Delete, and Move Files and Folders (C# Programming Guide)</span></span>](./how-to-copy-delete-and-move-files-and-folders.md)  
  
 [<span data-ttu-id="14444-128">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="14444-128">C# Programming Guide</span></span>](../index.md)  
  
 [<span data-ttu-id="14444-129">Soubory, složky a jednotky</span><span class="sxs-lookup"><span data-stu-id="14444-129">Files, Folders and Drives</span></span>](./index.md)  
  
 <xref:System.IO?displayProperty=nameWithType>
