---
title: 'Postupy: Načtení žádosti WebResponse specifické pro protokol, která odpovídá žádosti WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: fee2b725afbceef45b9651a7cd88a61b37952e32
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59087375"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="009db-102">Postupy: Načtení žádosti WebResponse specifické pro protokol, která odpovídá žádosti WebRequest</span><span class="sxs-lookup"><span data-stu-id="009db-102">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="009db-103">Tento příklad ukazuje, jak načíst WebResponse specifické pro protokol, který odpovídá položce WebRequest.</span><span class="sxs-lookup"><span data-stu-id="009db-103">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="009db-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="009db-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="009db-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="009db-105">Compiling the Code</span></span>  
 <span data-ttu-id="009db-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="009db-106">This example requires:</span></span>  
  
-   <span data-ttu-id="009db-107">Odkazy **System.Net** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="009db-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="009db-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="009db-108">See also</span></span>

- [<span data-ttu-id="009db-109">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="009db-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
