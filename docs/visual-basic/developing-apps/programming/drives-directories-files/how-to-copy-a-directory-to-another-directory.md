---
title: 'Postupy: Zkopírování adresáře do jiného adresáře'
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
ms.openlocfilehash: a23079f093f53ab8e20eb71c684a594dcf7f894b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348866"
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a><span data-ttu-id="01ce1-102">Postupy: Zkopírování adresáře do jiného adresáře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="01ce1-102">How to: Copy a Directory to Another Directory in Visual Basic</span></span>

<span data-ttu-id="01ce1-103">K zkopírování adresáře do jiného adresáře použijte <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="01ce1-103">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> method to copy a directory to another directory.</span></span> <span data-ttu-id="01ce1-104">Tato metoda zkopíruje obsah adresáře a také samotný adresář.</span><span class="sxs-lookup"><span data-stu-id="01ce1-104">This method copies the contents of the directory as well as the directory itself.</span></span> <span data-ttu-id="01ce1-105">Pokud cílový adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="01ce1-105">If the target directory does not exist, it will be created.</span></span> <span data-ttu-id="01ce1-106">Pokud v cílovém umístění existuje adresář se stejným názvem a `overwrite` je nastaven na `False`hodnotu, obsah obou adresářů bude sloučen.</span><span class="sxs-lookup"><span data-stu-id="01ce1-106">If a directory with the same name exists in the target location and `overwrite` is set to `False`, the contents of the two directories will be merged.</span></span> <span data-ttu-id="01ce1-107">Během operace můžete zadat nový název adresáře.</span><span class="sxs-lookup"><span data-stu-id="01ce1-107">You can specify a new name for the directory during the operation.</span></span>

<span data-ttu-id="01ce1-108">Při kopírování souborů v adresáři mohou být vyvolány výjimky, které jsou způsobeny konkrétním souborem, jako je například soubor existující během sloučení, `overwrite` zatímco je nastavena `False`na.</span><span class="sxs-lookup"><span data-stu-id="01ce1-108">When copying files within a directory, exceptions may be thrown that are caused by specific file, such as a file existing during a merge while `overwrite` is set to `False`.</span></span> <span data-ttu-id="01ce1-109">Pokud jsou tyto výjimky vyvolány, jsou konsolidovány do jediné výjimky, `Data` jejíž vlastnost obsahuje položky, ve kterých je soubor nebo cesta k adresáři klíč a specifická zpráva výjimky je obsažena v odpovídající hodnotě.</span><span class="sxs-lookup"><span data-stu-id="01ce1-109">When such exceptions are thrown, they are consolidated into a single exception, whose `Data` property holds entries in which the file or directory path is the key and the specific exception message is contained in the corresponding value.</span></span>

## <a name="to-copy-a-directory-to-another-directory"></a><span data-ttu-id="01ce1-110">Zkopírování adresáře do jiného adresáře</span><span class="sxs-lookup"><span data-stu-id="01ce1-110">To copy a directory to another directory</span></span>

- <span data-ttu-id="01ce1-111">Použijte metodu `CopyDirectory` , která určuje název zdrojového a cílového adresáře.</span><span class="sxs-lookup"><span data-stu-id="01ce1-111">Use the `CopyDirectory` method, specifying source and destination directory names.</span></span> <span data-ttu-id="01ce1-112">Následující příklad zkopíruje adresář s názvem `TestDirectory1` do `TestDirectory2`a přepíše stávající soubory.</span><span class="sxs-lookup"><span data-stu-id="01ce1-112">The following example copies the directory named `TestDirectory1` into `TestDirectory2`, overwriting existing files.</span></span>

    [!code-vb[VbVbcnMyFileSystem#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#16)]

    <span data-ttu-id="01ce1-113">Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="01ce1-113">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="01ce1-114">Ve výběru fragmentu kódu se nachází v **systému souborů – zpracování jednotek, složek a souborů**.</span><span class="sxs-lookup"><span data-stu-id="01ce1-114">In the code snippet picker, it is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="01ce1-115">Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="01ce1-115">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>

## <a name="robust-programming"></a><span data-ttu-id="01ce1-116">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="01ce1-116">Robust Programming</span></span>

<span data-ttu-id="01ce1-117">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="01ce1-117">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="01ce1-118">Nový název zadaný pro adresář obsahuje dvojtečku (:) nebo lomítko (\ nebo/)<xref:System.ArgumentException>().</span><span class="sxs-lookup"><span data-stu-id="01ce1-118">The new name specified for the directory contains a colon (:) or slash (\ or /) (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="01ce1-119">Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná \\ \\na.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="01ce1-119">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="01ce1-120">Cesta není platná, protože je `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="01ce1-120">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="01ce1-121">`destinationDirectoryName`je `Nothing` nebo prázdný řetězec (<xref:System.ArgumentNullException>)</span><span class="sxs-lookup"><span data-stu-id="01ce1-121">`destinationDirectoryName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>)</span></span>

- <span data-ttu-id="01ce1-122">Zdrojový adresář neexistuje (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="01ce1-122">The source directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="01ce1-123">Zdrojový adresář je kořenový adresář (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="01ce1-123">The source directory is a root directory (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="01ce1-124">Kombinovaná cesta odkazuje na existující soubor (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="01ce1-124">The combined path points to an existing file (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="01ce1-125">Cesta ke zdroji a cílová cesta jsou stejné (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="01ce1-125">The source path and target path are the same (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="01ce1-126">`ShowUI`je nastaven na `UIOption.AllDialogs` hodnotu a uživatel operaci zruší nebo jeden či více souborů v adresáři nelze zkopírovat (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="01ce1-126">`ShowUI` is set to `UIOption.AllDialogs` and the user cancels the operation, or one or more files in the directory cannot be copied (<xref:System.OperationCanceledException>).</span></span>

- <span data-ttu-id="01ce1-127">Operace je cyklická (<xref:System.InvalidOperationException>).</span><span class="sxs-lookup"><span data-stu-id="01ce1-127">The operation is cyclic (<xref:System.InvalidOperationException>).</span></span>

- <span data-ttu-id="01ce1-128">Cesta obsahuje dvojtečku (:) (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="01ce1-128">The path contains a colon (:) (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="01ce1-129">Cesta přesahuje maximální povolenou délku (<xref:System.IO.PathTooLongException>) definovanou systémem.</span><span class="sxs-lookup"><span data-stu-id="01ce1-129">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="01ce1-130">Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo má neplatnou hodnotu format<xref:System.NotSupportedException>().</span><span class="sxs-lookup"><span data-stu-id="01ce1-130">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="01ce1-131">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="01ce1-131">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="01ce1-132">Cílový soubor existuje, ale nelze k němu přistupovat (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="01ce1-132">A destination file exists but cannot be accessed (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="01ce1-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="01ce1-133">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>
- [<span data-ttu-id="01ce1-134">Postupy: Hledání podadresářů pomocí specifického vzoru</span><span class="sxs-lookup"><span data-stu-id="01ce1-134">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="01ce1-135">Postupy: Získání kolekce souborů z adresáře</span><span class="sxs-lookup"><span data-stu-id="01ce1-135">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
