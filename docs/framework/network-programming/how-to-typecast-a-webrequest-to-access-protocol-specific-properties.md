---
title: 'Postupy: Zadání žádosti WebRequest pro přístup k vlastnostem specifickým pro protokol'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d9a8eae2-7454-46f9-b43b-c98477c5bcde
ms.openlocfilehash: a9488e484aad7ba3df23c33b2cb5b79f234b758e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642422"
---
# <a name="how-to-typecast-a-webrequest-to-access-protocol-specific-properties"></a>Postupy: Zadání žádosti WebRequest pro přístup k vlastnostem specifickým pro protokol
Tento příklad ukazuje, jak zadání žádosti WebRequest, aby měli přístup ke konkrétním vlastnostem protokolu.  
  
## <a name="example"></a>Příklad  
  
```csharp  
HttpWebRequest httpreq =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
```  
  
```vb  
Dim httpreq As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
```  
  
## <a name="see-also"></a>Viz také:

- [Programování připojitelných protokolů](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
