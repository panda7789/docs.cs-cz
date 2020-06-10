---
title: 'Postupy: Vytvoření kontraktu požadavku a odpovědi'
ms.date: 03/30/2017
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
ms.openlocfilehash: 8a09c265c77edc584b591477e64314f1e76e332b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593435"
---
# <a name="how-to-create-a-request-reply-contract"></a>Postupy: Vytvoření kontraktu požadavku a odpovědi
Kontrakt požadavek-odpověď určuje metodu, která vrací odpověď. Odpověď musí být zaslána a koreluje s požadavkem v rámci podmínek této smlouvy. I v případě, že metoda nevrátí žádnou odpověď ( `void` v jazyce C# nebo `Sub` v Visual Basic), infrastruktura vytvoří a pošle prázdnou zprávu volajícímu. Chcete-li zabránit odeslání prázdné zprávy s odpovědí, použijte pro tuto operaci jednosměrný kontrakt.  
  
### <a name="to-create-a-request-reply-contract"></a>Vytvoření kontraktu požadavku a odpovědi  
  
1. Vytvořte rozhraní v programovacím jazyce podle vašeho výběru.  
  
2. Použijte <xref:System.ServiceModel.ServiceContractAttribute> atribut pro rozhraní.  
  
3. Použijte <xref:System.ServiceModel.OperationContractAttribute> atribut na každou metodu, kterou mohou klienti vyvolat.  
  
4. Nepovinný parametr. Nastavte hodnotu <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnosti na, chcete `true` -li zabránit odeslání prázdné zprávy s odpovědí. Ve výchozím nastavení jsou všechny operace kontraktů požadavků a odpovědí.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje kontrakt pro službu kalkulačky, která poskytuje `Add` metody a `Subtract` . `Multiply`Metoda není součástí kontraktu, protože není označena <xref:System.ServiceModel.OperationContractAttribute> třídou, takže není přístupná pro klienty.  
  
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
  
- Další informace o tom, jak zadat kontrakty operací, naleznete v tématu <xref:System.ServiceModel.OperationContractAttribute> Třída a <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> vlastnost.  
  
- Použití <xref:System.ServiceModel.ServiceContractAttribute> atributů a <xref:System.ServiceModel.OperationContractAttribute> způsobuje automatickou generaci definic kontraktů služby v dokumentu WSDL (Web Services Description Language) po nasazení služby. Dokument se stáhne připojením `?wsdl` k základní adrese http služby. Například `http://microsoft/CalculatorService?wsdl`.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.OperationContractAttribute>
- [Navrhování kontraktů služby](../designing-service-contracts.md)
- [Postupy: Vytvoření duplexního kontraktu](how-to-create-a-duplex-contract.md)
