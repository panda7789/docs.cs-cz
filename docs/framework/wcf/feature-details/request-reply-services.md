---
title: Služby požadavku a odpovědi
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: 1ff11b1cae4ec8f6fe886a55cb0add27831048d0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59177811"
---
# <a name="request-reply-services"></a>Služby požadavku a odpovědi
Služby požadavku a odpovědi jsou výchozí typ operace kontraktu Windows Communication Foundation (WCF). Klienti volání operací služby a čekat na odpověď ze služby. Můžete provádět volání operace služby buď synchronně, kde blokuje, dokud klient obdrží odpověď ze služby nebo časy volání, nebo asynchronně, pokračuje v práci tam, kde klient provede volání operace služby a přijímá odpověď od služby v jiném vlákně.  
  
 Vytvoření kontraktu požadavku a odpovědi služby, definujte servisní smlouvě a použít <xref:System.ServiceModel.OperationContractAttribute> třídy pro každou operaci, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 Není nutné nastavit <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost `false` vzhledem k tomu, že toto je výchozí chování.  
  
## <a name="see-also"></a>Viz také:

- [Jednosměrné služby](../../../../docs/framework/wcf/feature-details/one-way-services.md)
- [Duplexní služby](../../../../docs/framework/wcf/feature-details/duplex-services.md)
