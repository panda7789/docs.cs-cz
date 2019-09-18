---
title: 'Postupy: Registrace vlastního protokolu pomocí žádosti WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: 05b6f6c3f0f1fc1b36b60e8b0dae50de2826aba4
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048255"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a>Postupy: Registrace vlastního protokolu pomocí žádosti WebRequest
Tento příklad ukazuje, jak registrovat třídu specifickou pro protokol, která je definována jinde. V tomto příkladu `CustomWebRequestCreator` je uživatelem implementovaný objekt, který implementuje `CustomWebRequest` metodu **Create** , která vrací objekt. Příklad kódu předpokládá, že jste napsali `CustomWebRequest` kód, který implementuje vlastní protokol.  
  
## <a name="example"></a>Příklad  
  
```csharp  
WebRequest.RegisterPrefix("custom", new CustomWebRequestCreator());  
WebRequest req = WebRequest.Create("custom://customHost.contoso.com/");  
```  
  
```vb  
WebRequest.RegisterPrefix("custom", New CustomWebRequestCreator())  
Dim req As WebRequest = WebRequest.Create("custom://customHost.contoso.com/")  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
 Odkazy na <xref:System.Net> obor názvů.  
  
## <a name="see-also"></a>Viz také:

- [Programování připojitelných protokolů](programming-pluggable-protocols.md)
