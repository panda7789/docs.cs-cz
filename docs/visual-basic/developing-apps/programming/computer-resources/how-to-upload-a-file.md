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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345563"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a><span data-ttu-id="58d5d-102">Postupy: Odeslání souboru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="58d5d-102">How to: Upload a File in Visual Basic</span></span>

<span data-ttu-id="58d5d-103">Metodu <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> lze použít k nahrání souboru a jeho uložení do vzdáleného umístění.</span><span class="sxs-lookup"><span data-stu-id="58d5d-103">The <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> method can be used to upload a file and store it to a remote location.</span></span> <span data-ttu-id="58d5d-104">Pokud je parametr `ShowUI` nastaven na `True`, zobrazí se dialogové okno s informacemi o průběhu nahrávání a umožňuje uživatelům zrušit operaci.</span><span class="sxs-lookup"><span data-stu-id="58d5d-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed that shows the progress of the upload and allows users to cancel the operation.</span></span>  
  
### <a name="to-upload-a-file"></a><span data-ttu-id="58d5d-105">Nahrání souboru</span><span class="sxs-lookup"><span data-stu-id="58d5d-105">To upload a file</span></span>  
  
- <span data-ttu-id="58d5d-106">Použijte metodu `UploadFile` k nahrání souboru, určení umístění zdrojového souboru a umístění cílového adresáře jako řetězce nebo identifikátoru URI (Uniform Resource Identifier). Tento příklad nahraje soubor `Order.txt` k `http://www.cohowinery.com/uploads.aspx`.</span><span class="sxs-lookup"><span data-stu-id="58d5d-106">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI (Uniform Resource Identifier).This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`.</span></span>  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a><span data-ttu-id="58d5d-107">Nahrání souboru a zobrazení průběhu operace</span><span class="sxs-lookup"><span data-stu-id="58d5d-107">To upload a file and show the progress of the operation</span></span>  
  
- <span data-ttu-id="58d5d-108">Použijte metodu `UploadFile` k nahrání souboru, určení umístění zdrojového souboru a umístění cílového adresáře jako řetězce nebo identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="58d5d-108">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI.</span></span> <span data-ttu-id="58d5d-109">Tento příklad nahraje soubor `Order.txt` do `http://www.cohowinery.com/uploads.aspx` bez zadání uživatelského jména nebo hesla, zobrazí průběh nahrávání a má časový limit 500 milisekund.</span><span class="sxs-lookup"><span data-stu-id="58d5d-109">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx` without supplying a user name or password, shows the progress of the upload, and has a time-out interval of 500 milliseconds.</span></span>  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="58d5d-110">Pokud chcete nahrát soubor, zadejte uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="58d5d-110">To upload a file, supplying a user name and password</span></span>  
  
- <span data-ttu-id="58d5d-111">Použijte metodu `UploadFile` k nahrání souboru, určení umístění zdrojového souboru a umístění cílového adresáře jako řetězce nebo identifikátoru URI a zadání uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="58d5d-111">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI, and specifying the user name and the password.</span></span> <span data-ttu-id="58d5d-112">Tento příklad nahraje soubor `Order.txt` do `http://www.cohowinery.com/uploads.aspx`a poskytne uživatelské jméno `anonymous` a prázdné heslo.</span><span class="sxs-lookup"><span data-stu-id="58d5d-112">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`, supplying the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="58d5d-113">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="58d5d-113">Robust Programming</span></span>  

 <span data-ttu-id="58d5d-114">Následující podmínky mohou vyvolat výjimku:</span><span class="sxs-lookup"><span data-stu-id="58d5d-114">The following conditions may throw an exception:</span></span>  
  
- <span data-ttu-id="58d5d-115">Cesta k místnímu souboru není platná (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="58d5d-115">The local file path is not valid (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="58d5d-116">Ověřování se nezdařilo (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="58d5d-116">Authentication failed (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="58d5d-117">Vypršel časový limit připojení (<xref:System.TimeoutException>).</span><span class="sxs-lookup"><span data-stu-id="58d5d-117">The connection timed out (<xref:System.TimeoutException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58d5d-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="58d5d-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [<span data-ttu-id="58d5d-119">Postupy: Stažení souboru</span><span class="sxs-lookup"><span data-stu-id="58d5d-119">How to: Download a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)
- [<span data-ttu-id="58d5d-120">Postupy: Analýza cest k souborům</span><span class="sxs-lookup"><span data-stu-id="58d5d-120">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
