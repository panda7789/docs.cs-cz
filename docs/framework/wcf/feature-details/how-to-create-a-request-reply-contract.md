---
title: "Postupy: Vytvoření kontraktu požadavku a odpovědi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1ad32807227844e379dd44e63c61b3ff15d2a2ef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-request-reply-contract"></a>Postupy: Vytvoření kontraktu požadavku a odpovědi
Kontraktu požadavku a odpovědi určuje metodu, která vrátí odpověď. Odpovědi musí být odeslána a korelována žádost v souladu s podmínkami této smlouvy. I v případě, že metoda vrátí odpověď (`void` v jazyce C# nebo `Sub` v jazyce Visual Basic), infrastruktura vytvoří a odešle zprávu o prázdný volajícímu. Aby odesílání zprávy odpovědi prázdná, použijte jednosměrného kontraktu pro operaci.  
  
### <a name="to-create-a-request-reply-contract"></a>K vytvoření kontraktu požadavku a odpovědi  
  
1.  Vytvořte rozhraní v programovací jazyk podle vašeho výběru.  
  
2.  Použít <xref:System.ServiceModel.ServiceContractAttribute> atribut rozhraní.  
  
3.  Použít <xref:System.ServiceModel.OperationContractAttribute> atribut každá metoda, který lze vyvolat klientů.  
  
4.  Volitelné. Nastavte hodnotu <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost `true` zabránit odesílání zprávy prázdnou odpověď. Ve výchozím nastavení jsou všechny operace kontraktů požadavek odpověď.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje kontrakt služby kalkulačky, která poskytuje `Add` a `Subtract` metody. `Multiply` Metoda není součástí kontraktu protože není označena pomocí <xref:System.ServiceModel.OperationContractAttribute> třídy a proto není přístupná pro klienty.  
  
```
using System.ServiceModel;

[ServiceContract]
public interface ICalculator
{
    [OperationContract]
    // It would be equivalent to write explicitly:
    // [OperationContract(IsOneWay=false)]
    int Add(int a, int b);
    
    [OperationContract]
    int Subtract(int a, int b);
    
    int Multiply(int a, int b)
}
```
  
-   [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Zadejte kontrakty operaci naleznete v tématu <xref:System.ServiceModel.OperationContractAttribute> třídy a <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost.  
  
-   Použití <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> atributy způsobí automatické generování definice kontraktu služby webové služby popis Language (WSDL) dokumentu po nasazení služby. Stažení dokumentu připojením `?wsdl` na HTTP základní adresa pro službu. Třeba `http://microsoft/CalculatorService?wsdl`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.OperationContractAttribute>  
 [Navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md)  
 [Postupy: vytvoření duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
