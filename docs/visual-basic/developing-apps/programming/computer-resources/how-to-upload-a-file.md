---
title: 'Postupy: Odeslání souboru v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- networks, uploading files
- files [Visual Basic], uploading
- uploading files [Visual Basic]
- UploadFile method [Visual Basic]
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
ms.openlocfilehash: 769c04430f8323dfde680fca45cfcd67809bdab0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33583783"
---
# <a name="how-to-upload-a-file-in-visual-basic"></a><span data-ttu-id="e719c-102">Postupy: Odeslání souboru v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e719c-102">How to: Upload a File in Visual Basic</span></span>
<span data-ttu-id="e719c-103"><xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> Metoda slouží k nahrání souboru a jeho uložení do vzdáleného umístění.</span><span class="sxs-lookup"><span data-stu-id="e719c-103">The <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> method can be used to upload a file and store it to a remote location.</span></span> <span data-ttu-id="e719c-104">Pokud `ShowUI` parametr je nastaven na `True`, se zobrazí dialogové okno, které zobrazuje průběh nahrávání a umožňuje uživatelům na tlačítko Storno.</span><span class="sxs-lookup"><span data-stu-id="e719c-104">If the `ShowUI` parameter is set to `True`, a dialog box is displayed that shows the progress of the upload and allows users to cancel the operation.</span></span>  
  
### <a name="to-upload-a-file"></a><span data-ttu-id="e719c-105">Pro nahrání souboru</span><span class="sxs-lookup"><span data-stu-id="e719c-105">To upload a file</span></span>  
  
-   <span data-ttu-id="e719c-106">Použití `UploadFile` metodu pro nahrání souboru, zadáte umístění zdrojových souborů a cílové umístění adresáře jako řetězec nebo identifikátor URI (Uniform Resource Identifier). Tento příklad nahrávání souboru `Order.txt` k `http://www.cohowinery.com/uploads.aspx`.</span><span class="sxs-lookup"><span data-stu-id="e719c-106">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI (Uniform Resource Identifier).This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`.</span></span>  
  
     [!code-vb[VbResourceTasks#6](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_1.vb)]  
  
### <a name="to-upload-a-file-and-show-the-progress-of-the-operation"></a><span data-ttu-id="e719c-107">Nahrát soubor a zobrazit průběh operace</span><span class="sxs-lookup"><span data-stu-id="e719c-107">To upload a file and show the progress of the operation</span></span>  
  
-   <span data-ttu-id="e719c-108">Použití `UploadFile` metodu pro nahrání souboru, zadáte umístění zdrojových souborů a cílové umístění adresáře jako řetězec nebo identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="e719c-108">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI.</span></span> <span data-ttu-id="e719c-109">Tento příklad nahrávání souboru `Order.txt` k `http://www.cohowinery.com/uploads.aspx` bez uživatelské jméno a heslo, zobrazí průběh nahrávání a interval časového limitu na 500 milisekund.</span><span class="sxs-lookup"><span data-stu-id="e719c-109">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx` without supplying a user name or password, shows the progress of the upload, and has a time-out interval of 500 milliseconds.</span></span>  
  
     [!code-vb[VbResourceTasks#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_2.vb)]  
  
### <a name="to-upload-a-file-supplying-a-user-name-and-password"></a><span data-ttu-id="e719c-110">Nahrát soubor s poskytnutím uživatelské jméno a heslo</span><span class="sxs-lookup"><span data-stu-id="e719c-110">To upload a file, supplying a user name and password</span></span>  
  
-   <span data-ttu-id="e719c-111">Použití `UploadFile` metodu pro nahrání souboru, zadáním umístění zdrojových souborů a cílové umístění adresáře jako řetězec nebo identifikátor URI a uživatelské jméno a heslo.</span><span class="sxs-lookup"><span data-stu-id="e719c-111">Use the `UploadFile` method to upload a file, specifying the source file's location and the target directory location as a string or URI, and specifying the user name and the password.</span></span> <span data-ttu-id="e719c-112">Tento příklad nahrávání souboru `Order.txt` k `http://www.cohowinery.com/uploads.aspx`, poskytuje uživatelské jméno `anonymous` a prázdné heslo.</span><span class="sxs-lookup"><span data-stu-id="e719c-112">This example uploads the file `Order.txt` to `http://www.cohowinery.com/uploads.aspx`, supplying the user name `anonymous` and a blank password.</span></span>  
  
     [!code-vb[VbResourceTasks#8](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_3.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="e719c-113">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="e719c-113">Robust Programming</span></span>  
 <span data-ttu-id="e719c-114">Následujících podmínek může vyvolat výjimku:</span><span class="sxs-lookup"><span data-stu-id="e719c-114">The following conditions may throw an exception:</span></span>  
  
-   <span data-ttu-id="e719c-115">Cestu k místnímu souboru není platný (<xref:System.ArgumentException>).</span><span class="sxs-lookup"><span data-stu-id="e719c-115">The local file path is not valid (<xref:System.ArgumentException>).</span></span>  
  
-   <span data-ttu-id="e719c-116">Ověření se nezdařilo (<xref:System.Security.SecurityException>).</span><span class="sxs-lookup"><span data-stu-id="e719c-116">Authentication failed (<xref:System.Security.SecurityException>).</span></span>  
  
-   <span data-ttu-id="e719c-117">Vypršel časový limit připojení (<xref:System.TimeoutException>).</span><span class="sxs-lookup"><span data-stu-id="e719c-117">The connection timed out (<xref:System.TimeoutException>).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e719c-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="e719c-118">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>  
 [<span data-ttu-id="e719c-119">Postupy: Stažení souboru</span><span class="sxs-lookup"><span data-stu-id="e719c-119">How to: Download a File</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)  
 [<span data-ttu-id="e719c-120">Postupy: Analýza cest k souborům</span><span class="sxs-lookup"><span data-stu-id="e719c-120">How to: Parse File Paths</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)
