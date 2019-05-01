---
title: 'Postupy: Odstranění souboru v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 288c54fa854d753e9b8030463968137b32353b4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62038308"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a><span data-ttu-id="65055-102">Postupy: Odstranění souboru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="65055-102">How to: Delete a File in Visual Basic</span></span>
<span data-ttu-id="65055-103">`DeleteFile` Metodu `My.Computer.FileSystem` objekt umožňuje odstranění souboru.</span><span class="sxs-lookup"><span data-stu-id="65055-103">The `DeleteFile` method of the `My.Computer.FileSystem` object allows you to delete a file.</span></span> <span data-ttu-id="65055-104">Nabízí možnosti jsou:, jestli se má odeslat odstraněný soubor **koše**, zda požádat uživatele o potvrzení, že soubor by měl odstranit a co dělat, když uživatel ruší operaci.</span><span class="sxs-lookup"><span data-stu-id="65055-104">Among the options it offers are: whether to send the deleted file to the **Recycle Bin**, whether to ask the user to confirm that the file should be deleted, and what to do when the user cancels the operation.</span></span>  
  
### <a name="to-delete-a-text-file"></a><span data-ttu-id="65055-105">Chcete-li odstranit textového souboru</span><span class="sxs-lookup"><span data-stu-id="65055-105">To delete a text file</span></span>  
  
- <span data-ttu-id="65055-106">Použití `DeleteFile` metodu pro stejný soubor odstranit také.</span><span class="sxs-lookup"><span data-stu-id="65055-106">Use the `DeleteFile` method to delete the file.</span></span> <span data-ttu-id="65055-107">Následující kód ukazuje, jak odstranit soubor s názvem `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="65055-107">The following code demonstrates how to delete the file named `test.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a><span data-ttu-id="65055-108">Chcete odstranit textového souboru a požádat uživatele, abyste potvrdili, že soubor by se měla odstranit</span><span class="sxs-lookup"><span data-stu-id="65055-108">To delete a text file and ask the user to confirm that the file should be deleted</span></span>  
  
- <span data-ttu-id="65055-109">Použití `DeleteFile` metoda odstranit soubor nastavení `showUI` k `AllDialogs`.</span><span class="sxs-lookup"><span data-stu-id="65055-109">Use the `DeleteFile` method to delete the file, setting `showUI` to `AllDialogs`.</span></span> <span data-ttu-id="65055-110">Následující kód ukazuje, jak odstranit soubor s názvem `test.txt` a umožnit uživateli pro potvrzení, že soubor by měl odstranit.</span><span class="sxs-lookup"><span data-stu-id="65055-110">The following code demonstrates how to delete the file named `test.txt` and allow the user to confirm that the file should be deleted.</span></span>  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a><span data-ttu-id="65055-111">Chcete odstranit textového souboru a odeslat ho do složky Koš</span><span class="sxs-lookup"><span data-stu-id="65055-111">To delete a text file and send it to the Recycle Bin</span></span>  
  
- <span data-ttu-id="65055-112">Použití `DeleteFile` metodu pro odstranění souboru, zadávání `SendToRecycleBin` pro `recycle` parametru.</span><span class="sxs-lookup"><span data-stu-id="65055-112">Use the `DeleteFile` method to delete the file, specifying `SendToRecycleBin` for the `recycle` parameter.</span></span> <span data-ttu-id="65055-113">Následující kód ukazuje, jak odstranit soubor s názvem `test.txt` a odeslat ji **koše**.</span><span class="sxs-lookup"><span data-stu-id="65055-113">The following code demonstrates how to delete the file named `test.txt` and send it to the **Recycle Bin**.</span></span>  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a><span data-ttu-id="65055-114">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="65055-114">Robust Programming</span></span>  
 <span data-ttu-id="65055-115">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="65055-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="65055-116">Cesta není platná pro jednu z následujících důvodů: Jedná se o řetězec nulové délky, obsahuje pouze mezeru, obsahuje neplatné znaky nebo je cesta zařízení (začíná \\ \\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="65055-116">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="65055-117">Cesta není platná, protože se jedná `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="65055-117">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="65055-118">Cesta přesahuje maximální délka definovaná systémem (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="65055-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="65055-119">Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo je v neplatném formátu (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="65055-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="65055-120">Soubor je používán (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="65055-120">The file is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="65055-121">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="65055-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="65055-122">Soubor neexistuje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="65055-122">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="65055-123">Uživatel nemá oprávnění k odstranění souboru nebo souboru je jen pro čtení (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="65055-123">The user does not have permission to delete the file, or the file is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="65055-124">Částečné důvěryhodnosti situace existuje, ve kterém uživatel nemá dostatečná oprávnění (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="65055-124">A partial-trust situation exists in which the user does not have sufficient permissions (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="65055-125">Uživatel zrušil operaci a `onUserCancel` je nastavena na `ThrowException` (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="65055-125">The user cancelled the operation and `onUserCancel` is set to `ThrowException` (<xref:System.OperationCanceledException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65055-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65055-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [<span data-ttu-id="65055-127">Postupy: Získání kolekce souborů v adresáři</span><span class="sxs-lookup"><span data-stu-id="65055-127">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
