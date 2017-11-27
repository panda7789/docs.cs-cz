---
title: "Postupy: načtení WebResponse specifické pro protokol, který odpovídá WebRequest"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d8c90785-f16b-42a5-8439-ed2f731b2ba8
caps.latest.revision: "8"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: cbf6b6eab3502f8f04f33f6f11d5d071e3406a7a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-a-protocol-specific-webresponse-that-matches-a-webrequest"></a>Postupy: načtení WebResponse specifické pro protokol, který odpovídá WebRequest
Tento příklad ukazuje, jak načíst WebResponse specifické pro protokol, který odpovídá WebRequest.  
  
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
  
-   Odkazuje na **System.Net** oboru názvů.  
  
## <a name="see-also"></a>Viz také  
 [Požadavek na Data](../../../docs/framework/network-programming/requesting-data.md)
