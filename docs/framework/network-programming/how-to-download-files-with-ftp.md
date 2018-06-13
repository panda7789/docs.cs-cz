---
title: 'Postupy: stažení souborů s FTP'
ms.date: 03/30/2017
ms.assetid: 892548b8-954a-4f6a-9bca-2ae620c3700f
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a3e0b5773a98b42411e4dd76668dafb834b5cbd3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394846"
---
# <a name="how-to-download-files-with-ftp"></a><span data-ttu-id="94cd1-102">Postupy: stažení souborů s FTP</span><span class="sxs-lookup"><span data-stu-id="94cd1-102">How to: Download Files with FTP</span></span>
<span data-ttu-id="94cd1-103">Tento příklad ukazuje, jak stáhnout soubor ze serveru FTP.</span><span class="sxs-lookup"><span data-stu-id="94cd1-103">This sample shows how to download a file from an FTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94cd1-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="94cd1-104">Example</span></span>  
  
```csharp  
using System;  
using System.IO;  
using System.Net;  
using System.Text;  
  
namespace Examples.System.Net  
{  
    public class WebRequestGetExample  
    {  
        public static void Main ()  
        {  
            // Get the object used to communicate with the server.  
            FtpWebRequest request = (FtpWebRequest)WebRequest.Create("ftp://www.contoso.com/test.htm");  
            request.Method = WebRequestMethods.Ftp.DownloadFile;  
  
            // This example assumes the FTP site uses anonymous logon.  
            request.Credentials = new NetworkCredential ("anonymous","janeDoe@contoso.com");  
  
            FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
  
            Stream responseStream = response.GetResponseStream();  
            StreamReader reader = new StreamReader(responseStream);  
            Console.WriteLine(reader.ReadToEnd());  
  
            Console.WriteLine("Download Complete, status {0}", response.StatusDescription);  
  
            reader.Close();  
            response.Close();    
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="94cd1-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="94cd1-105">Compiling the Code</span></span>  
 <span data-ttu-id="94cd1-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="94cd1-106">This example requires:</span></span>  
  
-   <span data-ttu-id="94cd1-107">Odkazuje na **System.Net** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="94cd1-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="94cd1-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="94cd1-108">Robust Programming</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="94cd1-109">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="94cd1-109">.NET Framework Security</span></span>
