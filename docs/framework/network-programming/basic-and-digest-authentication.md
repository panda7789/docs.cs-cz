---
title: Základní ověřování a ověřování hodnotou hash
description: Naučte se používat základní ověřování a ověřování algoritmem Digest, kde aplikace poskytuje uživatelské jméno a heslo v objektu WebRequest, který používá k vyžádání dat.
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
ms.openlocfilehash: 7772430b508b52a63d716550b69018385418c132
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502692"
---
# <a name="basic-and-digest-authentication"></a><span data-ttu-id="33db4-103">Základní ověřování a ověřování hodnotou hash</span><span class="sxs-lookup"><span data-stu-id="33db4-103">Basic and Digest Authentication</span></span>
<span data-ttu-id="33db4-104"><xref:System.Net>Implementace základního ověřování a ověřování algoritmem Digest vyhovuje RFC2617 – ověřování http: základní a ověřování hodnotou hash (k dispozici na webu [konsorcium World Wide Web](https://www.w3.org) ).</span><span class="sxs-lookup"><span data-stu-id="33db4-104">The <xref:System.Net> implementation of basic and digest authentication complies with RFC2617 – HTTP Authentication: Basic and Digest Authentication (available on the [World Wide Web Consortium's](https://www.w3.org) website).</span></span>  
  
 <span data-ttu-id="33db4-105">Chcete-li použít základní ověřování a ověřování algoritmem Digest, aplikace musí zadat uživatelské jméno a heslo ve <xref:System.Net.WebRequest.Credentials%2A> vlastnosti <xref:System.Net.WebRequest> objektu, který používá k vyžádání dat z Internetu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="33db4-105">To use basic and digest authentication, an application must provide a user name and password in the <xref:System.Net.WebRequest.Credentials%2A> property of the <xref:System.Net.WebRequest> object that it uses to request data from the Internet, as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="33db4-106">Data odesílaná pomocí základního ověřování a ověřování algoritmem Digest nejsou šifrována, takže je lze zobrazit pomocí nežádoucí osoba.</span><span class="sxs-lookup"><span data-stu-id="33db4-106">Data sent with Basic and Digest Authentication is not encrypted, so the data can be seen by an adversary.</span></span> <span data-ttu-id="33db4-107">Navíc se přihlašovací údaje základního ověřování (uživatelské jméno a heslo) odesílají jasně a je možné je zachytit.</span><span class="sxs-lookup"><span data-stu-id="33db4-107">Additionally, Basic Authentication credentials (user name and password) are sent in the clear and can be intercepted.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33db4-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="33db4-108">See also</span></span>

- [<span data-ttu-id="33db4-109">Ověřování NTLM a Kerberos</span><span class="sxs-lookup"><span data-stu-id="33db4-109">NTLM and Kerberos Authentication</span></span>](ntlm-and-kerberos-authentication.md)
- [<span data-ttu-id="33db4-110">Ověřování v internetu</span><span class="sxs-lookup"><span data-stu-id="33db4-110">Internet Authentication</span></span>](internet-authentication.md)
