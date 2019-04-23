---
title: Implementace kontraktů služeb
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: 766e0c4d30a4fa0eed9ce154ca932f5371a43211
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59196317"
---
# <a name="implementing-service-contracts"></a>Implementace kontraktů služeb
Služba je třída, která zpřístupňuje funkce, které jsou k dispozici pro klienty na jeden nebo více koncových bodů. Pokud chcete vytvořit službu, zápis třídu, která implementuje kontraktu Windows Communication Foundation (WCF). Provedete to jedním ze dvou způsobů. Můžete definovat kontrakt samostatně jako rozhraní a pak vytvořit třídu, která implementuje rozhraní. Alternativně můžete vytvořit třídu a kontrakt přímo tak, že <xref:System.ServiceModel.ServiceContractAttribute> atributu na vlastní třídy a <xref:System.ServiceModel.OperationContractAttribute> atributů pro metody, které jsou k dispozici pro klienty službu.  
  
## <a name="creating-a-service-class"></a>Vytvoření třídy služby  
 Následuje příklad služby, který implementuje `IMath` kontrakt, který byl definován samostatně.  
  
```csharp  
// Define the IMath contract.  
[ServiceContract]  
public interface IMath  
{  
    [OperationContract]   
    double Add(double A, double B);  
  
    [OperationContract]  
    double Multiply (double A, double B);  
}  
  
// Implement the IMath contract in the MathService class.  
public class MathService : IMath  
{  
    public double Add (double A, double B) { return A + B; }  
    public double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 Služby, případně můžete zveřejnění kontraktu přímo. Následující je příkladem služby třídu, která definuje a implementuje `MathService` kontraktu.  
  
```csharp  
// Define the MathService contract directly on the service class.  
[ServiceContract]  
class MathService  
{  
    [OperationContract]  
    public double Add(double A, double B) { return A + B; }  
    [OperationContract]  
    private double Multiply (double A, double B) { return A * B; }  
}  
```  
  
 Všimněte si, že předchozí služby vystavují různé kontrakty, protože se liší názvy kontraktu. V prvním případě je zveřejněné kontraktu s názvem "`IMath`"zatímco ve druhém případě je s názvem kontraktu"`MathService`".  
  
 Pár věcí můžete nastavit na služby a operace implementace úrovně, jako je například souběžnosti a vytváření instancí. Další informace najdete v tématu [návrh a implementace služeb](../../../docs/framework/wcf/designing-and-implementing-services.md).  
  
 Po implementaci kontraktu služby, je potřeba vytvořit jeden nebo víc koncových bodů služby. Další informace najdete v tématu [Přehled vytváření koncových bodů](../../../docs/framework/wcf/endpoint-creation-overview.md). Další informace o tom, jak spustit službu, naleznete v tématu [hostování služeb](../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Navrhování a implementace služeb](../../../docs/framework/wcf/designing-and-implementing-services.md)
- [Postupy: Vytvoření služby s třídou kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [Postupy: Vytvoření služby pomocí rozhraní kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [Určování chování služby za běhu](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
