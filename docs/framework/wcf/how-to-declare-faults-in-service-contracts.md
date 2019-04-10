---
title: 'Postupy: Deklarace chyb v kontraktech služeb'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
ms.openlocfilehash: 0e173f71201d5f98a04d2ad922469e4ff6666681
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59327071"
---
# <a name="how-to-declare-faults-in-service-contracts"></a><span data-ttu-id="57009-102">Postupy: Deklarace chyb v kontraktech služeb</span><span class="sxs-lookup"><span data-stu-id="57009-102">How to: Declare Faults in Service Contracts</span></span>
<span data-ttu-id="57009-103">Ve spravovaném kódu jsou výjimky vyvolány, když dojde k chybě podmínek.</span><span class="sxs-lookup"><span data-stu-id="57009-103">In managed code, exceptions are thrown when error conditions occur.</span></span> <span data-ttu-id="57009-104">V aplikacích Windows Communication Foundation (WCF) nicméně kontrakty služeb určit, jaké informace o chybě je vrácena klientům deklarováním chyb SOAP v kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="57009-104">In Windows Communication Foundation (WCF) applications, however, service contracts specify what error information is returned to clients by declaring SOAP faults in the service contract.</span></span> <span data-ttu-id="57009-105">Přehled o vztah mezi výjimek a chyb, naleznete v tématu [zadání a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="57009-105">For an overview of the relationship between exceptions and faults, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
### <a name="create-a-service-contract-that-specifies-a-soap-fault"></a><span data-ttu-id="57009-106">Vytvoření kontraktu služby, který určuje nastala chyba protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="57009-106">Create a service contract that specifies a SOAP fault</span></span>  
  
1. <span data-ttu-id="57009-107">Vytvoření kontraktu služby, který obsahuje alespoň jednu operaci.</span><span class="sxs-lookup"><span data-stu-id="57009-107">Create a service contract that contains at least one operation.</span></span> <span data-ttu-id="57009-108">Příklad najdete v tématu [jak: Definování kontraktu služby](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="57009-108">For an example, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>  
  
2. <span data-ttu-id="57009-109">Vyberte operaci, která můžete zadat chybového stavu o tom, které klienty můžete očekávat, že chcete být upozorňováni.</span><span class="sxs-lookup"><span data-stu-id="57009-109">Select an operation that can specify an error condition about which clients can expect to be notified.</span></span> <span data-ttu-id="57009-110">Rozhodněte, které chybové stavy zarovnat vracení chyb SOAP pro klienty, najdete v článku [zadání a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="57009-110">To decide which error conditions justify returning SOAP faults to clients, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
3. <span data-ttu-id="57009-111">Použít <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> vybranou operaci a předejte serializovatelný chybu typu konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="57009-111">Apply a <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> to the selected operation and pass a serializable fault type to the constructor.</span></span> <span data-ttu-id="57009-112">Podrobnosti o vytváření a používání Serializovatelné typy najdete v tématu [zadání přenosu dat v kontraktech služeb](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="57009-112">For details about creating and using serializable types, see [Specifying Data Transfer in Service Contracts](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span></span> <span data-ttu-id="57009-113">Následující příklad ukazuje, jak určit, že `SampleMethod` můžou výsledkem operace `GreetingFault`.</span><span class="sxs-lookup"><span data-stu-id="57009-113">The following example shows how to specify that the `SampleMethod` operation can result in a `GreetingFault`.</span></span>  
  
     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
4. <span data-ttu-id="57009-114">Zopakujte kroky 2 a 3 pro všechny operace v kontraktu, které komunikují chybové stavy klientům.</span><span class="sxs-lookup"><span data-stu-id="57009-114">Repeat steps 2 and 3 for all operations in the contract that communicate error conditions to clients.</span></span>  
  
## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a><span data-ttu-id="57009-115">Implementace operace vrátit chybu zadaného protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="57009-115">Implementing an Operation to Return a Specified SOAP Fault</span></span>  
 <span data-ttu-id="57009-116">Po operaci určil, že konkrétní chyba protokolu SOAP mohou být vráceny (například v předchozím postupu) ke komunikaci chybový stav volající aplikace, dalším krokem je implementace specifikaci.</span><span class="sxs-lookup"><span data-stu-id="57009-116">Once an operation has specified that a specific SOAP fault can be returned (such as in the preceding procedure) to communicate an error condition to a calling application, the next step is to implement that specification.</span></span>  
  
#### <a name="throw-the-specified-soap-fault-in-the-operation"></a><span data-ttu-id="57009-117">Vyvolá zadanou chybu protokolu SOAP v operaci</span><span class="sxs-lookup"><span data-stu-id="57009-117">Throw the specified SOAP fault in the operation</span></span>  
  
1. <span data-ttu-id="57009-118">Když <xref:System.ServiceModel.FaultContractAttribute>– zadané dojde k chybě v operaci throw nový <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> kde zadanou chybu protokolu SOAP je parametr typu.</span><span class="sxs-lookup"><span data-stu-id="57009-118">When a <xref:System.ServiceModel.FaultContractAttribute>-specified error condition occurs in an operation, throw a new <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> where the specified SOAP fault is the type parameter.</span></span> <span data-ttu-id="57009-119">Následující příklad ukazuje, jak vyvolat `GreetingFault` v `SampleMethod` je znázorněno v předchozím postupu a v části kódu.</span><span class="sxs-lookup"><span data-stu-id="57009-119">The following example shows how to throw the `GreetingFault` in the `SampleMethod` shown in the preceding procedure and in the following Code section.</span></span>  
  
     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="57009-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="57009-120">Example</span></span>  
 <span data-ttu-id="57009-121">Následující příklad kódu ukazuje implementaci, který určuje jednu operaci `GreetingFault` pro `SampleMethod` operace.</span><span class="sxs-lookup"><span data-stu-id="57009-121">The following code example shows an implementation of a single operation that specifies a `GreetingFault` for the `SampleMethod` operation.</span></span>  
  
 [!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
 [!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="57009-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57009-122">See also</span></span>

- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
