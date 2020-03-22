---
title: 'Postupy: Hledání souborů pomocí specifického vzoru'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: 5faaa16615f52714db3de6853786990265716501
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348761"
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="62cf8-102">Postupy: Hledání souborů pomocí specifického vzoru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="62cf8-102">How to: Find Files with a Specific Pattern in Visual Basic</span></span>

<span data-ttu-id="62cf8-103">Metoda <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> vrátí kolekci řetězců jen pro čtení představující názvy cest pro soubory.</span><span class="sxs-lookup"><span data-stu-id="62cf8-103">The <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> method returns a read-only collection of strings representing the path names for the files.</span></span> <span data-ttu-id="62cf8-104">`wildCards` Parametr můžete použít k určení určitého vzoru.</span><span class="sxs-lookup"><span data-stu-id="62cf8-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="62cf8-105">Pokud chcete do hledání zahrnout podadresáře, `searchType` nastavte `SearchOption.SearchAllSubDirectories`parametr na .</span><span class="sxs-lookup"><span data-stu-id="62cf8-105">If you would like to include subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>  
  
 <span data-ttu-id="62cf8-106">Prázdná kolekce je vrácena, pokud jsou nalezeny žádné soubory odpovídající zadanému vzoru.</span><span class="sxs-lookup"><span data-stu-id="62cf8-106">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="62cf8-107">Informace o vrácení seznamu souborů pomocí `DirectoryInfo` třídy `System.IO` oboru názvů <xref:System.IO.DirectoryInfo.GetFiles%2A>naleznete v tématu .</span><span class="sxs-lookup"><span data-stu-id="62cf8-107">For information about returning a file list by using the `DirectoryInfo` class of the `System.IO` namespace, see <xref:System.IO.DirectoryInfo.GetFiles%2A>.</span></span>  
  
### <a name="to-find-files-with-a-specified-pattern"></a><span data-ttu-id="62cf8-108">Hledání souborů se zadaným vzorkem</span><span class="sxs-lookup"><span data-stu-id="62cf8-108">To find files with a specified pattern</span></span>  
  
- <span data-ttu-id="62cf8-109">Použijte `GetFiles` metodu, která zadá název a cestu adresáře, který chcete prohledat, a zadejte vzorek.</span><span class="sxs-lookup"><span data-stu-id="62cf8-109">Use the `GetFiles` method, supplying the name and path of the directory you want to search and specifying the pattern.</span></span> <span data-ttu-id="62cf8-110">Následující příklad vrátí všechny soubory `.dll` s příponou `ListBox1`v adresáři a přidá je do aplikace .</span><span class="sxs-lookup"><span data-stu-id="62cf8-110">The following example returns all files with the extension `.dll` in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbFileIOMisc#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#4)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="62cf8-111">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="62cf8-111">.NET Framework Security</span></span>  

 <span data-ttu-id="62cf8-112">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="62cf8-112">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="62cf8-113">Cesta není platná z jednoho z následujících důvodů: jedná se o řetězec nulové délky, obsahuje pouze prázdné znaky, \\ \\\\obsahuje neplatné znaky nebo se jedná o cestu zařízení (začíná na . ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="62cf8-113">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="62cf8-114">Cesta není platná, protože `Nothing` <xref:System.ArgumentNullException>je ( ).</span><span class="sxs-lookup"><span data-stu-id="62cf8-114">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="62cf8-115">`directory`neexistuje (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="62cf8-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="62cf8-116">`directory`odkazuje na existující<xref:System.IO.IOException>soubor ( ).</span><span class="sxs-lookup"><span data-stu-id="62cf8-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="62cf8-117">Cesta překračuje maximální délku definovanou<xref:System.IO.PathTooLongException>systémem ( ).</span><span class="sxs-lookup"><span data-stu-id="62cf8-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="62cf8-118">Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="62cf8-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="62cf8-119">Uživatel nemá potřebná oprávnění k<xref:System.Security.SecurityException>zobrazení cesty ( ).</span><span class="sxs-lookup"><span data-stu-id="62cf8-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="62cf8-120">Uživatel nemá potřebná<xref:System.UnauthorizedAccessException>oprávnění ( ).</span><span class="sxs-lookup"><span data-stu-id="62cf8-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62cf8-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="62cf8-121">See also</span></span>

- <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>
- [<span data-ttu-id="62cf8-122">Postupy: Hledání podadresářů pomocí specifického vzoru</span><span class="sxs-lookup"><span data-stu-id="62cf8-122">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="62cf8-123">Řešení potíží: Čtení z textových souborů a zápis do nich</span><span class="sxs-lookup"><span data-stu-id="62cf8-123">Troubleshooting: Reading from and Writing to Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
- [<span data-ttu-id="62cf8-124">Postupy: Získání kolekce souborů z adresáře</span><span class="sxs-lookup"><span data-stu-id="62cf8-124">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
