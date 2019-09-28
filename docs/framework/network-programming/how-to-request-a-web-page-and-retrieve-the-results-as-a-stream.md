---
title: 'Postupy: Vyžádání webové stránky a načtení výsledků jako streamu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: 65bda268cd77959dbcd786c365d0a30c324b89ce
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71393105"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="0455b-102">Postupy: Vyžádání webové stránky a načtení výsledků jako streamu</span><span class="sxs-lookup"><span data-stu-id="0455b-102">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>

<span data-ttu-id="0455b-103">Tento příklad ukazuje, jak vyžádat webovou stránku a načíst výsledky v datovém proudu.</span><span class="sxs-lookup"><span data-stu-id="0455b-103">This example shows how to request a Web page and retrieve the results in a stream.</span></span>
  
## <a name="example"></a><span data-ttu-id="0455b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="0455b-104">Example</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="0455b-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="0455b-105">Compiling the Code</span></span>

 <span data-ttu-id="0455b-106">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="0455b-106">This example requires:</span></span>

- <span data-ttu-id="0455b-107">Odkazy na <xref:System.IO> obory <xref:System.Net> názvů a.</span><span class="sxs-lookup"><span data-stu-id="0455b-107">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="0455b-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0455b-108">See also</span></span>

- [<span data-ttu-id="0455b-109">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="0455b-109">Requesting Data</span></span>](requesting-data.md)
