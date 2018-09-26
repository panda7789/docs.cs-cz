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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: e7638b9558363b77b03208d86d98330b922b414c
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47171225"
---
# <a name="ntlm-and-kerberos-authentication"></a>Ověřování NTLM a Kerberos
Výchozí ověřování NTLM a Kerberos používat přihlašovací údaje uživatelů Microsoft Windows NT přidružené volající aplikace k ověřování se serverem. Při použití ověřování NTLM jiné než výchozí, aplikace nastaví typ ověřování NTLM a použije <xref:System.Net.NetworkCredential> objekt k předávání uživatelské jméno, heslo a doménu na hostitele, jak je znázorněno v následujícím příkladu.  
  
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
  
 Aplikace, které potřebují k připojení k Internetu služby pomocí přihlašovacích údajů uživatele, aplikace lze provést pomocí výchozích přihlašovacích údajů uživatele, jak je znázorněno v následujícím příkladu.  
  
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
  
 Modul negotiate ověřování určuje, zda vzdálený server používá ověřování NTLM nebo Kerberos a odešle odpovídající odpověď.  
  
> [!NOTE]
>  Ověřování protokolem NTLM, nefunguje přes proxy server.  
  
## <a name="see-also"></a>Viz také  
 [Základní ověřování a ověřování algoritmem Digest](../../../docs/framework/network-programming/basic-and-digest-authentication.md)  
 [Ověřování v internetu](../../../docs/framework/network-programming/internet-authentication.md)
