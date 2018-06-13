---
title: Pomocí zabezpečené sokety vrstvy
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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2baedaa445f81e3e204f7414c5142232755581ed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33396243"
---
# <a name="using-secure-sockets-layer"></a><span data-ttu-id="e0f52-102">Pomocí zabezpečené sokety vrstvy</span><span class="sxs-lookup"><span data-stu-id="e0f52-102">Using Secure Sockets Layer</span></span>
<span data-ttu-id="e0f52-103"><xref:System.Net> Třídy použít Secure Sockets Layer (SSL) k šifrování připojení několik síťových protokolů.</span><span class="sxs-lookup"><span data-stu-id="e0f52-103">The <xref:System.Net> classes use the Secure Sockets Layer (SSL) to encrypt the connection for several network protocols.</span></span>  
  
 <span data-ttu-id="e0f52-104">Pro připojení protokolu http <xref:System.Net.WebRequest> a <xref:System.Net.WebResponse> třídy používat protokol SSL pro komunikaci s weboví hostitelé, které podporují protokol SSL.</span><span class="sxs-lookup"><span data-stu-id="e0f52-104">For http connections, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes use SSL to communicate with web hosts that support SSL.</span></span> <span data-ttu-id="e0f52-105">Rozhodnutí ohledně používání protokolu SSL je provedené <xref:System.Net.WebRequest> třídy, na základě v identifikátoru URI je zadána.</span><span class="sxs-lookup"><span data-stu-id="e0f52-105">The decision to use SSL is made by the <xref:System.Net.WebRequest> class, based on the URI it is given.</span></span> <span data-ttu-id="e0f52-106">Pokud identifikátor URI začíná řetězcem "https:", se používá protokol SSL; Pokud identifikátor URI začíná řetězcem "http:", je použít nešifrované připojení.</span><span class="sxs-lookup"><span data-stu-id="e0f52-106">If the URI begins with "https:", SSL is used; if the URI begins with "http:", an unencrypted connection is used.</span></span>  
  
 <span data-ttu-id="e0f52-107">Chcete-li používat protokol SSL pomocí protokolu FTP (File Transfer), nastavte <xref:System.Net.FtpWebRequest.EnableSsl> vlastnost na hodnotu true před voláním <xref:System.Net.FtpWebRequest.GetResponse>.</span><span class="sxs-lookup"><span data-stu-id="e0f52-107">To use SSL with File Transfer Protocol (FTP), set the <xref:System.Net.FtpWebRequest.EnableSsl> property to true prior to calling <xref:System.Net.FtpWebRequest.GetResponse>.</span></span> <span data-ttu-id="e0f52-108">Podobně, chcete-li používat protokol SSL s transportní protokol SMTP (Simple Mail), nastavte <xref:System.Net.Mail.SmtpClient.EnableSsl> vlastnost na hodnotu true před odesláním e-mailu.</span><span class="sxs-lookup"><span data-stu-id="e0f52-108">Similarly, to use SSL with Simple Mail Transport Protocol (SMTP), set the <xref:System.Net.Mail.SmtpClient.EnableSsl> property to true prior to sending the email.</span></span>  
  
 <span data-ttu-id="e0f52-109"><xref:System.Net.Security.SslStream> Třída poskytuje abstrakci se na základě datového proudu pro protokol SSL a nabízí mnoho způsobů, jak nakonfigurovat metody handshake SSL.</span><span class="sxs-lookup"><span data-stu-id="e0f52-109">The <xref:System.Net.Security.SslStream> class provides a stream-based abstraction for SSL, and offers many ways to configure the SSL handshake.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0f52-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0f52-110">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="e0f52-111">Kód</span><span class="sxs-lookup"><span data-stu-id="e0f52-111">Code</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="e0f52-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e0f52-112">Compiling the Code</span></span>  
 <span data-ttu-id="e0f52-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e0f52-113">This example requires:</span></span>  
  
-   <span data-ttu-id="e0f52-114">Odkazuje na **System.Net** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e0f52-114">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0f52-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0f52-115">See Also</span></span>  
 [<span data-ttu-id="e0f52-116">Zabezpečení v síťovém programování</span><span class="sxs-lookup"><span data-stu-id="e0f52-116">Security in Network Programming</span></span>](../../../docs/framework/network-programming/security-in-network-programming.md)  
 [<span data-ttu-id="e0f52-117">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="e0f52-117">Network Programming in the .NET Framework</span></span>](../../../docs/framework/network-programming/index.md)  
 [<span data-ttu-id="e0f52-118">Výběr a ověření certifikátu</span><span class="sxs-lookup"><span data-stu-id="e0f52-118">Certificate Selection and Validation</span></span>](../../../docs/framework/network-programming/certificate-selection-and-validation.md)
