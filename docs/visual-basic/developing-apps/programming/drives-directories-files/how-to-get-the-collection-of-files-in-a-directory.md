---
title: 'Postupy: Získání kolekce souborů v adresáři v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
ms.openlocfilehash: 788e3d572be1b4e76574af8679ebcff4b61197a5
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818836"
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a><span data-ttu-id="53dee-102">Postupy: Získání kolekce souborů v adresáři v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="53dee-102">How to: Get the Collection of Files in a Directory in Visual Basic</span></span>
<span data-ttu-id="53dee-103">Přetížení <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> metoda vrátit jen pro čtení kolekce řetězců, které představují názvy souborů v adresáři:</span><span class="sxs-lookup"><span data-stu-id="53dee-103">The overloads of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method return a read-only collection of strings representing the names of the files within a directory:</span></span>  
  
-   <span data-ttu-id="53dee-104">Použití <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> přetížení pro hledání jednoduchého souboru v zadaném adresáři, bez vyhledávání podadresářů.</span><span class="sxs-lookup"><span data-stu-id="53dee-104">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> overload for a simple file search in a specified directory, without searching subdirectories.</span></span>  
  
-   <span data-ttu-id="53dee-105">Použití <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> přetížení k určení dalších možností pro hledání.</span><span class="sxs-lookup"><span data-stu-id="53dee-105">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> overload to specify additional options for your search.</span></span> <span data-ttu-id="53dee-106">Můžete použít `wildCards` parametr k určení vzoru hledání.</span><span class="sxs-lookup"><span data-stu-id="53dee-106">You can use the `wildCards` parameter to specify a search pattern.</span></span> <span data-ttu-id="53dee-107">Chcete-li do hledání zahrnout podadresářů, nastavte `searchType` parametr <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="53dee-107">To include subdirectories in the search, set the `searchType` parameter to <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="53dee-108">Prázdná kolekce je vrácena, pokud se nenajdou žádné soubory odpovídající zadanému vzoru.</span><span class="sxs-lookup"><span data-stu-id="53dee-108">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
### <a name="to-list-files-in-a-directory"></a><span data-ttu-id="53dee-109">Pro vytvoření seznamu souborů v adresáři</span><span class="sxs-lookup"><span data-stu-id="53dee-109">To list files in a directory</span></span>  
  
-   <span data-ttu-id="53dee-110">Použijte jednu z <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> přetížení metody poskytnutí název a cesta k adresáři pro hledání v `directory` parametru.</span><span class="sxs-lookup"><span data-stu-id="53dee-110">Use one of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method overloads, supplying the name and path of the directory to search in the `directory` parameter.</span></span> <span data-ttu-id="53dee-111">Následující příklad vrátí všechny soubory v adresáři a přidá je do `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="53dee-111">The following example returns all files in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#32)]  
  
## <a name="robust-programming"></a><span data-ttu-id="53dee-112">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="53dee-112">Robust Programming</span></span>  
 <span data-ttu-id="53dee-113">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="53dee-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="53dee-114">Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje pouze mezeru, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="53dee-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="53dee-115">Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="53dee-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="53dee-116">`directory` neexistuje (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="53dee-116">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="53dee-117">`directory` odkaz na existující soubor (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="53dee-117">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="53dee-118">Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="53dee-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="53dee-119">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="53dee-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="53dee-120">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="53dee-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="53dee-121">Uživatel nemá potřebná oprávnění (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="53dee-121">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53dee-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53dee-122">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>
- [<span data-ttu-id="53dee-123">Postupy: Hledání souborů pomocí specifického vzoru</span><span class="sxs-lookup"><span data-stu-id="53dee-123">How to: Find Files with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
- [<span data-ttu-id="53dee-124">Postupy: Hledání podadresářů pomocí specifického vzoru</span><span class="sxs-lookup"><span data-stu-id="53dee-124">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
