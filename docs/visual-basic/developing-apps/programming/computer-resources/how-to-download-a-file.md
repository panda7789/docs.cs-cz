---
title: 'Postupy: Stažení souboru'
ms.date: 07/20/2015
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
ms.openlocfilehash: a5b379da00656f65476e4d9504457bf8b464beac
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84411652"
---
# <a name="how-to-download-a-file-in-visual-basic"></a><span data-ttu-id="3fe29-102">Postupy: Stažení souboru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3fe29-102">How to: Download a File in Visual Basic</span></span>

<span data-ttu-id="3fe29-103"><xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>Metoda může být použita ke stažení vzdáleného souboru a jeho uložení do konkrétního umístění.</span><span class="sxs-lookup"><span data-stu-id="3fe29-103">The <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> method can be used to download a remote file and store it to a specific location.</span></span> <span data-ttu-id="3fe29-104">Pokud `ShowUI` je parametr nastaven na hodnotu `True` , zobrazí se dialogové okno s informacemi o průběhu stahování a umožňující uživatelům zrušit operaci.</span><span class="sxs-lookup"><span data-stu-id="3fe29-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed showing the progress of the download and allowing users to cancel the operation.</span></span> <span data-ttu-id="3fe29-105">Ve výchozím nastavení nejsou přepsány existující soubory se stejným názvem. Pokud chcete přepsat existující soubory, nastavte `overwrite` parametr na `True` .</span><span class="sxs-lookup"><span data-stu-id="3fe29-105">By default, existing files having the same name are not overwritten; if you want to overwrite existing files, set the `overwrite` parameter to `True`.</span></span>

<span data-ttu-id="3fe29-106">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="3fe29-106">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="3fe29-107">Název jednotky není platný ( <xref:System.ArgumentException> ).</span><span class="sxs-lookup"><span data-stu-id="3fe29-107">Drive name is not valid (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="3fe29-108">Nezbytné ověření nebylo zadáno ( <xref:System.UnauthorizedAccessException> nebo <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="3fe29-108">Necessary authentication has not been supplied (<xref:System.UnauthorizedAccessException> or <xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="3fe29-109">Server nereaguje v rámci zadaného `connectionTimeout` ( <xref:System.TimeoutException> ).</span><span class="sxs-lookup"><span data-stu-id="3fe29-109">The server does not respond within the specified `connectionTimeout` (<xref:System.TimeoutException>).</span></span>

- <span data-ttu-id="3fe29-110">Požadavek byl zamítnut webovým serverem ( <xref:System.Net.WebException> ).</span><span class="sxs-lookup"><span data-stu-id="3fe29-110">The request is denied by the Web site (<xref:System.Net.WebException>).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

> [!IMPORTANT]
> <span data-ttu-id="3fe29-111">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="3fe29-111">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="3fe29-112">Například soubor Form1. vb nemusí být Visual Basic zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="3fe29-112">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="3fe29-113">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="3fe29-113">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="3fe29-114">Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.</span><span class="sxs-lookup"><span data-stu-id="3fe29-114">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>

### <a name="to-download-a-file"></a><span data-ttu-id="3fe29-115">Stažení souboru</span><span class="sxs-lookup"><span data-stu-id="3fe29-115">To download a file</span></span>

- <span data-ttu-id="3fe29-116">Použijte `DownloadFile` metodu ke stažení souboru, určení umístění cílového souboru jako řetězce nebo identifikátoru URI a určení umístění, kam chcete soubor uložit.</span><span class="sxs-lookup"><span data-stu-id="3fe29-116">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file.</span></span> <span data-ttu-id="3fe29-117">Tento příklad stáhne soubor `WineList.txt` z `http://www.cohowinery.com/downloads` a uloží ho do `C:\Documents and Settings\All Users\Documents` :</span><span class="sxs-lookup"><span data-stu-id="3fe29-117">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`:</span></span>

  [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]

### <a name="to-download-a-file-specifying-a-time-out-interval"></a><span data-ttu-id="3fe29-118">Stažení souboru s určením intervalu časového limitu</span><span class="sxs-lookup"><span data-stu-id="3fe29-118">To download a file, specifying a time-out interval</span></span>

- <span data-ttu-id="3fe29-119">Použijte `DownloadFile` metodu ke stažení souboru, určení umístění cílového souboru jako řetězce nebo identifikátoru URI, určení umístění, do kterého se má soubor uložit, a určení intervalu časového limitu v milisekundách (výchozí hodnota je 1000).</span><span class="sxs-lookup"><span data-stu-id="3fe29-119">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI, specifying the location at which to store the file, and specifying the time-out interval in milliseconds (the default is 1000).</span></span> <span data-ttu-id="3fe29-120">Tento příklad stáhne soubor `WineList.txt` z `http://www.cohowinery.com/downloads` a uloží ho do a `C:\Documents and Settings\All Users\Documents` určí časový limit 500 milisekund:</span><span class="sxs-lookup"><span data-stu-id="3fe29-120">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, specifying a time-out interval of 500 milliseconds:</span></span>

  [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]

### <a name="to-download-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="3fe29-121">Stažení souboru a zadání uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="3fe29-121">To download a file, supplying a user name and password</span></span>

- <span data-ttu-id="3fe29-122">Použijte `DownLoadFile` metodu ke stažení souboru, určení umístění cílového souboru jako řetězce nebo identifikátoru URI a určení umístění, kam chcete soubor uložit, uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="3fe29-122">Use the `DownLoadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file, the user name, and the password.</span></span> <span data-ttu-id="3fe29-123">Tento příklad stáhne soubor `WineList.txt` z `http://www.cohowinery.com/downloads` a uloží jej do `C:\Documents and Settings\All Users\Documents` , s uživatelským jménem `anonymous` a prázdným heslem.</span><span class="sxs-lookup"><span data-stu-id="3fe29-123">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, with the user name `anonymous` and a blank password.</span></span>

  [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]

  > [!IMPORTANT]
  > <span data-ttu-id="3fe29-124">Protokol FTP používaný `DownLoadFile` metodou odesílá informace, včetně hesel, do prostého textu a neměl by se používat k přenosu citlivých informací.</span><span class="sxs-lookup"><span data-stu-id="3fe29-124">The FTP protocol used by the `DownLoadFile` method sends information, including passwords, in plain text and should not be used for transmitting sensitive information.</span></span>

## <a name="see-also"></a><span data-ttu-id="3fe29-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="3fe29-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [<span data-ttu-id="3fe29-126">Postupy: Nahrání souboru</span><span class="sxs-lookup"><span data-stu-id="3fe29-126">How to: Upload a File</span></span>](how-to-upload-a-file.md)
- [<span data-ttu-id="3fe29-127">Postupy: Analýza cest k souborům</span><span class="sxs-lookup"><span data-stu-id="3fe29-127">How to: Parse File Paths</span></span>](../drives-directories-files/how-to-parse-file-paths.md)
