---
title: Implementace kontraktů služeb
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: 4e6570291571815781ce543f5991ae40ed57d1e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-service-contracts"></a>Implementace kontraktů služeb
Služba je třída, která poskytuje funkce, které jsou k dispozici pro klienty na jeden nebo více koncových bodů. Pokud chcete vytvořit službu, zapisovat třídu, která implementuje kontraktu Windows Communication Foundation (WCF). Provedete to jedním ze dvou způsobů. Můžete definovat kontrakt samostatně jako rozhraní a pak vytvořte třídu, která implementuje rozhraní. Alternativně můžete vytvořit třídu a kontrakt přímo tím, že <xref:System.ServiceModel.ServiceContractAttribute> atributu na vlastní třídy a <xref:System.ServiceModel.OperationContractAttribute> atribut pro metody, které jsou k dispozici pro klienty služby.  
  
## <a name="creating-a-service-class"></a>Vytvoření třídy služby  
 Následuje příklad služby, který implementuje `IMath` kontraktu, která byla definována samostatně.  
  
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
  
 Službu můžete taky můžou zpřístupnit kontraktu přímo. Následuje příklad třídy služby, která definuje a implementuje `MathService` kontrakt.  
  
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
  
 Všimněte si, že předchozí služby vystavit různých kontrakty vzhledem k tomu, že názvy kontraktu se liší. V prvním případě zveřejněné kontrakt název "`IMath`"při v druhém případě je název kontraktu"`MathService`".  
  
 Pár věcí můžete nastavit na služby a operace implementace úrovně, jako je například souběžnosti a vytváření instancí. Další informace najdete v tématu [návrh a implementace služeb](../../../docs/framework/wcf/designing-and-implementing-services.md).  
  
 Po implementaci kontraktu služby, je nutné vytvořit jeden nebo více koncových bodů pro službu. Další informace najdete v tématu [Přehled vytváření koncových bodů](../../../docs/framework/wcf/endpoint-creation-overview.md). Další informace o tom, jak spustit služby najdete v tématu [hostování služeb](../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Navrhování a implementace služeb](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [Postupy: Vytvoření služby s třídou kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md)  
 [Postupy: Vytvoření služby pomocí rozhraní kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md)  
 [Určování chování služby za běhu](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
