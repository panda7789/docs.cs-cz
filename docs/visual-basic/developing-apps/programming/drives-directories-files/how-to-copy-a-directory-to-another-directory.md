---
title: 'Postupy: Zkopírování adresáře do jiného adresáře v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
ms.openlocfilehash: 9b6e095d061619cf9d2e2d87a7247cbdbc51cbe2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588581"
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a><span data-ttu-id="45cad-102">Postupy: Zkopírování adresáře do jiného adresáře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="45cad-102">How to: Copy a Directory to Another Directory in Visual Basic</span></span>
<span data-ttu-id="45cad-103">Použití <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> metodu pro zkopírování adresáře do jiného adresáře.</span><span class="sxs-lookup"><span data-stu-id="45cad-103">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> method to copy a directory to another directory.</span></span> <span data-ttu-id="45cad-104">Tato metoda zkopíruje obsah adresáře, jakož i daný adresář.</span><span class="sxs-lookup"><span data-stu-id="45cad-104">This method copies the contents of the directory as well as the directory itself.</span></span> <span data-ttu-id="45cad-105">Pokud cílový adresář neexistuje, bude vytvořen.</span><span class="sxs-lookup"><span data-stu-id="45cad-105">If the target directory does not exist, it will be created.</span></span> <span data-ttu-id="45cad-106">Pokud adresář se stejným názvem existuje v cílovém umístění a `overwrite` je nastaven na `False`, se sloučí obsah dva adresáře.</span><span class="sxs-lookup"><span data-stu-id="45cad-106">If a directory with the same name exists in the target location and `overwrite` is set to `False`, the contents of the two directories will be merged.</span></span> <span data-ttu-id="45cad-107">Během operace můžete zadat nový název pro adresář.</span><span class="sxs-lookup"><span data-stu-id="45cad-107">You can specify a new name for the directory during the operation.</span></span>  
  
 <span data-ttu-id="45cad-108">Při kopírování souborů v adresáři, můžou být vyvolány výjimky vzniklé v konkrétním souborem, jako je například existující soubor během sloučení při `overwrite` je nastaven na `False`.</span><span class="sxs-lookup"><span data-stu-id="45cad-108">When copying files within a directory, exceptions may be thrown that are caused by specific file, such as a file existing during a merge while `overwrite` is set to `False`.</span></span> <span data-ttu-id="45cad-109">Pokud je vyvolána, jsou spojeny do jednoho výjimky, jejichž `Data` vlastnost obsahuje položky, které cestu soubor nebo adresář je klíč a zprávu výjimky s odpovídající hodnotou.</span><span class="sxs-lookup"><span data-stu-id="45cad-109">When such exceptions are thrown, they are consolidated into a single exception, whose `Data` property holds entries in which the file or directory path is the key and the specific exception message is contained in the corresponding value.</span></span>  
  
### <a name="to-copy-a-directory-to-another-directory"></a><span data-ttu-id="45cad-110">Pro zkopírování adresáře do jiného adresáře</span><span class="sxs-lookup"><span data-stu-id="45cad-110">To copy a directory to another directory</span></span>  
  
-   <span data-ttu-id="45cad-111">Použití `CopyDirectory` metoda, zadání zdrojové a cílové názvy adresářů.</span><span class="sxs-lookup"><span data-stu-id="45cad-111">Use the `CopyDirectory` method, specifying source and destination directory names.</span></span> <span data-ttu-id="45cad-112">Následující příklad zkopíruje adresář s názvem `TestDirectory1` do `TestDirectory2`, přepíše existující soubory.</span><span class="sxs-lookup"><span data-stu-id="45cad-112">The following example copies the directory named `TestDirectory1` into `TestDirectory2`, overwriting existing files.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-a-directory-to-another-directory_1.vb)]  
  
     <span data-ttu-id="45cad-113">Tento příklad kódu je také k dispozici jako IntelliSense fragment kódu.</span><span class="sxs-lookup"><span data-stu-id="45cad-113">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="45cad-114">V Sběrač fragmentů kódu je umístěn v **systému - zpracování jednotek, složek a souborů souborů**.</span><span class="sxs-lookup"><span data-stu-id="45cad-114">In the code snippet picker, it is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="45cad-115">Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="45cad-115">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="45cad-116">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="45cad-116">Robust Programming</span></span>  
 <span data-ttu-id="45cad-117">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="45cad-117">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="45cad-118">Nový název adresáře obsahuje dvojtečku (:) nebo lomítko (\ nebo /) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="45cad-118">The new name specified for the directory contains a colon (:) or slash (\ or /) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="45cad-119">Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje jenom prázdné znaky, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="45cad-119">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="45cad-120">Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="45cad-120">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="45cad-121">`destinationDirectoryName` je `Nothing` nebo prázdný řetězec (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="45cad-121">`destinationDirectoryName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>)</span></span>  
  
-   <span data-ttu-id="45cad-122">Zadaný zdrojový adresář neexistuje (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="45cad-122">The source directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>  
  
-   <span data-ttu-id="45cad-123">Zadaný zdrojový adresář je kořenový adresář (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="45cad-123">The source directory is a root directory (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="45cad-124">Kombinované cesta odkazuje na existující soubor (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="45cad-124">The combined path points to an existing file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="45cad-125">Zdrojová cesta a cílová cesta jsou stejné (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="45cad-125">The source path and target path are the same (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="45cad-126">`ShowUI` je nastavena na `UIOption.AllDialogs` a uživatel zrušil operaci, nebo nelze zkopírovat jeden nebo více souborů v adresáři (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="45cad-126">`ShowUI` is set to `UIOption.AllDialogs` and the user cancels the operation, or one or more files in the directory cannot be copied (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="45cad-127">Operace je cyklická (<xref:System.InvalidOperationException>).</span><span class="sxs-lookup"><span data-stu-id="45cad-127">The operation is cyclic (<xref:System.InvalidOperationException>).</span></span>  
  
-   <span data-ttu-id="45cad-128">Cesta obsahuje dvojtečku (:) (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="45cad-128">The path contains a colon (:) (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="45cad-129">Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="45cad-129">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="45cad-130">Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="45cad-130">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="45cad-131">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="45cad-131">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="45cad-132">Cílový soubor existuje, ale není přístupná (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="45cad-132">A destination file exists but cannot be accessed (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45cad-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="45cad-133">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>  
 [<span data-ttu-id="45cad-134">Postupy: Hledání podadresářů pomocí specifického vzoru</span><span class="sxs-lookup"><span data-stu-id="45cad-134">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)  
 [<span data-ttu-id="45cad-135">Postupy: Získání kolekce souborů z adresáře</span><span class="sxs-lookup"><span data-stu-id="45cad-135">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
