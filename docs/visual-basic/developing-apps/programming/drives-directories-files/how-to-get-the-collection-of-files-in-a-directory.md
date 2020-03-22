---
title: 'Postupy: Získání kolekce souborů z adresáře'
ms.date: 07/20/2015
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
ms.openlocfilehash: bb07ae25b413334f94456b378f0a2339402ac668
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74335340"
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a><span data-ttu-id="00985-102">Postupy: Získání kolekce souborů z adresáře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="00985-102">How to: Get the Collection of Files in a Directory in Visual Basic</span></span>

<span data-ttu-id="00985-103">Přetížení <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> metody vrátí kolekci řetězců jen pro čtení představující názvy souborů v adresáři:</span><span class="sxs-lookup"><span data-stu-id="00985-103">The overloads of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method return a read-only collection of strings representing the names of the files within a directory:</span></span>  
  
- <span data-ttu-id="00985-104">Přetížení <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> použijte pro jednoduché hledání souborů v zadaném adresáři bez vyhledávání podadresářů.</span><span class="sxs-lookup"><span data-stu-id="00985-104">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> overload for a simple file search in a specified directory, without searching subdirectories.</span></span>  
  
- <span data-ttu-id="00985-105">Pomocí <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> přetížení zadejte další možnosti pro hledání.</span><span class="sxs-lookup"><span data-stu-id="00985-105">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> overload to specify additional options for your search.</span></span> <span data-ttu-id="00985-106">`wildCards` Parametr můžete použít k určení vyhledávacího vzoru.</span><span class="sxs-lookup"><span data-stu-id="00985-106">You can use the `wildCards` parameter to specify a search pattern.</span></span> <span data-ttu-id="00985-107">Chcete-li do hledání zahrnout podadresáře, nastavte `searchType` parametr na <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="00985-107">To include subdirectories in the search, set the `searchType` parameter to <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="00985-108">Prázdná kolekce je vrácena, pokud jsou nalezeny žádné soubory odpovídající zadanému vzoru.</span><span class="sxs-lookup"><span data-stu-id="00985-108">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
### <a name="to-list-files-in-a-directory"></a><span data-ttu-id="00985-109">Seznam souborů v adresáři</span><span class="sxs-lookup"><span data-stu-id="00985-109">To list files in a directory</span></span>  
  
- <span data-ttu-id="00985-110">Použijte jednu <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> z přetížení metody a zadejte název a cestu `directory` k hledání v parametru.</span><span class="sxs-lookup"><span data-stu-id="00985-110">Use one of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method overloads, supplying the name and path of the directory to search in the `directory` parameter.</span></span> <span data-ttu-id="00985-111">Následující příklad vrátí všechny soubory v adresáři a přidá je do aplikace `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="00985-111">The following example returns all files in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#32)]  
  
## <a name="robust-programming"></a><span data-ttu-id="00985-112">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="00985-112">Robust Programming</span></span>  

 <span data-ttu-id="00985-113">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="00985-113">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="00985-114">Cesta není platná z jednoho z následujících důvodů: jedná se o řetězec nulové délky, obsahuje pouze prázdné znaky, \\ \\\\obsahuje neplatné znaky nebo se jedná o cestu zařízení (začíná na . ) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="00985-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="00985-115">Cesta není platná, protože `Nothing` <xref:System.ArgumentNullException>je ( ).</span><span class="sxs-lookup"><span data-stu-id="00985-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="00985-116">`directory`neexistuje (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="00985-116">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
- <span data-ttu-id="00985-117">`directory`odkazuje na existující<xref:System.IO.IOException>soubor ( ).</span><span class="sxs-lookup"><span data-stu-id="00985-117">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="00985-118">Cesta překračuje maximální délku definovanou<xref:System.IO.PathTooLongException>systémem ( ).</span><span class="sxs-lookup"><span data-stu-id="00985-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="00985-119">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="00985-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="00985-120">Uživatel nemá potřebná oprávnění k<xref:System.Security.SecurityException>zobrazení cesty ( ).</span><span class="sxs-lookup"><span data-stu-id="00985-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="00985-121">Uživatel nemá potřebná<xref:System.UnauthorizedAccessException>oprávnění ( ).</span><span class="sxs-lookup"><span data-stu-id="00985-121">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00985-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="00985-122">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>
- [<span data-ttu-id="00985-123">Postupy: Hledání souborů pomocí specifického vzoru</span><span class="sxs-lookup"><span data-stu-id="00985-123">How to: Find Files with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
- [<span data-ttu-id="00985-124">Postupy: Hledání podadresářů pomocí specifického vzoru</span><span class="sxs-lookup"><span data-stu-id="00985-124">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
