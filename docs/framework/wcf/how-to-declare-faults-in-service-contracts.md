---
title: 'Postupy: Deklarace chyb v kontraktech služeb'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
ms.openlocfilehash: 0e173f71201d5f98a04d2ad922469e4ff6666681
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61929282"
---
# <a name="how-to-declare-faults-in-service-contracts"></a>Postupy: Deklarace chyb v kontraktech služeb
Ve spravovaném kódu jsou výjimky vyvolány, když dojde k chybě podmínek. V aplikacích Windows Communication Foundation (WCF) nicméně kontrakty služeb určit, jaké informace o chybě je vrácena klientům deklarováním chyb SOAP v kontraktu služby. Přehled o vztah mezi výjimek a chyb, naleznete v tématu [zadání a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
### <a name="create-a-service-contract-that-specifies-a-soap-fault"></a>Vytvoření kontraktu služby, který určuje nastala chyba protokolu SOAP  
  
1. Vytvoření kontraktu služby, který obsahuje alespoň jednu operaci. Příklad najdete v tématu [jak: Definování kontraktu služby](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).  
  
2. Vyberte operaci, která můžete zadat chybového stavu o tom, které klienty můžete očekávat, že chcete být upozorňováni. Rozhodněte, které chybové stavy zarovnat vracení chyb SOAP pro klienty, najdete v článku [zadání a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).  
  
3. Použít <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> vybranou operaci a předejte serializovatelný chybu typu konstruktoru. Podrobnosti o vytváření a používání Serializovatelné typy najdete v tématu [zadání přenosu dat v kontraktech služeb](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md). Následující příklad ukazuje, jak určit, že `SampleMethod` můžou výsledkem operace `GreetingFault`.  
  
     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
4. Zopakujte kroky 2 a 3 pro všechny operace v kontraktu, které komunikují chybové stavy klientům.  
  
## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a>Implementace operace vrátit chybu zadaného protokolu SOAP  
 Po operaci určil, že konkrétní chyba protokolu SOAP mohou být vráceny (například v předchozím postupu) ke komunikaci chybový stav volající aplikace, dalším krokem je implementace specifikaci.  
  
#### <a name="throw-the-specified-soap-fault-in-the-operation"></a>Vyvolá zadanou chybu protokolu SOAP v operaci  
  
1. Když <xref:System.ServiceModel.FaultContractAttribute>– zadané dojde k chybě v operaci throw nový <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> kde zadanou chybu protokolu SOAP je parametr typu. Následující příklad ukazuje, jak vyvolat `GreetingFault` v `SampleMethod` je znázorněno v předchozím postupu a v části kódu.  
  
     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje implementaci, který určuje jednu operaci `GreetingFault` pro `SampleMethod` operace.  
  
 [!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
 [!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
