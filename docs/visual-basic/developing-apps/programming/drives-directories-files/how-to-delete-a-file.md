---
title: 'Postupy: Odstranění souboru v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 2918b756d5f37de2489042a9eabfe7312841af81
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588620"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a><span data-ttu-id="dc44b-102">Postupy: Odstranění souboru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dc44b-102">How to: Delete a File in Visual Basic</span></span>
<span data-ttu-id="dc44b-103">`DeleteFile` Metodu `My.Computer.FileSystem` objekt umožňuje odstranit soubor.</span><span class="sxs-lookup"><span data-stu-id="dc44b-103">The `DeleteFile` method of the `My.Computer.FileSystem` object allows you to delete a file.</span></span> <span data-ttu-id="dc44b-104">Nabízí možnosti jsou: zda odstraněné soubor k **Koš**, zda má být požádat uživatele o potvrzení, že soubor by měl odstranit a co dělat, když uživatel operaci zruší.</span><span class="sxs-lookup"><span data-stu-id="dc44b-104">Among the options it offers are: whether to send the deleted file to the **Recycle Bin**, whether to ask the user to confirm that the file should be deleted, and what to do when the user cancels the operation.</span></span>  
  
### <a name="to-delete-a-text-file"></a><span data-ttu-id="dc44b-105">Chcete-li odstranit textový soubor</span><span class="sxs-lookup"><span data-stu-id="dc44b-105">To delete a text file</span></span>  
  
-   <span data-ttu-id="dc44b-106">Použití `DeleteFile` metoda k odstranění tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="dc44b-106">Use the `DeleteFile` method to delete the file.</span></span> <span data-ttu-id="dc44b-107">Následující kód ukazuje, jak odstranit soubor s názvem `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="dc44b-107">The following code demonstrates how to delete the file named `test.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#22](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_1.vb)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a><span data-ttu-id="dc44b-108">K odstranění textového souboru a požádat uživatele o potvrzení, že by měl odstranit soubor</span><span class="sxs-lookup"><span data-stu-id="dc44b-108">To delete a text file and ask the user to confirm that the file should be deleted</span></span>  
  
-   <span data-ttu-id="dc44b-109">Použití `DeleteFile` metoda k odstranění tohoto souboru, nastavení `showUI` k `AllDialogs`.</span><span class="sxs-lookup"><span data-stu-id="dc44b-109">Use the `DeleteFile` method to delete the file, setting `showUI` to `AllDialogs`.</span></span> <span data-ttu-id="dc44b-110">Následující kód ukazuje, jak odstranit soubor s názvem `test.txt` a povolit uživatele k potvrzení, že soubor měla by být odstraněna.</span><span class="sxs-lookup"><span data-stu-id="dc44b-110">The following code demonstrates how to delete the file named `test.txt` and allow the user to confirm that the file should be deleted.</span></span>  
  
     [!code-vb[VbFileIOMisc#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_2.vb)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a><span data-ttu-id="dc44b-111">K odstranění textového souboru a odeslat do koše</span><span class="sxs-lookup"><span data-stu-id="dc44b-111">To delete a text file and send it to the Recycle Bin</span></span>  
  
-   <span data-ttu-id="dc44b-112">Použití `DeleteFile` metoda k odstranění tohoto souboru zadání `SendToRecycleBin` pro `recycle` parametr.</span><span class="sxs-lookup"><span data-stu-id="dc44b-112">Use the `DeleteFile` method to delete the file, specifying `SendToRecycleBin` for the `recycle` parameter.</span></span> <span data-ttu-id="dc44b-113">Následující kód ukazuje, jak odstranit soubor s názvem `test.txt` a jeho odeslání **Koš**.</span><span class="sxs-lookup"><span data-stu-id="dc44b-113">The following code demonstrates how to delete the file named `test.txt` and send it to the **Recycle Bin**.</span></span>  
  
     [!code-vb[VbFileIOMisc#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_3.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="dc44b-114">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="dc44b-114">Robust Programming</span></span>  
 <span data-ttu-id="dc44b-115">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="dc44b-115">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="dc44b-116">Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje jenom prázdné znaky, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="dc44b-116">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="dc44b-117">Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="dc44b-117">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
-   <span data-ttu-id="dc44b-118">Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="dc44b-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
-   <span data-ttu-id="dc44b-119">Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="dc44b-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
-   <span data-ttu-id="dc44b-120">Soubor je používán (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="dc44b-120">The file is in use (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="dc44b-121">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="dc44b-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="dc44b-122">Soubor neexistuje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="dc44b-122">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
-   <span data-ttu-id="dc44b-123">Uživatel nemá oprávnění k odstranění tohoto souboru nebo souboru je jen pro čtení (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="dc44b-123">The user does not have permission to delete the file, or the file is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
-   <span data-ttu-id="dc44b-124">Částečné důvěryhodnosti situaci existuje, ve kterém uživatel nemá dostatečná oprávnění (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="dc44b-124">A partial-trust situation exists in which the user does not have sufficient permissions (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="dc44b-125">Uživatel zrušil operaci a `onUserCancel` je nastaven na `ThrowException` (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="dc44b-125">The user cancelled the operation and `onUserCancel` is set to `ThrowException` (<xref:System.OperationCanceledException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc44b-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc44b-126">See Also</span></span>  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.UIOption>  
 <xref:Microsoft.VisualBasic.FileIO.RecycleOption>  
 [<span data-ttu-id="dc44b-127">Postupy: Získání kolekce souborů z adresáře</span><span class="sxs-lookup"><span data-stu-id="dc44b-127">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
