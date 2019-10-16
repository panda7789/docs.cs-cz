---
title: Implementace kontraktů služeb
ms.date: 03/30/2017
helpviewer_keywords:
- implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
ms.openlocfilehash: ac27329278edc2b9ca693aa15bcc5bb58edffe05
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320164"
---
# <a name="implementing-service-contracts"></a>Implementace kontraktů služeb
Služba je třída, která zpřístupňuje funkce dostupné klientům v jednom nebo více koncových bodech. Chcete-li vytvořit službu, napište třídu, která implementuje kontrakt Windows Communication Foundation (WCF). To můžete provést jedním ze dvou způsobů. Kontrakt můžete definovat samostatně jako rozhraní a pak vytvořit třídu, která implementuje toto rozhraní. Alternativně můžete vytvořit třídu a kontrakt přímo tak, že umístíte atribut <xref:System.ServiceModel.ServiceContractAttribute> do samotné třídy a atribut <xref:System.ServiceModel.OperationContractAttribute> pro metody, které jsou k dispozici pro klienty služby.  
  
## <a name="creating-a-service-class"></a>Vytvoření třídy služby  
 Následuje příklad služby, která implementuje kontrakt `IMath`, který byl definován samostatně.  
  
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
  
 Případně může služba vystavit kontrakt přímo. Následuje příklad třídy služby, která definuje a implementuje kontrakt `MathService`.  
  
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
  
 Všimněte si, že předchozí služby zveřejňují různé kontrakty, protože názvy kontraktů se liší. V prvním případě se kontrakt s názvem "`IMath`" v druhém případě nazývá kontrakt "`MathService`".  
  
 Na úrovních implementace služby a operace můžete nastavit pár věcí, jako je například souběžnost a vytváření instancí. Další informace najdete v tématu [navrhování a implementace služeb](designing-and-implementing-services.md).  
  
 Po implementaci kontraktu služby musíte pro službu vytvořit jeden nebo více koncových bodů. Další informace najdete v tématu [Přehled vytváření koncových bodů](endpoint-creation-overview.md). Další informace o tom, jak spustit službu, najdete v tématu [hostingové služby](hosting-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Navrhování a implementace služeb](designing-and-implementing-services.md)
- [Postupy: Vytvoření služby s třídou kontraktu](./feature-details/how-to-create-a-wcf-contract-with-a-class.md)
- [Postupy: Vytvoření služby pomocí rozhraní kontraktu](./feature-details/how-to-create-a-service-with-a-contract-interface.md)
- [Určování chování služby za běhu](specifying-service-run-time-behavior.md)
