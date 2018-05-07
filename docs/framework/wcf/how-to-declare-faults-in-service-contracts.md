---
title: 'Postupy: deklarace chyb v kontraktech služby'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
ms.openlocfilehash: 142ad26702f0732bc5103e29d5a44bc57ab37625
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-declare-faults-in-service-contracts"></a>Postupy: deklarace chyb v kontraktech služby
Ve spravovaném kódu jsou výjimky vyvolány, když dojde k chybové stavy. V aplikacích Windows Communication Foundation (WCF) nicméně kontraktů služby určit, jaké informace o chybě vrátí klientům deklarace chyb protokolu SOAP v kontrakt služby. Přehled o vztah mezi výjimek a chyb naleznete v tématu [zadání a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
### <a name="create-a-service-contract-that-specifies-a-soap-fault"></a>Vytvoření kontraktu služby, který určuje protokolu SOAP  
  
1.  Vytvoření kontraktu služby, který obsahuje nejméně jednu operaci. Příklad, naleznete v části [postupy: definování kontraktu služby](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).  
  
2.  Vyberte operaci, můžete zadat o tom, které klienty můžete očekávat, že mají být informování chybový stav. Rozhodněte, které chybové stavy justify vrácení chyb SOAP klientům, najdete v tématu [zadání a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
3.  Použít <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> pro vybranou operaci a předejte jí typu serializable chybu konstruktoru. Podrobnosti o vytváření a používání Serializovatelné typy najdete v tématu [zadání přenos dat v kontraktech služby](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Následující příklad ukazuje, jak určit, že `SampleMethod` může mít za následek operace `GreetingFault`.  
  
     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
4.  Opakujte kroky 2 a 3 pro všechny operace v kontraktu, které komunikují chybové stavy klientům.  
  
## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a>Implementace operace vrátí zadaného protokolu SOAP  
 Po operaci byla zadána, že konkrétní chyba protokolu SOAP se může vracet (například jako v předchozím postupu) ke komunikaci chybový stav pro volající aplikace, dalším krokem je implementace této specifikaci.  
  
#### <a name="throw-the-specified-soap-fault-in-the-operation"></a>V operaci throw zadaný chybu protokolu SOAP  
  
1.  Když <xref:System.ServiceModel.FaultContractAttribute>-zadaný chybovému stavu dojde v operaci, throw novou <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> kde zadaný chybu protokolu SOAP se parametr typu. Následující příklad ukazuje, jak má být vyvolána `GreetingFault` v `SampleMethod` vidět v předchozím postupu a v následující části kódu.  
  
     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje implementaci pro jednu operaci, která určuje `GreetingFault` pro `SampleMethod` operaci.  
  
 [!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
 [!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>  
 <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
