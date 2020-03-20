---
title: 'Postupy: Vyžádání webové stránky a načtení výsledků jako streamu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: 65bda268cd77959dbcd786c365d0a30c324b89ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71393105"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="85c48-102">Postupy: Vyžádání webové stránky a načtení výsledků jako streamu</span><span class="sxs-lookup"><span data-stu-id="85c48-102">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>

<span data-ttu-id="85c48-103">Tento příklad ukazuje, jak požádat o webovou stránku a načíst výsledky v datovém proudu.</span><span class="sxs-lookup"><span data-stu-id="85c48-103">This example shows how to request a Web page and retrieve the results in a stream.</span></span>
  
## <a name="example"></a><span data-ttu-id="85c48-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="85c48-104">Example</span></span>

```csharp
var myClient = new WebClient();
Stream response = myClient.OpenRead("https://docs.microsoft.com/dotnet/");
// The stream data is used here.
response.Close();
```

```vb
Dim myClient As New WebClient()
Dim response As Stream = myClient.OpenRead("https://docs.microsoft.com/dotnet/")
' The stream data is used here.
response.Close()
```

## <a name="compiling-the-code"></a><span data-ttu-id="85c48-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="85c48-105">Compiling the Code</span></span>

 <span data-ttu-id="85c48-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="85c48-106">This example requires:</span></span>

- <span data-ttu-id="85c48-107">Odkazy na <xref:System.IO> obory názvů a. <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="85c48-107">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="85c48-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="85c48-108">See also</span></span>

- [<span data-ttu-id="85c48-109">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="85c48-109">Requesting Data</span></span>](requesting-data.md)
