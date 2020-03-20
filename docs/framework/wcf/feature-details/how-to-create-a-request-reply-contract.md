---
title: 'Postupy: Vytvoření kontraktu požadavku a odpovědi'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 793f7214f8319e87c3e344990577841fc029bc55
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185034"
---
# <a name="how-to-create-a-request-reply-contract"></a>Postupy: Vytvoření kontraktu požadavku a odpovědi
Smlouva požadavek odpověď určuje metodu, která vrací odpověď. Odpověď musí být zaslána a korelována s žádostí podle podmínek této smlouvy. I v případě, že`void` metoda vrátí žádnou odpověď (v jazyce C#, nebo `Sub` v jazyce Visual Basic), infrastruktura vytvoří a odešle prázdnou zprávu volajícímu. Chcete-li zabránit odeslání prázdné zprávy s odpovědí, použijte pro operaci jednosměrnou smlouvu.  
  
### <a name="to-create-a-request-reply-contract"></a>Vytvoření smlouvy požadavku a odpovědi  
  
1. Vytvořte rozhraní v programovacím jazyce dle vašeho výběru.  
  
2. Použijte <xref:System.ServiceModel.ServiceContractAttribute> atribut rozhraní.  
  
3. Použijte <xref:System.ServiceModel.OperationContractAttribute> atribut pro každou metodu, kterou mohou klienti vyvolat.  
  
4. Nepovinný parametr. Nastavte hodnotu <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnosti, chcete-li `true` zabránit odeslání prázdné zprávy odpovědi. Ve výchozím nastavení jsou všechny operace smlouvy požadavku odpověď.  
  
## <a name="example"></a>Příklad  
 Následující ukázka definuje smlouvu pro službu kalkulačky, která poskytuje `Add` a `Subtract` metody. Metoda `Multiply` není součástí smlouvy, protože není označena <xref:System.ServiceModel.OperationContractAttribute> třídou, a proto není přístupná klientům.  
  
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
  
- Další informace o tom, jak určit <xref:System.ServiceModel.OperationContractAttribute> smlouvy <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> operace, naleznete třídy a vlastnost.  
  
- Použití <xref:System.ServiceModel.ServiceContractAttribute> atributů a <xref:System.ServiceModel.OperationContractAttribute> způsobí automatické generování definic servisnísmlouvy v dokumentu jazyka WSDL (Web Services Description Language) po nasazení služby. Dokument se stáhne připojením `?wsdl` k základní adrese HTTP pro službu. Například `http://microsoft/CalculatorService?wsdl`.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.OperationContractAttribute>
- [Navrhování kontraktů služby](../../../../docs/framework/wcf/designing-service-contracts.md)
- [Postupy: Vytvoření duplexního kontraktu](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)
