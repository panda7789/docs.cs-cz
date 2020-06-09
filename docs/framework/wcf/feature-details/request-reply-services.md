---
title: Služby požadavku a odpovědi
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], request-reply services
- contracts [WCF], request-reply services
- WCF [WCF], request-reply services
- request-reply contracts [WCF]
ms.assetid: 2fa710f1-47f4-4598-b063-3ab3bd22ebba
ms.openlocfilehash: df42f3fa8f5a15572987b0d4859856c7f838e632
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586231"
---
# <a name="request-reply-services"></a>Služby požadavku a odpovědi
Služby požadavku a odpovědi jsou výchozím typem kontraktu operace v Windows Communication Foundation (WCF). Klienti volají operace se službami a čekají na odpověď od služby. Můžete provést volání do operace služby buď synchronně, kde klient blokuje odpověď, dokud neobdrží odpověď ze služby nebo času volání, nebo asynchronně, kde klient provede volání operace služby, pokračuje v práci a přijme odpověď ze služby v jiném vlákně.  
  
 Chcete-li vytvořit kontrakt služby požadavek-odpověď, definujte kontrakt služby a použijte <xref:System.ServiceModel.OperationContractAttribute> pro každou operaci třídu, jak je znázorněno v následujícím ukázkovém kódu.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IRequestReplyCalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
}  
```  
  
 Vlastnost není nutné nastavovat <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> , `false` protože se jedná o výchozí chování.  
  
## <a name="see-also"></a>Viz také

- [Jednosměrné služby](one-way-services.md)
- [Duplexní služby](duplex-services.md)
