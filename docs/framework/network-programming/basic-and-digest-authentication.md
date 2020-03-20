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
ms.openlocfilehash: 9a1ad701e1e8f4ee9966ebd56922c29e2bae7a03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048904"
---
# <a name="basic-and-digest-authentication"></a><span data-ttu-id="4be52-102">Základní ověřování a ověřování hodnotou hash</span><span class="sxs-lookup"><span data-stu-id="4be52-102">Basic and Digest Authentication</span></span>
<span data-ttu-id="4be52-103">Implementace <xref:System.Net> základního ověřování a ověřování algoritmem Digest je v souladu s protokolem RFC2617 – Ověřování HTTP: Základní a ověřování algoritmem Digest (k dispozici na webu [konsorcia World Wide Web Consortium).](https://www.w3.org)</span><span class="sxs-lookup"><span data-stu-id="4be52-103">The <xref:System.Net> implementation of basic and digest authentication complies with RFC2617 – HTTP Authentication: Basic and Digest Authentication (available on the [World Wide Web Consortium's](https://www.w3.org) website).</span></span>  
  
 <span data-ttu-id="4be52-104">Chcete-li použít základní a digest ověřování, aplikace musí <xref:System.Net.WebRequest.Credentials%2A> poskytnout <xref:System.Net.WebRequest> uživatelské jméno a heslo ve vlastnosti objektu, který používá k vyžádání dat z Internetu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="4be52-104">To use basic and digest authentication, an application must provide a user name and password in the <xref:System.Net.WebRequest.Credentials%2A> property of the <xref:System.Net.WebRequest> object that it uses to request data from the Internet, as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="4be52-105">Data odeslaná pomocí základního ověřování a ověřování algoritmem Digest nejsou šifrována, takže je může vidět protivník.</span><span class="sxs-lookup"><span data-stu-id="4be52-105">Data sent with Basic and Digest Authentication is not encrypted, so the data can be seen by an adversary.</span></span> <span data-ttu-id="4be52-106">Kromě toho základní ověřování pověření (uživatelské jméno a heslo) jsou odesílány v vymazat a mohou být zachyceny.</span><span class="sxs-lookup"><span data-stu-id="4be52-106">Additionally, Basic Authentication credentials (user name and password) are sent in the clear and can be intercepted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4be52-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="4be52-107">See also</span></span>

- [<span data-ttu-id="4be52-108">Ověřování NTLM a Kerberos</span><span class="sxs-lookup"><span data-stu-id="4be52-108">NTLM and Kerberos Authentication</span></span>](ntlm-and-kerberos-authentication.md)
- [<span data-ttu-id="4be52-109">Ověřování v internetu</span><span class="sxs-lookup"><span data-stu-id="4be52-109">Internet Authentication</span></span>](internet-authentication.md)
