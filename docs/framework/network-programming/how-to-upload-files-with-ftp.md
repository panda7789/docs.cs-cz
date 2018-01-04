---
title: "Postupy: odeslání souborů pomocí protokolu FTP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e40f17c5-dd12-4c62-9dbf-00ab491382dc
caps.latest.revision: "5"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 0772e77d699d11e29d17770bb2c737247ed1771d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-upload-files-with-ftp"></a><span data-ttu-id="4b981-102">Postupy: odeslání souborů pomocí protokolu FTP</span><span class="sxs-lookup"><span data-stu-id="4b981-102">How to: Upload Files with FTP</span></span>
<span data-ttu-id="4b981-103">Tento příklad ukazuje, jak nahrát soubor do serveru FTP.</span><span class="sxs-lookup"><span data-stu-id="4b981-103">This sample shows how to upload a file to an FTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b981-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="4b981-104">Example</span></span>  
  
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
            request.Method = WebRequestMethods.Ftp.UploadFile;  
  
            // This example assumes the FTP site uses anonymous logon.  
            request.Credentials = new NetworkCredential ("anonymous","janeDoe@contoso.com");  
  
            // Copy the contents of the file to the request stream.  
            StreamReader sourceStream = new StreamReader("testfile.txt");  
            byte [] fileContents = Encoding.UTF8.GetBytes(sourceStream.ReadToEnd());  
            sourceStream.Close();  
            request.ContentLength = fileContents.Length;  
  
            Stream requestStream = request.GetRequestStream();  
            requestStream.Write(fileContents, 0, fileContents.Length);  
            requestStream.Close();  
  
            FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
  
            Console.WriteLine("Upload File Complete, status {0}", response.StatusDescription);  
  
            response.Close();  
        }  
    }  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4b981-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4b981-105">Compiling the Code</span></span>  
 <span data-ttu-id="4b981-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="4b981-106">This example requires:</span></span>  
  
-   <span data-ttu-id="4b981-107">Odkazuje na **System.Net** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="4b981-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4b981-108">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="4b981-108">Robust Programming</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="4b981-109">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4b981-109">.NET Framework Security</span></span>
