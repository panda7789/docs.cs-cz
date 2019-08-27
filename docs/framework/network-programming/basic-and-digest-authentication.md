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
ms.openlocfilehash: 029243f9f8b02275c0f0a6ec1a74a9a2ca198d9c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044116"
---
# <a name="basic-and-digest-authentication"></a>Základní ověřování a ověřování hodnotou hash
<xref:System.Net> Implementace základního ověřování a ověřování algoritmem Digest vyhovuje RFC2617 – ověřování http: Základní ověřování a ověřování algoritmem Digest (k dispozici na webu [konsorcium World Wide Web](https://www.w3.org) ).  
  
 Chcete-li použít základní ověřování a ověřování algoritmem Digest, aplikace musí zadat uživatelské jméno a <xref:System.Net.WebRequest.Credentials%2A> heslo ve vlastnosti <xref:System.Net.WebRequest> objektu, který používá k vyžádání dat z Internetu, jak je znázorněno v následujícím příkladu.  
  
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
> Data odesílaná pomocí základního ověřování a ověřování algoritmem Digest nejsou šifrována, takže je lze zobrazit pomocí nežádoucí osoba. Navíc se přihlašovací údaje základního ověřování (uživatelské jméno a heslo) odesílají jasně a je možné je zachytit.  
  
## <a name="see-also"></a>Viz také:

- [Ověřování NTLM a Kerberos](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)
- [Ověřování v internetu](../../../docs/framework/network-programming/internet-authentication.md)
