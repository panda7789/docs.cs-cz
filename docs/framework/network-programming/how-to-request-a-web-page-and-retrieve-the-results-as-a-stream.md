---
title: 'Postupy: Vyžádání webové stránky a načtení výsledků jako Stream'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: 5ef1867d84b619c58a7b3e29ed0f81f9db0c07a5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54578582"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a>Postupy: Vyžádání webové stránky a načtení výsledků jako Stream
Tento příklad ukazuje, jak k vyžádání webové stránky a načtení výsledků v datovém proudu.  
  
## <a name="example"></a>Příklad  
  
```csharp  
WebClient myClient = new WebClient();  
Stream response = myClient.OpenRead("http://www.contoso.com/index.htm");  
// The stream data is used here.  
response.Close();  
```  
  
```vb  
Dim myClient As WebClient = New WebClient()  
Dim response As Stream = myClient.OpenRead("http://www.contoso.com/index.htm")  
' The stream data is used here.  
response.Close()  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy <xref:System.IO> a <xref:System.Net> obory názvů.  
  
## <a name="see-also"></a>Viz také:
- [Žádosti o data](../../../docs/framework/network-programming/requesting-data.md)
