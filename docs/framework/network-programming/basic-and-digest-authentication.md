---
title: Základní ověřování a ověřování hodnotou hash
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
ms.openlocfilehash: 9a1ad701e1e8f4ee9966ebd56922c29e2bae7a03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048904"
---
# <a name="basic-and-digest-authentication"></a>Základní ověřování a ověřování hodnotou hash
Implementace <xref:System.Net> základního ověřování a ověřování algoritmem Digest je v souladu s protokolem RFC2617 – Ověřování HTTP: Základní a ověřování algoritmem Digest (k dispozici na webu [konsorcia World Wide Web Consortium).](https://www.w3.org)  
  
 Chcete-li použít základní a digest ověřování, aplikace musí <xref:System.Net.WebRequest.Credentials%2A> poskytnout <xref:System.Net.WebRequest> uživatelské jméno a heslo ve vlastnosti objektu, který používá k vyžádání dat z Internetu, jak je znázorněno v následujícím příkladu.  
  
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
> Data odeslaná pomocí základního ověřování a ověřování algoritmem Digest nejsou šifrována, takže je může vidět protivník. Kromě toho základní ověřování pověření (uživatelské jméno a heslo) jsou odesílány v vymazat a mohou být zachyceny.  
  
## <a name="see-also"></a>Viz také

- [Ověřování NTLM a Kerberos](ntlm-and-kerberos-authentication.md)
- [Ověřování v internetu](internet-authentication.md)
