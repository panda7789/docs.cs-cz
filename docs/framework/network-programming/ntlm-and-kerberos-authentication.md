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
# <a name="ntlm-and-kerberos-authentication"></a>Ověřování NTLM a Kerberos
Výchozí ověřování pomocí protokolu NTLM a ověřování protokolem Kerberos používají přihlašovací údaje uživatele systému Microsoft Windows NT přidružené k volající aplikaci k pokusu o ověření u serveru. Pokud používáte jiné než výchozí ověřování NTLM, aplikace nastaví typ ověřování na NTLM a pomocí <xref:System.Net.NetworkCredential> objektu předáte uživatelské jméno, heslo a doménu do hostitele, jak je znázorněno v následujícím příkladu.  
  
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
  
 Aplikace, které se potřebují připojit k internetovým službám pomocí přihlašovacích údajů uživatele aplikace, můžou tak učinit pomocí výchozích přihlašovacích údajů uživatele, jak je znázorněno v následujícím příkladu.  
  
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
  
 Modul vyjednávání ověřování určuje, zda vzdálený server používá ověřování protokolem NTLM nebo Kerberos, a odešle příslušnou odpověď.  
  
> [!NOTE]
> Ověřování protokolem NTLM nefunguje prostřednictvím proxy server.  
  
## <a name="see-also"></a>Viz také:

- [Základní ověřování a ověřování algoritmem Digest](basic-and-digest-authentication.md)
- [Ověřování v internetu](internet-authentication.md)
