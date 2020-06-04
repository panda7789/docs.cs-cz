---
title: 'Postupy: Hledání souborů pomocí specifického vzoru'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: 71073672ed14cb2d5df5b5365266b718c59cb18f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401638"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="90e2b-102">Postupy: Hledání souborů pomocí specifického vzoru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="90e2b-102">How to: Find Files with a Specific Pattern in Visual Basic</span></span>

<span data-ttu-id="90e2b-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>Metoda vrátí kolekci řetězců jen pro čtení, které představují názvy cest pro soubory.</span><span class="sxs-lookup"><span data-stu-id="90e2b-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="90e2b-104">`wildCards`K určení konkrétního vzoru můžete použít parametr.</span><span class="sxs-lookup"><span data-stu-id="90e2b-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="90e2b-105">Chcete-li do hledání zahrnout podadresáře, nastavte `searchType` parametr na `SearchOption.SearchAllSubDirectories` .</span><span class="sxs-lookup"><span data-stu-id="90e2b-105">If you would like to include subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>  
  
 <span data-ttu-id="90e2b-106">Pokud se nenajde žádné soubory, které odpovídají zadanému vzoru, vrátí se prázdná kolekce.</span><span class="sxs-lookup"><span data-stu-id="90e2b-106">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90e2b-107">Informace o vrácení seznamu souborů pomocí `DirectoryInfo` třídy `System.IO` oboru názvů naleznete v tématu <xref:System.IO.DirectoryInfo.GetFiles%2A> .</span><span class="sxs-lookup"><span data-stu-id="90e2b-107">For information about returning a file list by using the `DirectoryInfo` class of the `System.IO` namespace, see <xref:System.IO.DirectoryInfo.GetFiles%2A>.</span></span>  
  
### <a name="to-find-files-with-a-specified-pattern"></a><span data-ttu-id="90e2b-108">Vyhledání souborů se zadaným vzorem</span><span class="sxs-lookup"><span data-stu-id="90e2b-108">To find files with a specified pattern</span></span>  
  
- <span data-ttu-id="90e2b-109">Použijte `GetFiles` metodu, zadejte název a cestu k adresáři, který chcete vyhledat, a určete jeho vzor.</span><span class="sxs-lookup"><span data-stu-id="90e2b-109">Use the `GetFiles` method, supplying the name and path of the directory you want to search and specifying the pattern.</span></span> <span data-ttu-id="90e2b-110">Následující příklad vrátí všechny soubory s příponou `.dll` v adresáři a přidá je do `ListBox1` .</span><span class="sxs-lookup"><span data-stu-id="90e2b-110">The following example returns all files with the extension `.dll` in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="90e2b-111">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="90e2b-111">.NET Framework Security</span></span>  

 <span data-ttu-id="90e2b-112">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="90e2b-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="90e2b-113">Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\ \\ . \\ ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="90e2b-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="90e2b-114">Cesta není platná, protože je `Nothing` ( <xref:System.ArgumentNullException> ).</span><span class="sxs-lookup"><span data-stu-id="90e2b-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="90e2b-115">`directory`neexistuje ( <xref:System.IO.DirectoryNotFoundException> ).</span><span class="sxs-lookup"><span data-stu-id="90e2b-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="90e2b-116">`directory`odkazuje na existující soubor ( <xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="90e2b-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="90e2b-117">Cesta přesahuje maximální povolenou délku () definovanou systémem <xref:System.IO.PathTooLongException> .</span><span class="sxs-lookup"><span data-stu-id="90e2b-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="90e2b-118">Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu Format ( <xref:System.NotSupportedException> ).</span><span class="sxs-lookup"><span data-stu-id="90e2b-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="90e2b-119">Uživatel nemá potřebná oprávnění k zobrazení cesty ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="90e2b-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="90e2b-120">Uživatel nemá potřebná oprávnění ( <xref:System.UnauthorizedAccessException> ).</span><span class="sxs-lookup"><span data-stu-id="90e2b-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90e2b-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="90e2b-121">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="90e2b-122">Postupy: Hledání podadresářů pomocí specifického vzoru</span><span class="sxs-lookup"><span data-stu-id="90e2b-122">How to: Find Subdirectories with a Specific Pattern</span></span>](how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="90e2b-123">Řešení potíží: Čtení z textových souborů a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="90e2b-123">Troubleshooting: Reading from and Writing to Text Files</span></span>](troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="90e2b-124">Postupy: Získání kolekce souborů z adresáře</span><span class="sxs-lookup"><span data-stu-id="90e2b-124">How to: Get the Collection of Files in a Directory</span></span>](how-to-get-the-collection-of-files-in-a-directory.md)
