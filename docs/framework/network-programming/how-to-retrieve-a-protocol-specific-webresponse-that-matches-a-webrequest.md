---
title: 'Postupy: Načtení žádosti WebResponse specifické pro protokol, která odpovídá žádosti WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
ms.openlocfilehash: 21a5a81c6a5457897078db03fe35eaff330ed62d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64647371"
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a>Postupy: Načtení žádosti WebResponse specifické pro protokol, která odpovídá žádosti WebRequest
Tento příklad ukazuje, jak načíst WebResponse specifické pro protokol, který odpovídá položce WebRequest.  
  
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
  
- Odkazy **System.Net** oboru názvů.  
  
## <a name="see-also"></a>Viz také:

- [Žádosti o data](../../../docs/framework/network-programming/requesting-data.md)
