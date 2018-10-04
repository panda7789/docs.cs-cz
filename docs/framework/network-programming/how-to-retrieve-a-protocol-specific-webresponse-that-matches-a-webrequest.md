---
title: 'Postupy: načtení WebResponse specifické pro protokol, který odpovídá položce WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 2a72e57156903c9d436a49aaf6da596868af4003
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48581842"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="09930-102">Postupy: načtení WebResponse specifické pro protokol, který odpovídá položce WebRequest</span><span class="sxs-lookup"><span data-stu-id="09930-102">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="09930-103">Tento příklad ukazuje, jak načíst WebResponse specifické pro protokol, který odpovídá položce WebRequest.</span><span class="sxs-lookup"><span data-stu-id="09930-103">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="09930-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="09930-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="09930-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="09930-105">Compiling the Code</span></span>  
 <span data-ttu-id="09930-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="09930-106">This example requires:</span></span>  
  
-   <span data-ttu-id="09930-107">Odkazy **System.Net** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="09930-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09930-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="09930-108">See Also</span></span>  
 [<span data-ttu-id="09930-109">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="09930-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
