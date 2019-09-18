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
ms.openlocfilehash: ca9e1b9bf6235fdaeea25b8975155af429848ae3
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71047531"
---
# <a name="ntlm-and-kerberos-authentication"></a><span data-ttu-id="65438-102">Ověřování NTLM a Kerberos</span><span class="sxs-lookup"><span data-stu-id="65438-102">NTLM and Kerberos Authentication</span></span>
<span data-ttu-id="65438-103">Výchozí ověřování pomocí protokolu NTLM a ověřování protokolem Kerberos používají přihlašovací údaje uživatele systému Microsoft Windows NT přidružené k volající aplikaci k pokusu o ověření u serveru.</span><span class="sxs-lookup"><span data-stu-id="65438-103">Default NTLM authentication and Kerberos authentication use the Microsoft Windows NT user credentials associated with the calling application to attempt authentication with the server.</span></span> <span data-ttu-id="65438-104">Pokud používáte jiné než výchozí ověřování NTLM, aplikace nastaví typ ověřování na NTLM a pomocí <xref:System.Net.NetworkCredential> objektu předáte uživatelské jméno, heslo a doménu do hostitele, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="65438-104">When using non-default NTLM authentication, the application sets the authentication type to NTLM and uses a <xref:System.Net.NetworkCredential> object to pass the user name, password, and domain to the host, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="65438-105">Aplikace, které se potřebují připojit k internetovým službám pomocí přihlašovacích údajů uživatele aplikace, můžou tak učinit pomocí výchozích přihlašovacích údajů uživatele, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="65438-105">Applications that need to connect to Internet services using the credentials of the application user can do so with the user's default credentials, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="65438-106">Modul vyjednávání ověřování určuje, zda vzdálený server používá ověřování protokolem NTLM nebo Kerberos, a odešle příslušnou odpověď.</span><span class="sxs-lookup"><span data-stu-id="65438-106">The negotiate authentication module determines whether the remote server is using NTLM or Kerberos authentication, and sends the appropriate response.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="65438-107">Ověřování protokolem NTLM nefunguje prostřednictvím proxy server.</span><span class="sxs-lookup"><span data-stu-id="65438-107">NTLM authentication does not work through a proxy server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65438-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65438-108">See also</span></span>

- [<span data-ttu-id="65438-109">Základní ověřování a ověřování algoritmem Digest</span><span class="sxs-lookup"><span data-stu-id="65438-109">Basic and Digest Authentication</span></span>](basic-and-digest-authentication.md)
- [<span data-ttu-id="65438-110">Ověřování v internetu</span><span class="sxs-lookup"><span data-stu-id="65438-110">Internet Authentication</span></span>](internet-authentication.md)
