---
title: Použití protokolu SSL (Secure Sockets Layer)
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
ms.openlocfilehash: ef2abc7574aea1b4f77ff93545ad84678c66ce48
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71046906"
---
# <a name="using-secure-sockets-layer"></a>Použití protokolu SSL (Secure Sockets Layer)
<xref:System.Net> Třídy používají SSL (Secure Sockets Layer) (SSL) k šifrování připojení pro několik síťových protokolů.  
  
 U připojení <xref:System.Net.WebRequest> http třídy a <xref:System.Net.WebResponse> používají protokol SSL ke komunikaci s webovými hostiteli, kteří podporují protokol SSL. Rozhodnutí o použití protokolu SSL <xref:System.Net.WebRequest> provádí třída na základě identifikátoru URI, který je přidělen. Pokud identifikátor URI začíná na "https:", používá se SSL; Pokud identifikátor URI začíná řetězcem "http:", je použito nešifrované připojení.  
  
 Chcete-li použít protokol SSL s protokol FTP (File Transfer Protocol) (FTP) <xref:System.Net.FtpWebRequest.EnableSsl> , nastavte před voláním <xref:System.Net.FtpWebRequest.GetResponse>vlastnost na hodnotu true. Podobně pokud chcete použít protokol SSL s protokolem SMTP (Simple Mail Transport Protocol) <xref:System.Net.Mail.SmtpClient.EnableSsl> , nastavte před odesláním e-mailu vlastnost na hodnotu true.  
  
 <xref:System.Net.Security.SslStream> Třída poskytuje abstrakci založenou na datovém proudu pro SSL a nabízí mnoho způsobů konfigurace metody handshake protokolu SSL.  
  
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
