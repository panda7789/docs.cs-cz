---
title: 'Postupy: Hledání existujících souborů a adresářů v izolovaném úložišti'
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 277f7d562d5e345556a9047f6e4bf2b60eaef462
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61751732"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a><span data-ttu-id="04d76-102">Postupy: Hledání existujících souborů a adresářů v izolovaném úložišti</span><span class="sxs-lookup"><span data-stu-id="04d76-102">How to: Find Existing Files and Directories in Isolated Storage</span></span>

<span data-ttu-id="04d76-103">Chcete-li vyhledat adresář v izolovaném úložišti, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="04d76-103">To search for a directory in isolated storage, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="04d76-104">Tato metoda přebírá řetězec, který představuje vzor hledání.</span><span class="sxs-lookup"><span data-stu-id="04d76-104">This method takes a string that represents a search pattern.</span></span> <span data-ttu-id="04d76-105">Můžete použít jedním znakem (?) a více znaků (\*) zástupné znaky v vzor hledání, ale zástupné znaky musí být uvedena v poslední části názvu.</span><span class="sxs-lookup"><span data-stu-id="04d76-105">You can use both single-character (?) and multi-character (\*) wildcard characters in the search pattern, but the wildcard characters must appear in the final portion of the name.</span></span> <span data-ttu-id="04d76-106">Například `directory1/*ect*` je platný hledaný řetězec, ale `*ect*/directory2` není.</span><span class="sxs-lookup"><span data-stu-id="04d76-106">For example, `directory1/*ect*` is a valid search string, but `*ect*/directory2` is not.</span></span>  
  
 <span data-ttu-id="04d76-107">Chcete-li vyhledat soubor, použijte <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="04d76-107">To search for a file, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="04d76-108">Omezení zástupných znaků v řetězci pro vyhledávání, které se vztahuje na <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> platí také pro <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span><span class="sxs-lookup"><span data-stu-id="04d76-108">The restriction for wildcard characters in search strings that applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> also applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span></span>  
  
 <span data-ttu-id="04d76-109">Ani jeden z těchto metod je rekurzivní. <xref:System.IO.IsolatedStorage.IsolatedStorageFile> třída neposkytuje žádné metody pro zobrazení seznamu všech adresářů a souborů v úložišti.</span><span class="sxs-lookup"><span data-stu-id="04d76-109">Neither of these methods is recursive; the <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class does not supply any methods for listing all directories or files in your store.</span></span> <span data-ttu-id="04d76-110">Rekurzivní metody jsou však uvedeny v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="04d76-110">However, recursive methods are shown in the following code example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="04d76-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="04d76-111">Example</span></span>  
 <span data-ttu-id="04d76-112">Následující příklad kódu ukazuje, jak vytváření souborů a adresářů v izolovaném úložišti.</span><span class="sxs-lookup"><span data-stu-id="04d76-112">The following code example illustrates how to create files and directories in an isolated store.</span></span> <span data-ttu-id="04d76-113">Nejprve je úložiště, které je izolováno podle uživatele, domény a sestavení načten a umístí do `isoStore` proměnné.</span><span class="sxs-lookup"><span data-stu-id="04d76-113">First, a store that is isolated for user, domain, and assembly is retrieved and placed in the `isoStore` variable.</span></span> <span data-ttu-id="04d76-114"><xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> Metoda se používá k několika různým adresářům, nastavení a <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> konstruktor vytvoří některé soubory v těchto adresářích.</span><span class="sxs-lookup"><span data-stu-id="04d76-114">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> method is used to set up a few different directories, and the <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> constructor creates some files in these directories.</span></span> <span data-ttu-id="04d76-115">Kód poté prochází výsledky `GetAllDirectories` metody.</span><span class="sxs-lookup"><span data-stu-id="04d76-115">The code then loops through the results of the `GetAllDirectories` method.</span></span> <span data-ttu-id="04d76-116">Tato metoda používá <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> najít všechny názvy adresářů v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="04d76-116">This method uses <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> to find all the directory names in the current directory.</span></span> <span data-ttu-id="04d76-117">Tyto názvy jsou uloženy v poli a potom `GetAllDirectories` zavolá sama sebe, předávání v každém adresáři se nenašel.</span><span class="sxs-lookup"><span data-stu-id="04d76-117">These names are stored in an array, and then `GetAllDirectories` calls itself, passing in each directory it has found.</span></span> <span data-ttu-id="04d76-118">V důsledku toho jsou všechny názvy adresářů vrátí ve formě pole.</span><span class="sxs-lookup"><span data-stu-id="04d76-118">As a result, all the directory names are returned in an array.</span></span> <span data-ttu-id="04d76-119">V dalším kroku kód volá `GetAllFiles` metody.</span><span class="sxs-lookup"><span data-stu-id="04d76-119">Next, the code calls the `GetAllFiles` method.</span></span> <span data-ttu-id="04d76-120">Tato metoda volá `GetAllDirectories` Pokud chcete zjistit, názvy všech adresářů a poté zkontroluje každý adresář pro soubory pomocí <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="04d76-120">This method calls `GetAllDirectories` to find out the names of all the directories, and then it checks each directory for files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> method.</span></span> <span data-ttu-id="04d76-121">Výsledek se vrátí v poli pro zobrazení.</span><span class="sxs-lookup"><span data-stu-id="04d76-121">The result is returned in an array for display.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="04d76-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04d76-122">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="04d76-123">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="04d76-123">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
