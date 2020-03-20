---
title: 'Postupy: Načtení položky WebResponse specifické pro protokol, která odpovídá položce WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: 0cb2d11306f52df767d8c053e8ab745696bb8e47
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048142"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="b46d6-102">Postupy: Načtení položky WebResponse specifické pro protokol, která odpovídá položce WebRequest</span><span class="sxs-lookup"><span data-stu-id="b46d6-102">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="b46d6-103">Tento příklad ukazuje, jak načíst webovou odezvu specifickou pro protokol, která odpovídá požadavku WebRequest.</span><span class="sxs-lookup"><span data-stu-id="b46d6-103">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b46d6-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b46d6-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b46d6-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b46d6-105">Compiling the Code</span></span>  
 <span data-ttu-id="b46d6-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="b46d6-106">This example requires:</span></span>  
  
- <span data-ttu-id="b46d6-107">Odkazy na **System.Net** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b46d6-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b46d6-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="b46d6-108">See also</span></span>

- [<span data-ttu-id="b46d6-109">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="b46d6-109">Requesting Data</span></span>](requesting-data.md)
