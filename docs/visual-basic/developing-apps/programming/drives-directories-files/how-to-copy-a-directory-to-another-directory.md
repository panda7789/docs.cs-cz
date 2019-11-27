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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348866"
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a><span data-ttu-id="5394d-102">Postupy: Zkopírování adresáře do jiného adresáře v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5394d-102">How to: Copy a Directory to Another Directory in Visual Basic</span></span>

<span data-ttu-id="5394d-103">K zkopírování adresáře do jiného adresáře použijte metodu <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>.</span><span class="sxs-lookup"><span data-stu-id="5394d-103">Use the <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> method to copy a directory to another directory.</span></span> <span data-ttu-id="5394d-104">Tato metoda zkopíruje obsah adresáře a také samotný adresář.</span><span class="sxs-lookup"><span data-stu-id="5394d-104">This method copies the contents of the directory as well as the directory itself.</span></span> <span data-ttu-id="5394d-105">Pokud cílový adresář neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="5394d-105">If the target directory does not exist, it will be created.</span></span> <span data-ttu-id="5394d-106">Pokud v cílovém umístění existuje adresář se stejným názvem a `overwrite` je nastavená na `False`, obsah obou adresářů se sloučí.</span><span class="sxs-lookup"><span data-stu-id="5394d-106">If a directory with the same name exists in the target location and `overwrite` is set to `False`, the contents of the two directories will be merged.</span></span> <span data-ttu-id="5394d-107">Během operace můžete zadat nový název adresáře.</span><span class="sxs-lookup"><span data-stu-id="5394d-107">You can specify a new name for the directory during the operation.</span></span>

<span data-ttu-id="5394d-108">Při kopírování souborů v adresáři mohou být vyvolány výjimky, které jsou způsobeny konkrétním souborem, jako je například soubor existující během sloučení, zatímco `overwrite` je nastavena na hodnotu `False`.</span><span class="sxs-lookup"><span data-stu-id="5394d-108">When copying files within a directory, exceptions may be thrown that are caused by specific file, such as a file existing during a merge while `overwrite` is set to `False`.</span></span> <span data-ttu-id="5394d-109">Pokud jsou tyto výjimky vyvolány, jsou konsolidovány do jediné výjimky, jejíž `Data` vlastnost obsahuje položky, ve kterých je soubor nebo cesta adresáře klíč, a specifická zpráva výjimky je obsažena v odpovídající hodnotě.</span><span class="sxs-lookup"><span data-stu-id="5394d-109">When such exceptions are thrown, they are consolidated into a single exception, whose `Data` property holds entries in which the file or directory path is the key and the specific exception message is contained in the corresponding value.</span></span>

## <a name="to-copy-a-directory-to-another-directory"></a><span data-ttu-id="5394d-110">Zkopírování adresáře do jiného adresáře</span><span class="sxs-lookup"><span data-stu-id="5394d-110">To copy a directory to another directory</span></span>

- <span data-ttu-id="5394d-111">Použijte metodu `CopyDirectory` a zadejte názvy zdrojového a cílového adresáře.</span><span class="sxs-lookup"><span data-stu-id="5394d-111">Use the `CopyDirectory` method, specifying source and destination directory names.</span></span> <span data-ttu-id="5394d-112">Následující příklad zkopíruje adresář s názvem `TestDirectory1` do `TestDirectory2`a přepíše stávající soubory.</span><span class="sxs-lookup"><span data-stu-id="5394d-112">The following example copies the directory named `TestDirectory1` into `TestDirectory2`, overwriting existing files.</span></span>

    [!code-vb[VbVbcnMyFileSystem#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#16)]

    <span data-ttu-id="5394d-113">Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="5394d-113">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="5394d-114">Ve výběru fragmentu kódu se nachází v **systému souborů – zpracování jednotek, složek a souborů**.</span><span class="sxs-lookup"><span data-stu-id="5394d-114">In the code snippet picker, it is located in **File system - Processing Drives, Folders, and Files**.</span></span> <span data-ttu-id="5394d-115">Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="5394d-115">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>

## <a name="robust-programming"></a><span data-ttu-id="5394d-116">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="5394d-116">Robust Programming</span></span>

<span data-ttu-id="5394d-117">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="5394d-117">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="5394d-118">Nový název zadaný pro adresář obsahuje dvojtečku (:) nebo lomítko (\ nebo/) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="5394d-118">The new name specified for the directory contains a colon (:) or slash (\ or /) (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="5394d-119">Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="5394d-119">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="5394d-120">Cesta není platná, protože je `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="5394d-120">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>

- <span data-ttu-id="5394d-121">`destinationDirectoryName` je `Nothing` nebo prázdný řetězec (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="5394d-121">`destinationDirectoryName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>)</span></span>

- <span data-ttu-id="5394d-122">Zdrojový adresář neexistuje (<xref:System.IO.DirectoryNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="5394d-122">The source directory does not exist (<xref:System.IO.DirectoryNotFoundException>).</span></span>

- <span data-ttu-id="5394d-123">Zdrojový adresář je kořenový adresář (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="5394d-123">The source directory is a root directory (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="5394d-124">Kombinovaná cesta odkazuje na existující soubor (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="5394d-124">The combined path points to an existing file (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="5394d-125">Cesta ke zdroji a cílová cesta jsou stejné (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="5394d-125">The source path and target path are the same (<xref:System.IO.IOException>).</span></span>

- <span data-ttu-id="5394d-126">`ShowUI` je nastavená na `UIOption.AllDialogs` a uživatel operaci zruší nebo jeden nebo více souborů v adresáři nelze zkopírovat (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="5394d-126">`ShowUI` is set to `UIOption.AllDialogs` and the user cancels the operation, or one or more files in the directory cannot be copied (<xref:System.OperationCanceledException>).</span></span>

- <span data-ttu-id="5394d-127">Operace je cyklická (<xref:System.InvalidOperationException>).</span><span class="sxs-lookup"><span data-stu-id="5394d-127">The operation is cyclic (<xref:System.InvalidOperationException>).</span></span>

- <span data-ttu-id="5394d-128">Cesta obsahuje dvojtečku (:) (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="5394d-128">The path contains a colon (:) (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="5394d-129">Cesta překračuje maximální povolenou délku systému (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="5394d-129">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>

- <span data-ttu-id="5394d-130">Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo má neplatný formát (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="5394d-130">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>

- <span data-ttu-id="5394d-131">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="5394d-131">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="5394d-132">Cílový soubor existuje, ale nelze k němu přistupovat (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="5394d-132">A destination file exists but cannot be accessed (<xref:System.UnauthorizedAccessException>).</span></span>

## <a name="see-also"></a><span data-ttu-id="5394d-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5394d-133">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>
- [<span data-ttu-id="5394d-134">Postupy: Hledání podadresářů pomocí specifického vzoru</span><span class="sxs-lookup"><span data-stu-id="5394d-134">How to: Find Subdirectories with a Specific Pattern</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [<span data-ttu-id="5394d-135">Postupy: Získání kolekce souborů z adresáře</span><span class="sxs-lookup"><span data-stu-id="5394d-135">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
