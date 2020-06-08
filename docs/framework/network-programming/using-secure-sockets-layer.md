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
# <a name="using-secure-sockets-layer"></a><span data-ttu-id="ae854-103">Použití protokolu SSL (Secure Sockets Layer)</span><span class="sxs-lookup"><span data-stu-id="ae854-103">Using Secure Sockets Layer</span></span>
<span data-ttu-id="ae854-104"><xref:System.Net>Třídy používají SSL (Secure Sockets Layer) (SSL) k šifrování připojení pro několik síťových protokolů.</span><span class="sxs-lookup"><span data-stu-id="ae854-104">The <xref:System.Net> classes use the Secure Sockets Layer (SSL) to encrypt the connection for several network protocols.</span></span>  
  
 <span data-ttu-id="ae854-105">U připojení http <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> třídy a používají protokol SSL ke komunikaci s webovými hostiteli, kteří podporují protokol SSL.</span><span class="sxs-lookup"><span data-stu-id="ae854-105">For http connections, the <xref:System.Net.WebRequest> and <xref:System.Net.WebResponse> classes use SSL to communicate with web hosts that support SSL.</span></span> <span data-ttu-id="ae854-106">Rozhodnutí o použití protokolu SSL provádí <xref:System.Net.WebRequest> Třída na základě identifikátoru URI, který je přidělen.</span><span class="sxs-lookup"><span data-stu-id="ae854-106">The decision to use SSL is made by the <xref:System.Net.WebRequest> class, based on the URI it is given.</span></span> <span data-ttu-id="ae854-107">Pokud identifikátor URI začíná na "https:", používá se SSL; Pokud identifikátor URI začíná řetězcem "http:", je použito nešifrované připojení.</span><span class="sxs-lookup"><span data-stu-id="ae854-107">If the URI begins with "https:", SSL is used; if the URI begins with "http:", an unencrypted connection is used.</span></span>  
  
 <span data-ttu-id="ae854-108">Chcete-li použít protokol SSL s protokol FTP (File Transfer Protocol) (FTP), nastavte <xref:System.Net.FtpWebRequest.EnableSsl> před voláním vlastnost na hodnotu true <xref:System.Net.FtpWebRequest.GetResponse> .</span><span class="sxs-lookup"><span data-stu-id="ae854-108">To use SSL with File Transfer Protocol (FTP), set the <xref:System.Net.FtpWebRequest.EnableSsl> property to true prior to calling <xref:System.Net.FtpWebRequest.GetResponse>.</span></span> <span data-ttu-id="ae854-109">Podobně pokud chcete použít protokol SSL s protokolem SMTP (Simple Mail Transport Protocol), nastavte <xref:System.Net.Mail.SmtpClient.EnableSsl> před odesláním e-mailu vlastnost na hodnotu true.</span><span class="sxs-lookup"><span data-stu-id="ae854-109">Similarly, to use SSL with Simple Mail Transport Protocol (SMTP), set the <xref:System.Net.Mail.SmtpClient.EnableSsl> property to true prior to sending the email.</span></span>  
  
 <span data-ttu-id="ae854-110"><xref:System.Net.Security.SslStream>Třída poskytuje abstrakci založenou na datovém proudu pro SSL a nabízí mnoho způsobů konfigurace metody handshake protokolu SSL.</span><span class="sxs-lookup"><span data-stu-id="ae854-110">The <xref:System.Net.Security.SslStream> class provides a stream-based abstraction for SSL, and offers many ways to configure the SSL handshake.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae854-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae854-111">Example</span></span>  
  
### <a name="code"></a><span data-ttu-id="ae854-112">Kód</span><span class="sxs-lookup"><span data-stu-id="ae854-112">Code</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="ae854-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ae854-113">Compiling the Code</span></span>  
 <span data-ttu-id="ae854-114">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="ae854-114">This example requires:</span></span>  
  
- <span data-ttu-id="ae854-115">Odkazuje na obor názvů **System.NET** .</span><span class="sxs-lookup"><span data-stu-id="ae854-115">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae854-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae854-116">See also</span></span>

- [<span data-ttu-id="ae854-117">Zabezpečení v síťovém programování</span><span class="sxs-lookup"><span data-stu-id="ae854-117">Security in Network Programming</span></span>](security-in-network-programming.md)
- [<span data-ttu-id="ae854-118">Síťové programování v rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ae854-118">Network Programming in the .NET Framework</span></span>](index.md)
- [<span data-ttu-id="ae854-119">Výběr a ověření certifikátu</span><span class="sxs-lookup"><span data-stu-id="ae854-119">Certificate Selection and Validation</span></span>](certificate-selection-and-validation.md)
