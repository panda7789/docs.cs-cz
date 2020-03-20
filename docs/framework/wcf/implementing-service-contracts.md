---
title: Implementace kontraktů služeb
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: aefe146a8941d98d7d9138e4ece83c330c967034
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184006"
---
# <a name="implementing-service-contracts"></a>Implementace kontraktů služeb
Služba je třída, která zveřejňuje funkce, které jsou k dispozici klientům v jednom nebo více koncových bodech. Chcete-li vytvořit službu, napište třídu, která implementuje smlouvu WCF (Windows Communication Foundation). Můžete to provést dvěma způsoby. Můžete definovat smlouvu samostatně jako rozhraní a potom vytvořit třídu, která implementuje toto rozhraní. Případně můžete vytvořit třídu a smlouvu <xref:System.ServiceModel.ServiceContractAttribute> přímo umístěním atributu <xref:System.ServiceModel.OperationContractAttribute> na samotnou třídu a atribut na metody, které jsou k dispozici klientům služby.  
  
## <a name="creating-a-service-class"></a>Vytvoření třídy služeb  
 Následuje příklad služby, která implementuje smlouvu, `IMath` která byla definována samostatně.  
  
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
  
 Alternativně služba může vystavit smlouvy přímo. Následuje příklad třídy služeb, která definuje a `MathService` implementuje smlouvu.  
  
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
  
 Všimněte si, že předchozí služby vystavit různé smlouvy, protože názvy smluv se liší. V prvním případě je exponovaná`IMath`smlouva pojmenována " ",`MathService`zatímco v druhém případě je smlouva pojmenována " ".  
  
 Můžete nastavit několik věcí na úrovni implementace služby a operace, jako je například souběžnost a instance. Další informace naleznete v [tématu Návrh a implementace služeb](designing-and-implementing-services.md).  
  
 Po implementaci smlouvy o poskytování služeb je nutné vytvořit jeden nebo více koncových bodů pro službu. Další informace naleznete v [tématu Přehled vytváření koncových bodů](endpoint-creation-overview.md). Další informace o spuštění služby naleznete v [tématu Hosting Services](hosting-services.md).  
  
## <a name="see-also"></a>Viz také

- [Navrhování a implementace služeb](designing-and-implementing-services.md)
- [Postupy: Vytvoření služby s třídou kontraktu](./feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [Postupy: Vytvoření služby pomocí rozhraní kontraktu](./feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [Určování chování služby za běhu](specifying-service-run-time-behavior.md)
