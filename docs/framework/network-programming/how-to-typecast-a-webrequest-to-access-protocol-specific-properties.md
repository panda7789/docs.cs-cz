---
title: 'Postupy: zadání žádosti WebRequest pro přístup k protokolu konkrétním vlastnostem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d9a8eae2-7454-46f9-b43b-c98477c5bcde
author: mcleblanc
ms.author: markl
ms.openlocfilehash: b4cde78ead9bdb8becf0f12497f4b37ad5a73bb3
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48582236"
---
# <a name="how-to-typecast-a-webrequest-to-access-protocol-specific-properties"></a><span data-ttu-id="690d0-102">Postupy: zadání žádosti WebRequest pro přístup k protokolu konkrétním vlastnostem</span><span class="sxs-lookup"><span data-stu-id="690d0-102">How to: Typecast a WebRequest to Access Protocol Specific Properties</span></span>
<span data-ttu-id="690d0-103">Tento příklad ukazuje, jak zadání žádosti WebRequest, aby měli přístup ke konkrétním vlastnostem protokolu.</span><span class="sxs-lookup"><span data-stu-id="690d0-103">This example shows how to typecast a WebRequest so that you can access protocol specific properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="690d0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="690d0-104">Example</span></span>  
  
```csharp  
HttpWebRequest httpreq =   
   (HttpWebRequest) WebRequest.Create("http://www.contoso.com/");  
```  
  
```vb  
Dim httpreq As HttpWebRequest = _  
   CType(WebRequest.Create("http://www.contoso.com/"), HttpWebRequest)  
```  
  
## <a name="see-also"></a><span data-ttu-id="690d0-105">Viz také</span><span class="sxs-lookup"><span data-stu-id="690d0-105">See Also</span></span>  
 [<span data-ttu-id="690d0-106">Programování připojitelných protokolů</span><span class="sxs-lookup"><span data-stu-id="690d0-106">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
