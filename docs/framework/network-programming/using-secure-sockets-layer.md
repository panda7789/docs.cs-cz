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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71046906"
---
# <a name="using-secure-sockets-layer"></a>Použití protokolu SSL (Secure Sockets Layer)
Třídy <xref:System.Net> používají ssl (Secure Sockets L) k šifrování připojení pro několik síťových protokolů.  
  
 Pro připojení http <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> a třídy používají SSL ke komunikaci s webovými hostiteli, které podporují protokol SSL. Rozhodnutí o použití SSL je <xref:System.Net.WebRequest> provedeno třídou na základě identifikátoru URI, který je dán. Pokud identifikátor URI začíná na "https:", použije se protokol SSL. Pokud identifikátor URI začíná na "http:", použije se nešifrované připojení.  
  
 Chcete-li použít protokol SSL s protokolem FTP (File Transfer Protocol), nastavte <xref:System.Net.FtpWebRequest.EnableSsl> vlastnost před voláním <xref:System.Net.FtpWebRequest.GetResponse>na hodnotu true . Podobně chcete-li použít protokol SSL s protokolem SMTP (SMTP) nastavte <xref:System.Net.Mail.SmtpClient.EnableSsl> vlastnost na hodnotu true před odesláním e-mailu.  
  
 Třída <xref:System.Net.Security.SslStream> poskytuje abstrakce založené na datovém proudu pro SSL a nabízí mnoho způsobů konfigurace protokolu SSL handshake.  
  
## <a name="example"></a>Příklad  
  
### <a name="code"></a>kód  
  
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
  
- Odkazy na **System.Net** oboru názvů.  
  
## <a name="see-also"></a>Viz také

- [Zabezpečení v síťovém programování](security-in-network-programming.md)
- [Síťové programování v rozhraní .NET Framework](index.md)
- [Výběr a ověření certifikátu](certificate-selection-and-validation.md)
