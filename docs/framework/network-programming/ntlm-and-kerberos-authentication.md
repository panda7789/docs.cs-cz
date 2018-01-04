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
ms.workload: dotnet
ms.openlocfilehash: c1662e5b0f8afd4ef92d2893a11c25457dbce024
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ntlm-and-kerberos-authentication"></a>Ověřování protokolu Kerberos a NTLM
Výchozí ověřování protokolem NTLM a Kerberos používat pověření systému Microsoft Windows NT přidružené volající aplikace k pokusu o ověření se serverem. Při použití ověřování protokolem NTLM jiné než výchozí, aplikace nastaví typ ověřování NTLM a použije <xref:System.Net.NetworkCredential> objektu k předávání uživatelské jméno, heslo a doménu na hostitele, jak je znázorněno v následujícím příkladu.  
  
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
  
 Aplikace, které potřebují k připojení k internetové služby, pomocí přihlašovacích údajů uživatele, aplikace, můžete použít výchozí přihlašovací údaje uživatele, jak je znázorněno v následujícím příkladu.  
  
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
  
 Modul ověřování negotiate Určuje, zda je pomocí ověřování protokolem NTLM nebo Kerberos vzdáleného serveru a odešle odpovídající odpověď.  
  
> [!NOTE]
>  Ověřování protokolem NTLM nefunguje přes proxy server.  
  
## <a name="see-also"></a>Viz také  
 [Základní ověřování a ověřování algoritmem Digest](../../../docs/framework/network-programming/basic-and-digest-authentication.md)  
 [Ověřování v internetu](../../../docs/framework/network-programming/internet-authentication.md)
