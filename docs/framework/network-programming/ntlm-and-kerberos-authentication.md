---
title: "Ověřování protokolu Kerberos a NTLM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "9"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 36e88b163ab857180a02278828dba7dcec457736
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ntlm-and-kerberos-authentication"></a><span data-ttu-id="84d64-102">Ověřování protokolu Kerberos a NTLM</span><span class="sxs-lookup"><span data-stu-id="84d64-102">NTLM and Kerberos Authentication</span></span>
<span data-ttu-id="84d64-103">Výchozí ověřování protokolem NTLM a Kerberos používat pověření systému Microsoft Windows NT přidružené volající aplikace k pokusu o ověření se serverem.</span><span class="sxs-lookup"><span data-stu-id="84d64-103">Default NTLM authentication and Kerberos authentication use the Microsoft Windows NT user credentials associated with the calling application to attempt authentication with the server.</span></span> <span data-ttu-id="84d64-104">Při použití ověřování protokolem NTLM jiné než výchozí, aplikace nastaví typ ověřování NTLM a použije <xref:System.Net.NetworkCredential> objektu k předávání uživatelské jméno, heslo a doménu na hostitele, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="84d64-104">When using non-default NTLM authentication, the application sets the authentication type to NTLM and uses a <xref:System.Net.NetworkCredential> object to pass the user name, password, and domain to the host, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="84d64-105">Aplikace, které potřebují k připojení k internetové služby, pomocí přihlašovacích údajů uživatele, aplikace, můžete použít výchozí přihlašovací údaje uživatele, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="84d64-105">Applications that need to connect to Internet services using the credentials of the application user can do so with the user's default credentials, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="84d64-106">Modul ověřování negotiate Určuje, zda je pomocí ověřování protokolem NTLM nebo Kerberos vzdáleného serveru a odešle odpovídající odpověď.</span><span class="sxs-lookup"><span data-stu-id="84d64-106">The negotiate authentication module determines whether the remote server is using NTLM or Kerberos authentication, and sends the appropriate response.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84d64-107">Ověřování protokolem NTLM nefunguje přes proxy server.</span><span class="sxs-lookup"><span data-stu-id="84d64-107">NTLM authentication does not work through a proxy server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84d64-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="84d64-108">See Also</span></span>  
 [<span data-ttu-id="84d64-109">Základní a ověřování algoritmem Digest</span><span class="sxs-lookup"><span data-stu-id="84d64-109">Basic and Digest Authentication</span></span>](../../../docs/framework/network-programming/basic-and-digest-authentication.md)  
 [<span data-ttu-id="84d64-110">Ověřování v Internetu</span><span class="sxs-lookup"><span data-stu-id="84d64-110">Internet Authentication</span></span>](../../../docs/framework/network-programming/internet-authentication.md)
