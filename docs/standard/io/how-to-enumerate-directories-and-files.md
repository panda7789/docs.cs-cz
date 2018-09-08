---
title: 'Postupy: Vytvoření výčtu adresářů a souborů'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3de83395df9e8c89a92e85b96ddd15e9f0be6ad5
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44207691"
---
# <a name="how-to-enumerate-directories-and-files"></a><span data-ttu-id="c30fd-102">Postupy: Vytvoření výčtu adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="c30fd-102">How to: Enumerate Directories and Files</span></span>
<span data-ttu-id="c30fd-103">Můžete zobrazit výčet adresářů a souborů pomocí metod, které vrací vyčíslitelné kolekce řetězců názvů.</span><span class="sxs-lookup"><span data-stu-id="c30fd-103">You can enumerate directories and files by using methods that return an enumerable collection of strings of their names.</span></span> <span data-ttu-id="c30fd-104">Můžete také použít metody, které vrací vyčíslitelné kolekce <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, nebo <xref:System.IO.FileSystemInfo> objekty.</span><span class="sxs-lookup"><span data-stu-id="c30fd-104">You can also use methods that return an enumerable collection of <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, or <xref:System.IO.FileSystemInfo> objects.</span></span> <span data-ttu-id="c30fd-105">Vyčíslitelné kolekce poskytují lepší výkon než pole při práci s rozsáhlých kolekcí adresářů a souborů.</span><span class="sxs-lookup"><span data-stu-id="c30fd-105">Enumerable collections provide better performance than arrays when you work with large collections of directories and files.</span></span>  
  
 <span data-ttu-id="c30fd-106">Vyčíslitelné kolekce získané z těchto metod můžete také použít k zadání <xref:System.Collections.Generic.IEnumerable%601> parametr pro konstruktory kolekce tříd, jako <xref:System.Collections.Generic.List%601> třídy.</span><span class="sxs-lookup"><span data-stu-id="c30fd-106">You can also use enumerable collections obtained from these methods to supply the <xref:System.Collections.Generic.IEnumerable%601> parameter for constructors of collection classes such as the <xref:System.Collections.Generic.List%601> class.</span></span>  
  
 <span data-ttu-id="c30fd-107">Pokud chcete získat jenom názvy adresářů a souborů, použijte metody výčet <xref:System.IO.Directory> třídy.</span><span class="sxs-lookup"><span data-stu-id="c30fd-107">If you want to obtain only the names of directories or files, use the enumeration methods of the <xref:System.IO.Directory> class.</span></span> <span data-ttu-id="c30fd-108">Pokud chcete získat další vlastnosti adresářů a souborů, použijte <xref:System.IO.DirectoryInfo> a <xref:System.IO.FileSystemInfo> třídy.</span><span class="sxs-lookup"><span data-stu-id="c30fd-108">If you want to obtain other properties of directories or files, use the <xref:System.IO.DirectoryInfo> and <xref:System.IO.FileSystemInfo> classes.</span></span>  
  
 <span data-ttu-id="c30fd-109">Následující tabulka obsahuje pokyny pro metody, které vrací vyčíslitelné kolekce.</span><span class="sxs-lookup"><span data-stu-id="c30fd-109">The following table provides a guide to the methods that return enumerable collections.</span></span>  
  
|<span data-ttu-id="c30fd-110">Výčet</span><span class="sxs-lookup"><span data-stu-id="c30fd-110">To enumerate</span></span>|<span data-ttu-id="c30fd-111">Vyčíslitelné kolekce pro vrácení</span><span class="sxs-lookup"><span data-stu-id="c30fd-111">Enumerable collection to return</span></span>|<span data-ttu-id="c30fd-112">Metoda se má použít</span><span class="sxs-lookup"><span data-stu-id="c30fd-112">Method to use</span></span>|  
|------------------|-------------------------------------|-------------------|  
|<span data-ttu-id="c30fd-113">Adresáře</span><span class="sxs-lookup"><span data-stu-id="c30fd-113">Directories</span></span>|<span data-ttu-id="c30fd-114">Názvy adresářů</span><span class="sxs-lookup"><span data-stu-id="c30fd-114">Directory names</span></span>|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="c30fd-115">Informace o adresáři (<xref:System.IO.DirectoryInfo>)</span><span class="sxs-lookup"><span data-stu-id="c30fd-115">Directory information (<xref:System.IO.DirectoryInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c30fd-116">Soubory</span><span class="sxs-lookup"><span data-stu-id="c30fd-116">Files</span></span>|<span data-ttu-id="c30fd-117">Názvy souborů</span><span class="sxs-lookup"><span data-stu-id="c30fd-117">File names</span></span>|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="c30fd-118">Informace o souboru (<xref:System.IO.FileInfo>)</span><span class="sxs-lookup"><span data-stu-id="c30fd-118">File information (<xref:System.IO.FileInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="c30fd-119">Informace o systému souborů</span><span class="sxs-lookup"><span data-stu-id="c30fd-119">File system information</span></span>|<span data-ttu-id="c30fd-120">Položky systémového souboru</span><span class="sxs-lookup"><span data-stu-id="c30fd-120">File system entries</span></span>|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
||<span data-ttu-id="c30fd-121">Informace o souborovém systému (<xref:System.IO.FileSystemInfo>)</span><span class="sxs-lookup"><span data-stu-id="c30fd-121">File system information (<xref:System.IO.FileSystemInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
  
 <span data-ttu-id="c30fd-122">I když můžete okamžitě vytvořit výčet všech souborů v podadresářích nadřazený adresář pomocí <xref:System.IO.SearchOption.AllDirectories> poskytuje možnosti vyhledávání <xref:System.IO.SearchOption> výčet, před neoprávněným přístupem výjimky (<xref:System.UnauthorizedAccessException>) může způsobit, že bude výčet nebudou úplné.</span><span class="sxs-lookup"><span data-stu-id="c30fd-122">Although you can immediately enumerate all the files in the subdirectories of a parent directory by using the <xref:System.IO.SearchOption.AllDirectories> search option provided by the <xref:System.IO.SearchOption> enumeration, unauthorized access exceptions (<xref:System.UnauthorizedAccessException>) may cause the enumeration to be incomplete.</span></span> <span data-ttu-id="c30fd-123">Pokud jsou tyto výjimky je to možné, můžete jejich zachycení a pokračovat tak, že nejprve vytváření výčtů adresářů a potom výčet souborů.</span><span class="sxs-lookup"><span data-stu-id="c30fd-123">If these exceptions are possible, you can catch them and continue by first enumerating directories and then enumerating files.</span></span>  
  
### <a name="to-enumerate-directory-names"></a><span data-ttu-id="c30fd-124">Výčet názvů adresářů</span><span class="sxs-lookup"><span data-stu-id="c30fd-124">To enumerate directory names</span></span>  
  
-   <span data-ttu-id="c30fd-125">Použití <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> metoda získat seznam názvů adresářů nejvyšší úrovně v zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="c30fd-125">Use the <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> method to obtain a list of the top-level directory names in a specified path.</span></span>  
  
     [!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
     [!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  
  
### <a name="to-enumerate-file-names-in-a-directory-and-subdirectories"></a><span data-ttu-id="c30fd-126">Výčet názvů souborů v adresáři a jeho podadresářích</span><span class="sxs-lookup"><span data-stu-id="c30fd-126">To enumerate file names in a directory and subdirectories</span></span>  
  
-   <span data-ttu-id="c30fd-127">Použití <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> metoda prohledat adresář a (volitelně) jeho podadresářích a získat seznam názvů souborů, které odpovídají zadanému vyhledávacímu vzoru.</span><span class="sxs-lookup"><span data-stu-id="c30fd-127">Use the <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> method to search a directory and (optionally) its subdirectories, and to obtain a list of file names that match a specified search pattern.</span></span>  
  
     [!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
     [!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-directoryinfo-objects"></a><span data-ttu-id="c30fd-128">Vytvoření výčtu kolekce DirectoryInfo objektů</span><span class="sxs-lookup"><span data-stu-id="c30fd-128">To enumerate a collection of DirectoryInfo objects</span></span>  
  
-   <span data-ttu-id="c30fd-129">Použití <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> metody pro získání kolekce adresářů nejvyšší úrovně.</span><span class="sxs-lookup"><span data-stu-id="c30fd-129">Use the <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> method to obtain a collection of top-level directories.</span></span>  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb#1)]  
  
### <a name="to-enumerate-a-collection-of-fileinfo-objects-in-all-directories"></a><span data-ttu-id="c30fd-130">Vytvoření výčtu kolekce FileInfo objektů ve všech adresářích</span><span class="sxs-lookup"><span data-stu-id="c30fd-130">To enumerate a collection of FileInfo objects in all directories</span></span>  
  
-   <span data-ttu-id="c30fd-131">Použití <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> metody pro získání kolekce souborů, které vyhovují zadanému vyhledávacímu vzoru ve všech adresářích.</span><span class="sxs-lookup"><span data-stu-id="c30fd-131">Use the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> method to obtain a collection of files that match a specified search pattern in all directories.</span></span> <span data-ttu-id="c30fd-132">Tento příklad nejprve vytvoří výčet adresářů nejvyšší úrovně pro zachycení výjimky je to možné neoprávněného přístupu a pak vytvoří výčet souborů.</span><span class="sxs-lookup"><span data-stu-id="c30fd-132">This example first enumerates the top-level directories to catch possible unauthorized access exceptions, and then enumerates the files.</span></span>  
  
     [!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
     [!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c30fd-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c30fd-133">See also</span></span>

- [<span data-ttu-id="c30fd-134">Vstup/výstup souborů a streamů</span><span class="sxs-lookup"><span data-stu-id="c30fd-134">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
