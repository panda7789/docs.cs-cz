---
title: 'Postupy: Registrace vlastního protokolu pomocí žádosti WebRequest'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 98ddbdb9-66b1-4080-92ad-51f5c447fcf8
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 1f78f98f94daa51c17a1294285e13dfddd457106
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2018
ms.locfileid: "48244547"
---
# <a name="how-to-register-a-custom-protocol-using-webrequest"></a>Postupy: Registrace vlastního protokolu pomocí žádosti WebRequest
Tento příklad ukazuje, jak registrovat protokol, který konkrétní classthat je definována jinde. V tomto příkladu `CustomWebRequestCreator` je implementované uživatele objekt, který implementuje **vytvořit** metodu, která vrací `CustomWebRequest` objektu. Příklad kódu předpokládá, že jste napsali `CustomWebRequest` kód, který implementuje vlastní protokol.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Programování připojitelných protokolů](../../../docs/framework/network-programming/programming-pluggable-protocols.md)
