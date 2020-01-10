---
title: Systém souborů a průvodce C# programováním v registru
ms.date: 07/20/2015
helpviewer_keywords:
- file system [C#]
- registry [C#]
- files [C#]
ms.assetid: 0f2511cf-2b02-4b41-b001-b1754677c38f
ms.openlocfilehash: 2540c816a102a7f11f1f103b993194cccf0f4688
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75704518"
---
# <a name="file-system-and-the-registry-c-programming-guide"></a><span data-ttu-id="4989c-102">Systém souborů a registr (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="4989c-102">File System and the Registry (C# Programming Guide)</span></span>
<span data-ttu-id="4989c-103">Následující témata ukazují, jak používat C# a .NET Framework k provádění různých základních operací se soubory, složkami a registrem.</span><span class="sxs-lookup"><span data-stu-id="4989c-103">The following topics show how to use C# and the .NET Framework to perform various basic operations on files, folders, and the Registry.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4989c-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4989c-104">In This Section</span></span>  
  
|<span data-ttu-id="4989c-105">**Název**</span><span class="sxs-lookup"><span data-stu-id="4989c-105">**Title**</span></span>|<span data-ttu-id="4989c-106">**Popis**</span><span class="sxs-lookup"><span data-stu-id="4989c-106">**Description**</span></span>|  
|---------------|---------------------|  
|[<span data-ttu-id="4989c-107">Postup iterace v adresářovém stromu</span><span class="sxs-lookup"><span data-stu-id="4989c-107">How to iterate through a directory tree</span></span>](./how-to-iterate-through-a-directory-tree.md)|<span data-ttu-id="4989c-108">Ukazuje, jak ručně iterovat prostřednictvím stromu adresářů.</span><span class="sxs-lookup"><span data-stu-id="4989c-108">Shows how to manually iterate through a directory tree.</span></span>|  
|[<span data-ttu-id="4989c-109">Jak získat informace o souborech, složkách a jednotkách</span><span class="sxs-lookup"><span data-stu-id="4989c-109">How to get information about files, folders, and drives</span></span>](./how-to-get-information-about-files-folders-and-drives.md)|<span data-ttu-id="4989c-110">Ukazuje, jak načítat informace, jako jsou časy a velikost vytvoření, informace o souborech, složkách a jednotkách.</span><span class="sxs-lookup"><span data-stu-id="4989c-110">Shows how to retrieve information such as creation times and size, about files, folders and drives.</span></span>|  
|[<span data-ttu-id="4989c-111">Postup vytvoření souboru nebo složky</span><span class="sxs-lookup"><span data-stu-id="4989c-111">How to create a file or folder</span></span>](./how-to-create-a-file-or-folder.md)|<span data-ttu-id="4989c-112">Ukazuje, jak vytvořit nový soubor nebo složku.</span><span class="sxs-lookup"><span data-stu-id="4989c-112">Shows how to create a new file or folder.</span></span>|  
|[<span data-ttu-id="4989c-113">Postup kopírování, odstraňování a přesouvání souborů a složek (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="4989c-113">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](./how-to-copy-delete-and-move-files-and-folders.md)|<span data-ttu-id="4989c-114">Ukazuje, jak kopírovat, odstraňovat a přesouvat soubory a složky.</span><span class="sxs-lookup"><span data-stu-id="4989c-114">Shows how to copy, delete and move files and folders.</span></span>|  
|[<span data-ttu-id="4989c-115">Postup poskytnutí dialogového okna průběhu pro operace se soubory</span><span class="sxs-lookup"><span data-stu-id="4989c-115">How to provide a progress dialog box for file operations</span></span>](./how-to-provide-a-progress-dialog-box-for-file-operations.md)|<span data-ttu-id="4989c-116">Ukazuje, jak zobrazit standardní dialog průběhu Windows pro určité operace se soubory.</span><span class="sxs-lookup"><span data-stu-id="4989c-116">Shows how to display a standard Windows progress dialog for certain file operations.</span></span>|  
|[<span data-ttu-id="4989c-117">Zápis do textového souboru</span><span class="sxs-lookup"><span data-stu-id="4989c-117">How to write to a text file</span></span>](./how-to-write-to-a-text-file.md)|<span data-ttu-id="4989c-118">Ukazuje, jak zapisovat do textového souboru.</span><span class="sxs-lookup"><span data-stu-id="4989c-118">Shows how to write to a text file.</span></span>|  
|[<span data-ttu-id="4989c-119">Čtení z textového souboru</span><span class="sxs-lookup"><span data-stu-id="4989c-119">How to read from a text file</span></span>](./how-to-read-from-a-text-file.md)|<span data-ttu-id="4989c-120">Ukazuje, jak číst z textového souboru.</span><span class="sxs-lookup"><span data-stu-id="4989c-120">Shows how to read from a text file.</span></span>|  
|[<span data-ttu-id="4989c-121">Jak číst textový soubor po jednotlivých řádcích</span><span class="sxs-lookup"><span data-stu-id="4989c-121">How to read a text file one line at a time</span></span>](./how-to-read-a-text-file-one-line-at-a-time.md)|<span data-ttu-id="4989c-122">Ukazuje, jak načíst text ze souboru po jednom řádku.</span><span class="sxs-lookup"><span data-stu-id="4989c-122">Shows how to retrieve text from a file one line at a time.</span></span>|  
|[<span data-ttu-id="4989c-123">Postup vytvoření klíče v registru</span><span class="sxs-lookup"><span data-stu-id="4989c-123">How to create a key in the registry</span></span>](./how-to-create-a-key-in-the-registry.md)|<span data-ttu-id="4989c-124">Ukazuje, jak zapsat klíč do systémového registru.</span><span class="sxs-lookup"><span data-stu-id="4989c-124">Shows how to write a key to the system registry.</span></span>|  
  
## <a name="related-sections"></a><span data-ttu-id="4989c-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="4989c-125">Related Sections</span></span>  
 [<span data-ttu-id="4989c-126">Vstup/výstup souborů a datových proudů</span><span class="sxs-lookup"><span data-stu-id="4989c-126">File and Stream I/O</span></span>](../../../standard/io/index.md)  
  
 [<span data-ttu-id="4989c-127">Postup kopírování, odstraňování a přesouvání souborů a složek (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="4989c-127">How to copy, delete, and move files and folders (C# Programming Guide)</span></span>](./how-to-copy-delete-and-move-files-and-folders.md)
  
 [<span data-ttu-id="4989c-128">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="4989c-128">C# Programming Guide</span></span>](../index.md)  
  
 [<span data-ttu-id="4989c-129">Soubory, složky a jednotky</span><span class="sxs-lookup"><span data-stu-id="4989c-129">Files, Folders and Drives</span></span>](./index.md)  
  
 <xref:System.IO?displayProperty=nameWithType>
