---
title: 'Postupy: Nahrát soubor v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: 486351bc140a2bbf18bb8f85f761fc491f028bba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58840351"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a><span data-ttu-id="15aa4-102">Postupy: Nahrát soubor v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="15aa4-102">How to: Upload a File in Visual Basic</span></span>
<span data-ttu-id="15aa4-103"><xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> Metodu je možné nahrát soubor a uloží je do vzdáleného umístění.</span><span class="sxs-lookup"><span data-stu-id="15aa4-103">The <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> method can be used to upload a file and store it to a remote location.</span></span> <span data-ttu-id="15aa4-104">Pokud `ShowUI` parametr je nastaven na `True`, se zobrazí dialogové okno, které zobrazí průběh nahrávání a umožňuje uživatelům na zrušení operace.</span><span class="sxs-lookup"><span data-stu-id="15aa4-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed that shows the progress of the upload and allows users to cancel the operation.</span></span>  
  
### <a name="to-upload-a-file"></a><span data-ttu-id="15aa4-105">Pokud chcete nahrát soubor</span><span class="sxs-lookup"><span data-stu-id="15aa4-105">To upload a file</span></span>  
  
-   <span data-ttu-id="15aa4-106">Použití `UploadFile` metodu pro nahrání souboru, zadáte umístění zdrojového souboru a umístění cílového adresáře jako řetězec nebo identifikátor URI (Uniform Resource Identifier). Tento příklad nahraje soubor `Order.txt` k `http://www.cohowinery.com/uploads.aspx`.</span><span class="sxs-lookup"><span data-stu-id="15aa4-106">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI (Uniform Resource Identifier).This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`.</span></span>  
  
     [!code-vb[VbResourceTasks#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#6)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a><span data-ttu-id="15aa4-107">Nahrát soubor a zobrazí průběh operace</span><span class="sxs-lookup"><span data-stu-id="15aa4-107">To upload a file and show the progress of the operation</span></span>  
  
-   <span data-ttu-id="15aa4-108">Použití `UploadFile` metodu pro nahrání souboru, jako řetězec nebo identifikátor URI určující umístění zdrojového souboru a umístění cílového adresáře.</span><span class="sxs-lookup"><span data-stu-id="15aa4-108">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI.</span></span> <span data-ttu-id="15aa4-109">Tento příklad nahraje soubor `Order.txt` k `http://www.cohowinery.com/uploads.aspx` bez uživatelského jména a hesla, zobrazí se průběh nahrávání a má interval časového limitu 500 milisekund.</span><span class="sxs-lookup"><span data-stu-id="15aa4-109">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx` without supplying a user name or password, shows the progress of the upload, and has a time-out interval of 500 milliseconds.</span></span>  
  
     [!code-vb[VbResourceTasks#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#7)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="15aa4-110">Pokud chcete nahrát soubor, zadáním uživatelského jména a hesla</span><span class="sxs-lookup"><span data-stu-id="15aa4-110">To upload a file, supplying a user name and password</span></span>  
  
-   <span data-ttu-id="15aa4-111">Použití `UploadFile` metodu pro nahrání souboru, jako řetězec nebo identifikátor URI určující umístění zdrojového souboru a umístění cílového adresáře a uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="15aa4-111">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI, and specifying the user name and the password.</span></span> <span data-ttu-id="15aa4-112">Tento příklad nahraje soubor `Order.txt` k `http://www.cohowinery.com/uploads.aspx`, zadáním uživatelského jména `anonymous` a heslo necháte prázdné.</span><span class="sxs-lookup"><span data-stu-id="15aa4-112">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`, supplying the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbResourceTasks/VB/Class1.vb#8)]  
  
## <a name="robust-programming"></a><span data-ttu-id="15aa4-113">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="15aa4-113">Robust Programming</span></span>  
 <span data-ttu-id="15aa4-114">Následující podmínky mohou vyvolat výjimku:</span><span class="sxs-lookup"><span data-stu-id="15aa4-114">The following conditions may throw an exception:</span></span>  
  
-   <span data-ttu-id="15aa4-115">Cestu k místnímu souboru není platný (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="15aa4-115">The local file path is not valid (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="15aa4-116">Ověření se nezdařilo (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="15aa4-116">Authentication failed (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="15aa4-117">Vypršel časový limit připojení (<xref:System.TimeoutException>).</span><span class="sxs-lookup"><span data-stu-id="15aa4-117">The connection timed out (<xref:System.TimeoutException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15aa4-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="15aa4-118">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>
- [<span data-ttu-id="15aa4-119">Postupy: Stažení souboru</span><span class="sxs-lookup"><span data-stu-id="15aa4-119">How to: Download a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)
- [<span data-ttu-id="15aa4-120">Postupy: Analýza cest k souborům</span><span class="sxs-lookup"><span data-stu-id="15aa4-120">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
