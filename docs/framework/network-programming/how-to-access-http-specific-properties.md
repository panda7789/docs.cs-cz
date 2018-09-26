---
title: 'Postupy: přístup k vlastnostem specifickým pro HTTP'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: f8848c7e-f5c5-4d42-b86d-9951ff8f4146
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f008cf82b80e29f8fe741034a0e820b5eae5b0ba
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084810"
---
# <a name="how-to-access-http-specific-properties"></a>Postupy: přístup k vlastnostem specifickým pro HTTP
Tento příklad ukazuje, jak chcete-li vypnout HTTP **Keep-alive** chování a získejte verzi protokolu číslo z webového serveru.  
  
## <a name="example"></a>Příklad  
  
```vb  
Dim HttpWReq As HttpWebRequest= _  
    CType(WebRequest.Create("http://www.contoso.com"), HttpWebRequest)  
' Turn off connection keep-alives.  
HttpWReq.KeepAlive = False  
  
Dim HttpWResp As HttpWebResponse = _  
    CType(HttpWReq.GetResponse(), HttpWebResponse)  
  
' Get the HTTP protocol version number returned by the server.  
Dim ver As String = HttpWResp.ProtocolVersion.ToString()  
HttpWResp.Close()  
```  
  
```csharp  
HttpWebRequest HttpWReq =   
    (HttpWebRequest)WebRequest.Create("http://www.contoso.com");  
// Turn off connection keep-alives.  
HttpWReq.KeepAlive = false;  
  
HttpWebResponse HttpWResp = (HttpWebResponse)HttpWReq.GetResponse();  
  
// Get the HTTP protocol version number returned by the server.  
String ver = HttpWResp.ProtocolVersion.ToString();  
HttpWResp.Close();  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy **System.Net** oboru názvů.  
  
## <a name="see-also"></a>Viz také  
 [Přístup k internetu přes proxy server](../../../docs/framework/network-programming/accessing-the-internet-through-a-proxy.md)  
 [Použití aplikačních protokolů](../../../docs/framework/network-programming/using-application-protocols.md)  
 [HTTP](../../../docs/framework/network-programming/http.md)
