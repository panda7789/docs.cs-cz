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

- Odkazy na <xref:System.IO> <xref:System.Net> obory názvů a.

## <a name="see-also"></a>Viz také:

- [Žádosti o data](requesting-data.md)
