---
title: 'Postupy: Vytvoření výčtu adresářů a souborů'
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 863335cf080dbccd76b38c7222b74637b99ae2f0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751814"
---
# <a name="how-to-enumerate-directories-and-files"></a><span data-ttu-id="79fbe-102">Postupy: Vytvoření výčtu adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="79fbe-102">How to: Enumerate directories and files</span></span>
<span data-ttu-id="79fbe-103">Vyčíslitelné kolekce poskytují lepší výkon než pole při práci s rozsáhlých kolekcí adresářů a souborů.</span><span class="sxs-lookup"><span data-stu-id="79fbe-103">Enumerable collections provide better performance than arrays when you work with large collections of directories and files.</span></span> <span data-ttu-id="79fbe-104">Vytvoření výčtu adresářů a souborů, použijte metody, které vrací vyčíslitelné kolekce názvů adresář nebo soubor, nebo jejich <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, nebo <xref:System.IO.FileSystemInfo> objekty.</span><span class="sxs-lookup"><span data-stu-id="79fbe-104">To enumerate directories and files, use methods that return an enumerable collection of directory or file names, or their <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, or <xref:System.IO.FileSystemInfo> objects.</span></span>  
  
<span data-ttu-id="79fbe-105">Pokud chcete vyhledat a vrátí pouze názvy adresářů a souborů, použijte metody výčet <xref:System.IO.Directory> třídy.</span><span class="sxs-lookup"><span data-stu-id="79fbe-105">If you want to search and return only the names of directories or files, use the enumeration methods of the <xref:System.IO.Directory> class.</span></span> <span data-ttu-id="79fbe-106">Pokud chcete vyhledat a vrátit jiné vlastnosti adresářů a souborů, použijte <xref:System.IO.DirectoryInfo> a <xref:System.IO.FileSystemInfo> třídy.</span><span class="sxs-lookup"><span data-stu-id="79fbe-106">If you want to search and return other properties of directories or files, use the <xref:System.IO.DirectoryInfo> and <xref:System.IO.FileSystemInfo> classes.</span></span>  
  
<span data-ttu-id="79fbe-107">Můžete použít vyčíslitelné kolekce z těchto metod, jako <xref:System.Collections.Generic.IEnumerable%601> parametr pro konstruktory tříd kolekcí, jako jsou <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="79fbe-107">You can use enumerable collections from these methods as the <xref:System.Collections.Generic.IEnumerable%601> parameter for constructors of collection classes like <xref:System.Collections.Generic.List%601>.</span></span>  
  
<span data-ttu-id="79fbe-108">Následující tabulka shrnuje metody, které vrací vyčíslitelné kolekce souborů a adresářů:</span><span class="sxs-lookup"><span data-stu-id="79fbe-108">The following table summarizes the methods that return enumerable collections of files and directories:</span></span>  
  
|<span data-ttu-id="79fbe-109">K vyhledání a vrácení</span><span class="sxs-lookup"><span data-stu-id="79fbe-109">To search and return</span></span>|<span data-ttu-id="79fbe-110">Použít – metoda</span><span class="sxs-lookup"><span data-stu-id="79fbe-110">Use method</span></span>|  
|------------------|-------------------------------------|-------------------|  
|<span data-ttu-id="79fbe-111">Názvy adresářů</span><span class="sxs-lookup"><span data-stu-id="79fbe-111">Directory names</span></span>|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="79fbe-112">Informace o adresáři (<xref:System.IO.DirectoryInfo>)</span><span class="sxs-lookup"><span data-stu-id="79fbe-112">Directory information (<xref:System.IO.DirectoryInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="79fbe-113">Názvy souborů</span><span class="sxs-lookup"><span data-stu-id="79fbe-113">File names</span></span>|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="79fbe-114">Informace o souboru (<xref:System.IO.FileInfo>)</span><span class="sxs-lookup"><span data-stu-id="79fbe-114">File information (<xref:System.IO.FileInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="79fbe-115">Názvy pro položku systému souborů</span><span class="sxs-lookup"><span data-stu-id="79fbe-115">File system entry names</span></span>|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="79fbe-116">Informace o souborovém systému položku (<xref:System.IO.FileSystemInfo>)</span><span class="sxs-lookup"><span data-stu-id="79fbe-116">File system entry information (<xref:System.IO.FileSystemInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="79fbe-117">Názvy adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="79fbe-117">Directory and file names</span></span> |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> <span data-ttu-id="79fbe-118">I když můžete okamžitě vytvořit výčet všech souborů v podadresářích nadřazený adresář pomocí <xref:System.IO.SearchOption.AllDirectories> možnost volitelné <xref:System.IO.SearchOption> výčet, <xref:System.UnauthorizedAccessException> chyby může být výčet neúplné.</span><span class="sxs-lookup"><span data-stu-id="79fbe-118">Although you can immediately enumerate all the files in the subdirectories of a parent directory by using the <xref:System.IO.SearchOption.AllDirectories> option of the optional <xref:System.IO.SearchOption> enumeration, <xref:System.UnauthorizedAccessException> errors may make the enumeration incomplete.</span></span> <span data-ttu-id="79fbe-119">Zachytit tyto výjimky tak, že nejprve vytváření výčtů adresářů a potom výčet souborů.</span><span class="sxs-lookup"><span data-stu-id="79fbe-119">You can catch these exceptions by first enumerating directories and then enumerating files.</span></span>  
  
## <a name="examples-use-the-directory-class"></a><span data-ttu-id="79fbe-120">Příklady: Použití třídy adresáře</span><span class="sxs-lookup"><span data-stu-id="79fbe-120">Examples: Use the Directory class</span></span>  
  
<span data-ttu-id="79fbe-121">V následujícím příkladu <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> metodu k získání seznamu názvů adresář nejvyšší úrovně v zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="79fbe-121">The following example uses the <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> method to get a list of the top-level directory names in a specified path.</span></span>  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

<span data-ttu-id="79fbe-122">V následujícím příkladu <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> metoda rekurzivně výčet všechny názvy souborů v adresáře a podadresářů, které odpovídají určité vzoru.</span><span class="sxs-lookup"><span data-stu-id="79fbe-122">The following example uses the <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> method to recursively enumerate all file names in a directory and subdirectories that match a certain pattern.</span></span> <span data-ttu-id="79fbe-123">Pak přečte každý řádek v jednotlivých souborů a zobrazí řádky, které obsahují zadaného řetězce s názvy souborů a cesty.</span><span class="sxs-lookup"><span data-stu-id="79fbe-123">It then reads each line of each file and displays the lines that contain a specified string, with their filenames and paths.</span></span>

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a><span data-ttu-id="79fbe-124">Příklady: Použití třídy DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="79fbe-124">Examples: Use the DirectoryInfo class</span></span>  
  
<span data-ttu-id="79fbe-125">V následujícím příkladu <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> metodu do seznamu kolekce adresářů nejvyšší úrovně jehož <xref:System.IO.FileSystemInfo.CreationTimeUtc> je starší než určitým <xref:System.DateTime> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="79fbe-125">The following example uses the <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> method to list a collection of top-level directories whose <xref:System.IO.FileSystemInfo.CreationTimeUtc> is earlier than a certain <xref:System.DateTime> value.</span></span>  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
<span data-ttu-id="79fbe-126">V následujícím příkladu <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> metodu pro výpis všech souborů, jejichž <xref:System.IO.FileInfo.Length> přesahuje 10 MB.</span><span class="sxs-lookup"><span data-stu-id="79fbe-126">The following example uses the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> method to list all files whose <xref:System.IO.FileInfo.Length> exceeds 10MB.</span></span> <span data-ttu-id="79fbe-127">Tento příklad nejprve vytvoří výčet adresářů nejvyšší úrovně, jak zachytávat výjimky možné neoprávněnému přístupu a potom vytvoří výčet souborů.</span><span class="sxs-lookup"><span data-stu-id="79fbe-127">This example first enumerates the top-level directories, to catch possible unauthorized access exceptions, and then enumerates the files.</span></span>  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="79fbe-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79fbe-128">See also</span></span>

- [<span data-ttu-id="79fbe-129">Vstupně-výstupních operací souborů a datových proudů</span><span class="sxs-lookup"><span data-stu-id="79fbe-129">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
