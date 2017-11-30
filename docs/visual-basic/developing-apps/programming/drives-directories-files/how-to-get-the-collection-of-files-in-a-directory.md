---
title: "Postupy: Získání kolekce souborů z adresáře v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1c9245ab2593dfed5201640ecf84713582890334
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a><span data-ttu-id="3f27a-102">Postupy: Získání kolekce souborů z adresáře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3f27a-102">How to: Get the Collection of Files in a Directory in Visual Basic</span></span>
<span data-ttu-id="3f27a-103">Přetížení <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> metoda vrátit jen pro čtení kolekce řetězce představující názvy souborů v adresáři:</span><span class="sxs-lookup"><span data-stu-id="3f27a-103">The overloads of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method return a read-only collection of strings representing the names of the files within a directory:</span></span>  
  
-   <span data-ttu-id="3f27a-104">Použití <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> přetížení pro hledání jednoduchého souboru v daném adresáři, bez hledání podadresářů.</span><span class="sxs-lookup"><span data-stu-id="3f27a-104">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> overload for a simple file search in a specified directory, without searching subdirectories.</span></span>  
  
-   <span data-ttu-id="3f27a-105">Použití <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> přetížení k určení dalších možností pro hledání.</span><span class="sxs-lookup"><span data-stu-id="3f27a-105">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> overload to specify additional options for your search.</span></span> <span data-ttu-id="3f27a-106">Můžete použít `wildCards` parametr k určení vzoru hledání.</span><span class="sxs-lookup"><span data-stu-id="3f27a-106">You can use the `wildCards` parameter to specify a search pattern.</span></span> <span data-ttu-id="3f27a-107">Chcete-li do vyhledávání přidat podadresáře, nastavte `searchType` parametru <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="3f27a-107">To include subdirectories in the search, set the `searchType` parameter to <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="3f27a-108">Prázdná kolekce je vrácena, pokud nejsou nalezeny žádné soubory odpovídající zadanému vzoru.</span><span class="sxs-lookup"><span data-stu-id="3f27a-108">An empty collection is returned if no files matching the specified pattern are found.</span></span>  
  
### <a name="to-list-files-in-a-directory"></a><span data-ttu-id="3f27a-109">Pro vytvoření seznamu souborů v adresáři</span><span class="sxs-lookup"><span data-stu-id="3f27a-109">To list files in a directory</span></span>  
  
-   <span data-ttu-id="3f27a-110">Použijte jednu z <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> přetížení metody zadávání název a cestu k adresáři pro hledání v `directory` parametr.</span><span class="sxs-lookup"><span data-stu-id="3f27a-110">Use one of the <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> method overloads, supplying the name and path of the directory to search in the `directory` parameter.</span></span> <span data-ttu-id="3f27a-111">Následující příklad vrátí všechny soubory v adresáři a přidá je do `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="3f27a-111">The following example returns all files in the directory and adds them to `ListBox1`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#32](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-get-the-collection-of-files-in-a-directory_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="3f27a-112">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="3f27a-112">Robust Programming</span></span>  
 <span data-ttu-id="3f27a-113">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="3f27a-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="3f27a-114">Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje jenom prázdné znaky, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="3f27a-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="3f27a-115">Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="3f27a-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="3f27a-116">`directory`neexistuje (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="3f27a-116">`directory` does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="3f27a-117">`directory`ukazuje na existující soubor (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="3f27a-117">`directory` points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="3f27a-118">Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="3f27a-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="3f27a-119">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="3f27a-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="3f27a-120">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="3f27a-120">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="3f27a-121">Uživatel nemá potřebná oprávnění (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="3f27a-121">The user lacks necessary permissions (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f27a-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="3f27a-122">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>  
 [<span data-ttu-id="3f27a-123">Postupy: hledání souborů pomocí specifického vzoru</span><span class="sxs-lookup"><span data-stu-id="3f27a-123">How to: Find Files with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)  
 [<span data-ttu-id="3f27a-124">Postupy: hledání podadresářů pomocí specifického vzoru</span><span class="sxs-lookup"><span data-stu-id="3f27a-124">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
