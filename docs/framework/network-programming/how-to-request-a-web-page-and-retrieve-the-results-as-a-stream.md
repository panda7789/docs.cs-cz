---
title: 'Postupy: vyžádání webové stránky a načtení výsledků jako Stream'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: 6481e923c8daabfcfa94adc45d7d4172e47a779a
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/26/2018
ms.locfileid: "50041606"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="c8663-102">Postupy: vyžádání webové stránky a načtení výsledků jako Stream</span><span class="sxs-lookup"><span data-stu-id="c8663-102">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>
<span data-ttu-id="c8663-103">Tento příklad ukazuje, jak k vyžádání webové stránky a načtení výsledků v datovém proudu.</span><span class="sxs-lookup"><span data-stu-id="c8663-103">This example shows how to request a Web page and retrieve the results in a stream.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8663-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c8663-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="c8663-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c8663-105">Compiling the Code</span></span>  
 <span data-ttu-id="c8663-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="c8663-106">This example requires:</span></span>  
  
-   <span data-ttu-id="c8663-107">Odkazy <xref:System.IO> a <xref:System.Net> obory názvů.</span><span class="sxs-lookup"><span data-stu-id="c8663-107">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8663-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="c8663-108">See Also</span></span>  
 [<span data-ttu-id="c8663-109">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="c8663-109">Requesting Data</span></span>](../../../docs/framework/network-programming/requesting-data.md)
