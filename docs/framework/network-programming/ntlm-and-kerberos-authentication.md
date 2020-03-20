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
# <a name="ntlm-and-kerberos-authentication"></a>Ověřování NTLM a Kerberos
Výchozí ověřování NTLM a ověřování protokolem Kerberos používají k pokusu o ověření se serverem pověření uživatele systému Microsoft Windows NT přidružená k volající aplikaci. Při použití jiného než výchozího ověřování NTLM nastaví aplikace <xref:System.Net.NetworkCredential> typ ověřování na NTLM a použije objekt k předání uživatelského jména, hesla a domény hostiteli, jak je znázorněno v následujícím příkladu.  
  
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
  
 Aplikace, které se potřebují připojit k internetovým službám pomocí pověření uživatele aplikace, tak mohou učinit s výchozími pověřeními uživatele, jak je znázorněno v následujícím příkladu.  
  
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
  
 Modul ověřování vyjednávání určuje, zda vzdálený server používá ověřování NTLM nebo Kerberos, a odešle příslušnou odpověď.  
  
> [!NOTE]
> Ověřování NTLM nefunguje prostřednictvím serveru proxy.  
  
## <a name="see-also"></a>Viz také

- [Základní a digest ověřování](basic-and-digest-authentication.md)
- [Ověřování v internetu](internet-authentication.md)
