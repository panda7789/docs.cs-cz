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
ms.openlocfilehash: a0af2fa8bbe2efb2dc4fb3d1177c4950dcec87cf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59135798"
---
# <a name="using-secure-sockets-layer"></a>Použití protokolu SSL (Secure Sockets Layer)
<xref:System.Net> Třídy použít k šifrování připojení pro několik síťových protokolů vrstvy SSL (Secure Sockets).  
  
 Pro připojení prostřednictvím protokolu http <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy používat protokol SSL ke komunikaci s weboví hostitelé, které podporují protokol SSL. Provádí rozhodnutí pro použití protokolu SSL <xref:System.Net.WebRequest> třídy založené na identifikátor URI se klíči přiřadí. Pokud identifikátor URI začíná řetězcem "https:", se používá protokol SSL; Pokud identifikátor URI začíná řetězcem "http:", se používá s nešifrovaným připojením.  
  
 Chcete-li používat protokol SSL pomocí protokolu FTP (File Transfer), nastavte <xref:System.Net.FtpWebRequest.EnableSsl> vlastnost na hodnotu true před voláním <xref:System.Net.FtpWebRequest.GetResponse>. Podobně pro použití protokolu SSL s přenosu protokolu SMTP (Simple Mail), nastavte <xref:System.Net.Mail.SmtpClient.EnableSsl> vlastnost na hodnotu true, před odesláním e-mailu.  
  
 <xref:System.Net.Security.SslStream> Třída poskytuje abstrakce založené na datový proud pro protokol SSL a nabízí mnoho způsobů, jak konfigurovat metodu handshake SSL.  
  
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
  
-   Odkazy **System.Net** oboru názvů.  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení v síťovém programování](../../../docs/framework/network-programming/security-in-network-programming.md)
- [Síťové programování v rozhraní .NET Framework](../../../docs/framework/network-programming/index.md)
- [Výběr a ověření certifikátu](../../../docs/framework/network-programming/certificate-selection-and-validation.md)
