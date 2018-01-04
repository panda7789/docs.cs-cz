---
title: "Služby požadavku a odpovědi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e9e8c01fa3451cbeb335c4771e287566af1c104b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="request-reply-services"></a>Služby požadavku a odpovědi
Služby požadavku a odpovědi jsou výchozí typ operace kontrakt [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]. Klienti volat operace služby a čekat na odpověď ze služby. Můžete provádět volání operace služby buď synchronně, kde klient blokuje až ji přijme odpověď ze služby nebo časy volání nebo asynchronně, pokračuje v práci tam, kde klient podá volání operace služby a přijímá odpověď ze služby na jiné vlákno.  
  
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
