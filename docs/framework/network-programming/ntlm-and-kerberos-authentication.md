---
title: Ověřování NTLM a Kerberos
description: Přečtěte si, jak výchozí ověřování NTLM a ověřování protokolem Kerberos fungují pro .NET Framework aplikaci, a zjistěte, které nevýchozí ověřování NTLM.
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
ms.openlocfilehash: d91ebca084d84acd4eb8facb82ff08679ec35cd0
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502233"
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
