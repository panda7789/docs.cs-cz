---
title: 'Postupy: Stažení souboru v Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: 9986a784e73f12698281f17a9d8e022e806504cb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69957831"
---
# <a name="how-to-download-a-file-in-visual-basic"></a><span data-ttu-id="db226-102">Postupy: Stažení souboru v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="db226-102">How to: Download a File in Visual Basic</span></span>
<span data-ttu-id="db226-103"><xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> Metoda může být použita ke stažení vzdáleného souboru a jeho uložení do konkrétního umístění.</span><span class="sxs-lookup"><span data-stu-id="db226-103">The <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> method can be used to download a remote file and store it to a specific location.</span></span> <span data-ttu-id="db226-104">`True`Pokud je `ShowUI` parametr nastaven na hodnotu, zobrazí se dialogové okno s informacemi o průběhu stahování a umožňující uživatelům zrušit operaci.</span><span class="sxs-lookup"><span data-stu-id="db226-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed showing the progress of the download and allowing users to cancel the operation.</span></span> <span data-ttu-id="db226-105">Ve výchozím nastavení nejsou přepsány existující soubory se stejným názvem. Pokud chcete přepsat existující soubory, nastavte `overwrite` parametr na. `True`</span><span class="sxs-lookup"><span data-stu-id="db226-105">By default, existing files having the same name are not overwritten; if you want to overwrite existing files, set the `overwrite` parameter to `True`.</span></span>  
  
 <span data-ttu-id="db226-106">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="db226-106">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="db226-107">Název jednotky není platný (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="db226-107">Drive name is not valid (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="db226-108">Nezbytné ověření nebylo zadáno (<xref:System.UnauthorizedAccessException> nebo <xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="db226-108">Necessary authentication has not been supplied (<xref:System.UnauthorizedAccessException> or <xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="db226-109">Server nereaguje v rámci zadaného `connectionTimeout` (<xref:System.TimeoutException>).</span><span class="sxs-lookup"><span data-stu-id="db226-109">The server does not respond within the specified `connectionTimeout` (<xref:System.TimeoutException>).</span></span>  
  
- <span data-ttu-id="db226-110">Požadavek byl zamítnut webovým serverem (<xref:System.Net.WebException>).</span><span class="sxs-lookup"><span data-stu-id="db226-110">The request is denied by the Web site (<xref:System.Net.WebException>).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
> <span data-ttu-id="db226-111">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="db226-111">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="db226-112">Například soubor Form1. vb nemusí být Visual Basic zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="db226-112">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="db226-113">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="db226-113">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="db226-114">Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.</span><span class="sxs-lookup"><span data-stu-id="db226-114">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
### <a name="to-download-a-file"></a><span data-ttu-id="db226-115">Stažení souboru</span><span class="sxs-lookup"><span data-stu-id="db226-115">To download a file</span></span>  
  
- <span data-ttu-id="db226-116">`DownloadFile` Použijte metodu ke stažení souboru, určení umístění cílového souboru jako řetězce nebo identifikátoru URI a určení umístění, kam chcete soubor uložit.</span><span class="sxs-lookup"><span data-stu-id="db226-116">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file.</span></span> <span data-ttu-id="db226-117">Tento příklad stáhne soubor `WineList.txt` z `http://www.cohowinery.com/downloads` a uloží ho do `C:\Documents and Settings\All Users\Documents`:</span><span class="sxs-lookup"><span data-stu-id="db226-117">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`:</span></span>  
  
     [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a><span data-ttu-id="db226-118">Stažení souboru s určením intervalu časového limitu</span><span class="sxs-lookup"><span data-stu-id="db226-118">To download a file, specifying a time-out interval</span></span>  
  
- <span data-ttu-id="db226-119">`DownloadFile` Použijte metodu ke stažení souboru, určení umístění cílového souboru jako řetězce nebo identifikátoru URI, určení umístění, do kterého se má soubor uložit, a určení intervalu časového limitu v milisekundách (výchozí hodnota je 1000).</span><span class="sxs-lookup"><span data-stu-id="db226-119">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI, specifying the location at which to store the file, and specifying the time-out interval in milliseconds (the default is 1000).</span></span> <span data-ttu-id="db226-120">Tento příklad stáhne soubor `WineList.txt` z `http://www.cohowinery.com/downloads` a uloží ho do `C:\Documents and Settings\All Users\Documents`a určí časový limit 500 milisekund:</span><span class="sxs-lookup"><span data-stu-id="db226-120">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, specifying a time-out interval of 500 milliseconds:</span></span>  
  
     [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="db226-121">Stažení souboru a zadání uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="db226-121">To download a file, supplying a user name and password</span></span>  
  
- <span data-ttu-id="db226-122">`DownLoadFile` Použijte metodu ke stažení souboru, určení umístění cílového souboru jako řetězce nebo identifikátoru URI a určení umístění, kam chcete soubor uložit, uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="db226-122">Use the `DownLoadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file, the user name, and the password.</span></span> <span data-ttu-id="db226-123">Tento příklad stáhne `WineList.txt` soubor z `http://www.cohowinery.com/downloads` a uloží jej do `C:\Documents and Settings\All Users\Documents`, s uživatelským jménem `anonymous` a prázdným heslem.</span><span class="sxs-lookup"><span data-stu-id="db226-123">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, with the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="db226-124">Protokol FTP používaný `DownLoadFile` metodou odesílá informace, včetně hesel, do prostého textu a neměl by se používat k přenosu citlivých informací.</span><span class="sxs-lookup"><span data-stu-id="db226-124">The FTP protocol used by the `DownLoadFile` method sends information, including passwords, in plain text and should not be used for transmitting sensitive information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db226-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db226-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [<span data-ttu-id="db226-126">Postupy: Nahrání souboru</span><span class="sxs-lookup"><span data-stu-id="db226-126">How to: Upload a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)
- [<span data-ttu-id="db226-127">Postupy: Analyzovat cesty k souborům</span><span class="sxs-lookup"><span data-stu-id="db226-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
