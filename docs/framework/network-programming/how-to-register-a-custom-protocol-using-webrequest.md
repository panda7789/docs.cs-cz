---
title: 'Postupy: Registrace vlastního protokolu pomocí WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e6902adeac04d95d576ae72469624a5b4f8aa0c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33394589"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a>Postupy: Registrace vlastního protokolu pomocí WebRequest
Tento příklad ukazuje postup registrace protokolu, které konkrétní classthat je definovaný v jiné oblasti. V tomto příkladu `CustomWebRequestCreator` je implementované uživatele objekt, který implementuje **vytvořit** metodu, která vrátí `CustomWebRequest` objektu. Příklad kódu předpokládá, že jste napsali `CustomWebRequest` kód, který implementuje vlastního protokolu.  
  
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
  
 Odkazuje na <xref:System.Net> oboru názvů.  
  
## <a name="see-also"></a>Viz také  
 [Programování připojitelných protokolů](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
