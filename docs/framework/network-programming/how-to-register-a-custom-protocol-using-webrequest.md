---
title: 'Postupy: Registrace vlastního protokolu pomocí žádosti WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 5c9a81fc61a2272056ba34fa387fdafee6203824
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59079497"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="5600f-102">Postupy: Registrace vlastního protokolu pomocí žádosti WebRequest</span><span class="sxs-lookup"><span data-stu-id="5600f-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="5600f-103">Tento příklad ukazuje, jak registrovat protokol určité třídy, která je definována jinde.</span><span class="sxs-lookup"><span data-stu-id="5600f-103">This example shows how to register a protocol specific class that is defined elsewhere.</span></span> <span data-ttu-id="5600f-104">V tomto příkladu `CustomWebRequestCreator` je implementované uživatele objekt, který implementuje **vytvořit** metodu, která vrací `CustomWebRequest` objektu.</span><span class="sxs-lookup"><span data-stu-id="5600f-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="5600f-105">Příklad kódu předpokládá, že jste napsali `CustomWebRequest` kód, který implementuje vlastní protokol.</span><span class="sxs-lookup"><span data-stu-id="5600f-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5600f-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="5600f-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5600f-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="5600f-107">Compiling the Code</span></span>  
 <span data-ttu-id="5600f-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="5600f-108">This example requires:</span></span>  
  
 <span data-ttu-id="5600f-109">Odkazy <xref:System.Net> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5600f-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5600f-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5600f-110">See also</span></span>

- [<span data-ttu-id="5600f-111">Programování připojitelných protokolů</span><span class="sxs-lookup"><span data-stu-id="5600f-111">Programming Pluggable Protocols</span></span>](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
