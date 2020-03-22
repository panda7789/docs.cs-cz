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
ms.openlocfilehash: 4923feb46ff638de9514a4d70fc00367491a6f44
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345625"
---
# <a name="how-to-download-a-file-in-visual-basic"></a><span data-ttu-id="24573-102">Postupy: Stažení souboru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24573-102">How to: Download a File in Visual Basic</span></span>

<span data-ttu-id="24573-103">Metodu <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> lze použít ke stažení vzdáleného souboru a jeho uložení do určitého umístění.</span><span class="sxs-lookup"><span data-stu-id="24573-103">The <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> method can be used to download a remote file and store it to a specific location.</span></span> <span data-ttu-id="24573-104">Pokud `ShowUI` je parametr `True`nastaven na , zobrazí se dialogové okno, které ukazuje průběh stahování a umožňuje uživatelům operaci zrušit.</span><span class="sxs-lookup"><span data-stu-id="24573-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed showing the progress of the download and allowing users to cancel the operation.</span></span> <span data-ttu-id="24573-105">Ve výchozím nastavení nejsou existující soubory se stejným názvem přepsány. Pokud chcete přepsat existující soubory, `overwrite` nastavte `True`parametr na .</span><span class="sxs-lookup"><span data-stu-id="24573-105">By default, existing files having the same name are not overwritten; if you want to overwrite existing files, set the `overwrite` parameter to `True`.</span></span>

<span data-ttu-id="24573-106">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="24573-106">The following conditions may cause an exception:</span></span>

- <span data-ttu-id="24573-107">Název jednotky není<xref:System.ArgumentException>platný ( ).</span><span class="sxs-lookup"><span data-stu-id="24573-107">Drive name is not valid (<xref:System.ArgumentException>).</span></span>

- <span data-ttu-id="24573-108">Nebylo zadáno nezbytné<xref:System.UnauthorizedAccessException> ověření <xref:System.Security.SecurityException>( nebo ).</span><span class="sxs-lookup"><span data-stu-id="24573-108">Necessary authentication has not been supplied (<xref:System.UnauthorizedAccessException> or <xref:System.Security.SecurityException>).</span></span>

- <span data-ttu-id="24573-109">Server nereaguje v rámci `connectionTimeout` <xref:System.TimeoutException>zadaného ( ).</span><span class="sxs-lookup"><span data-stu-id="24573-109">The server does not respond within the specified `connectionTimeout` (<xref:System.TimeoutException>).</span></span>

- <span data-ttu-id="24573-110">Požadavek je webem zamítnut<xref:System.Net.WebException>( ).</span><span class="sxs-lookup"><span data-stu-id="24573-110">The request is denied by the Web site (<xref:System.Net.WebException>).</span></span>

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

> [!IMPORTANT]
> <span data-ttu-id="24573-111">Nečiňte rozhodnutí o obsahu souboru na základě jeho názvu.</span><span class="sxs-lookup"><span data-stu-id="24573-111">Do not make decisions about the contents of the file based on the name of the file.</span></span> <span data-ttu-id="24573-112">Například soubor Form1.vb nemusí být zdrojový soubor jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="24573-112">For example, the file Form1.vb may not be a Visual Basic source file.</span></span> <span data-ttu-id="24573-113">Před použitím dat ve své aplikaci ověřte všechny vstupy.</span><span class="sxs-lookup"><span data-stu-id="24573-113">Verify all inputs before using the data in your application.</span></span> <span data-ttu-id="24573-114">Soubor nemusí mít obsah, jaký očekáváte, a metody pro čtení z tohoto souboru mohou selhat.</span><span class="sxs-lookup"><span data-stu-id="24573-114">The contents of the file may not be what is expected, and methods to read from the file may fail.</span></span>

### <a name="to-download-a-file"></a><span data-ttu-id="24573-115">Stažení souboru</span><span class="sxs-lookup"><span data-stu-id="24573-115">To download a file</span></span>

- <span data-ttu-id="24573-116">Pomocí `DownloadFile` této metody stáhněte soubor, zadejte umístění cílového souboru jako řetězec nebo identifikátor URI a umístění, ve kterém má být soubor ukládán.</span><span class="sxs-lookup"><span data-stu-id="24573-116">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file.</span></span> <span data-ttu-id="24573-117">Tento příklad stáhne `WineList.txt` `http://www.cohowinery.com/downloads` soubor z a `C:\Documents and Settings\All Users\Documents`uloží jej do :</span><span class="sxs-lookup"><span data-stu-id="24573-117">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`:</span></span>

  [!code-vb[VbResourceTasks#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#9)]

### <a name="to-download-a-file-specifying-a-time-out-interval"></a><span data-ttu-id="24573-118">Stažení souboru určením časového intervalu</span><span class="sxs-lookup"><span data-stu-id="24573-118">To download a file, specifying a time-out interval</span></span>

- <span data-ttu-id="24573-119">Pomocí `DownloadFile` metody stáhněte soubor, určení umístění cílového souboru jako řetězec nebo IDENTIFIKÁTOR URI, určení umístění, ve kterém chcete soubor uložit, a určení časového limitu v milisekundách (výchozí hodnota je 1000).</span><span class="sxs-lookup"><span data-stu-id="24573-119">Use the `DownloadFile` method to download the file, specifying the target file's location as a string or URI, specifying the location at which to store the file, and specifying the time-out interval in milliseconds (the default is 1000).</span></span> <span data-ttu-id="24573-120">Tento příklad stáhne `WineList.txt` `http://www.cohowinery.com/downloads` soubor z a `C:\Documents and Settings\All Users\Documents`uloží jej do aplikace , a zadává interval časového intervalu 500 milisekund:</span><span class="sxs-lookup"><span data-stu-id="24573-120">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, specifying a time-out interval of 500 milliseconds:</span></span>

  [!code-vb[VbResourceTasks#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#10)]

### <a name="to-download-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="24573-121">Stažení souboru zadáním uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="24573-121">To download a file, supplying a user name and password</span></span>

- <span data-ttu-id="24573-122">Pomocí `DownLoadFile` této metody stáhněte soubor, zadejte umístění cílového souboru jako řetězec nebo identifikátor URI a umístění, do kterého chcete soubor uložit, uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="24573-122">Use the `DownLoadFile` method to download the file, specifying the target file's location as a string or URI and specifying the location at which to store the file, the user name, and the password.</span></span> <span data-ttu-id="24573-123">Tento příklad stáhne `WineList.txt` `http://www.cohowinery.com/downloads` soubor z a `C:\Documents and Settings\All Users\Documents`uloží jej `anonymous` do aplikace s uživatelským jménem a prázdným heslem.</span><span class="sxs-lookup"><span data-stu-id="24573-123">This example downloads the file `WineList.txt` from `http://www.cohowinery.com/downloads` and saves it to `C:\Documents and Settings\All Users\Documents`, with the user name `anonymous` and a blank password.</span></span>

  [!code-vb[VbResourceTasks#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#11)]

  > [!IMPORTANT]
  > <span data-ttu-id="24573-124">Protokol FTP používaný `DownLoadFile` metodou odesílá informace, včetně hesel, ve formátu prostého textu a neměl by být používán pro přenos citlivých informací.</span><span class="sxs-lookup"><span data-stu-id="24573-124">The FTP protocol used by the `DownLoadFile` method sends information, including passwords, in plain text and should not be used for transmitting sensitive information.</span></span>

## <a name="see-also"></a><span data-ttu-id="24573-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="24573-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network>
- <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>
- [<span data-ttu-id="24573-126">Postupy: Nahrání souboru</span><span class="sxs-lookup"><span data-stu-id="24573-126">How to: Upload a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)
- [<span data-ttu-id="24573-127">Postupy: Analýza cest k souborům</span><span class="sxs-lookup"><span data-stu-id="24573-127">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
