---
title: "Implementace kontraktů služeb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: implementing service contracts [WCF]
ms.assetid: aefb6f56-47e3-4f24-ab0a-9bc07bf9885f
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0b40b93b33e57bf15b7ab614405ccffa44abb8df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-service-contracts"></a>Implementace kontraktů služeb
Služba je třída, která poskytuje funkce, které jsou k dispozici pro klienty na jeden nebo více koncových bodů. Pokud chcete vytvořit službu, zápis třídu, která implementuje [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] kontrakt. Provedete to jedním ze dvou způsobů. Můžete definovat kontrakt samostatně jako rozhraní a pak vytvořte třídu, která implementuje rozhraní. Alternativně můžete vytvořit třídu a kontrakt přímo tím, že <xref:System.ServiceModel.ServiceContractAttribute> atributu na vlastní třídy a <xref:System.ServiceModel.OperationContractAttribute> atribut pro metody, které jsou k dispozici pro klienty služby.  
  
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
  
 Pár věcí můžete nastavit na služby a operace implementace úrovně, jako je například souběžnosti a vytváření instancí. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Navrhování a implementace služeb](../../../docs/framework/wcf/designing-and-implementing-services.md).  
  
 Po implementaci kontraktu služby, je nutné vytvořit jeden nebo více koncových bodů pro službu. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][Přehled vytváření koncových bodů](../../../docs/framework/wcf/endpoint-creation-overview.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)]spuštění služby najdete v tématu [hostování služeb](../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Navrhování a implementace služeb](../../../docs/framework/wcf/designing-and-implementing-services.md)  
 [Postupy: vytvoření služby s třídou kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-wcf-contract-with-a-class.md)  
 [Postupy: vytvoření služby pomocí rozhraní kontraktu](../../../docs/framework/wcf/feature-details/how-to-create-a-service-with-a-contract-interface.md)  
 [Určení chování služby](../../../docs/framework/wcf/specifying-service-run-time-behavior.md)
