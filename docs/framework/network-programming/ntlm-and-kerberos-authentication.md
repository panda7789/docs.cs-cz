---
title: Ověřování NTLM a Kerberos
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- authentication [.NET Framework], NTLM
- authentication [.NET Framework], Kerberos
- user authentication, Kerberos
- user authentication, NTLM
- Kerberos authentication
- receiving data, authentication
- NTLM authentication
- Internet, authentication
- client authentication, Kerberos
- sending data, authentication
- network resources, authentication
- classes [.NET Framework], authentication
- client authentication, NTLM
ms.assetid: 9ef65560-f596-4469-bcce-f4d5407b55cd
ms.openlocfilehash: 254ffea79612c10f147984dda37d0117edbf9e3e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190291"
---
# <a name="ntlm-and-kerberos-authentication"></a><span data-ttu-id="553c1-102">Ověřování NTLM a Kerberos</span><span class="sxs-lookup"><span data-stu-id="553c1-102">NTLM and Kerberos Authentication</span></span>
<span data-ttu-id="553c1-103">Výchozí ověřování NTLM a Kerberos používat přihlašovací údaje uživatelů Microsoft Windows NT přidružené volající aplikace k ověřování se serverem.</span><span class="sxs-lookup"><span data-stu-id="553c1-103">Default NTLM authentication and Kerberos authentication use the Microsoft Windows NT user credentials associated with the calling application to attempt authentication with the server.</span></span> <span data-ttu-id="553c1-104">Při použití ověřování NTLM jiné než výchozí, aplikace nastaví typ ověřování NTLM a použije <xref:System.Net.NetworkCredential> objekt k předávání uživatelské jméno, heslo a doménu na hostitele, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="553c1-104">When using non-default NTLM authentication, the application sets the authentication type to NTLM and uses a <xref:System.Net.NetworkCredential> object to pass the user name, password, and domain to the host, as shown in the following example.</span></span>  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = _  
    New NetworkCredential(UserName, SecurelyStoredPassword, Domain)  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials =   
    new NetworkCredential(UserName, SecurelyStoredPassword, Domain);  
```  
  
 <span data-ttu-id="553c1-105">Aplikace, které potřebují k připojení k Internetu služby pomocí přihlašovacích údajů uživatele, aplikace lze provést pomocí výchozích přihlašovacích údajů uživatele, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="553c1-105">Applications that need to connect to Internet services using the credentials of the application user can do so with the user's default credentials, as shown in the following example.</span></span>  
  
```vb  
Dim MyURI As String = "http://www.contoso.com/"  
Dim WReq As WebRequest = WebRequest.Create(MyURI)  
WReq.Credentials = CredentialCache.DefaultCredentials  
```  
  
```csharp  
String MyURI = "http://www.contoso.com/";  
WebRequest WReq = WebRequest.Create (MyURI);  
WReq.Credentials = CredentialCache.DefaultCredentials;  
```  
  
 <span data-ttu-id="553c1-106">Modul negotiate ověřování určuje, zda vzdálený server používá ověřování NTLM nebo Kerberos a odešle odpovídající odpověď.</span><span class="sxs-lookup"><span data-stu-id="553c1-106">The negotiate authentication module determines whether the remote server is using NTLM or Kerberos authentication, and sends the appropriate response.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="553c1-107">Ověřování protokolem NTLM, nefunguje přes proxy server.</span><span class="sxs-lookup"><span data-stu-id="553c1-107">NTLM authentication does not work through a proxy server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="553c1-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="553c1-108">See Also</span></span>  
 [<span data-ttu-id="553c1-109">Základní ověřování a ověřování algoritmem Digest</span><span class="sxs-lookup"><span data-stu-id="553c1-109">Basic and Digest Authentication</span></span>](../../../docs/framework/network-programming/basic-and-digest-authentication.md)  
 [<span data-ttu-id="553c1-110">Ověřování v internetu</span><span class="sxs-lookup"><span data-stu-id="553c1-110">Internet Authentication</span></span>](../../../docs/framework/network-programming/internet-authentication.md)
