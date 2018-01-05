---
title: "Postupy: žádosti o webovou stránku a načtěte výsledky jako datový proud"
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
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 35b46bcfdbf99b311d5d0c0f8bf81f6cc7961afb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="672ed-102">Postupy: žádosti o webovou stránku a načtěte výsledky jako datový proud</span><span class="sxs-lookup"><span data-stu-id="672ed-102">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>
<span data-ttu-id="672ed-103">Tento příklad ukazuje, jak k vyžádání webové stránky a načtěte výsledky v datovém proudu.</span><span class="sxs-lookup"><span data-stu-id="672ed-103">This example shows how to request a Web page and retrieve the results in a stream.</span></span>  
  
## <a name="example"></a><span data-ttu-id="672ed-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="672ed-104">Example</span></span>  
  
```csharp  
WebClient myClient = new WebClient();  
Stream response = myClient.OpenRead("http://www.contoso.com/index.htm");  
// The stream data is used here.  
response.Close();  
```  
  
```vb  
Dim myClient As WebClient = New WebClient()  
Dim response As Stream = myClient.OpenRead("http://www.contoso.com/index.htm")  
' The stream data is used here.  
response.Close()  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="672ed-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="672ed-105">Compiling the Code</span></span>  
 <span data-ttu-id="672ed-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="672ed-106">This example requires:</span></span>  
  
-   <span data-ttu-id="672ed-107">Odkazuje na <xref:System.IO> a <xref:System.Net> obory názvů.</span><span class="sxs-lookup"><span data-stu-id="672ed-107">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="672ed-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="672ed-108">See Also</span></span>  
 [<span data-ttu-id="672ed-109">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="672ed-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
