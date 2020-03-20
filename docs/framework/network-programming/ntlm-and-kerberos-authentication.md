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
ms.openlocfilehash: 372101763bdd84b454e6e2db3ec6cf0ebdf3f991
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180704"
---
# <a name="ntlm-and-kerberos-authentication"></a><span data-ttu-id="166e2-102">Ověřování NTLM a Kerberos</span><span class="sxs-lookup"><span data-stu-id="166e2-102">NTLM and Kerberos Authentication</span></span>
<span data-ttu-id="166e2-103">Výchozí ověřování NTLM a ověřování protokolem Kerberos používají k pokusu o ověření se serverem pověření uživatele systému Microsoft Windows NT přidružená k volající aplikaci.</span><span class="sxs-lookup"><span data-stu-id="166e2-103">Default NTLM authentication and Kerberos authentication use the Microsoft Windows NT user credentials associated with the calling application to attempt authentication with the server.</span></span> <span data-ttu-id="166e2-104">Při použití jiného než výchozího ověřování NTLM nastaví aplikace <xref:System.Net.NetworkCredential> typ ověřování na NTLM a použije objekt k předání uživatelského jména, hesla a domény hostiteli, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="166e2-104">When using non-default NTLM authentication, the application sets the authentication type to NTLM and uses a <xref:System.Net.NetworkCredential> object to pass the user name, password, and domain to the host, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="166e2-105">Aplikace, které se potřebují připojit k internetovým službám pomocí pověření uživatele aplikace, tak mohou učinit s výchozími pověřeními uživatele, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="166e2-105">Applications that need to connect to Internet services using the credentials of the application user can do so with the user's default credentials, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="166e2-106">Modul ověřování vyjednávání určuje, zda vzdálený server používá ověřování NTLM nebo Kerberos, a odešle příslušnou odpověď.</span><span class="sxs-lookup"><span data-stu-id="166e2-106">The negotiate authentication module determines whether the remote server is using NTLM or Kerberos authentication, and sends the appropriate response.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="166e2-107">Ověřování NTLM nefunguje prostřednictvím serveru proxy.</span><span class="sxs-lookup"><span data-stu-id="166e2-107">NTLM authentication does not work through a proxy server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="166e2-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="166e2-108">See also</span></span>

- [<span data-ttu-id="166e2-109">Základní a digest ověřování</span><span class="sxs-lookup"><span data-stu-id="166e2-109">Basic and Digest Authentication</span></span>](basic-and-digest-authentication.md)
- [<span data-ttu-id="166e2-110">Ověřování v internetu</span><span class="sxs-lookup"><span data-stu-id="166e2-110">Internet Authentication</span></span>](internet-authentication.md)
