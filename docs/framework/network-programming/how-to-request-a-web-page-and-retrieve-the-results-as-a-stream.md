---
title: 'Postupy: Vyžádání webové stránky a načtení výsledků jako streamu'
description: Tento příklad ukazuje, jak požádat o webovou stránku a načíst výsledky v datovém proudu v .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d32b7f35-29d8-4fb7-ad71-d219edc5e359
ms.openlocfilehash: bd57f9af6be29c783d044e785ebb36aaa8592df2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502480"
---
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a><span data-ttu-id="104ff-103">Postupy: Vyžádání webové stránky a načtení výsledků jako streamu</span><span class="sxs-lookup"><span data-stu-id="104ff-103">How to: Request a Web Page and Retrieve the Results as a Stream</span></span>

<span data-ttu-id="104ff-104">Tento příklad ukazuje, jak vyžádat webovou stránku a načíst výsledky v datovém proudu.</span><span class="sxs-lookup"><span data-stu-id="104ff-104">This example shows how to request a Web page and retrieve the results in a stream.</span></span>
  
## <a name="example"></a><span data-ttu-id="104ff-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="104ff-105">Example</span></span>

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

## <a name="compiling-the-code"></a><span data-ttu-id="104ff-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="104ff-106">Compiling the Code</span></span>

 <span data-ttu-id="104ff-107">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="104ff-107">This example requires:</span></span>

- <span data-ttu-id="104ff-108">Odkazy na <xref:System.IO> <xref:System.Net> obory názvů a.</span><span class="sxs-lookup"><span data-stu-id="104ff-108">References to the <xref:System.IO> and <xref:System.Net> namespaces.</span></span>

## <a name="see-also"></a><span data-ttu-id="104ff-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="104ff-109">See also</span></span>

- [<span data-ttu-id="104ff-110">Žádosti o data</span><span class="sxs-lookup"><span data-stu-id="104ff-110">Requesting Data</span></span>](requesting-data.md)
