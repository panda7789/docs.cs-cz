---
title: 'Postupy: Nahrání souboru'
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: cee6811d6b6d295c28eb683c5d2f7bcbb5fe94ab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401807"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a><span data-ttu-id="70fbf-102">Postupy: Odeslání souboru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="70fbf-102">How to: Upload a File in Visual Basic</span></span>

<span data-ttu-id="70fbf-103"><xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>Metodu lze použít k nahrání souboru a jeho uložení do vzdáleného umístění.</span><span class="sxs-lookup"><span data-stu-id="70fbf-103">The <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> method can be used to upload a file and store it to a remote location.</span></span> <span data-ttu-id="70fbf-104">Pokud `ShowUI` je parametr nastaven na hodnotu `True` , zobrazí se dialogové okno, které zobrazuje průběh nahrávání a umožňuje uživatelům zrušit operaci.</span><span class="sxs-lookup"><span data-stu-id="70fbf-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed that shows the progress of the upload and allows users to cancel the operation.</span></span>  
  
### <a name="to-upload-a-file"></a><span data-ttu-id="70fbf-105">Nahrání souboru</span><span class="sxs-lookup"><span data-stu-id="70fbf-105">To upload a file</span></span>  
  
- <span data-ttu-id="70fbf-106">Použijte `UploadFile` metodu pro nahrání souboru, určení umístění zdrojového souboru a umístění cílového adresáře jako řetězce nebo identifikátor URI (Uniform Resource Identifier). Tento příklad nahraje soubor `Order.txt` do `http://www.cohowinery.com/uploads.aspx` .</span><span class="sxs-lookup"><span data-stu-id="70fbf-106">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI (Uniform Resource Identifier).This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`.</span></span>  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a><span data-ttu-id="70fbf-107">Nahrání souboru a zobrazení průběhu operace</span><span class="sxs-lookup"><span data-stu-id="70fbf-107">To upload a file and show the progress of the operation</span></span>  
  
- <span data-ttu-id="70fbf-108">Použijte `UploadFile` metodu k nahrání souboru, určení umístění zdrojového souboru a umístění cílového adresáře jako řetězce nebo identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="70fbf-108">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI.</span></span> <span data-ttu-id="70fbf-109">Tento příklad nahraje soubor do, `Order.txt` `http://www.cohowinery.com/uploads.aspx` aniž by zadal uživatelské jméno nebo heslo, zobrazuje průběh nahrávání a má časový limit 500 milisekund.</span><span class="sxs-lookup"><span data-stu-id="70fbf-109">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx` without supplying a user name or password, shows the progress of the upload, and has a time-out interval of 500 milliseconds.</span></span>  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="70fbf-110">Pokud chcete nahrát soubor, zadejte uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="70fbf-110">To upload a file, supplying a user name and password</span></span>  
  
- <span data-ttu-id="70fbf-111">Použijte `UploadFile` metodu k nahrání souboru, určení umístění zdrojového souboru a umístění cílového adresáře jako řetězce nebo identifikátoru URI a zadání uživatelského jména a hesla.</span><span class="sxs-lookup"><span data-stu-id="70fbf-111">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI, and specifying the user name and the password.</span></span> <span data-ttu-id="70fbf-112">Tento příklad nahraje soubor `Order.txt` do `http://www.cohowinery.com/uploads.aspx` , zadáním uživatelského jména `anonymous` a prázdného hesla.</span><span class="sxs-lookup"><span data-stu-id="70fbf-112">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`, supplying the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="70fbf-113">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="70fbf-113">Robust Programming</span></span>  

 <span data-ttu-id="70fbf-114">Následující podmínky mohou vyvolat výjimku:</span><span class="sxs-lookup"><span data-stu-id="70fbf-114">The following conditions may throw an exception:</span></span>  
  
- <span data-ttu-id="70fbf-115">Cesta k místnímu souboru není platná ( <xref:System.ArgumentException> ).</span><span class="sxs-lookup"><span data-stu-id="70fbf-115">The local file path is not valid (<xref:System.ArgumentException>).</span></span>  
  
- <span data-ttu-id="70fbf-116">Ověřování se nezdařilo ( <xref:System.Security.SecurityException> ).</span><span class="sxs-lookup"><span data-stu-id="70fbf-116">Authentication failed (<xref:System.Security.SecurityException>).</span></span>  
  
- <span data-ttu-id="70fbf-117">Vypršel časový limit připojení ( <xref:System.TimeoutException> ).</span><span class="sxs-lookup"><span data-stu-id="70fbf-117">The connection timed out (<xref:System.TimeoutException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70fbf-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="70fbf-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [<span data-ttu-id="70fbf-119">Postupy: Stažení souboru</span><span class="sxs-lookup"><span data-stu-id="70fbf-119">How to: Download a File</span></span>](how-to-download-a-file.md)
- [<span data-ttu-id="70fbf-120">Postupy: Analýza cest k souborům</span><span class="sxs-lookup"><span data-stu-id="70fbf-120">How to: Parse File Paths</span></span>](../drives-directories-files/how-to-parse-file-paths.md)
