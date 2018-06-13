---
title: Služby požadavku a odpovědi
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: 8fe1343a4b3590622becf71f1167f4b19dbc67af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33490942"
---
# <a name="request-reply-services"></a>Služby požadavku a odpovědi
Služby požadavku a odpovědi jsou výchozí typ operace kontraktu Windows Communication Foundation (WCF). Klienti volat operace služby a čekat na odpověď ze služby. Můžete provádět volání operace služby buď synchronně, kde klient blokuje až ji přijme odpověď ze služby nebo časy volání nebo asynchronně, pokračuje v práci tam, kde klient podá volání operace služby a přijímá odpověď ze služby na jiné vlákno.  
  
 K vytvoření kontraktu služby požadavku a odpovědi, zadejte své smlouvy a použít <xref:System.ServiceModel.OperationContractAttribute> třídy na každou operaci, jak je znázorněno v následujícím ukázkovém kódu.  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 Není nutné nastavit <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost `false` vzhledem k tomu, že toto je výchozí chování.  
  
## <a name="see-also"></a>Viz také  
 [Jednosměrné služby](../../../../docs/framework/wcf/feature-details/one-way-services.md)  
 [Duplexní služby](../../../../docs/framework/wcf/feature-details/duplex-services.md)
