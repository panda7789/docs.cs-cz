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
ms.openlocfilehash: 471b4dc36cdb32ff7e68aa25c5a2036fec7b1293
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-typecast-a-webrequest-to-access-protocol-specific-properties"></a><span data-ttu-id="237b3-102">Postupy: přiřazení typu WebRequest na specifické vlastnosti protokolu přístupu</span><span class="sxs-lookup"><span data-stu-id="237b3-102">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>
<span data-ttu-id="237b3-103">Tento příklad ukazuje postup přiřazení typu WebRequest, aby mohli používat určité vlastnosti protokolu.</span><span class="sxs-lookup"><span data-stu-id="237b3-103">This example shows how to typecast a WebRequest so that you can access protocol specific properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="237b3-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="237b3-104">Example</span></span>  
  
```csharp  
HttpWebRequest httpreq =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
```  
  
```vb  
Dim httpreq As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
```  
  
## <a name="see-also"></a><span data-ttu-id="237b3-105">Viz také</span><span class="sxs-lookup"><span data-stu-id="237b3-105">See Also</span></span>  
 [<span data-ttu-id="237b3-106">Modulární protokoly programování</span><span class="sxs-lookup"><span data-stu-id="237b3-106">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
