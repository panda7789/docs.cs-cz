---
title: 'Postupy: Registrace vlastního protokolu pomocí žádosti WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 05b6f6c3f0f1fc1b36b60e8b0dae50de2826aba4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048255"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="22ea6-102">Postupy: Registrace vlastního protokolu pomocí žádosti WebRequest</span><span class="sxs-lookup"><span data-stu-id="22ea6-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="22ea6-103">Tento příklad ukazuje, jak zaregistrovat třídu specifickou pro protokol, která je definována jinde.</span><span class="sxs-lookup"><span data-stu-id="22ea6-103">This example shows how to register a protocol specific class that is defined elsewhere.</span></span> <span data-ttu-id="22ea6-104">V tomto `CustomWebRequestCreator` příkladu je uživatelem implementovaný objekt, který `CustomWebRequest` implementuje **Create** metoda, která vrací objekt.</span><span class="sxs-lookup"><span data-stu-id="22ea6-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="22ea6-105">Příklad kódu předpokládá, že jste `CustomWebRequest` napsali kód, který implementuje vlastní protokol.</span><span class="sxs-lookup"><span data-stu-id="22ea6-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22ea6-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="22ea6-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="22ea6-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="22ea6-107">Compiling the Code</span></span>  
 <span data-ttu-id="22ea6-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="22ea6-108">This example requires:</span></span>  
  
 <span data-ttu-id="22ea6-109">Odkazy na <xref:System.Net> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="22ea6-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22ea6-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="22ea6-110">See also</span></span>

- [<span data-ttu-id="22ea6-111">Programování připojitelných protokolů</span><span class="sxs-lookup"><span data-stu-id="22ea6-111">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)
