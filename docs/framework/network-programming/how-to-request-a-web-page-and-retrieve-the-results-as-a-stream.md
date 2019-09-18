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
# <a name="how-to-request-a-web-page-and-retrieve-the-results-as-a-stream"></a>Postupy: Vyžádání webové stránky a načtení výsledků jako streamu
Tento příklad ukazuje, jak vyžádat webovou stránku a načíst výsledky v datovém proudu.  
  
## <a name="example"></a>Příklad  
  
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
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na <xref:System.IO> obory <xref:System.Net> názvů a.  
  
## <a name="see-also"></a>Viz také:

- [Žádosti o data](requesting-data.md)
