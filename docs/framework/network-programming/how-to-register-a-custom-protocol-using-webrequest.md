---
title: 'Postupy: Registrace vlastního protokolu pomocí žádosti WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 05b6f6c3f0f1fc1b36b60e8b0dae50de2826aba4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048255"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a><span data-ttu-id="d9bca-102">Postupy: Registrace vlastního protokolu pomocí žádosti WebRequest</span><span class="sxs-lookup"><span data-stu-id="d9bca-102">How to: Register a Custom Protocol Using WebRequest</span></span>
<span data-ttu-id="d9bca-103">Tento příklad ukazuje, jak registrovat třídu specifickou pro protokol, která je definována jinde.</span><span class="sxs-lookup"><span data-stu-id="d9bca-103">This example shows how to register a protocol specific class that is defined elsewhere.</span></span> <span data-ttu-id="d9bca-104">V tomto příkladu `CustomWebRequestCreator` je uživatelem implementovaný objekt, který implementuje `CustomWebRequest` metodu **Create** , která vrací objekt.</span><span class="sxs-lookup"><span data-stu-id="d9bca-104">In this example, `CustomWebRequestCreator` is the user-implemented object that implements the **Create** method that returns the `CustomWebRequest` object.</span></span> <span data-ttu-id="d9bca-105">Příklad kódu předpokládá, že jste napsali `CustomWebRequest` kód, který implementuje vlastní protokol.</span><span class="sxs-lookup"><span data-stu-id="d9bca-105">The code example assumes that you have written the `CustomWebRequest` code that implements the custom protocol.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9bca-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="d9bca-106">Example</span></span>  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d9bca-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d9bca-107">Compiling the Code</span></span>  
 <span data-ttu-id="d9bca-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="d9bca-108">This example requires:</span></span>  
  
 <span data-ttu-id="d9bca-109">Odkazy na <xref:System.Net> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="d9bca-109">References to the <xref:System.Net> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9bca-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9bca-110">See also</span></span>

- [<span data-ttu-id="d9bca-111">Programování připojitelných protokolů</span><span class="sxs-lookup"><span data-stu-id="d9bca-111">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)
