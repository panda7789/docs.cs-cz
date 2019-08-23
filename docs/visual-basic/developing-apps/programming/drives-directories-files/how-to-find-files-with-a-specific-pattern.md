---
title: 'Postupy: Hledání souborů s určitým vzorem v Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: f35222d958f8b02f83c6575d940d24e359c3ae00
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914720"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="447d6-102">Postupy: Hledání souborů s určitým vzorem v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="447d6-102">How to: Find Files with a Specific Pattern in Visual Basic</span></span>
<span data-ttu-id="447d6-103"><xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> Metoda vrátí kolekci řetězců jen pro čtení, které představují názvy cest pro soubory.</span><span class="sxs-lookup"><span data-stu-id="447d6-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="447d6-104">K určení konkrétního `wildCards` vzoru můžete použít parametr.</span><span class="sxs-lookup"><span data-stu-id="447d6-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="447d6-105">Chcete-li do hledání zahrnout podadresáře, nastavte `searchType` parametr na. `SearchOption.SearchAllSubDirectories`</span><span class="sxs-lookup"><span data-stu-id="447d6-105">If you would like to include subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>  
  
 <span data-ttu-id="447d6-106">Pokud se nenajde žádné soubory, které odpovídají zadanému vzoru, vrátí se prázdná kolekce.</span><span class="sxs-lookup"><span data-stu-id="447d6-106">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="447d6-107">Informace o vrácení seznamu souborů pomocí `DirectoryInfo` třídy `System.IO` oboru názvů naleznete v tématu <xref:System.IO.DirectoryInfo.GetFiles%2A>.</span><span class="sxs-lookup"><span data-stu-id="447d6-107">For information about returning a file list by using the `DirectoryInfo` class of the `System.IO` namespace, see <xref:System.IO.DirectoryInfo.GetFiles%2A>.</span></span>  
  
### <a name="to-find-files-with-a-specified-pattern"></a><span data-ttu-id="447d6-108">Vyhledání souborů se zadaným vzorem</span><span class="sxs-lookup"><span data-stu-id="447d6-108">To find files with a specified pattern</span></span>  
  
- <span data-ttu-id="447d6-109">`GetFiles` Použijte metodu, zadejte název a cestu k adresáři, který chcete vyhledat, a určete jeho vzor.</span><span class="sxs-lookup"><span data-stu-id="447d6-109">Use the `GetFiles` method, supplying the name and path of the directory you want to search and specifying the pattern.</span></span> <span data-ttu-id="447d6-110">Následující příklad vrátí všechny soubory s příponou `.dll` v adresáři a přidá je do. `ListBox1`</span><span class="sxs-lookup"><span data-stu-id="447d6-110">The following example returns all files with the extension `.dll` in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="447d6-111">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="447d6-111">.NET Framework Security</span></span>  
 <span data-ttu-id="447d6-112">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="447d6-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="447d6-113">Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná \\ \\na.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="447d6-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="447d6-114">Cesta není platná, protože je `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="447d6-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="447d6-115">`directory`neexistuje (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="447d6-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="447d6-116">`directory`odkazuje na existující soubor (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="447d6-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="447d6-117">Cesta přesahuje maximální povolenou délku (<xref:System.IO.PathTooLongException>) definovanou systémem.</span><span class="sxs-lookup"><span data-stu-id="447d6-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="447d6-118">Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu format<xref:System.NotSupportedException>().</span><span class="sxs-lookup"><span data-stu-id="447d6-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="447d6-119">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="447d6-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="447d6-120">Uživatel nemá potřebná oprávnění (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="447d6-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="447d6-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="447d6-121">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="447d6-122">Postupy: Najde podadresáře s určitým vzorem.</span><span class="sxs-lookup"><span data-stu-id="447d6-122">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="447d6-123">Odstraňování potíží: Čtení z textových souborů a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="447d6-123">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="447d6-124">Postupy: Získání kolekce souborů v adresáři</span><span class="sxs-lookup"><span data-stu-id="447d6-124">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
