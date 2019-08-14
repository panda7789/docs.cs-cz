---
title: 'Postupy: Deklarace chyb v kontraktech služeb'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
ms.openlocfilehash: 6f08ef6eb62b31b0969779d51d0a068145a23fc0
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68971972"
---
# <a name="how-to-declare-faults-in-service-contracts"></a><span data-ttu-id="ba0e6-102">Postupy: Deklarace chyb v kontraktech služeb</span><span class="sxs-lookup"><span data-stu-id="ba0e6-102">How to: Declare Faults in Service Contracts</span></span>

<span data-ttu-id="ba0e6-103">Ve spravovaném kódu jsou výjimky vyvolány, pokud dojde k chybovým podmínkám.</span><span class="sxs-lookup"><span data-stu-id="ba0e6-103">In managed code, exceptions are thrown when error conditions occur.</span></span> <span data-ttu-id="ba0e6-104">V aplikacích Windows Communication Foundation (WCF) však kontrakty služby určují, jaké informace o chybách se vrátí klientům prostřednictvím deklarace chyb protokolu SOAP v kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="ba0e6-104">In Windows Communication Foundation (WCF) applications, however, service contracts specify what error information is returned to clients by declaring SOAP faults in the service contract.</span></span> <span data-ttu-id="ba0e6-105">Přehled vztahů mezi výjimkami a chybami najdete v tématu [určení a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="ba0e6-105">For an overview of the relationship between exceptions and faults, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>

## <a name="create-a-service-contract-that-specifies-a-soap-fault"></a><span data-ttu-id="ba0e6-106">Vytvoření kontraktu služby, který určuje chybu protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="ba0e6-106">Create a service contract that specifies a SOAP fault</span></span>

1. <span data-ttu-id="ba0e6-107">Vytvořte kontrakt služby, který obsahuje alespoň jednu operaci.</span><span class="sxs-lookup"><span data-stu-id="ba0e6-107">Create a service contract that contains at least one operation.</span></span> <span data-ttu-id="ba0e6-108">Příklad naleznete v tématu [How to: Definujte kontrakt](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md)služby.</span><span class="sxs-lookup"><span data-stu-id="ba0e6-108">For an example, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>

2. <span data-ttu-id="ba0e6-109">Vyberte operaci, která může určit chybový stav, o které můžou klienti očekávat upozorňování.</span><span class="sxs-lookup"><span data-stu-id="ba0e6-109">Select an operation that can specify an error condition about which clients can expect to be notified.</span></span> <span data-ttu-id="ba0e6-110">Informace o tom, které chybové stavy opravňují k vrácení chyb protokolu SOAP klientům, najdete v tématu [určení a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="ba0e6-110">To decide which error conditions justify returning SOAP faults to clients, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>

3. <span data-ttu-id="ba0e6-111"><xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> Použijte pro vybranou operaci a předejte do konstruktoru serializovatelný typ selhání.</span><span class="sxs-lookup"><span data-stu-id="ba0e6-111">Apply a <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> to the selected operation and pass a serializable fault type to the constructor.</span></span> <span data-ttu-id="ba0e6-112">Podrobnosti o vytváření a používání serializovatelných typů najdete v tématu [určení přenos dat v kontraktech služeb](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="ba0e6-112">For details about creating and using serializable types, see [Specifying Data Transfer in Service Contracts](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span></span> <span data-ttu-id="ba0e6-113">Následující příklad ukazuje, jak určit, že `SampleMethod` operace může mít za následek. `GreetingFault`</span><span class="sxs-lookup"><span data-stu-id="ba0e6-113">The following example shows how to specify that the `SampleMethod` operation can result in a `GreetingFault`.</span></span>

     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]

4. <span data-ttu-id="ba0e6-114">Opakujte kroky 2 a 3 pro všechny operace v kontraktu, které komunikují chybové stavy klientům.</span><span class="sxs-lookup"><span data-stu-id="ba0e6-114">Repeat steps 2 and 3 for all operations in the contract that communicate error conditions to clients.</span></span>

## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a><span data-ttu-id="ba0e6-115">Implementace operace pro vrácení zadané chyby protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="ba0e6-115">Implementing an Operation to Return a Specified SOAP Fault</span></span>
 <span data-ttu-id="ba0e6-116">Jakmile operace určí, že může být vrácena konkrétní chyba protokolu SOAP (například v předchozím postupu) pro komunikaci s chybovou podmínkou volající aplikace, je dalším krokem implementace této specifikace.</span><span class="sxs-lookup"><span data-stu-id="ba0e6-116">Once an operation has specified that a specific SOAP fault can be returned (such as in the preceding procedure) to communicate an error condition to a calling application, the next step is to implement that specification.</span></span>

### <a name="throw-the-specified-soap-fault-in-the-operation"></a><span data-ttu-id="ba0e6-117">Vygenerovat určenou chybu protokolu SOAP v operaci</span><span class="sxs-lookup"><span data-stu-id="ba0e6-117">Throw the specified SOAP fault in the operation</span></span>

1. <span data-ttu-id="ba0e6-118">Pokud se v operaci vyskytne chybový stav, vyvolejte nový <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> , kde zadaná Chyba protokolu SOAP je parametr typu. <xref:System.ServiceModel.FaultContractAttribute></span><span class="sxs-lookup"><span data-stu-id="ba0e6-118">When a <xref:System.ServiceModel.FaultContractAttribute>-specified error condition occurs in an operation, throw a new <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> where the specified SOAP fault is the type parameter.</span></span> <span data-ttu-id="ba0e6-119">Následující příklad ukazuje, jak vyvolat `GreetingFault` `SampleMethod` v uvedeném postupu v předchozím postupu a v následující části kódu.</span><span class="sxs-lookup"><span data-stu-id="ba0e6-119">The following example shows how to throw the `GreetingFault` in the `SampleMethod` shown in the preceding procedure and in the following Code section.</span></span>

     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]

## <a name="example"></a><span data-ttu-id="ba0e6-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="ba0e6-120">Example</span></span>

<span data-ttu-id="ba0e6-121">Následující příklad kódu ukazuje implementaci jediné operace, která určuje `GreetingFault` `SampleMethod` pro operaci.</span><span class="sxs-lookup"><span data-stu-id="ba0e6-121">The following code example shows an implementation of a single operation that specifies a `GreetingFault` for the `SampleMethod` operation.</span></span>

[!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
[!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]

## <a name="see-also"></a><span data-ttu-id="ba0e6-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba0e6-122">See also</span></span>

- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
