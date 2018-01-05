---
title: "Základní a ověřování algoritmem Digest"
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
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 7ca66a65c05da3d515358c0fdb26682fa4ec1438
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="basic-and-digest-authentication"></a>Základní a ověřování algoritmem Digest
<xref:System.Net> Implementace basic a ověřování algoritmem digest splňuje RFC2617 – ověřování pomocí protokolu HTTP: Basic a ověřování algoritmem Digest (k dispozici na webu World Wide Web Consortium na www.w3.org).  
  
 Použijte základní a ověřování algoritmem digest, musí aplikace zadejte uživatelské jméno a heslo v <xref:System.Net.WebRequest.Credentials%2A> vlastnost <xref:System.Net.WebRequest> objekt, který se používá k vyžádání dat z Internetu, jak je znázorněno v následujícím příkladu.  
  
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
>  Data odeslaná s Basic a ověřování algoritmem Digest nejsou šifrována, takže nežádoucí osoba může zobrazit data. Kromě toho základní ověřovací pověření (uživatelské jméno a heslo) se odesílají v nešifrované a mohou být zachyceny.  
  
## <a name="see-also"></a>Viz také  
 [Ověřování NTLM a Kerberos](../../../docs/framework/network-programming/ntlm-and-kerberos-authentication.md)  
 [Ověřování v internetu](../../../docs/framework/network-programming/internet-authentication.md)
