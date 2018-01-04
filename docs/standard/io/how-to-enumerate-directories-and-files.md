---
title: "Postupy: Vytvoření výčtu adresářů a souborů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
caps.latest.revision: "18"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5d0f22853210144881e49c4192ea38a5c3e57cda
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-enumerate-directories-and-files"></a><span data-ttu-id="186a5-102">Postupy: Vytvoření výčtu adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="186a5-102">How to: Enumerate Directories and Files</span></span>
<span data-ttu-id="186a5-103">Můžete vytvořit výčet adresářů a souborů pomocí metod, které vrací vyčíslitelná kolekce řetězců jejich názvů.</span><span class="sxs-lookup"><span data-stu-id="186a5-103">You can enumerate directories and files by using methods that return an enumerable collection of strings of their names.</span></span> <span data-ttu-id="186a5-104">Můžete také použít metody, které vrací kolekce vyčíslitelná <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, nebo <xref:System.IO.FileSystemInfo> objekty.</span><span class="sxs-lookup"><span data-stu-id="186a5-104">You can also use methods that return an enumerable collection of <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, or <xref:System.IO.FileSystemInfo> objects.</span></span> <span data-ttu-id="186a5-105">Vyčíslitelná kolekce poskytují lepší výkon než pole při práci s rozsáhlých kolekcí adresářů a souborů.</span><span class="sxs-lookup"><span data-stu-id="186a5-105">Enumerable collections provide better performance than arrays when you work with large collections of directories and files.</span></span>  
  
 <span data-ttu-id="186a5-106">Vyčíslitelná kolekce získané z těchto metod můžete také použít k poskytování <xref:System.Collections.Generic.IEnumerable%601> parametr pro konstruktory kolekce tříd, jako <xref:System.Collections.Generic.List%601> třídy.</span><span class="sxs-lookup"><span data-stu-id="186a5-106">You can also use enumerable collections obtained from these methods to supply the <xref:System.Collections.Generic.IEnumerable%601> parameter for constructors of collection classes such as the <xref:System.Collections.Generic.List%601> class.</span></span>  
  
 <span data-ttu-id="186a5-107">Pokud chcete získat pouze názvy adresáře nebo soubory, použijte výčtové metody <xref:System.IO.Directory> třídy.</span><span class="sxs-lookup"><span data-stu-id="186a5-107">If you want to obtain only the names of directories or files, use the enumeration methods of the <xref:System.IO.Directory> class.</span></span> <span data-ttu-id="186a5-108">Pokud chcete získat další vlastnosti adresáře nebo soubory, použijte <xref:System.IO.DirectoryInfo> a <xref:System.IO.FileSystemInfo> třídy.</span><span class="sxs-lookup"><span data-stu-id="186a5-108">If you want to obtain other properties of directories or files, use the <xref:System.IO.DirectoryInfo> and <xref:System.IO.FileSystemInfo> classes.</span></span>  
  
 <span data-ttu-id="186a5-109">Následující tabulka poskytuje vodítko k metody, které vracejí vyčíslitelná kolekce.</span><span class="sxs-lookup"><span data-stu-id="186a5-109">The following table provides a guide to the methods that return enumerable collections.</span></span>  
  
|<span data-ttu-id="186a5-110">Výčet</span><span class="sxs-lookup"><span data-stu-id="186a5-110">To enumerate</span></span>|<span data-ttu-id="186a5-111">Vyčíslitelná kolekce vrátit</span><span class="sxs-lookup"><span data-stu-id="186a5-111">Enumerable collection to return</span></span>|<span data-ttu-id="186a5-112">Metoda se má použít</span><span class="sxs-lookup"><span data-stu-id="186a5-112">Method to use</span></span>|  
|------------------|-------------------------------------|-------------------|  
|<span data-ttu-id="186a5-113">Adresáře</span><span class="sxs-lookup"><span data-stu-id="186a5-113">Directories</span></span>|<span data-ttu-id="186a5-114">Názvy adresářů</span><span class="sxs-lookup"><span data-stu-id="186a5-114">Directory names</span></span>|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="186a5-115">Informace o adresáři (<xref:System.IO.DirectoryInfo>)</span><span class="sxs-lookup"><span data-stu-id="186a5-115">Directory information (<xref:System.IO.DirectoryInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="186a5-116">Soubory</span><span class="sxs-lookup"><span data-stu-id="186a5-116">Files</span></span>|<span data-ttu-id="186a5-117">Názvy souborů</span><span class="sxs-lookup"><span data-stu-id="186a5-117">File names</span></span>|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="186a5-118">Informace o souborech (<xref:System.IO.FileInfo>)</span><span class="sxs-lookup"><span data-stu-id="186a5-118">File information (<xref:System.IO.FileInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="186a5-119">Informace o systému souborů</span><span class="sxs-lookup"><span data-stu-id="186a5-119">File system information</span></span>|<span data-ttu-id="186a5-120">Položky systémového souboru</span><span class="sxs-lookup"><span data-stu-id="186a5-120">File system entries</span></span>|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="186a5-121">V systému souborů (<xref:System.IO.FileSystemInfo>)</span><span class="sxs-lookup"><span data-stu-id="186a5-121">File system information (<xref:System.IO.FileSystemInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="186a5-122">I když můžete okamžitě vytvořit výčet všech souborů v podadresářích adresáře nadřazené pomocí <xref:System.IO.SearchOption.AllDirectories> hledání možnost poskytované <xref:System.IO.SearchOption> výčtu, výjimky neoprávněného přístupu (<xref:System.UnauthorizedAccessException>) může způsobit, že bude výčet být neúplné.</span><span class="sxs-lookup"><span data-stu-id="186a5-122">Although you can immediately enumerate all the files in the subdirectories of a parent directory by using the <xref:System.IO.SearchOption.AllDirectories> search option provided by the <xref:System.IO.SearchOption> enumeration, unauthorized access exceptions (<xref:System.UnauthorizedAccessException>) may cause the enumeration to be incomplete.</span></span> <span data-ttu-id="186a5-123">Pokud tyto výjimky je možné, můžete je zachytit a pokračovat tak, že nejprve vytváření výčtu adresářů a pak výčet souborů.</span><span class="sxs-lookup"><span data-stu-id="186a5-123">If these exceptions are possible, you can catch them and continue by first enumerating directories and then enumerating files.</span></span>  
  
### <a name="to-enumerate-directory-names"></a><span data-ttu-id="186a5-124">Vytvoření výčtu názvů adresářů</span><span class="sxs-lookup"><span data-stu-id="186a5-124">To enumerate directory names</span></span>  
  
-   <span data-ttu-id="186a5-125">Použití <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> metodu k získání seznamu názvů adresář nejvyšší úrovně v zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="186a5-125">Use the <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> method to obtain a list of the top-level directory names in a specified path.</span></span>  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### <a name="to-enumerate-file-names-in-a-directory-and-subdirectories"></a><span data-ttu-id="186a5-126">Výčet názvů souborů v adresáři a podadresáře</span><span class="sxs-lookup"><span data-stu-id="186a5-126">To enumerate file names in a directory and subdirectories</span></span>  
  
-   <span data-ttu-id="186a5-127">Použití <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> metoda k hledání a (volitelně) jeho podadresářů adresáře a získat seznam názvů souborů, které odpovídají zadaný hledaný vzorku.</span><span class="sxs-lookup"><span data-stu-id="186a5-127">Use the <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> method to search a directory and (optionally) its subdirectories, and to obtain a list of file names that match a specified search pattern.</span></span>  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-directoryinfo-objects"></a><span data-ttu-id="186a5-128">Vytvoření výčtu kolekce objektů DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="186a5-128">To enumerate a collection of DirectoryInfo objects</span></span>  
  
-   <span data-ttu-id="186a5-129">Použití <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> metody pro získání kolekce adresářů nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="186a5-129">Use the <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> method to obtain a collection of top-level directories.</span></span>  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-fileinfo-objects-in-all-directories"></a><span data-ttu-id="186a5-130">Vytvoření výčtu kolekce objektů FileInfo ve všech adresářích</span><span class="sxs-lookup"><span data-stu-id="186a5-130">To enumerate a collection of FileInfo objects in all directories</span></span>  
  
-   <span data-ttu-id="186a5-131">Použití <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> metodu za účelem získání kolekce souborů, které odpovídají zadanému vyhledávacímu vzorku ve všech adresářích.</span><span class="sxs-lookup"><span data-stu-id="186a5-131">Use the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> method to obtain a collection of files that match a specified search pattern in all directories.</span></span> <span data-ttu-id="186a5-132">Tento příklad nejprve vytvoří výčet adresářů nejvyšší úrovně k zachycení výjimky možné neoprávněného přístupu a potom vytvoří výčet souborů.</span><span class="sxs-lookup"><span data-stu-id="186a5-132">This example first enumerates the top-level directories to catch possible unauthorized access exceptions, and then enumerates the files.</span></span>  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="186a5-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="186a5-133">See Also</span></span>  
 [<span data-ttu-id="186a5-134">Souborová služba a datový proud I-O</span><span class="sxs-lookup"><span data-stu-id="186a5-134">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
