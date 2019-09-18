---
title: 'Postupy: Vyžádání webové stránky a načtení výsledků jako streamu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: b3d24a958ec93084d03d2ad2e0eb6d9d2507e155
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048179"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="148e7-102">Postupy: Vyžádání webové stránky a načtení výsledků jako streamu</span><span class="sxs-lookup"><span data-stu-id="148e7-102">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>
<span data-ttu-id="148e7-103">Tento příklad ukazuje, jak vyžádat webovou stránku a načíst výsledky v datovém proudu.</span><span class="sxs-lookup"><span data-stu-id="148e7-103">This example shows how to request a Web page and retrieve the results in a stream.</span></span>  
  
## <a name="example"></a><span data-ttu-id="148e7-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="148e7-104">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="148e7-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="148e7-105">Compiling the Code</span></span>  
 <span data-ttu-id="148e7-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="148e7-106">This example requires:</span></span>  
  
- <span data-ttu-id="148e7-107">Odkazy na <xref:System.IO> obory <xref:System.Net> názvů a.</span><span class="sxs-lookup"><span data-stu-id="148e7-107">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="148e7-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="148e7-108">See also</span></span>

- [<span data-ttu-id="148e7-109">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="148e7-109">Requesting Data</span></span>](requesting-data.md)
