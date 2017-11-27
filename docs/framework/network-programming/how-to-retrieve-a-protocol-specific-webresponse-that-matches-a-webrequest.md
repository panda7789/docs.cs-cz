---
title: "Postupy: načtení WebResponse specifické pro protokol, který odpovídá WebRequest"
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
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: cbf6b6eab3502f8f04f33f6f11d5d071e3406a7a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a><span data-ttu-id="6ad12-102">Postupy: načtení WebResponse specifické pro protokol, který odpovídá WebRequest</span><span class="sxs-lookup"><span data-stu-id="6ad12-102">How to: Retrieve a Protocol-Specific WebResponse that Matches a WebRequest</span></span>
<span data-ttu-id="6ad12-103">Tento příklad ukazuje, jak načíst WebResponse specifické pro protokol, který odpovídá WebRequest.</span><span class="sxs-lookup"><span data-stu-id="6ad12-103">This example shows how to retrieve a protocol-specific WebResponse that matches a WebRequest.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ad12-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ad12-104">Example</span></span>  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6ad12-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="6ad12-105">Compiling the Code</span></span>  
 <span data-ttu-id="6ad12-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="6ad12-106">This example requires:</span></span>  
  
-   <span data-ttu-id="6ad12-107">Odkazuje na **System.Net** oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="6ad12-107">References to the **System.Net** namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ad12-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="6ad12-108">See Also</span></span>  
 [<span data-ttu-id="6ad12-109">Požadavek na Data</span><span class="sxs-lookup"><span data-stu-id="6ad12-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
