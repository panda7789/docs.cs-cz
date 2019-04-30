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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796770"
---
# <a name="using-secure-sockets-layer"></a><span data-ttu-id="57a80-102">Použití protokolu SSL (Secure Sockets Layer)</span><span class="sxs-lookup"><span data-stu-id="57a80-102">Using Secure Sockets Layer</span></span>
<span data-ttu-id="57a80-103"><xref:System.Net> Třídy použít k šifrování připojení pro několik síťových protokolů vrstvy SSL (Secure Sockets).</span><span class="sxs-lookup"><span data-stu-id="57a80-103">The <xref:System.Net> classes use the Secure Sockets Layer (SSL) to encrypt the connection for several network protocols.</span></span>  
  
 <span data-ttu-id="57a80-104">Pro připojení prostřednictvím protokolu http <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy používat protokol SSL ke komunikaci s weboví hostitelé, které podporují protokol SSL.</span><span class="sxs-lookup"><span data-stu-id="57a80-104">For http connections, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes use SSL to communicate with web hosts that support SSL.</span></span> <span data-ttu-id="57a80-105">Provádí rozhodnutí pro použití protokolu SSL <xref:System.Net.WebRequest> třídy založené na identifikátor URI se klíči přiřadí.</span><span class="sxs-lookup"><span data-stu-id="57a80-105">The decision to use SSL is made by the <xref:System.Net.WebRequest> class, based on the URI it is given.</span></span> <span data-ttu-id="57a80-106">Pokud identifikátor URI začíná řetězcem "https:", se používá protokol SSL; Pokud identifikátor URI začíná řetězcem "http:", se používá s nešifrovaným připojením.</span><span class="sxs-lookup"><span data-stu-id="57a80-106">If the URI begins with "https:", SSL is used; if the URI begins with "http:", an unencrypted connection is used.</span></span>  
  
 <span data-ttu-id="57a80-107">Chcete-li používat protokol SSL pomocí protokolu FTP (File Transfer), nastavte <xref:System.Net.FtpWebRequest.EnableSsl> vlastnost na hodnotu true před voláním <xref:System.Net.FtpWebRequest.GetResponse>.</span><span class="sxs-lookup"><span data-stu-id="57a80-107">To use SSL with File Transfer Protocol (FTP), set the <xref:System.Net.FtpWebRequest.EnableSsl> property to true prior to calling <xref:System.Net.FtpWebRequest.GetResponse>.</span></span> <span data-ttu-id="57a80-108">Podobně pro použití protokolu SSL s přenosu protokolu SMTP (Simple Mail), nastavte <xref:System.Net.Mail.SmtpClient.EnableSsl> vlastnost na hodnotu true, před odesláním e-mailu.</span><span class="sxs-lookup"><span data-stu-id="57a80-108">Similarly, to use SSL with Simple Mail Transport Protocol (SMTP), set the <xref:System.Net.Mail.SmtpClient.EnableSsl> property to true prior to sending the email.</span></span>  
  
 <span data-ttu-id="57a80-109"><xref:System.Net.Security.SslStream> Třída poskytuje abstrakce založené na datový proud pro protokol SSL a nabízí mnoho způsobů, jak konfigurovat metodu handshake SSL.</span><span class="sxs-lookup"><span data-stu-id="57a80-109">The <xref:System.Net.Security.SslStream> class provides a stream-based abstraction for SSL, and offers many ways to configure the SSL handshake.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57a80-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="57a80-110">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="57a80-111">Kód</span><span class="sxs-lookup"><span data-stu-id="57a80-111">Code</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="57a80-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="57a80-112">Compiling the Code</span></span>  
 <span data-ttu-id="57a80-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="57a80-113">This example requires:</span></span>  
  
- <span data-ttu-id="57a80-114">Odkazy **System.Net** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="57a80-114">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57a80-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57a80-115">See also</span></span>

- [<span data-ttu-id="57a80-116">Zabezpečení v síťovém programování</span><span class="sxs-lookup"><span data-stu-id="57a80-116">Security in Network Programming</span></span>](../../../docs/framework/network-programming/security-in-network-programming.md)
- [<span data-ttu-id="57a80-117">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="57a80-117">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)
- [<span data-ttu-id="57a80-118">Výběr a ověření certifikátu</span><span class="sxs-lookup"><span data-stu-id="57a80-118">Certificate Selection and Validation</span></span>](../../../docs/framework/network-programming/certificate-selection-and-validation.md)
