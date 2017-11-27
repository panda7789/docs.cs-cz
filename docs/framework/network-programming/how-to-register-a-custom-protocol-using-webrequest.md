---
title: "Postupy: Registrace vlastního protokolu pomocí WebRequest"
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
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 4fdb1188aeb7fd754ab21a268070830f55347441
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="829f3-102">Postupy: Registrace vlastního protokolu pomocí WebRequest</span><span class="sxs-lookup"><span data-stu-id="829f3-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="829f3-103">Tento příklad ukazuje postup registrace protokolu, které konkrétní classthat je definovaný v jiné oblasti.</span><span class="sxs-lookup"><span data-stu-id="829f3-103">This example shows how to register a protocol specific classthat is defined elsewhere.</span></span> <span data-ttu-id="829f3-104">V tomto příkladu `CustomWebRequestCreator` je implementované uživatele objekt, který implementuje **vytvořit** metodu, která vrátí `CustomWebRequest` objektu.</span><span class="sxs-lookup"><span data-stu-id="829f3-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="829f3-105">Příklad kódu předpokládá, že jste napsali `CustomWebRequest` kód, který implementuje vlastního protokolu.</span><span class="sxs-lookup"><span data-stu-id="829f3-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="829f3-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="829f3-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="829f3-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="829f3-107">Compiling the Code</span></span>  
 <span data-ttu-id="829f3-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="829f3-108">This example requires:</span></span>  
  
 <span data-ttu-id="829f3-109">Odkazuje na <xref:System.Net> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="829f3-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="829f3-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="829f3-110">See Also</span></span>  
 [<span data-ttu-id="829f3-111">Modulární protokoly programování</span><span class="sxs-lookup"><span data-stu-id="829f3-111">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
