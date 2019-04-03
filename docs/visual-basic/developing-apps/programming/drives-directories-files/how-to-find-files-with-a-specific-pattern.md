---
title: 'Postupy: Hledání souborů pomocí specifického vzoru v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: e4d40c4ad3a694b3f7e830604edf94d90cb4c395
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825323"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="14588-102">Postupy: Hledání souborů pomocí specifického vzoru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="14588-102">How to: Find Files with a Specific Pattern in Visual Basic</span></span>
<span data-ttu-id="14588-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> Metoda vrátí kolekci řetězců, které představují názvy cest souborů jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="14588-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="14588-104">Můžete použít `wildCards` parametr k určení určitému vzoru.</span><span class="sxs-lookup"><span data-stu-id="14588-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="14588-105">Pokud chcete do hledání zahrnout podadresářů, nastavte `searchType` parametr `SearchOption.SearchAllSubDirectories`.</span><span class="sxs-lookup"><span data-stu-id="14588-105">If you would like to include subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>  
  
 <span data-ttu-id="14588-106">Prázdná kolekce je vrácena, pokud se nenajdou žádné soubory odpovídající zadanému vzoru.</span><span class="sxs-lookup"><span data-stu-id="14588-106">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="14588-107">Informace o vrácení seznamu souborů pomocí `DirectoryInfo` třídu `System.IO` obor názvů, naleznete v tématu <xref:System.IO.DirectoryInfo.GetFiles%2A>.</span><span class="sxs-lookup"><span data-stu-id="14588-107">For information about returning a file list by using the `DirectoryInfo` class of the `System.IO` namespace, see <xref:System.IO.DirectoryInfo.GetFiles%2A>.</span></span>  
  
### <a name="to-find-files-with-a-specified-pattern"></a><span data-ttu-id="14588-108">K vyhledání souborů s zadanému vzoru</span><span class="sxs-lookup"><span data-stu-id="14588-108">To find files with a specified pattern</span></span>  
  
-   <span data-ttu-id="14588-109">Použití `GetFiles` metody poskytnutí název a cesta k adresáři, kterou chcete vyhledat a určení vzoru.</span><span class="sxs-lookup"><span data-stu-id="14588-109">Use the `GetFiles` method, supplying the name and path of the directory you want to search and specifying the pattern.</span></span> <span data-ttu-id="14588-110">Následující příklad vrátí všechny soubory s příponou `.dll` v adresáři a přidá je do `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="14588-110">The following example returns all files with the extension `.dll` in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="14588-111">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="14588-111">.NET Framework Security</span></span>  
 <span data-ttu-id="14588-112">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="14588-112">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="14588-113">Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje pouze mezeru, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="14588-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="14588-114">Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="14588-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="14588-115">`directory` neexistuje (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="14588-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="14588-116">`directory` odkaz na existující soubor (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="14588-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="14588-117">Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="14588-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="14588-118">Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="14588-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="14588-119">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="14588-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="14588-120">Uživatel nemá potřebná oprávnění (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="14588-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14588-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14588-121">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="14588-122">Postupy: Hledání podadresářů pomocí specifického vzoru</span><span class="sxs-lookup"><span data-stu-id="14588-122">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="14588-123">Řešení potíží: Čtení a zápis do textových souborů</span><span class="sxs-lookup"><span data-stu-id="14588-123">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="14588-124">Postupy: Získání kolekce souborů v adresáři</span><span class="sxs-lookup"><span data-stu-id="14588-124">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
