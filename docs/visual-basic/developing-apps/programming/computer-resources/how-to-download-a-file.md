---
title: "Postupy: Stažení souboru v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- downloading Internet resources [Visual Basic], files
- downloading files [Visual Basic]
- remote computers [Visual Basic], downloading from
- files [Visual Basic], downloading
- files [Visual Basic], transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: dc67d28b870f86c6464e86f7682f71e6e36ea9e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-download-a-file-in-visual-basic"></a><span data-ttu-id="45be0-102">Postupy: Stažení souboru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="45be0-102">How to: Download a File in Visual Basic</span></span>
<span data-ttu-id="45be0-103"><xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> Metoda slouží k stažení vzdáleného souboru a uložte ho do určitého umístění.</span><span class="sxs-lookup"><span data-stu-id="45be0-103">The <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> method can be used to download a remote file and store it to a specific location.</span></span> <span data-ttu-id="45be0-104">Pokud `ShowUI` parametr je nastaven na `True`, zobrazí se dialogové okno zobrazující průběh stahování a umožníte uživatelům na tlačítko Storno.</span><span class="sxs-lookup"><span data-stu-id="45be0-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed showing the progress of the download and allowing users to cancel the operation.</span></span> <span data-ttu-id="45be0-105">Ve výchozím nastavení nepřepisují existující soubory se stejným názvem; Pokud chcete přepsat existující soubory, nastavte `overwrite` parametru `True`.</span><span class="sxs-lookup"><span data-stu-id="45be0-105">By default, existing files having the same name are not overwritten; if you want to overwrite existing files, set the `overwrite` parameter to `True`.</span></span>  
  
 <span data-ttu-id="45be0-106">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="45be0-106">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="45be0-107">Název jednotky je neplatný (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="45be0-107">Drive name is not valid (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="45be0-108">Nebyl zadán nezbytné ověřování (<xref:System.UnauthorizedAccessException> nebo <xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="45be0-108">Necessary authentication has not been supplied (<xref:System.UnauthorizedAccessException> or <xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="45be0-109">Server neodpověděl v rámci zadaného `connectionTimeout` (<xref:System.TimeoutException>).</span><span class="sxs-lookup"><span data-stu-id="45be0-109">The server does not respond within the specified `connectionTimeout` (<xref:System.TimeoutException>).</span></span>  
  
-   <span data-ttu-id="45be0-110">Požadavek se odmítne webovým serverem (<xref:System.Net.WebException>).</span><span class="sxs-lookup"><span data-stu-id="45be0-110">The request is denied by the Web site (<xref:System.Net.WebException>).</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
>  <span data-ttu-id="45be0-111">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="45be0-111">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="45be0-112">Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="45be0-112">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="45be0-113">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="45be0-113">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="45be0-114">Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.</span><span class="sxs-lookup"><span data-stu-id="45be0-114">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>  
  
### <a name="to-download-a-file"></a><span data-ttu-id="45be0-115">Ke stažení souboru</span><span class="sxs-lookup"><span data-stu-id="45be0-115">To download a file</span></span>  
  
-   <span data-ttu-id="45be0-116">Použití `DownloadFile` metoda stažení souboru, zadáním umístění cílového souboru jako řetězec nebo identifikátor URI a určením umístění, kam chcete soubor uložit.</span><span class="sxs-lookup"><span data-stu-id="45be0-116">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file.</span></span> <span data-ttu-id="45be0-117">Tento příklad stáhne soubor `WineList.txt` z `http://www.cohowinery.com/downloads` a ukládá ji do `C:\Documents and Settings\All Users\Documents`:</span><span class="sxs-lookup"><span data-stu-id="45be0-117">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`:</span></span>  
  
     [!code-vb[VbResourceTasks#9](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_1.vb)]  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a><span data-ttu-id="45be0-118">Ke stažení souboru, zadání interval časového limitu</span><span class="sxs-lookup"><span data-stu-id="45be0-118">To download a file, specifying a time-out interval</span></span>  
  
-   <span data-ttu-id="45be0-119">Použití `DownloadFile` metoda stažení souboru, zadáním umístění cílového souboru jako řetězec nebo identifikátor URI, zadáte umístění, kam chcete uložit soubor a určením časového limitu v milisekundách (výchozí hodnota je 1000).</span><span class="sxs-lookup"><span data-stu-id="45be0-119">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI, specifying the location at which to store the file, and specifying the time-out interval in milliseconds (the default is 1000).</span></span> <span data-ttu-id="45be0-120">Tento příklad stáhne soubor `WineList.txt` z `http://www.cohowinery.com/downloads` a ukládá ji do `C:\Documents and Settings\All Users\Documents`, zadání interval časového limitu na 500 milisekund:</span><span class="sxs-lookup"><span data-stu-id="45be0-120">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, specifying a time-out interval of 500 milliseconds:</span></span>  
  
     [!code-vb[VbResourceTasks#10](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_2.vb)]  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="45be0-121">Ke stažení souboru, poskytnutí uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="45be0-121">To download a file, supplying a user name and password</span></span>  
  
-   <span data-ttu-id="45be0-122">Použití `DownLoadFile` metoda stažení souboru, zadáním umístění cílového souboru jako řetězec nebo identifikátor URI a zadáte umístění, kam chcete uložit soubor, uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="45be0-122">Use the `DownLoadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file, the user name, and the password.</span></span> <span data-ttu-id="45be0-123">Tento příklad stáhne soubor `WineList.txt` z `http://www.cohowinery.com/downloads` a ukládá ji do `C:\Documents and Settings\All Users\Documents`, s uživatelským jménem `anonymous` a prázdné heslo.</span><span class="sxs-lookup"><span data-stu-id="45be0-123">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, with the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_3.vb)]  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="45be0-124">Protokol FTP používá `DownLoadFile` metoda odesílá informace, včetně hesel ve formátu prostého textu a neměl by se používat k přenosu citlivých informací.</span><span class="sxs-lookup"><span data-stu-id="45be0-124">The FTP protocol used by the `DownLoadFile` method sends information, including passwords, in plain text and should not be used for transmitting sensitive information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45be0-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="45be0-125">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Network>  
 <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>  
 [<span data-ttu-id="45be0-126">Postupy: odeslání souboru</span><span class="sxs-lookup"><span data-stu-id="45be0-126">How to: Upload a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)  
 [<span data-ttu-id="45be0-127">Postupy: Analýza cest k souborům</span><span class="sxs-lookup"><span data-stu-id="45be0-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
