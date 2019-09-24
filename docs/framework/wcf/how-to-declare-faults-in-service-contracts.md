---
title: 'Postupy: Deklarace chyb v kontraktech služeb'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
ms.openlocfilehash: 2de14a76fd2ce8ad656c2b64f5f9e5b17d81eebc
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216860"
---
# <a name="how-to-declare-faults-in-service-contracts"></a>Postupy: Deklarace chyb v kontraktech služeb

Ve spravovaném kódu jsou výjimky vyvolány, pokud dojde k chybovým podmínkám. V aplikacích Windows Communication Foundation (WCF) však kontrakty služby určují, jaké informace o chybách se vrátí klientům prostřednictvím deklarace chyb protokolu SOAP v kontraktu služby. Přehled vztahů mezi výjimkami a chybami najdete v tématu [určení a zpracování chyb v kontraktech a službách](specifying-and-handling-faults-in-contracts-and-services.md).

## <a name="create-a-service-contract-that-specifies-a-soap-fault"></a>Vytvoření kontraktu služby, který určuje chybu protokolu SOAP

1. Vytvořte kontrakt služby, který obsahuje alespoň jednu operaci. Příklad naleznete v tématu [How to: Definujte kontrakt](how-to-define-a-wcf-service-contract.md)služby.

2. Vyberte operaci, která může určit chybový stav, o které můžou klienti očekávat upozorňování. Informace o tom, které chybové stavy opravňují k vrácení chyb protokolu SOAP klientům, najdete v tématu [určení a zpracování chyb v kontraktech a službách](specifying-and-handling-faults-in-contracts-and-services.md).

3. <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> Použijte pro vybranou operaci a předejte do konstruktoru serializovatelný typ selhání. Podrobnosti o vytváření a používání serializovatelných typů najdete v tématu [určení přenos dat v kontraktech služeb](./feature-details/specifying-data-transfer-in-service-contracts.md). Následující příklad ukazuje, jak určit, že `SampleMethod` operace může mít za následek. `GreetingFault`

     [!code-csharp[FaultContractAttribute#4](~/samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](~/samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]

4. Opakujte kroky 2 a 3 pro všechny operace v kontraktu, které komunikují chybové stavy klientům.

## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a>Implementace operace pro vrácení zadané chyby protokolu SOAP
 Jakmile operace určí, že může být vrácena konkrétní chyba protokolu SOAP (například v předchozím postupu) pro komunikaci s chybovou podmínkou volající aplikace, je dalším krokem implementace této specifikace.

### <a name="throw-the-specified-soap-fault-in-the-operation"></a>Vygenerovat určenou chybu protokolu SOAP v operaci

1. Pokud se v operaci vyskytne chybový stav, vyvolejte nový <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> , kde zadaná Chyba protokolu SOAP je parametr typu. <xref:System.ServiceModel.FaultContractAttribute> Následující příklad ukazuje, jak vyvolat `GreetingFault` `SampleMethod` v uvedeném postupu v předchozím postupu a v následující části kódu.

     [!code-csharp[FaultContractAttribute#5](~/samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](~/samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]

## <a name="example"></a>Příklad

Následující příklad kódu ukazuje implementaci jediné operace, která určuje `GreetingFault` `SampleMethod` pro operaci.

[!code-csharp[FaultContractAttribute#1](~/samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
[!code-vb[FaultContractAttribute#1](~/samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]

## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
