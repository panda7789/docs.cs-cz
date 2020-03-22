---
title: 'Postupy: Odeslání souboru'
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: 52b731606c74ab7ff06a42dfdbe078616ba33d88
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345563"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a><span data-ttu-id="68438-102">Postupy: Odeslání souboru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="68438-102">How to: Upload a File in Visual Basic</span></span>

<span data-ttu-id="68438-103">Metodu <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> lze použít k nahrání souboru a jeho uložení do vzdáleného umístění.</span><span class="sxs-lookup"><span data-stu-id="68438-103">The <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> method can be used to upload a file and store it to a remote location.</span></span> <span data-ttu-id="68438-104">Pokud `ShowUI` je parametr `True`nastaven na , zobrazí se dialogové okno, které zobrazuje průběh nahrávání a umožňuje uživatelům operaci zrušit.</span><span class="sxs-lookup"><span data-stu-id="68438-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed that shows the progress of the upload and allows users to cancel the operation.</span></span>  
  
### <a name="to-upload-a-file"></a><span data-ttu-id="68438-105">Nahrání souboru</span><span class="sxs-lookup"><span data-stu-id="68438-105">To upload a file</span></span>  
  
- <span data-ttu-id="68438-106">Pomocí `UploadFile` této metody můžete nahrát soubor a zadat umístění zdrojového souboru a umístění cílového adresáře jako řetězec nebo identifikátor URI (Identifikátor jednotného prostředku). Tento příklad odešle `Order.txt` `http://www.cohowinery.com/uploads.aspx`soubor do aplikace .</span><span class="sxs-lookup"><span data-stu-id="68438-106">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI (Uniform Resource Identifier).This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`.</span></span>  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a><span data-ttu-id="68438-107">Nahrání souboru a zobrazení průběhu operace</span><span class="sxs-lookup"><span data-stu-id="68438-107">To upload a file and show the progress of the operation</span></span>  
  
- <span data-ttu-id="68438-108">Pomocí `UploadFile` této metody můžete nahrát soubor a zadat umístění zdrojového souboru a umístění cílového adresáře jako řetězec nebo identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="68438-108">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI.</span></span> <span data-ttu-id="68438-109">Tento příklad odešle `Order.txt` `http://www.cohowinery.com/uploads.aspx` soubor bez zadání uživatelského jména nebo hesla, zobrazí průběh nahrávání a má interval časového intervalu 500 milisekund.</span><span class="sxs-lookup"><span data-stu-id="68438-109">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx` without supplying a user name or password, shows the progress of the upload, and has a time-out interval of 500 milliseconds.</span></span>  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="68438-110">Odeslání souboru zadáním uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="68438-110">To upload a file, supplying a user name and password</span></span>  
  
- <span data-ttu-id="68438-111">Pomocí `UploadFile` této metody můžete nahrát soubor, zadat umístění zdrojového souboru a umístění cílového adresáře jako řetězec nebo identifikátor URI a zadat uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="68438-111">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI, and specifying the user name and the password.</span></span> <span data-ttu-id="68438-112">Tento příklad nahraje `Order.txt` `http://www.cohowinery.com/uploads.aspx`soubor do , `anonymous` zadání uživatelského jména a prázdné heslo.</span><span class="sxs-lookup"><span data-stu-id="68438-112">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`, supplying the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="68438-113">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="68438-113">Robust Programming</span></span>  

 <span data-ttu-id="68438-114">Následující podmínky mohou vyvolat výjimku:</span><span class="sxs-lookup"><span data-stu-id="68438-114">The following conditions may throw an exception:</span></span>  
  
- <span data-ttu-id="68438-115">Cesta k místnímu souboru není platná (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="68438-115">The local file path is not valid (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="68438-116">Ověřování se<xref:System.Security.SecurityException>nezdařilo ( ).</span><span class="sxs-lookup"><span data-stu-id="68438-116">Authentication failed (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="68438-117">Vypršel časový limit<xref:System.TimeoutException>připojení ( ).</span><span class="sxs-lookup"><span data-stu-id="68438-117">The connection timed out (<xref:System.TimeoutException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68438-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="68438-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [<span data-ttu-id="68438-119">Postupy: Stažení souboru</span><span class="sxs-lookup"><span data-stu-id="68438-119">How to: Download a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)
- [<span data-ttu-id="68438-120">Postupy: Analýza cest k souborům</span><span class="sxs-lookup"><span data-stu-id="68438-120">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
