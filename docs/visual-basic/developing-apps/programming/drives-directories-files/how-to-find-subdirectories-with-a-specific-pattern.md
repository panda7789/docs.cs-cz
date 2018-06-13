---
title: 'Postupy: Hledání podadresářů pomocí specifického vzoru v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: b3c80fccea06a48c78f37dc7d1c8dcc88e143de4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586435"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a><span data-ttu-id="beb1b-102">Postupy: Hledání podadresářů pomocí specifického vzoru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="beb1b-102">How to: Find Subdirectories with a Specific Pattern in Visual Basic</span></span>
<span data-ttu-id="beb1b-103"><xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> Metoda vrátí kolekci jen pro čtení řetězce představující názvy cest pro podadresáře v adresáři.</span><span class="sxs-lookup"><span data-stu-id="beb1b-103">The <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> method returns a read-only collection of strings representing the path names for the subdirectories in a directory.</span></span> <span data-ttu-id="beb1b-104">Můžete použít `wildCards` parametr k určení specifického vzoru.</span><span class="sxs-lookup"><span data-stu-id="beb1b-104">You can use the `wildCards` parameter to specify a specific pattern.</span></span> <span data-ttu-id="beb1b-105">Pokud chcete zahrnout obsah podadresářů hledání, nastavte `searchType` parametru `SearchOption.SearchAllSubDirectories`.</span><span class="sxs-lookup"><span data-stu-id="beb1b-105">If you would like to include the contents of subdirectories in the search, set the `searchType` parameter to `SearchOption.SearchAllSubDirectories`.</span></span>  
  
 <span data-ttu-id="beb1b-106">Prázdná kolekce je vrácena, pokud se nenajdou žádné adresáře odpovídající zadanému vzoru.</span><span class="sxs-lookup"><span data-stu-id="beb1b-106">An empty collection is returned if no directories matching the specified pattern are found.</span></span>  
  
### <a name="to-find-subdirectories-with-a-specific-pattern"></a><span data-ttu-id="beb1b-107">K hledání podadresářů pomocí specifického vzoru</span><span class="sxs-lookup"><span data-stu-id="beb1b-107">To find subdirectories with a specific pattern</span></span>  
  
-   <span data-ttu-id="beb1b-108">Použití `GetDirectories` metodu název a cestu k adresáři, kterou chcete vyhledat.</span><span class="sxs-lookup"><span data-stu-id="beb1b-108">Use the `GetDirectories` method, supplying the name and path of the directory you want to search.</span></span> <span data-ttu-id="beb1b-109">Následující příklad vrátí všechny adresáře struktury adresářů, obsahující slovo "Protokoly" v názvu a přidá je do `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="beb1b-109">The following example returns all the directories in the directory structure that contain the word "Logs" in their name, and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnFileAccess#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-find-subdirectories-with-a-specific-pattern_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="beb1b-110">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="beb1b-110">Robust Programming</span></span>  
 <span data-ttu-id="beb1b-111">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="beb1b-111">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="beb1b-112">Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje jenom prázdné znaky, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="beb1b-112">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="beb1b-113">Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="beb1b-113">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="beb1b-114">Jeden nebo více zadaný zástupné znaky je `Nothing`, prázdný řetězec, nebo obsahuje pouze mezery (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="beb1b-114">One or more of the specified wildcard characters is `Nothing`, an empty string, or contains only spaces (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="beb1b-115">`directory` neexistuje (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="beb1b-115">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="beb1b-116">`directory` ukazuje na existující soubor (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="beb1b-116">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="beb1b-117">Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="beb1b-117">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="beb1b-118">Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="beb1b-118">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="beb1b-119">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="beb1b-119">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="beb1b-120">Uživatel nemá potřebná oprávnění (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="beb1b-120">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beb1b-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="beb1b-121">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>  
 [<span data-ttu-id="beb1b-122">Postupy: Hledání souborů pomocí specifického vzoru</span><span class="sxs-lookup"><span data-stu-id="beb1b-122">How to: Find Files with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
