---
title: 'Postupy: Registrace vlastního protokolu pomocí žádosti WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 5f863aa61058e87a7911bab3b02c3ba345419596
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193601"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="e0d1e-102">Postupy: Registrace vlastního protokolu pomocí žádosti WebRequest</span><span class="sxs-lookup"><span data-stu-id="e0d1e-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="e0d1e-103">Tento příklad ukazuje, jak registrovat protokol, který konkrétní classthat je definována jinde.</span><span class="sxs-lookup"><span data-stu-id="e0d1e-103">This example shows how to register a protocol specific classthat is defined elsewhere.</span></span> <span data-ttu-id="e0d1e-104">V tomto příkladu `CustomWebRequestCreator` je implementované uživatele objekt, který implementuje **vytvořit** metodu, která vrací `CustomWebRequest` objektu.</span><span class="sxs-lookup"><span data-stu-id="e0d1e-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="e0d1e-105">Příklad kódu předpokládá, že jste napsali `CustomWebRequest` kód, který implementuje vlastní protokol.</span><span class="sxs-lookup"><span data-stu-id="e0d1e-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0d1e-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0d1e-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e0d1e-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e0d1e-107">Compiling the Code</span></span>  
 <span data-ttu-id="e0d1e-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e0d1e-108">This example requires:</span></span>  
  
 <span data-ttu-id="e0d1e-109">Odkazy <xref:System.Net> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e0d1e-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0d1e-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0d1e-110">See Also</span></span>  
 [<span data-ttu-id="e0d1e-111">Programování připojitelných protokolů</span><span class="sxs-lookup"><span data-stu-id="e0d1e-111">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
