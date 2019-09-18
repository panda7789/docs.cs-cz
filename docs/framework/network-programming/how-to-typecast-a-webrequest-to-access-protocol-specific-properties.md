---
title: 'Postupy: Zadání žádosti WebRequest pro přístup k vlastnostem specifickým pro protokol'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d9a8eae2-7454-46f9-b43b-c98477c5bcde
ms.openlocfilehash: a224d9dbab0157d77c05a5937fe35c027296a674
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048029"
---
# <a name="how-to-typecast-a-webrequest-to-access-protocol-specific-properties"></a><span data-ttu-id="73c56-102">Postupy: Zadání žádosti WebRequest pro přístup k vlastnostem specifickým pro protokol</span><span class="sxs-lookup"><span data-stu-id="73c56-102">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>
<span data-ttu-id="73c56-103">Tento příklad ukazuje, jak přetypovatovat WebRequest, abyste mohli získat přístup k vlastnostem specifickým pro protokol.</span><span class="sxs-lookup"><span data-stu-id="73c56-103">This example shows how to typecast a WebRequest so that you can access protocol specific properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73c56-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="73c56-104">Example</span></span>  
  
```csharp  
HttpWebRequest httpreq =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
```  
  
```vb  
Dim httpreq As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
```  
  
## <a name="see-also"></a><span data-ttu-id="73c56-105">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73c56-105">See also</span></span>

- [<span data-ttu-id="73c56-106">Programování připojitelných protokolů</span><span class="sxs-lookup"><span data-stu-id="73c56-106">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)
