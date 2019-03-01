---
title: 'Postupy: Přesunutí souboru v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], moving
ms.assetid: 53a7457b-5815-41ad-b37d-28537c1fb77a
ms.openlocfilehash: 90f315bc9153fd79f12e3dcbbfe0f238f4090b25
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56976873"
---
# <a name="how-to-move-a-file-in-visual-basic"></a><span data-ttu-id="8bf40-102">Postupy: Přesunutí souboru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8bf40-102">How to: Move a File in Visual Basic</span></span>
<span data-ttu-id="8bf40-103">`My.Computer.FileSystem.MoveFile` Metodu je možné přesunout soubor do jiné složky.</span><span class="sxs-lookup"><span data-stu-id="8bf40-103">The `My.Computer.FileSystem.MoveFile` method can be used to move a file to another folder.</span></span> <span data-ttu-id="8bf40-104">Pokud cílová struktura neexistuje, vytvoří se.</span><span class="sxs-lookup"><span data-stu-id="8bf40-104">If the target structure does not exist, it will be created.</span></span>  
  
### <a name="to-move-a-file"></a><span data-ttu-id="8bf40-105">Chcete-li přesunout soubor</span><span class="sxs-lookup"><span data-stu-id="8bf40-105">To move a file</span></span>  
  
-   <span data-ttu-id="8bf40-106">Použití `MoveFile` metoda se přesunout soubor, zadáním názvu souboru a umístění zdrojového souboru a cílový soubor.</span><span class="sxs-lookup"><span data-stu-id="8bf40-106">Use the `MoveFile` method to move the file, specifying the file name and location for both the source file and the target file.</span></span> <span data-ttu-id="8bf40-107">V tomto příkladu přesune soubor s názvem `test.txt` z `TestDir1` k `TestDir2`.</span><span class="sxs-lookup"><span data-stu-id="8bf40-107">This example moves the file named `test.txt` from `TestDir1` to `TestDir2`.</span></span> <span data-ttu-id="8bf40-108">Všimněte si, že je zadán název cílového souboru, i když je stejný jako název zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="8bf40-108">Note that the target file name is specified even though it is the same as the source file name.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#24)]  
  
### <a name="to-move-a-file-and-rename-it"></a><span data-ttu-id="8bf40-109">Chcete-li přesunout soubor a přejmenujte jej na</span><span class="sxs-lookup"><span data-stu-id="8bf40-109">To move a file and rename it</span></span>  
  
-   <span data-ttu-id="8bf40-110">Použití `MoveFile` metoda se přesunout soubor, zadáte název zdrojového souboru a umístění, cílové umístění a název nového v cílovém umístění.</span><span class="sxs-lookup"><span data-stu-id="8bf40-110">Use the `MoveFile` method to move the file, specifying the source file name and location, the target location, and the new name at the target location.</span></span> <span data-ttu-id="8bf40-111">V tomto příkladu přesune soubor s názvem `test.txt` z `TestDir1` k `TestDir2` a přejmenuje ho `nexttest.txt`.</span><span class="sxs-lookup"><span data-stu-id="8bf40-111">This example moves the file named `test.txt` from `TestDir1` to `TestDir2` and renames it `nexttest.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#25)]  
  
## <a name="robust-programming"></a><span data-ttu-id="8bf40-112">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="8bf40-112">Robust Programming</span></span>  
 <span data-ttu-id="8bf40-113">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="8bf40-113">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="8bf40-114">Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje pouze mezeru, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="8bf40-114">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="8bf40-115">Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="8bf40-115">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="8bf40-116">`destinationFileName` je `Nothing` nebo prázdný řetězec (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="8bf40-116">`destinationFileName` is `Nothing` or an empty string (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="8bf40-117">Zdrojový soubor je neplatný nebo neexistuje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="8bf40-117">The source file is not valid or does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="8bf40-118">Body kombinovanou cestu k existujícímu adresáři, cílový soubor existuje a `overwrite` je nastavena na `False`, soubor v cílovém adresáři se stejným názvem se používá, nebo uživatel nemá dostatečná oprávnění pro přístup k souboru (<xref:System.IO.IOException> ).</span><span class="sxs-lookup"><span data-stu-id="8bf40-118">The combined path points to an existing directory, the destination file exists and `overwrite` is set to `False`, a file in the target directory with the same name is in use, or the user does not have sufficient permissions to access the file (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="8bf40-119">Název souboru nebo adresáře v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="8bf40-119">A file or directory name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="8bf40-120">`showUI` je nastavena na `True`, `onUserCancel` je nastavena na `ThrowException`a buď uživatel zrušil operaci nebo dojde k nespecifikované chybě vstupně-výstupních operací (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="8bf40-120">`showUI` is set to `True`, `onUserCancel` is set to `ThrowException`, and either the user has cancelled the operation or an unspecified I/O error occurs (<xref:System.OperationCanceledException>).</span></span>  
  
-   <span data-ttu-id="8bf40-121">Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="8bf40-121">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="8bf40-122">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="8bf40-122">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="8bf40-123">Uživatel nemá požadovaná oprávnění (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="8bf40-123">The user does not have required permission (<xref:System.UnauthorizedAccessException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8bf40-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8bf40-124">See also</span></span>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.MoveFile%2A>
- [<span data-ttu-id="8bf40-125">Postupy: Přejmenovat soubor</span><span class="sxs-lookup"><span data-stu-id="8bf40-125">How to: Rename a File</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
- [<span data-ttu-id="8bf40-126">Postupy: Vytvoření kopie souboru v jiném adresáři</span><span class="sxs-lookup"><span data-stu-id="8bf40-126">How to: Create a Copy of a File in a Different Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
- [<span data-ttu-id="8bf40-127">Postupy: Analýza cest k souborům</span><span class="sxs-lookup"><span data-stu-id="8bf40-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
