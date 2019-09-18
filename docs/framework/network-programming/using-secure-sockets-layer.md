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
# <a name="using-secure-sockets-layer"></a><span data-ttu-id="f8728-102">Použití protokolu SSL (Secure Sockets Layer)</span><span class="sxs-lookup"><span data-stu-id="f8728-102">Using Secure Sockets Layer</span></span>
<span data-ttu-id="f8728-103"><xref:System.Net> Třídy používají SSL (Secure Sockets Layer) (SSL) k šifrování připojení pro několik síťových protokolů.</span><span class="sxs-lookup"><span data-stu-id="f8728-103">The <xref:System.Net> classes use the Secure Sockets Layer (SSL) to encrypt the connection for several network protocols.</span></span>  
  
 <span data-ttu-id="f8728-104">U připojení <xref:System.Net.WebRequest> http třídy a <xref:System.Net.WebResponse> používají protokol SSL ke komunikaci s webovými hostiteli, kteří podporují protokol SSL.</span><span class="sxs-lookup"><span data-stu-id="f8728-104">For http connections, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes use SSL to communicate with web hosts that support SSL.</span></span> <span data-ttu-id="f8728-105">Rozhodnutí o použití protokolu SSL <xref:System.Net.WebRequest> provádí třída na základě identifikátoru URI, který je přidělen.</span><span class="sxs-lookup"><span data-stu-id="f8728-105">The decision to use SSL is made by the <xref:System.Net.WebRequest> class, based on the URI it is given.</span></span> <span data-ttu-id="f8728-106">Pokud identifikátor URI začíná na "https:", používá se SSL; Pokud identifikátor URI začíná řetězcem "http:", je použito nešifrované připojení.</span><span class="sxs-lookup"><span data-stu-id="f8728-106">If the URI begins with "https:", SSL is used; if the URI begins with "http:", an unencrypted connection is used.</span></span>  
  
 <span data-ttu-id="f8728-107">Chcete-li použít protokol SSL s protokol FTP (File Transfer Protocol) (FTP) <xref:System.Net.FtpWebRequest.EnableSsl> , nastavte před voláním <xref:System.Net.FtpWebRequest.GetResponse>vlastnost na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="f8728-107">To use SSL with File Transfer Protocol (FTP), set the <xref:System.Net.FtpWebRequest.EnableSsl> property to true prior to calling <xref:System.Net.FtpWebRequest.GetResponse>.</span></span> <span data-ttu-id="f8728-108">Podobně pokud chcete použít protokol SSL s protokolem SMTP (Simple Mail Transport Protocol) <xref:System.Net.Mail.SmtpClient.EnableSsl> , nastavte před odesláním e-mailu vlastnost na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="f8728-108">Similarly, to use SSL with Simple Mail Transport Protocol (SMTP), set the <xref:System.Net.Mail.SmtpClient.EnableSsl> property to true prior to sending the email.</span></span>  
  
 <span data-ttu-id="f8728-109"><xref:System.Net.Security.SslStream> Třída poskytuje abstrakci založenou na datovém proudu pro SSL a nabízí mnoho způsobů konfigurace metody handshake protokolu SSL.</span><span class="sxs-lookup"><span data-stu-id="f8728-109">The <xref:System.Net.Security.SslStream> class provides a stream-based abstraction for SSL, and offers many ways to configure the SSL handshake.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8728-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8728-110">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="f8728-111">Kód</span><span class="sxs-lookup"><span data-stu-id="f8728-111">Code</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="f8728-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f8728-112">Compiling the Code</span></span>  
 <span data-ttu-id="f8728-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="f8728-113">This example requires:</span></span>  
  
- <span data-ttu-id="f8728-114">Odkazuje na obor názvů **System.NET** .</span><span class="sxs-lookup"><span data-stu-id="f8728-114">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8728-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8728-115">See also</span></span>

- [<span data-ttu-id="f8728-116">Zabezpečení v síťovém programování</span><span class="sxs-lookup"><span data-stu-id="f8728-116">Security in Network Programming</span></span>](security-in-network-programming.md)
- [<span data-ttu-id="f8728-117">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f8728-117">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="f8728-118">Výběr a ověření certifikátu</span><span class="sxs-lookup"><span data-stu-id="f8728-118">Certificate Selection and Validation</span></span>](certificate-selection-and-validation.md)
