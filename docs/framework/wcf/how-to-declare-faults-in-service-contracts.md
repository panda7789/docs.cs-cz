---
title: "Postupy: deklarace chyb v kontraktech služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: e8da98e7-d22f-4f60-ac82-3fb0928a353f
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bcf707e58586673097c89e0e0f4d72ea68ef7247
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-declare-faults-in-service-contracts"></a><span data-ttu-id="cd278-102">Postupy: deklarace chyb v kontraktech služby</span><span class="sxs-lookup"><span data-stu-id="cd278-102">How to: Declare Faults in Service Contracts</span></span>
<span data-ttu-id="cd278-103">Ve spravovaném kódu jsou výjimky vyvolány, když dojde k chybové stavy.</span><span class="sxs-lookup"><span data-stu-id="cd278-103">In managed code, exceptions are thrown when error conditions occur.</span></span> <span data-ttu-id="cd278-104">V [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikace, ale kontraktů služby určit, jaké informace o chybě vrátí klientům deklarace chyb protokolu SOAP v kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="cd278-104">In [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] applications, however, service contracts specify what error information is returned to clients by declaring SOAP faults in the service contract.</span></span> <span data-ttu-id="cd278-105">Přehled o vztah mezi výjimek a chyb naleznete v tématu [zadání a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="cd278-105">For an overview of the relationship between exceptions and faults, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
### <a name="create-a-service-contract-that-specifies-a-soap-fault"></a><span data-ttu-id="cd278-106">Vytvoření kontraktu služby, který určuje protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="cd278-106">Create a service contract that specifies a SOAP fault</span></span>  
  
1.  <span data-ttu-id="cd278-107">Vytvoření kontraktu služby, který obsahuje nejméně jednu operaci.</span><span class="sxs-lookup"><span data-stu-id="cd278-107">Create a service contract that contains at least one operation.</span></span> <span data-ttu-id="cd278-108">Příklad, naleznete v části [postupy: definování kontraktu služby](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span><span class="sxs-lookup"><span data-stu-id="cd278-108">For an example, see [How to: Define a Service Contract](../../../docs/framework/wcf/how-to-define-a-wcf-service-contract.md).</span></span>  
  
2.  <span data-ttu-id="cd278-109">Vyberte operaci, můžete zadat o tom, které klienty můžete očekávat, že mají být informování chybový stav.</span><span class="sxs-lookup"><span data-stu-id="cd278-109">Select an operation that can specify an error condition about which clients can expect to be notified.</span></span> <span data-ttu-id="cd278-110">Rozhodněte, které chybové stavy justify vrácení chyb SOAP klientům, najdete v tématu [zadání a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span><span class="sxs-lookup"><span data-stu-id="cd278-110">To decide which error conditions justify returning SOAP faults to clients, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md).</span></span>  
  
3.  <span data-ttu-id="cd278-111">Použít <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> pro vybranou operaci a předejte jí typu serializable chybu konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="cd278-111">Apply a <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType> to the selected operation and pass a serializable fault type to the constructor.</span></span> <span data-ttu-id="cd278-112">Podrobnosti o vytváření a používání Serializovatelné typy najdete v tématu [zadání přenos dat v kontraktech služby](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="cd278-112">For details about creating and using serializable types, see [Specifying Data Transfer in Service Contracts](../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).</span></span> <span data-ttu-id="cd278-113">Následující příklad ukazuje, jak určit, že `SampleMethod` může mít za následek operace `GreetingFault`.</span><span class="sxs-lookup"><span data-stu-id="cd278-113">The following example shows how to specify that the `SampleMethod` operation can result in a `GreetingFault`.</span></span>  
  
     [!code-csharp[FaultContractAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#4)]
     [!code-vb[FaultContractAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#4)]  
  
4.  <span data-ttu-id="cd278-114">Opakujte kroky 2 a 3 pro všechny operace v kontraktu, které komunikují chybové stavy klientům.</span><span class="sxs-lookup"><span data-stu-id="cd278-114">Repeat steps 2 and 3 for all operations in the contract that communicate error conditions to clients.</span></span>  
  
## <a name="implementing-an-operation-to-return-a-specified-soap-fault"></a><span data-ttu-id="cd278-115">Implementace operace vrátí zadaného protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="cd278-115">Implementing an Operation to Return a Specified SOAP Fault</span></span>  
 <span data-ttu-id="cd278-116">Po operaci byla zadána, že konkrétní chyba protokolu SOAP se může vracet (například jako v předchozím postupu) ke komunikaci chybový stav pro volající aplikace, dalším krokem je implementace této specifikaci.</span><span class="sxs-lookup"><span data-stu-id="cd278-116">Once an operation has specified that a specific SOAP fault can be returned (such as in the preceding procedure) to communicate an error condition to a calling application, the next step is to implement that specification.</span></span>  
  
#### <a name="throw-the-specified-soap-fault-in-the-operation"></a><span data-ttu-id="cd278-117">V operaci throw zadaný chybu protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="cd278-117">Throw the specified SOAP fault in the operation</span></span>  
  
1.  <span data-ttu-id="cd278-118">Když <xref:System.ServiceModel.FaultContractAttribute>-zadaný chybovému stavu dojde v operaci, throw novou <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> kde zadaný chybu protokolu SOAP se parametr typu.</span><span class="sxs-lookup"><span data-stu-id="cd278-118">When a <xref:System.ServiceModel.FaultContractAttribute>-specified error condition occurs in an operation, throw a new <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType> where the specified SOAP fault is the type parameter.</span></span> <span data-ttu-id="cd278-119">Následující příklad ukazuje, jak má být vyvolána `GreetingFault` v `SampleMethod` vidět v předchozím postupu a v následující části kódu.</span><span class="sxs-lookup"><span data-stu-id="cd278-119">The following example shows how to throw the `GreetingFault` in the `SampleMethod` shown in the preceding procedure and in the following Code section.</span></span>  
  
     [!code-csharp[FaultContractAttribute#5](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#5)]
     [!code-vb[FaultContractAttribute#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="cd278-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd278-120">Example</span></span>  
 <span data-ttu-id="cd278-121">Následující příklad kódu ukazuje implementaci pro jednu operaci, která určuje `GreetingFault` pro `SampleMethod` operaci.</span><span class="sxs-lookup"><span data-stu-id="cd278-121">The following code example shows an implementation of a single operation that specifies a `GreetingFault` for the `SampleMethod` operation.</span></span>  
  
 [!code-csharp[FaultContractAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CFX/faultcontractattribute/cs/services.cs#1)]
 [!code-vb[FaultContractAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/faultcontractattribute/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="cd278-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd278-122">See Also</span></span>  
 <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>  
 <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
