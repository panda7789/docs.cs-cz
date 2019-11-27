---
title: 'Postupy: Odstranění souboru'
ms.date: 07/20/2015
helpviewer_keywords:
- Delete method [Visual Basic]
- files [Visual Basic], deleting
- files [Visual Basic], manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
ms.openlocfilehash: 57182f1a1d92b7fe954fd26b32c5e4b1107823ee
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348784"
---
# <a name="how-to-delete-a-file-in-visual-basic"></a><span data-ttu-id="98f7d-102">Postupy: Odstranění souboru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="98f7d-102">How to: Delete a File in Visual Basic</span></span>

<span data-ttu-id="98f7d-103">Metoda `DeleteFile` objektu `My.Computer.FileSystem` umožňuje odstranit soubor.</span><span class="sxs-lookup"><span data-stu-id="98f7d-103">The `DeleteFile` method of the `My.Computer.FileSystem` object allows you to delete a file.</span></span> <span data-ttu-id="98f7d-104">Mezi možnosti, které nabízí, patří: bez ohledu na to, jestli se má odstraněný soubor poslat do **koše**, jestli se má uživatel položit, aby zkontroloval, jestli by se měl soubor odstranit, a co dělat, když uživatel operaci zruší.</span><span class="sxs-lookup"><span data-stu-id="98f7d-104">Among the options it offers are: whether to send the deleted file to the **Recycle Bin**, whether to ask the user to confirm that the file should be deleted, and what to do when the user cancels the operation.</span></span>  
  
### <a name="to-delete-a-text-file"></a><span data-ttu-id="98f7d-105">Odstranění textového souboru</span><span class="sxs-lookup"><span data-stu-id="98f7d-105">To delete a text file</span></span>  
  
- <span data-ttu-id="98f7d-106">K odstranění souboru použijte metodu `DeleteFile`.</span><span class="sxs-lookup"><span data-stu-id="98f7d-106">Use the `DeleteFile` method to delete the file.</span></span> <span data-ttu-id="98f7d-107">Následující kód ukazuje, jak odstranit soubor s názvem `test.txt`.</span><span class="sxs-lookup"><span data-stu-id="98f7d-107">The following code demonstrates how to delete the file named `test.txt`.</span></span>  
  
     [!code-vb[VbVbcnMyFileSystem#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#22)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a><span data-ttu-id="98f7d-108">Odstranění textového souboru a požádejte uživatele o potvrzení, že by se měl soubor odstranit</span><span class="sxs-lookup"><span data-stu-id="98f7d-108">To delete a text file and ask the user to confirm that the file should be deleted</span></span>  
  
- <span data-ttu-id="98f7d-109">Pomocí metody `DeleteFile` odstraňte soubor a nastavte `showUI` na `AllDialogs`.</span><span class="sxs-lookup"><span data-stu-id="98f7d-109">Use the `DeleteFile` method to delete the file, setting `showUI` to `AllDialogs`.</span></span> <span data-ttu-id="98f7d-110">Následující kód ukazuje, jak odstranit soubor s názvem `test.txt` a umožní uživateli potvrdit, že by měl být soubor smazán.</span><span class="sxs-lookup"><span data-stu-id="98f7d-110">The following code demonstrates how to delete the file named `test.txt` and allow the user to confirm that the file should be deleted.</span></span>  
  
     [!code-vb[VbFileIOMisc#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#9)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a><span data-ttu-id="98f7d-111">Odstranění textového souboru a jeho odeslání do odpadkového koše</span><span class="sxs-lookup"><span data-stu-id="98f7d-111">To delete a text file and send it to the Recycle Bin</span></span>  
  
- <span data-ttu-id="98f7d-112">Použijte metodu `DeleteFile` k odstranění souboru, zadáním `SendToRecycleBin` parametru `recycle`.</span><span class="sxs-lookup"><span data-stu-id="98f7d-112">Use the `DeleteFile` method to delete the file, specifying `SendToRecycleBin` for the `recycle` parameter.</span></span> <span data-ttu-id="98f7d-113">Následující kód ukazuje, jak odstranit soubor s názvem `test.txt` a odeslat ho do **odpadkového**koše.</span><span class="sxs-lookup"><span data-stu-id="98f7d-113">The following code demonstrates how to delete the file named `test.txt` and send it to the **Recycle Bin**.</span></span>  
  
     [!code-vb[VbFileIOMisc#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/Class1.vb#10)]  
  
## <a name="robust-programming"></a><span data-ttu-id="98f7d-114">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="98f7d-114">Robust Programming</span></span>  

 <span data-ttu-id="98f7d-115">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="98f7d-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="98f7d-116">Cesta není platná z některého z následujících důvodů: Jedná se o řetězec o nulové délce, obsahuje pouze prázdné znaky, obsahuje neplatné znaky nebo se jedná o cestu k zařízení (začíná na \\\\.\\) (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="98f7d-116">The path is not valid for one of the following reasons: it is a zero-length string, it contains only white space, it contains invalid characters, or it is a device path (starts with \\\\.\\) (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="98f7d-117">Cesta není platná, protože je `Nothing` (<xref:System.ArgumentNullException>).</span><span class="sxs-lookup"><span data-stu-id="98f7d-117">The path is not valid because it is `Nothing` (<xref:System.ArgumentNullException>).</span></span>  
  
- <span data-ttu-id="98f7d-118">Cesta překračuje maximální povolenou délku systému (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="98f7d-118">The path exceeds the system-defined maximum length (<xref:System.IO.PathTooLongException>).</span></span>  
  
- <span data-ttu-id="98f7d-119">Název souboru nebo složky v cestě obsahuje dvojtečku (:) nebo má neplatný formát (<xref:System.NotSupportedException>).</span><span class="sxs-lookup"><span data-stu-id="98f7d-119">A file or folder name in the path contains a colon (:) or is in an invalid format (<xref:System.NotSupportedException>).</span></span>  
  
- <span data-ttu-id="98f7d-120">Soubor se používá (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="98f7d-120">The file is in use (<xref:System.IO.IOException>).</span></span>  
  
- <span data-ttu-id="98f7d-121">Uživatel nemá potřebná oprávnění k zobrazení cesty (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="98f7d-121">The user lacks necessary permissions to view the path (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="98f7d-122">Soubor neexistuje (<xref:System.IO.FileNotFoundException>).</span><span class="sxs-lookup"><span data-stu-id="98f7d-122">The file does not exist (<xref:System.IO.FileNotFoundException>).</span></span>  
  
- <span data-ttu-id="98f7d-123">Uživatel nemá oprávnění k odstranění tohoto souboru, nebo je soubor jen pro čtení (<xref:System.UnauthorizedAccessException>).</span><span class="sxs-lookup"><span data-stu-id="98f7d-123">The user does not have permission to delete the file, or the file is read-only (<xref:System.UnauthorizedAccessException>).</span></span>  
  
- <span data-ttu-id="98f7d-124">V případě, že uživatel nemá dostatečná oprávnění (<xref:System.Security.SecurityException>), existuje situace s částečným vztahem důvěryhodnosti.</span><span class="sxs-lookup"><span data-stu-id="98f7d-124">A partial-trust situation exists in which the user does not have sufficient permissions (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="98f7d-125">Uživatel operaci zrušil a `onUserCancel` je nastaven na `ThrowException` (<xref:System.OperationCanceledException>).</span><span class="sxs-lookup"><span data-stu-id="98f7d-125">The user cancelled the operation and `onUserCancel` is set to `ThrowException` (<xref:System.OperationCanceledException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98f7d-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98f7d-126">See also</span></span>

- <xref:Microsoft.VisualBasic.FileIO.UICancelOption>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem>
- <xref:Microsoft.VisualBasic.FileIO.UIOption>
- <xref:Microsoft.VisualBasic.FileIO.RecycleOption>
- [<span data-ttu-id="98f7d-127">Postupy: Získání kolekce souborů z adresáře</span><span class="sxs-lookup"><span data-stu-id="98f7d-127">How to: Get the Collection of Files in a Directory</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
