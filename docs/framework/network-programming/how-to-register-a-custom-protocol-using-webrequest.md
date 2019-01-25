---
title: 'Postupy: Registrace vlastního protokolu pomocí žádosti WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
ms.openlocfilehash: d2056bee6c8847989556799511dfaea326dcdac1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669039"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a>Postupy: Registrace vlastního protokolu pomocí žádosti WebRequest
Tento příklad ukazuje, jak registrovat protokol určité třídy, která je definována jinde. V tomto příkladu `CustomWebRequestCreator` je implementované uživatele objekt, který implementuje **vytvořit** metodu, která vrací `CustomWebRequest` objektu. Příklad kódu předpokládá, že jste napsali `CustomWebRequest` kód, který implementuje vlastní protokol.  
  
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
  
 Odkazy <xref:System.Net> oboru názvů.  
  
## <a name="see-also"></a>Viz také:
- [Programování připojitelných protokolů](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
