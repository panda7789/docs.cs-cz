---
title: Služby požadavku a odpovědi
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: f58da6f1cdaad1b976659ee2e9febe12cc07726f
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991145"
---
# <a name="request-reply-services"></a>Služby požadavku a odpovědi
Služby požadavku a odpovědi jsou výchozím typem kontraktu operace v Windows Communication Foundation (WCF). Klienti volají operace se službami a čekají na odpověď od služby. Můžete provést volání do operace služby buď synchronně, kde klient blokuje odpověď, dokud neobdrží odpověď ze služby nebo času volání, nebo asynchronně, kde klient provádí volání operace služby, pokračuje v práci a přijímá odpověď ze služby v jiném vlákně.  
  
 Chcete-li vytvořit kontrakt služby požadavek-odpověď, definujte kontrakt služby a použijte <xref:System.ServiceModel.OperationContractAttribute> pro každou operaci třídu, jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> Vlastnost není nutné nastavovat, `false` protože se jedná o výchozí chování.  
  
## <a name="see-also"></a>Viz také:

- [Jednosměrné služby](../../../../docs/framework/wcf/feature-details/one-way-services.md)
- [Duplexní služby](../../../../docs/framework/wcf/feature-details/duplex-services.md)
