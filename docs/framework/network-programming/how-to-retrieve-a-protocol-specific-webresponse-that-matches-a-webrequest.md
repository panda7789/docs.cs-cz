---
title: 'Postupy: Načtení položky WebResponse specifické pro protokol, která odpovídá položce WebRequest'
description: Naučte se, jak načíst WebResponse specifickou pro protokol, který odpovídá WebRequest ve .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: 15b1912a7bd951df7f3c14eb96251c2bdf237b4f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502454"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="47c0d-103">Postupy: Načtení položky WebResponse specifické pro protokol, která odpovídá položce WebRequest</span><span class="sxs-lookup"><span data-stu-id="47c0d-103">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="47c0d-104">Tento příklad ukazuje, jak načíst WebResponse specifickou pro protokol, který odpovídá WebRequest.</span><span class="sxs-lookup"><span data-stu-id="47c0d-104">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47c0d-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="47c0d-105">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="47c0d-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="47c0d-106">Compiling the Code</span></span>  
 <span data-ttu-id="47c0d-107">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="47c0d-107">This example requires:</span></span>  
  
- <span data-ttu-id="47c0d-108">Odkazuje na obor názvů **System.NET** .</span><span class="sxs-lookup"><span data-stu-id="47c0d-108">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47c0d-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47c0d-109">See also</span></span>

- [<span data-ttu-id="47c0d-110">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="47c0d-110">Requesting Data</span></span>](requesting-data.md)
