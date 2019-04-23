---
title: 'Postupy: Vytvoření kontraktu požadavku a odpovědi'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 7a446db49dcc6a12b900292f1b19c9973835f2c1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59327474"
---
# <a name="how-to-create-a-request-reply-contract"></a>Postupy: Vytvoření kontraktu požadavku a odpovědi
Určuje kontraktů požadavek odpověď, která vrací odpověď. Odpovědi musí být odeslána a korelována žádost podle podmínek této smlouvy. I v případě, že metoda vrátí odpověď (`void` v jazyce C#, nebo `Sub` v jazyce Visual Basic), infrastruktura vytvoří a odešle zprávu o prázdný volajícímu. Pokud chcete zabránit odeslání odpovědi prázdný, použijte jednosměrného kontraktu pro operaci.  
  
### <a name="to-create-a-request-reply-contract"></a>Vytvoření kontraktu požadavku a odpovědi  
  
1. Vytvoření rozhraní v programovacím jazyce podle vašeho výběru.  
  
2. Použít <xref:System.ServiceModel.ServiceContractAttribute> atribut rozhraní.  
  
3. Použít <xref:System.ServiceModel.OperationContractAttribute> atribut pro jednotlivé metody, který může vyvolat klientů.  
  
4. Volitelné. Nastavte hodnotu <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost `true` zabránit odeslání zprávy prázdnou odpověď. Ve výchozím nastavení jsou všechny operace kontraktů požadavek odpověď.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje kontrakt pro službu kalkulačky, která poskytuje `Add` a `Subtract` metody. `Multiply` Metoda není součástí kontraktu proto není označeno atributem <xref:System.ServiceModel.OperationContractAttribute> třídy a proto není přístupný pro klienty.  
  
```csharp
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
  
-   Další informace o tom, jak určit operace kontrakty, najdete v článku <xref:System.ServiceModel.OperationContractAttribute> třídy a <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost.  
  
-   Použití <xref:System.ServiceModel.ServiceContractAttribute> a <xref:System.ServiceModel.OperationContractAttribute> atributy způsobí, že se automatické generování definice kontraktu služby ve webové služby WSDL (Description Language) dokumentu po nasazení služby. Dokument se stáhne přidáním `?wsdl` na HTTP základní adresa pro službu. Třeba `http://microsoft/CalculatorService?wsdl`.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.OperationContractAttribute>
- [Navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md)
- [Postupy: Vytvoření duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
