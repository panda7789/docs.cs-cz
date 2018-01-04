---
title: "Postupy: přiřazení typu WebRequest na specifické vlastnosti protokolu přístupu"
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
ms.assetid: d9a8eae2-7454-46f9-b43b-c98477c5bcde
caps.latest.revision: "6"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: e398fa0dce066aec735f149f20e2803e7cd5ce80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-typecast-a-webrequest-to-access-protocol-specific-properties"></a>Postupy: přiřazení typu WebRequest na specifické vlastnosti protokolu přístupu
Tento příklad ukazuje postup přiřazení typu WebRequest, aby mohli používat určité vlastnosti protokolu.  
  
## <a name="example"></a>Příklad  
  
```csharp  
HttpWebRequest httpreq =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
```  
  
```vb  
Dim httpreq As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
```  
  
## <a name="see-also"></a>Viz také  
 [Programování připojitelných protokolů](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
