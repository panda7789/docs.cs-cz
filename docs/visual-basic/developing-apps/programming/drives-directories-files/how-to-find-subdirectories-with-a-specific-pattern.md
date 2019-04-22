---
title: 'Postupy: Hledání podadresářů pomocí specifického vzoru v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: 705fa6e40d0e6d18826966e3f10cfd31d9e7a6ff
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58823399"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="9eb2c-102">Postupy: Hledání podadresářů pomocí specifického vzoru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9eb2c-102">How to: Find Subdirectories with a Specific Pattern in Visual Basic</span></span>
<span data-ttu-id="9eb2c-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> Metoda vrátí kolekci jen pro čtení řetězců, které představují názvy cest pro podadresářů v adresáři.</span><span class="sxs-lookup"><span data-stu-id="9eb2c-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> method returns a read-only collection of strings representing the path names for the subdirectories in a directory.</span></span> <span data-ttu-id="9eb2c-104">Můžete použít `wildCards` parametr k určení určitému vzoru.</span><span class="sxs-lookup"><span data-stu-id="9eb2c-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="9eb2c-105">Pokud chcete do hledání zahrnout obsah podadresářů, nastavte `searchType` parametr `SearchOption.SearchAllSubDirectories`.</span><span class="sxs-lookup"><span data-stu-id="9eb2c-105">If you would like to include the contents of subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>  
  
 <span data-ttu-id="9eb2c-106">Prázdná kolekce je vrácena, pokud nejsou nalezeny žádné adresáře odpovídající zadanému vzoru.</span><span class="sxs-lookup"><span data-stu-id="9eb2c-106">An empty collection is returned if no directories matching the specified pattern are found.</span></span>  
  
### <a name="to-find-subdirectories-with-a-specific-pattern"></a><span data-ttu-id="9eb2c-107">K hledání podadresářů pomocí specifického vzoru</span><span class="sxs-lookup"><span data-stu-id="9eb2c-107">To find subdirectories with a specific pattern</span></span>  
  
-   <span data-ttu-id="9eb2c-108">Použití `GetDirectories` metody poskytnutí název a cesta k adresáři, kterou chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="9eb2c-108">Use the `GetDirectories` method, supplying the name and path of the directory you want to search.</span></span> <span data-ttu-id="9eb2c-109">Následující příklad vrátí všechny adresáře do struktury adresářů, které obsahují slovo "Protokoly" v názvu a přidá je do `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="9eb2c-109">The following example returns all the directories in the directory structure that contain the word "Logs" in their name, and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnFileAccess#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnFileAccess/VB/Class1.vb#1)]  
  
## <a name="robust-programming"></a><span data-ttu-id="9eb2c-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="9eb2c-110">Robust Programming</span></span>  
 <span data-ttu-id="9eb2c-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="9eb2c-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="9eb2c-112">Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje pouze mezeru, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="9eb2c-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="9eb2c-113">Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="9eb2c-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="9eb2c-114">Jeden nebo více zadaným zástupných znaků je `Nothing`, prázdný řetězec, nebo obsahuje pouze mezery (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="9eb2c-114">One or more of the specified wildcard characters is `Nothing`, an empty string, or contains only spaces (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="9eb2c-115">`directory` neexistuje (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="9eb2c-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="9eb2c-116">`directory` odkaz na existující soubor (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="9eb2c-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="9eb2c-117">Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="9eb2c-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="9eb2c-118">Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="9eb2c-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="9eb2c-119">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="9eb2c-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="9eb2c-120">Uživatel nemá potřebná oprávnění (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="9eb2c-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eb2c-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9eb2c-121">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [<span data-ttu-id="9eb2c-122">Postupy: Hledání souborů pomocí specifického vzoru</span><span class="sxs-lookup"><span data-stu-id="9eb2c-122">How to: Find Files with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
