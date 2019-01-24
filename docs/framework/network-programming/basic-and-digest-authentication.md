---
title: Základní a ověřování algoritmem Digest
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
ms.openlocfilehash: 2c764909514eac74cb930df055cdb846bab7b249
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54502922"
---
# <a name="basic-and-digest-authentication"></a>Základní a ověřování algoritmem Digest
<xref:System.Net> Provádění basic a ověřování algoritmem digest splňuje RFC2617 – ověřování pomocí protokolu HTTP: Základní a ověřování algoritmem Digest (k dispozici na [World Wide Web Consortium](https://www.w3.org) webu).  
  
 Použijte základní a ověřování algoritmem digest, aplikace musíte zadat uživatelské jméno a heslo <xref:System.Net.WebRequest.Credentials%2A> vlastnost <xref:System.Net.WebRequest> objekt, který se použije k vyžádání dat z Internetu, jak je znázorněno v následujícím příkladu.  
  
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
>  Data odesílaná s Basic a ověřování algoritmem Digest se nešifrují, takže data můžete vidět nežádoucí osoba. Kromě toho pověření základního ověřování (uživatelské jméno a heslo) se odesílají v nešifrované podobě a může být zachycena.  
  
## <a name="see-also"></a>Viz také:
- [Ověřování NTLM a Kerberos](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)
- [Ověřování v internetu](../../../docs/framework/network-programming/internet-authentication.md)
