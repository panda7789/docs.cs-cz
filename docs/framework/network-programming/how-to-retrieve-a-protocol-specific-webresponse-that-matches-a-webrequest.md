---
title: 'Postupy: Načtení položky WebResponse specifické pro protokol, která odpovídá položce WebRequest'
description: Naučte se, jak načíst WebResponse specifickou pro protokol, který odpovídá WebRequest ve .NET Framework.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: 15b1912a7bd951df7f3c14eb96251c2bdf237b4f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502454"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a>Postupy: Načtení položky WebResponse specifické pro protokol, která odpovídá položce WebRequest
Tento příklad ukazuje, jak načíst WebResponse specifickou pro protokol, který odpovídá WebRequest.  
  
## <a name="example"></a>Příklad  
  
```csharp  
WebRequest req = WebRequest.Create("http://www.contoso.com/");  
WebResponse resp = req.GetResponse();  
```  
  
```vb  
Dim req As WebRequest = WebRequest.Create("http://www.contoso.com")  
Dim resp As WebResponse = req.GetResponse()  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazuje na obor názvů **System.NET** .  
  
## <a name="see-also"></a>Viz také:

- [Žádosti o data](requesting-data.md)
