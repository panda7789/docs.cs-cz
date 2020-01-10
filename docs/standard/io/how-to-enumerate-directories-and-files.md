---
title: 'Postupy: zobrazení výčtu adresářů a souborů'
ms.date: 12/27/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], enumerating directories and files
ms.assetid: 86b69a08-3bfa-4e5f-b4e1-3b7cb8478215
ms.openlocfilehash: 6a26d0ef529b81976c4d2caafed34bb5f08d8d46
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707742"
---
# <a name="how-to-enumerate-directories-and-files"></a><span data-ttu-id="80925-102">Postupy: zobrazení výčtu adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="80925-102">How to: Enumerate directories and files</span></span>
<span data-ttu-id="80925-103">Vyčíslitelné kolekce poskytují lepší výkon než pole při práci s velkými kolekcemi adresářů a souborů.</span><span class="sxs-lookup"><span data-stu-id="80925-103">Enumerable collections provide better performance than arrays when you work with large collections of directories and files.</span></span> <span data-ttu-id="80925-104">Chcete-li vytvořit výčet adresářů a souborů, použijte metody, které vracejí vyčíslitelné kolekce názvů adresářů nebo souborů, nebo jejich <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>nebo <xref:System.IO.FileSystemInfo> objektů.</span><span class="sxs-lookup"><span data-stu-id="80925-104">To enumerate directories and files, use methods that return an enumerable collection of directory or file names, or their <xref:System.IO.DirectoryInfo>, <xref:System.IO.FileInfo>, or <xref:System.IO.FileSystemInfo> objects.</span></span>  
  
<span data-ttu-id="80925-105">Pokud chcete vyhledávat a vracet pouze názvy adresářů nebo souborů, použijte metody výčtu třídy <xref:System.IO.Directory>.</span><span class="sxs-lookup"><span data-stu-id="80925-105">If you want to search and return only the names of directories or files, use the enumeration methods of the <xref:System.IO.Directory> class.</span></span> <span data-ttu-id="80925-106">Pokud chcete hledat a vracet jiné vlastnosti adresářů nebo souborů, použijte třídy <xref:System.IO.DirectoryInfo> a <xref:System.IO.FileSystemInfo>.</span><span class="sxs-lookup"><span data-stu-id="80925-106">If you want to search and return other properties of directories or files, use the <xref:System.IO.DirectoryInfo> and <xref:System.IO.FileSystemInfo> classes.</span></span>  
  
<span data-ttu-id="80925-107">Vyčíslitelné kolekce z těchto metod lze použít jako parametr <xref:System.Collections.Generic.IEnumerable%601> pro konstruktory tříd kolekcí, jako je například <xref:System.Collections.Generic.List%601>.</span><span class="sxs-lookup"><span data-stu-id="80925-107">You can use enumerable collections from these methods as the <xref:System.Collections.Generic.IEnumerable%601> parameter for constructors of collection classes like <xref:System.Collections.Generic.List%601>.</span></span>  
  
<span data-ttu-id="80925-108">Následující tabulka shrnuje metody, které vracejí vyčíslitelné kolekce souborů a adresářů:</span><span class="sxs-lookup"><span data-stu-id="80925-108">The following table summarizes the methods that return enumerable collections of files and directories:</span></span>  
  
|<span data-ttu-id="80925-109">Hledání a vrácení</span><span class="sxs-lookup"><span data-stu-id="80925-109">To search and return</span></span>|<span data-ttu-id="80925-110">Use – metoda</span><span class="sxs-lookup"><span data-stu-id="80925-110">Use method</span></span>|  
|------------------|-------------------------------------|-------------------|  
|<span data-ttu-id="80925-111">Názvy adresářů</span><span class="sxs-lookup"><span data-stu-id="80925-111">Directory names</span></span>|<xref:System.IO.Directory.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="80925-112">Informace o adresáři (<xref:System.IO.DirectoryInfo>)</span><span class="sxs-lookup"><span data-stu-id="80925-112">Directory information (<xref:System.IO.DirectoryInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="80925-113">Názvy souborů</span><span class="sxs-lookup"><span data-stu-id="80925-113">File names</span></span>|<xref:System.IO.Directory.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="80925-114">Informace o souboru (<xref:System.IO.FileInfo>)</span><span class="sxs-lookup"><span data-stu-id="80925-114">File information (<xref:System.IO.FileInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="80925-115">Názvy položek systému souborů</span><span class="sxs-lookup"><span data-stu-id="80925-115">File system entry names</span></span>|<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="80925-116">Informace o záznamech systému souborů (<xref:System.IO.FileSystemInfo>)</span><span class="sxs-lookup"><span data-stu-id="80925-116">File system entry information (<xref:System.IO.FileSystemInfo>)</span></span>|<xref:System.IO.DirectoryInfo.EnumerateFileSystemInfos%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="80925-117">Názvy adresářů a souborů</span><span class="sxs-lookup"><span data-stu-id="80925-117">Directory and file names</span></span> |<xref:System.IO.Directory.EnumerateFileSystemEntries%2A?displayProperty=nameWithType>|  

> [!NOTE]
> <span data-ttu-id="80925-118">I když můžete okamžitě vytvořit výčet všech souborů v podadresářích nadřazeného adresáře pomocí možnosti <xref:System.IO.SearchOption.AllDirectories> volitelného výčtu <xref:System.IO.SearchOption>, <xref:System.UnauthorizedAccessException> chyby můžou výčet nekompletní.</span><span class="sxs-lookup"><span data-stu-id="80925-118">Although you can immediately enumerate all the files in the subdirectories of a parent directory by using the <xref:System.IO.SearchOption.AllDirectories> option of the optional <xref:System.IO.SearchOption> enumeration, <xref:System.UnauthorizedAccessException> errors may make the enumeration incomplete.</span></span> <span data-ttu-id="80925-119">Tyto výjimky můžete zachytit při prvním vytváření výčtu adresářů a pak při vytváření výčtu souborů.</span><span class="sxs-lookup"><span data-stu-id="80925-119">You can catch these exceptions by first enumerating directories and then enumerating files.</span></span>  
  
## <a name="examples-use-the-directory-class"></a><span data-ttu-id="80925-120">Příklady: použití třídy adresáře</span><span class="sxs-lookup"><span data-stu-id="80925-120">Examples: Use the Directory class</span></span>  
  
<span data-ttu-id="80925-121">Následující příklad používá metodu <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> k získání seznamu názvů adresářů nejvyšší úrovně v zadané cestě.</span><span class="sxs-lookup"><span data-stu-id="80925-121">The following example uses the <xref:System.IO.Directory.EnumerateDirectories%28System.String%29?displayProperty=nameWithType> method to get a list of the top-level directory names in a specified path.</span></span>  

[!code-csharp[System.IO.EnumDirs1#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.enumdirs1/cs/program.cs#1)]
[!code-vb[System.IO.EnumDirs1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.enumdirs1/vb/program.vb#1)]  

<span data-ttu-id="80925-122">Následující příklad používá metodu <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> k rekurzivnímu zobrazení výčtu všech názvů souborů v adresáři a podadresářích, které odpovídají určitému vzoru.</span><span class="sxs-lookup"><span data-stu-id="80925-122">The following example uses the <xref:System.IO.Directory.EnumerateFiles%28System.String%2CSystem.String%2CSystem.IO.SearchOption%29?displayProperty=nameWithType> method to recursively enumerate all file names in a directory and subdirectories that match a certain pattern.</span></span> <span data-ttu-id="80925-123">Pak přečte jednotlivé řádky jednotlivých souborů a zobrazí řádky, které obsahují zadaný řetězec, s názvy souborů a cestami.</span><span class="sxs-lookup"><span data-stu-id="80925-123">It then reads each line of each file and displays the lines that contain a specified string, with their filenames and paths.</span></span>

[!code-csharp[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/cs/program.cs#1)]
[!code-vb[System.IO.Directory.EnumerateFiles#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directory.enumeratefiles/vb/program.vb#1)]  
  
## <a name="examples-use-the-directoryinfo-class"></a><span data-ttu-id="80925-124">Příklady: použití třídy DirectoryInfo</span><span class="sxs-lookup"><span data-stu-id="80925-124">Examples: Use the DirectoryInfo class</span></span>  
  
<span data-ttu-id="80925-125">Následující příklad používá metodu <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> k vypsání kolekce adresářů nejvyšší úrovně, jejichž <xref:System.IO.FileSystemInfo.CreationTimeUtc> je dřívější než určitá <xref:System.DateTime> hodnota.</span><span class="sxs-lookup"><span data-stu-id="80925-125">The following example uses the <xref:System.IO.DirectoryInfo.EnumerateDirectories%2A?displayProperty=nameWithType> method to list a collection of top-level directories whose <xref:System.IO.FileSystemInfo.CreationTimeUtc> is earlier than a certain <xref:System.DateTime> value.</span></span>  

[!code-csharp[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/cs/program.cs)]
[!code-vb[System.IO.DirectoryInfo.EnumDirs#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumdirs/vb/module1.vb)]  
  
<span data-ttu-id="80925-126">Následující příklad používá metodu <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> k vypsání všech souborů, jejichž <xref:System.IO.FileInfo.Length> překračuje 10 MB.</span><span class="sxs-lookup"><span data-stu-id="80925-126">The following example uses the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A?displayProperty=nameWithType> method to list all files whose <xref:System.IO.FileInfo.Length> exceeds 10MB.</span></span> <span data-ttu-id="80925-127">Tento příklad nejprve vytvoří výčet adresářů nejvyšší úrovně, aby se zachytily možné výjimky neoprávněného přístupu, a potom vytvoří výčet souborů.</span><span class="sxs-lookup"><span data-stu-id="80925-127">This example first enumerates the top-level directories, to catch possible unauthorized access exceptions, and then enumerates the files.</span></span>  

[!code-csharp[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/cs/program.cs#1)]
[!code-vb[System.IO.DirectoryInfo.EnumerateDirectories#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.directoryinfo.enumeratedirectories/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="80925-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="80925-128">See also</span></span>

- [<span data-ttu-id="80925-129">Vstupně-výstupní operace se soubory a datovým proudem</span><span class="sxs-lookup"><span data-stu-id="80925-129">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
