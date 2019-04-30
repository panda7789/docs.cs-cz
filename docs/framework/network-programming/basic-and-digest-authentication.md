---
title: Základní ověřování a ověřování hodnotou hash
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [.NET Framework], classes
- Basic authentication
- authentication [.NET Framework], basic
- client authentication, basic
- user authentication, basic
- authentication [.NET Framework], digest
- receiving data, authentication
- client authentication, digest
- Internet, authentication
- digest authentication
- sending data, authentication
- network resources, authentication
- user authentication, digest
ms.assetid: 8cce2742-8d52-4643-9dd2-64ddf38aa878
ms.openlocfilehash: 4f70d2aef3bb064a3df9db9c87671040776332a7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61866896"
---
# <a name="basic-and-digest-authentication"></a><span data-ttu-id="e6d8b-102">Základní ověřování a ověřování hodnotou hash</span><span class="sxs-lookup"><span data-stu-id="e6d8b-102">Basic and Digest Authentication</span></span>
<span data-ttu-id="e6d8b-103"><xref:System.Net> Provádění basic a ověřování algoritmem digest splňuje RFC2617 – ověřování pomocí protokolu HTTP: Základní a ověřování algoritmem Digest (k dispozici na [World Wide Web Consortium](https://www.w3.org) webu).</span><span class="sxs-lookup"><span data-stu-id="e6d8b-103">The <xref:System.Net> implementation of basic and digest authentication complies with RFC2617 – HTTP Authentication: Basic and Digest Authentication (available on the [World Wide Web Consortium's](https://www.w3.org) website).</span></span>  
  
 <span data-ttu-id="e6d8b-104">Použijte základní a ověřování algoritmem digest, aplikace musíte zadat uživatelské jméno a heslo <xref:System.Net.WebRequest.Credentials%2A> vlastnost <xref:System.Net.WebRequest> objekt, který se použije k vyžádání dat z Internetu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e6d8b-104">To use basic and digest authentication, an application must provide a user name and password in the <xref:System.Net.WebRequest.Credentials%2A> property of the <xref:System.Net.WebRequest> object that it uses to request data from the Internet, as shown in the following example.</span></span>  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = New NetworkCredential(UserName, SecurelyStoredPassword)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create(MyURI);  
WReq.Credentials = new NetworkCredential(UserName, SecurelyStoredPassword);  
```  
  
> [!CAUTION]
>  <span data-ttu-id="e6d8b-105">Data odesílaná s Basic a ověřování algoritmem Digest se nešifrují, takže data můžete vidět nežádoucí osoba.</span><span class="sxs-lookup"><span data-stu-id="e6d8b-105">Data sent with Basic and Digest Authentication is not encrypted, so the data can be seen by an adversary.</span></span> <span data-ttu-id="e6d8b-106">Kromě toho pověření základního ověřování (uživatelské jméno a heslo) se odesílají v nešifrované podobě a může být zachycena.</span><span class="sxs-lookup"><span data-stu-id="e6d8b-106">Additionally, Basic Authentication credentials (user name and password) are sent in the clear and can be intercepted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6d8b-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6d8b-107">See also</span></span>

- [<span data-ttu-id="e6d8b-108">Ověřování NTLM a Kerberos</span><span class="sxs-lookup"><span data-stu-id="e6d8b-108">NTLM and Kerberos Authentication</span></span>](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)
- [<span data-ttu-id="e6d8b-109">Ověřování v internetu</span><span class="sxs-lookup"><span data-stu-id="e6d8b-109">Internet Authentication</span></span>](../../../docs/framework/network-programming/internet-authentication.md)
