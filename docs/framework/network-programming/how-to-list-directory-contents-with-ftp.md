---
title: 'Postupy: Výpis obsahu adresáře s využitím protokolu FTP'
description: Tento článek popisuje ukázku toho, jak zobrazit obsah adresáře serveru FTP.
ms.date: 06/26/2018
dev_langs:
- csharp
- vb
ms.assetid: 130c64c9-7b7f-4672-9b3b-d946bd2616c5
ms.openlocfilehash: 924e6731ce585f127af319fdbfbdc8c12e61c46d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642617"
---
# <a name="how-to-list-directory-contents-with-ftp"></a>Postupy: Výpis obsahu adresáře s využitím protokolu FTP

Tento příklad ukazuje, jak zobrazit obsah adresáře serveru FTP.

## <a name="example"></a>Příklad

```csharp
using System;
using System.IO;
using System.Net;

namespace Examples.System.Net
{
    public class WebRequestGetExample
    {
        public static void Main ()
        {
            // Get the object used to communicate with the server.
            FtpWebRequest request = (FtpWebRequest)WebRequest.Create("ftp://www.contoso.com/");
            request.Method = WebRequestMethods.Ftp.ListDirectoryDetails;

            // This example assumes the FTP site uses anonymous logon.
            request.Credentials = new NetworkCredential ("anonymous","janeDoe@contoso.com");

            FtpWebResponse response = (FtpWebResponse)request.GetResponse();

            Stream responseStream = response.GetResponseStream();
            StreamReader reader = new StreamReader(responseStream);
            Console.WriteLine(reader.ReadToEnd());

            Console.WriteLine($"Directory List Complete, status {response.StatusDescription}");

            reader.Close();
            response.Close();
        }
    }
}
```

```vb
Imports System.IO
Imports System.Net

Namespace Examples.System.Net
    Public Module WebRequestGetExample
        Public Sub Main()
            ' Get the object used to communicate with the server.
            Dim request As FtpWebRequest = CType(WebRequest.Create("ftp://www.contoso.com/"), FtpWebRequest)
            request.Method = WebRequestMethods.Ftp.ListDirectoryDetails

            ' This example assumes the FTP site uses anonymous logon.
            request.Credentials = New NetworkCredential("anonymous", "janeDoe@contoso.com")

            Dim response As FtpWebResponse = CType(request.GetResponse(), FtpWebResponse)

            Dim responseStream As Stream = response.GetResponseStream()
            Dim reader As StreamReader = New StreamReader(responseStream)
            Console.WriteLine(reader.ReadToEnd())

            Console.WriteLine($"Directory List Complete, status {response.StatusDescription}")

            reader.Close()
            response.Close()
        End Sub
    End Module
End Namespace
```

Pokud potřebujete konkrétní adresář seznamu, stačí přidat adresář na konec identifikátoru URI, které používáte ve <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metody:

```csharp
FtpWebRequest request = (FtpWebRequest)WebRequest.Create("ftp://www.contoso.com/your_preferred_directory");
```

```vb
Dim request As FtpWebRequest = CType(WebRequest.Create("ftp://www.contoso.com/your_preferred_directory"), FtpWebRequest)
```
