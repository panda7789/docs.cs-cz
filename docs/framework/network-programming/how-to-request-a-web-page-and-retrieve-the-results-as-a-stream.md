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
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a>Postupy: Vyžádání webové stránky a načtení výsledků jako streamu

Tento příklad ukazuje, jak vyžádat webovou stránku a načíst výsledky v datovém proudu.
  
## <a name="example"></a>Příklad

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

## <a name="compiling-the-code"></a>Probíhá kompilace kódu

 Tento příklad vyžaduje:

- Odkazy na <xref:System.IO> obory <xref:System.Net> názvů a.

## <a name="see-also"></a>Viz také:

- [Žádosti o data](requesting-data.md)
