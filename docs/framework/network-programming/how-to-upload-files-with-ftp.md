---
title: 'Postup: Nahrávání souborů pomocí protokolu FTP'
description: Tento článek ukazuje ukázku, jak nahrát soubor na server FTP.
ms.date: 06/26/2018
dev_langs:
- csharp
- vb
ms.assetid: e40f17c5-dd12-4c62-9dbf-00ab491382dc
ms.openlocfilehash: 670bbc65078e6530cffbcfa7d324c36238014ffb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "65632811"
---
# <a name="how-to-upload-files-with-ftp"></a><span data-ttu-id="75427-103">Postup: Nahrávání souborů pomocí protokolu FTP</span><span class="sxs-lookup"><span data-stu-id="75427-103">How to: Upload files with FTP</span></span>

<span data-ttu-id="75427-104">Tato ukázka ukazuje, jak nahrát soubor na server FTP.</span><span class="sxs-lookup"><span data-stu-id="75427-104">This sample shows how to upload a file to an FTP server.</span></span>

## <a name="example"></a><span data-ttu-id="75427-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="75427-105">Example</span></span>

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
            request.Credentials = new NetworkCredential("anonymous", "janeDoe@contoso.com");

            // Copy the contents of the file to the request stream.
            byte[] fileContents;
            using (StreamReader sourceStream = new StreamReader("testfile.txt"))
            {
                fileContents = Encoding.UTF8.GetBytes(sourceStream.ReadToEnd());
            }

            request.ContentLength = fileContents.Length;

            using (Stream requestStream = request.GetRequestStream())
            {
                requestStream.Write(fileContents, 0, fileContents.Length);
            }

            using (FtpWebResponse response = (FtpWebResponse)request.GetResponse())
            {
                Console.WriteLine($"Upload File Complete, status {response.StatusDescription}");
            }
        }
    }
}
```

```vb
Imports System.IO
Imports System.Net
Imports System.Text

Namespace Examples.System.Net
    Public Module WebRequestGetExample
        Public Sub Main()
            ' Get the object used to communicate with the server.
            Dim request As FtpWebRequest = CType(WebRequest.Create("ftp://www.contoso.com/test.htm"), FtpWebRequest)
            request.Method = WebRequestMethods.Ftp.UploadFile

            ' This example assumes the FTP site uses anonymous logon.
            request.Credentials = New NetworkCredential("anonymous", "janeDoe@contoso.com")

            ' Copy the contents of the file to the request stream.
            Dim fileContents As Byte()

            Using sourceStream As StreamReader = New StreamReader("testfile.txt")
                fileContents = Encoding.UTF8.GetBytes(sourceStream.ReadToEnd())
            End Using

            request.ContentLength = fileContents.Length

            Using requestStream As Stream = request.GetRequestStream()
                requestStream.Write(fileContents, 0, fileContents.Length)
            End Using

            Using response As FtpWebResponse = CType(request.GetResponse(), FtpWebResponse)
                Console.WriteLine($"Upload File Complete, status {response.StatusDescription}")
            End Using
        End Sub
    End Module
End Namespace
```
