---
title: 'Postupy: Nastavení vlastnosti ProtectionLevel'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
ms.openlocfilehash: 4ff835f767852da586a3a35b7f4ce2edf99db283
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320916"
---
# <a name="how-to-set-the-protectionlevel-property"></a><span data-ttu-id="e3804-102">Postupy: Nastavení vlastnosti ProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="e3804-102">How to: Set the ProtectionLevel Property</span></span>
<span data-ttu-id="e3804-103">Úroveň ochrany můžete nastavit pomocí vhodného atributu a nastavením vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e3804-103">You can set the protection level by applying an appropriate attribute and setting the property.</span></span> <span data-ttu-id="e3804-104">Ochranu na úrovni služby můžete nastavit tak, aby ovlivnila všechny části každé zprávy, nebo můžete nastavit ochranu na stále podrobnějších úrovních, od metod až po části zpráv.</span><span class="sxs-lookup"><span data-stu-id="e3804-104">You can set protection at the service level to affect all parts of every message, or you can set protection at increasingly granular levels, from methods to message parts.</span></span> <span data-ttu-id="e3804-105">Další informace o vlastnosti `ProtectionLevel` najdete v tématu [Principy úrovně ochrany](understanding-protection-level.md).</span><span class="sxs-lookup"><span data-stu-id="e3804-105">For more information about the `ProtectionLevel` property, see [Understanding Protection Level](understanding-protection-level.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e3804-106">Úrovně ochrany lze nastavit pouze v kódu, nikoli v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="e3804-106">You can set protection levels only in code, not in configuration.</span></span>  
  
### <a name="to-sign-all-messages-for-a-service"></a><span data-ttu-id="e3804-107">Podepsání všech zpráv pro službu</span><span class="sxs-lookup"><span data-stu-id="e3804-107">To sign all messages for a service</span></span>  
  
1. <span data-ttu-id="e3804-108">Vytvořte rozhraní pro službu.</span><span class="sxs-lookup"><span data-stu-id="e3804-108">Create an interface for the service.</span></span>  
  
2. <span data-ttu-id="e3804-109">U služby použijte atribut <xref:System.ServiceModel.ServiceContractAttribute> a nastavte vlastnost <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> na <xref:System.Net.Security.ProtectionLevel.Sign>, jak je znázorněno v následujícím kódu (výchozí úroveň je <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span><span class="sxs-lookup"><span data-stu-id="e3804-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the service and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code (the default level is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span></span>  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a><span data-ttu-id="e3804-110">Podepsání všech částí zprávy pro operaci</span><span class="sxs-lookup"><span data-stu-id="e3804-110">To sign all message parts for an operation</span></span>  
  
1. <span data-ttu-id="e3804-111">Vytvořte rozhraní pro službu a použijte atribut <xref:System.ServiceModel.ServiceContractAttribute> pro rozhraní.</span><span class="sxs-lookup"><span data-stu-id="e3804-111">Create an interface for the service and apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
2. <span data-ttu-id="e3804-112">Přidejte do rozhraní deklaraci metody.</span><span class="sxs-lookup"><span data-stu-id="e3804-112">Add a method declaration to the interface.</span></span>  
  
3. <span data-ttu-id="e3804-113">Použijte atribut <xref:System.ServiceModel.OperationContractAttribute> u metody a nastavte vlastnost <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> na <xref:System.Net.Security.ProtectionLevel.Sign>, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="e3804-113">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to the method, and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a><span data-ttu-id="e3804-114">Ochrana chybových zpráv</span><span class="sxs-lookup"><span data-stu-id="e3804-114">Protecting Fault Messages</span></span>  
 <span data-ttu-id="e3804-115">Výjimky, které jsou vyvolány ve službě, lze odeslat klientovi jako chyby protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="e3804-115">Exceptions that are thrown on a service can be sent to a client as SOAP faults.</span></span> <span data-ttu-id="e3804-116">Další informace o vytváření chyb silného typu najdete v tématech [určení a zpracování chyb v kontraktech a službách](specifying-and-handling-faults-in-contracts-and-services.md) a [Postupy: deklarace chyb v kontraktech služeb](how-to-declare-faults-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="e3804-116">For more information about creating strongly typed faults, see [Specifying and Handling Faults in Contracts and Services](specifying-and-handling-faults-in-contracts-and-services.md) and [How to: Declare Faults in Service Contracts](how-to-declare-faults-in-service-contracts.md).</span></span>  
  
#### <a name="to-protect-a-fault-message"></a><span data-ttu-id="e3804-117">Ochrana zprávy o chybě</span><span class="sxs-lookup"><span data-stu-id="e3804-117">To protect a fault message</span></span>  
  
1. <span data-ttu-id="e3804-118">Vytvořte typ, který představuje zprávu o chybě.</span><span class="sxs-lookup"><span data-stu-id="e3804-118">Create a type that represents the fault message.</span></span> <span data-ttu-id="e3804-119">Následující příklad vytvoří třídu s názvem `MathFault` se dvěma poli.</span><span class="sxs-lookup"><span data-stu-id="e3804-119">The following example creates a class named `MathFault` with two fields.</span></span>  
  
2. <span data-ttu-id="e3804-120">Použijte atribut <xref:System.Runtime.Serialization.DataContractAttribute> na typ a atribut <xref:System.Runtime.Serialization.DataMemberAttribute> pro každé pole, které by mělo být serializováno, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="e3804-120">Apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type and a <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each field that should be serialized, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3. <span data-ttu-id="e3804-121">V rozhraní, které vrátí chybu, použijte atribut <xref:System.ServiceModel.FaultContractAttribute> na metodu, která vrátí chybu, a nastavte parametr `detailType` na typ třídy selhání.</span><span class="sxs-lookup"><span data-stu-id="e3804-121">In the interface that will return the fault, apply the <xref:System.ServiceModel.FaultContractAttribute> attribute to the method that will return the fault and set the `detailType` parameter to the type of the fault class.</span></span>  
  
4. <span data-ttu-id="e3804-122">Také v konstruktoru nastavte vlastnost <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> na hodnotu <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="e3804-122">Also in the constructor, set the <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a><span data-ttu-id="e3804-123">Ochrana částí zprávy</span><span class="sxs-lookup"><span data-stu-id="e3804-123">Protecting Message Parts</span></span>  
 <span data-ttu-id="e3804-124">Pomocí kontraktu zprávy můžete chránit části zprávy.</span><span class="sxs-lookup"><span data-stu-id="e3804-124">Use a message contract to protect parts of a message.</span></span> <span data-ttu-id="e3804-125">Další informace o kontraktech zpráv najdete v tématu [Použití kontraktů zpráv](./feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="e3804-125">For more information about message contracts, see [Using Message Contracts](./feature-details/using-message-contracts.md).</span></span>  
  
#### <a name="to-protect-a-message-body"></a><span data-ttu-id="e3804-126">Ochrana textu zprávy</span><span class="sxs-lookup"><span data-stu-id="e3804-126">To protect a message body</span></span>  
  
1. <span data-ttu-id="e3804-127">Vytvořte typ, který představuje zprávu.</span><span class="sxs-lookup"><span data-stu-id="e3804-127">Create a type that represents the message.</span></span> <span data-ttu-id="e3804-128">Následující příklad vytvoří třídu `Company` se dvěma poli, `CompanyName` a `CompanyID`.</span><span class="sxs-lookup"><span data-stu-id="e3804-128">The following example creates a `Company` class with two fields, `CompanyName` and `CompanyID`.</span></span>  
  
2. <span data-ttu-id="e3804-129">U třídy použijte atribut <xref:System.ServiceModel.MessageContractAttribute> a nastavte vlastnost <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> na hodnotu <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="e3804-129">Apply the <xref:System.ServiceModel.MessageContractAttribute> attribute to the class and set the <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
3. <span data-ttu-id="e3804-130">Použijte atribut <xref:System.ServiceModel.MessageHeaderAttribute> pro pole, které bude vyjádřeno jako záhlaví zprávy, a nastavte vlastnost `ProtectionLevel` na hodnotu <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="e3804-130">Apply the <xref:System.ServiceModel.MessageHeaderAttribute> attribute to a field that will be expressed as a message header and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
4. <span data-ttu-id="e3804-131">Použijte <xref:System.ServiceModel.MessageBodyMemberAttribute> pro každé pole, které bude vyjádřeno jako součást textu zprávy, a nastavte vlastnost `ProtectionLevel` na hodnotu <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e3804-131">Apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to any field that will be expressed as part of the message body, and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following example.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="e3804-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="e3804-132">Example</span></span>  
 <span data-ttu-id="e3804-133">Následující příklad nastaví vlastnost `ProtectionLevel` několika tříd atributů na různých místech ve službě.</span><span class="sxs-lookup"><span data-stu-id="e3804-133">The following example sets the `ProtectionLevel` property of several attribute classes at various places in a service.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e3804-134">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e3804-134">Compiling the Code</span></span>  
 <span data-ttu-id="e3804-135">Následující kód ukazuje obory názvů, které jsou požadovány pro zkompilování ukázkového kódu.</span><span class="sxs-lookup"><span data-stu-id="e3804-135">The following code shows the namespaces required to compile the example code.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="e3804-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e3804-136">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
- <xref:System.ServiceModel.FaultContractAttribute>
- <xref:System.ServiceModel.MessageContractAttribute>
- <xref:System.ServiceModel.MessageBodyMemberAttribute>
- [<span data-ttu-id="e3804-137">Princip úrovně ochrany</span><span class="sxs-lookup"><span data-stu-id="e3804-137">Understanding Protection Level</span></span>](understanding-protection-level.md)
