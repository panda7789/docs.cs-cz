---
title: 'Postupy: načtení WebResponse specifické pro protokol, který odpovídá položce WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: f1da226fb62c55f37183404765430c094f1cd63f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188271"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="e0511-102">Postupy: načtení WebResponse specifické pro protokol, který odpovídá položce WebRequest</span><span class="sxs-lookup"><span data-stu-id="e0511-102">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="e0511-103">Tento příklad ukazuje, jak načíst WebResponse specifické pro protokol, který odpovídá položce WebRequest.</span><span class="sxs-lookup"><span data-stu-id="e0511-103">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0511-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0511-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e0511-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e0511-105">Compiling the Code</span></span>  
 <span data-ttu-id="e0511-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e0511-106">This example requires:</span></span>  
  
-   <span data-ttu-id="e0511-107">Odkazy **System.Net** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e0511-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0511-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0511-108">See Also</span></span>  
 [<span data-ttu-id="e0511-109">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="e0511-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
