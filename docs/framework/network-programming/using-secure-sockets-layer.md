---
title: Použití protokolu SSL (Secure Sockets Layer)
description: Přečtěte si, jak System.Net a rozšiřující třídy používají SSL (Secure Sockets Layer) k šifrování připojení pro několik síťových protokolů v .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Networking
- SSL
- Secure Sockets Layer
- requesting data from Internet, Secure Sockets Layer
- sending data, Secure Sockets Layer
- Network Resources
- data requests, Secure Sockets Layer
- receiving data, Secure Sockets Layer
- Internet, Secure Sockets Layer
ms.assetid: 6e4289e6-d1b7-4e82-ab0d-e83e3b6063ed
ms.openlocfilehash: 67330962382e768849cbf67d5f412ea80f65569d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501986"
---
# <a name="using-secure-sockets-layer"></a>Použití protokolu SSL (Secure Sockets Layer)
<xref:System.Net>Třídy používají SSL (Secure Sockets Layer) (SSL) k šifrování připojení pro několik síťových protokolů.  
  
 U připojení http <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> třídy a používají protokol SSL ke komunikaci s webovými hostiteli, kteří podporují protokol SSL. Rozhodnutí o použití protokolu SSL provádí <xref:System.Net.WebRequest> Třída na základě identifikátoru URI, který je přidělen. Pokud identifikátor URI začíná na "https:", používá se SSL; Pokud identifikátor URI začíná řetězcem "http:", je použito nešifrované připojení.  
  
 Chcete-li použít protokol SSL s protokol FTP (File Transfer Protocol) (FTP), nastavte <xref:System.Net.FtpWebRequest.EnableSsl> před voláním vlastnost na hodnotu true <xref:System.Net.FtpWebRequest.GetResponse> . Podobně pokud chcete použít protokol SSL s protokolem SMTP (Simple Mail Transport Protocol), nastavte <xref:System.Net.Mail.SmtpClient.EnableSsl> před odesláním e-mailu vlastnost na hodnotu true.  
  
 <xref:System.Net.Security.SslStream>Třída poskytuje abstrakci založenou na datovém proudu pro SSL a nabízí mnoho způsobů konfigurace metody handshake protokolu SSL.  
  
## <a name="example"></a>Příklad  
  
### <a name="code"></a>Kód  
  
```vb  
Dim MyURI As String = "https://www.contoso.com/"  
Dim Wreq As WebRequest = WebRequest.Create(MyURI)  
  
Dim serverUri As String = "ftp://ftp.contoso.com/file.txt"  
Dim request As FtpWebRequest = CType(WebRequest.Create(serverUri), FtpWebRequest)  
request.Method = WebRequestMethods.Ftp.DeleteFile  
request.EnableSsl = True  
Dim response As FtpWebResponse = CType(request.GetResponse(), FtpWebResponse)  
```  
  
```csharp  
String MyURI = "https://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
  
String serverUri = "ftp://ftp.contoso.com/file.txt"  
FtpWebRequest request = (FtpWebRequest)WebRequest.Create(serverUri);  
request.EnableSsl = true;  
request.Method = WebRequestMethods.Ftp.DeleteFile;  
FtpWebResponse response = (FtpWebResponse)request.GetResponse();  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazuje na obor názvů **System.NET** .  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení v síťovém programování](security-in-network-programming.md)
- [Síťové programování v rozhraní .NET Framework](index.md)
- [Výběr a ověření certifikátu](certificate-selection-and-validation.md)
