---
title: "Postupy: Hledání existujících souborů a adresářů v izolovaném úložišti"
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
- cpp
helpviewer_keywords:
- stores, finding files and directories
- locating files in isolated storage file
- directories [.NET Framework], isolated storage
- isolated storage, finding files and directories
- data storage using isolated storage, finding files and directories
- files [.NET Framework], isolated storage
- data stores, finding files and directories
- locating directories in isolated storage file
- storing data using isolated storage, finding files and directories
ms.assetid: eb28458a-6161-4e7a-9ada-30ef93761b5c
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8d460f07e7558fdf9190561b1cac4307767ff245
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a><span data-ttu-id="91514-102">Postupy: Hledání existujících souborů a adresářů v izolovaném úložišti</span><span class="sxs-lookup"><span data-stu-id="91514-102">How to: Find Existing Files and Directories in Isolated Storage</span></span>
<span data-ttu-id="91514-103">Chcete-li vyhledat adresáře v izolovaném úložišti, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="91514-103">To search for a directory in isolated storage, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="91514-104">Tato metoda přebírá řetězec, který představuje vzor hledání.</span><span class="sxs-lookup"><span data-stu-id="91514-104">This method takes a string that represents a search pattern.</span></span> <span data-ttu-id="91514-105">Délce jednoho znaku (?) i více znak (*) můžete použít zástupné znaky v vzor hledání, ale musí být zadány v Závěrečná část názvu zástupné znaky.</span><span class="sxs-lookup"><span data-stu-id="91514-105">You can use both single-character (?) and multi-character (*) wildcard characters in the search pattern, but the wildcard characters must appear in the final portion of the name.</span></span> <span data-ttu-id="91514-106">Například `directory1/*ect*` je platný hledaný řetězec, ale `*ect*/directory2` není.</span><span class="sxs-lookup"><span data-stu-id="91514-106">For example, `directory1/*ect*` is a valid search string, but `*ect*/directory2` is not.</span></span>  
  
 <span data-ttu-id="91514-107">Chcete-li vyhledat soubor, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="91514-107">To search for a file, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="91514-108">Omezení pro zástupné znaky ve vyhledávacích řetězců, které se vztahují na <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> platí také pro <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span><span class="sxs-lookup"><span data-stu-id="91514-108">The restriction for wildcard characters in search strings that applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> also applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span></span>  
  
 <span data-ttu-id="91514-109">Ani jeden z těchto metod je rekurzivní. <xref:System.IO.IsolatedStorage.IsolatedStorageFile> třída neposkytuje žádné metody pro výpis všech adresářů nebo souborů v úložišti.</span><span class="sxs-lookup"><span data-stu-id="91514-109">Neither of these methods is recursive; the <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class does not supply any methods for listing all directories or files in your store.</span></span> <span data-ttu-id="91514-110">Ale rekurzivní metody jsou uvedeny v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="91514-110">However, recursive methods are shown in the following code example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91514-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="91514-111">Example</span></span>  
 <span data-ttu-id="91514-112">Následující příklad kódu ukazuje postup vytvoření souborů a adresářů v izolovaném úložišti.</span><span class="sxs-lookup"><span data-stu-id="91514-112">The following code example illustrates how to create files and directories in an isolated store.</span></span> <span data-ttu-id="91514-113">Nejprve je úložiště, které je pro uživatele, domény a sestavení izolované načíst a uložena v umístění `isoStore` proměnné.</span><span class="sxs-lookup"><span data-stu-id="91514-113">First, a store that is isolated for user, domain, and assembly is retrieved and placed in the `isoStore` variable.</span></span> <span data-ttu-id="91514-114"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> Metoda se používá k vytvoření několik různých adresářů a <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> konstruktor vytvoří některé soubory v těchto adresářích.</span><span class="sxs-lookup"><span data-stu-id="91514-114">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> method is used to set up a few different directories, and the <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> constructor creates some files in these directories.</span></span> <span data-ttu-id="91514-115">Kód pak prochází výsledky `GetAllDirectories` metoda.</span><span class="sxs-lookup"><span data-stu-id="91514-115">The code then loops through the results of the `GetAllDirectories` method.</span></span> <span data-ttu-id="91514-116">Tato metoda používá <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> k vyhledání všech názvů adresářů v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="91514-116">This method uses <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> to find all the directory names in the current directory.</span></span> <span data-ttu-id="91514-117">Tyto názvy jsou uložené v pole a potom `GetAllDirectories` volání sebe, předávání v každý adresář, který najde.</span><span class="sxs-lookup"><span data-stu-id="91514-117">These names are stored in an array, and then `GetAllDirectories` calls itself, passing in each directory it has found.</span></span> <span data-ttu-id="91514-118">V důsledku toho jsou vráceny všechny názvy adresářů v matici.</span><span class="sxs-lookup"><span data-stu-id="91514-118">As a result, all the directory names are returned in an array.</span></span> <span data-ttu-id="91514-119">V dalším kroku kód zavolá `GetAllFiles` metoda.</span><span class="sxs-lookup"><span data-stu-id="91514-119">Next, the code calls the `GetAllFiles` method.</span></span> <span data-ttu-id="91514-120">Tato metoda volá `GetAllDirectories` a zjistěte, názvy všech adresáře a poté zkontroluje každý adresář pro soubory pomocí <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="91514-120">This method calls `GetAllDirectories` to find out the names of all the directories, and then it checks each directory for files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> method.</span></span> <span data-ttu-id="91514-121">Výsledkem je vrácený v poli pro zobrazení.</span><span class="sxs-lookup"><span data-stu-id="91514-121">The result is returned in an array for display.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="91514-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="91514-122">See Also</span></span>  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile>  
 [<span data-ttu-id="91514-123">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="91514-123">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
