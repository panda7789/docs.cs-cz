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
ms.openlocfilehash: dfebcc9acf0b699f898c106921d15ce0294bc5d2
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75707130"
---
# <a name="how-to-find-existing-files-and-directories-in-isolated-storage"></a><span data-ttu-id="fcc0f-102">Postupy: Hledání existujících souborů a adresářů v izolovaném úložišti</span><span class="sxs-lookup"><span data-stu-id="fcc0f-102">How to: Find Existing Files and Directories in Isolated Storage</span></span>

<span data-ttu-id="fcc0f-103">Chcete-li vyhledat adresář v izolovaném úložišti, použijte metodu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcc0f-103">To search for a directory in isolated storage, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fcc0f-104">Tato metoda přebírá řetězec, který představuje vzor hledání.</span><span class="sxs-lookup"><span data-stu-id="fcc0f-104">This method takes a string that represents a search pattern.</span></span> <span data-ttu-id="fcc0f-105">Ve vzoru vyhledávání můžete použít zástupné znaky s jedním znakem (?) i více znaky (\*), ale zástupné znaky se musí objevit v poslední části názvu.</span><span class="sxs-lookup"><span data-stu-id="fcc0f-105">You can use both single-character (?) and multi-character (\*) wildcard characters in the search pattern, but the wildcard characters must appear in the final portion of the name.</span></span> <span data-ttu-id="fcc0f-106">Například `directory1/*ect*` je platný hledaný řetězec, ale `*ect*/directory2` není.</span><span class="sxs-lookup"><span data-stu-id="fcc0f-106">For example, `directory1/*ect*` is a valid search string, but `*ect*/directory2` is not.</span></span>  
  
 <span data-ttu-id="fcc0f-107">Chcete-li vyhledat soubor, použijte metodu <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fcc0f-107">To search for a file, use the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fcc0f-108">Omezení pro zástupné znaky ve vyhledávacích řetězcích, které platí pro <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A>, platí také pro <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span><span class="sxs-lookup"><span data-stu-id="fcc0f-108">The restriction for wildcard characters in search strings that applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> also applies to <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span></span>  
  
 <span data-ttu-id="fcc0f-109">Ani jedna z těchto metod není rekurzivní; Třída <xref:System.IO.IsolatedStorage.IsolatedStorageFile> neposkytuje žádné metody pro výpis všech adresářů nebo souborů ve vašem úložišti.</span><span class="sxs-lookup"><span data-stu-id="fcc0f-109">Neither of these methods is recursive; the <xref:System.IO.IsolatedStorage.IsolatedStorageFile> class does not supply any methods for listing all directories or files in your store.</span></span> <span data-ttu-id="fcc0f-110">Nicméně rekurzivní metody jsou uvedeny v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="fcc0f-110">However, recursive methods are shown in the following code example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fcc0f-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="fcc0f-111">Example</span></span>  
 <span data-ttu-id="fcc0f-112">Následující příklad kódu ukazuje, jak vytvořit soubory a adresáře v izolovaném úložišti.</span><span class="sxs-lookup"><span data-stu-id="fcc0f-112">The following code example illustrates how to create files and directories in an isolated store.</span></span> <span data-ttu-id="fcc0f-113">Nejprve se načte úložiště izolované pro uživatele, doménu a sestavení a umístí se do proměnné `isoStore`.</span><span class="sxs-lookup"><span data-stu-id="fcc0f-113">First, a store that is isolated for user, domain, and assembly is retrieved and placed in the `isoStore` variable.</span></span> <span data-ttu-id="fcc0f-114">Metoda <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> slouží k nastavení několika různých adresářů a konstruktor <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> vytvoří některé soubory v těchto adresářích.</span><span class="sxs-lookup"><span data-stu-id="fcc0f-114">The <xref:System.IO.IsolatedStorage.IsolatedStorageFile.CreateDirectory%2A> method is used to set up a few different directories, and the <xref:System.IO.IsolatedStorage.IsolatedStorageFileStream.%23ctor%28System.String%2CSystem.IO.FileMode%2CSystem.IO.IsolatedStorage.IsolatedStorageFile%29> constructor creates some files in these directories.</span></span> <span data-ttu-id="fcc0f-115">Kód pak projde výsledky metody `GetAllDirectories`.</span><span class="sxs-lookup"><span data-stu-id="fcc0f-115">The code then loops through the results of the `GetAllDirectories` method.</span></span> <span data-ttu-id="fcc0f-116">Tato metoda používá <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> k vyhledání všech názvů adresářů v aktuálním adresáři.</span><span class="sxs-lookup"><span data-stu-id="fcc0f-116">This method uses <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetDirectoryNames%2A> to find all the directory names in the current directory.</span></span> <span data-ttu-id="fcc0f-117">Tyto názvy jsou uloženy v poli a následně `GetAllDirectories` volání sebe sama a procházející v každém nalezeném adresáři.</span><span class="sxs-lookup"><span data-stu-id="fcc0f-117">These names are stored in an array, and then `GetAllDirectories` calls itself, passing in each directory it has found.</span></span> <span data-ttu-id="fcc0f-118">V důsledku toho jsou všechny názvy adresářů vráceny v poli.</span><span class="sxs-lookup"><span data-stu-id="fcc0f-118">As a result, all the directory names are returned in an array.</span></span> <span data-ttu-id="fcc0f-119">Dále kód volá metodu `GetAllFiles`.</span><span class="sxs-lookup"><span data-stu-id="fcc0f-119">Next, the code calls the `GetAllFiles` method.</span></span> <span data-ttu-id="fcc0f-120">Tato metoda volá `GetAllDirectories` pro zjištění názvů všech adresářů a pak zkontroluje každý adresář pro soubory pomocí metody <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A>.</span><span class="sxs-lookup"><span data-stu-id="fcc0f-120">This method calls `GetAllDirectories` to find out the names of all the directories, and then it checks each directory for files by using the <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetFileNames%2A> method.</span></span> <span data-ttu-id="fcc0f-121">Výsledek je vrácen v poli pro zobrazení.</span><span class="sxs-lookup"><span data-stu-id="fcc0f-121">The result is returned in an array for display.</span></span>  
  
 [!code-cpp[Conceptual.IsolatedStorage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source8.cpp#9)]
 [!code-csharp[Conceptual.IsolatedStorage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source8.cs#9)]
 [!code-vb[Conceptual.IsolatedStorage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source8.vb#9)]  
  
## <a name="see-also"></a><span data-ttu-id="fcc0f-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fcc0f-122">See also</span></span>

- <xref:System.IO.IsolatedStorage.IsolatedStorageFile>
- [<span data-ttu-id="fcc0f-123">Izolované úložiště</span><span class="sxs-lookup"><span data-stu-id="fcc0f-123">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)
