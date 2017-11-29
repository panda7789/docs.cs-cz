---
title: "Postupy: Nastavení vlastnosti ProtectionLevel"
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
helpviewer_keywords:
- WCF, security
- ProtectionLevel property
ms.assetid: 3d4e8f80-0f9e-4a26-9899-beb6584e78df
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3a5c1104ca38f625d5869b4c34e6c48dbb145fed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-the-protectionlevel-property"></a><span data-ttu-id="69789-102">Postupy: Nastavení vlastnosti ProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="69789-102">How to: Set the ProtectionLevel Property</span></span>
<span data-ttu-id="69789-103">Úroveň ochrany můžete nastavit tak, že použití odpovídajícího atributu a nastavení vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="69789-103">You can set the protection level by applying an appropriate attribute and setting the property.</span></span> <span data-ttu-id="69789-104">Můžete nastavit ochranu na úrovni služby a ovlivňují všechny části každé zprávy nebo můžete nastavit ochranu stále podrobné úrovni, z metody části zprávy.</span><span class="sxs-lookup"><span data-stu-id="69789-104">You can set protection at the service level to affect all parts of every message, or you can set protection at increasingly granular levels, from methods to message parts.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="69789-105">`ProtectionLevel` vlastnost, najdete v části [úroveň ochrany Principy](../../../docs/framework/wcf/understanding-protection-level.md).</span><span class="sxs-lookup"><span data-stu-id="69789-105"> the `ProtectionLevel` property, see [Understanding Protection Level](../../../docs/framework/wcf/understanding-protection-level.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="69789-106">Úrovně ochrany lze nastavit pouze v kódu, není v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="69789-106">You can set protection levels only in code, not in configuration.</span></span>  
  
### <a name="to-sign-all-messages-for-a-service"></a><span data-ttu-id="69789-107">Chcete-li odhlásit všechny zprávy pro službu</span><span class="sxs-lookup"><span data-stu-id="69789-107">To sign all messages for a service</span></span>  
  
1.  <span data-ttu-id="69789-108">Vytvořte rozhraní pro službu.</span><span class="sxs-lookup"><span data-stu-id="69789-108">Create an interface for the service.</span></span>  
  
2.  <span data-ttu-id="69789-109">Použít <xref:System.ServiceModel.ServiceContractAttribute> atribut služby a nastavte <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> vlastnost <xref:System.Net.Security.ProtectionLevel.Sign>, jak je znázorněno v následujícím kódu (výchozí úroveň je <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span><span class="sxs-lookup"><span data-stu-id="69789-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the service and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code (the default level is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>).</span></span>  
  
     [!code-csharp[C_ProtectionLevel#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#1)]
     [!code-vb[C_ProtectionLevel#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#1)]  
  
### <a name="to-sign-all-message-parts-for-an-operation"></a><span data-ttu-id="69789-110">K podepisování všech částí zprávy operace</span><span class="sxs-lookup"><span data-stu-id="69789-110">To sign all message parts for an operation</span></span>  
  
1.  <span data-ttu-id="69789-111">Vytvoření rozhraní pro službu a použití <xref:System.ServiceModel.ServiceContractAttribute> atribut rozhraní.</span><span class="sxs-lookup"><span data-stu-id="69789-111">Create an interface for the service and apply the <xref:System.ServiceModel.ServiceContractAttribute> attribute to the interface.</span></span>  
  
2.  <span data-ttu-id="69789-112">Přidejte deklaraci metodu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="69789-112">Add a method declaration to the interface.</span></span>  
  
3.  <span data-ttu-id="69789-113">Použít <xref:System.ServiceModel.OperationContractAttribute> atribut metodu a nastavit <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> vlastnost <xref:System.Net.Security.ProtectionLevel.Sign>, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="69789-113">Apply the <xref:System.ServiceModel.OperationContractAttribute> attribute to the method, and set the <xref:System.ServiceModel.ServiceContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.Sign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#2)]
     [!code-vb[C_ProtectionLevel#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#2)]  
  
## <a name="protecting-fault-messages"></a><span data-ttu-id="69789-114">Ochrana chybové zprávy</span><span class="sxs-lookup"><span data-stu-id="69789-114">Protecting Fault Messages</span></span>  
 <span data-ttu-id="69789-115">Výjimky, které jsou vyvolány ve službě může odeslat klientovi jako chyb SOAP.</span><span class="sxs-lookup"><span data-stu-id="69789-115">Exceptions that are thrown on a service can be sent to a client as SOAP faults.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="69789-116">vytváření silně typované chyb naleznete v tématu [zadání a zpracování chyb v kontraktech a službách](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) a [postupy: deklarace chyb v kontraktech služby](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="69789-116"> creating strongly typed faults, see [Specifying and Handling Faults in Contracts and Services](../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md) and [How to: Declare Faults in Service Contracts](../../../docs/framework/wcf/how-to-declare-faults-in-service-contracts.md).</span></span>  
  
#### <a name="to-protect-a-fault-message"></a><span data-ttu-id="69789-117">K ochraně zprávu o chybě</span><span class="sxs-lookup"><span data-stu-id="69789-117">To protect a fault message</span></span>  
  
1.  <span data-ttu-id="69789-118">Vytvořte typ, který představuje zprávu chyby.</span><span class="sxs-lookup"><span data-stu-id="69789-118">Create a type that represents the fault message.</span></span> <span data-ttu-id="69789-119">Následující příklad vytvoří třídu s názvem `MathFault` se dvěma poli.</span><span class="sxs-lookup"><span data-stu-id="69789-119">The following example creates a class named `MathFault` with two fields.</span></span>  
  
2.  <span data-ttu-id="69789-120">Použít <xref:System.Runtime.Serialization.DataContractAttribute> atribut typu a <xref:System.Runtime.Serialization.DataMemberAttribute> atribut každé pole, které by měly být serializovány, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="69789-120">Apply the <xref:System.Runtime.Serialization.DataContractAttribute> attribute to the type and a <xref:System.Runtime.Serialization.DataMemberAttribute> attribute to each field that should be serialized, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#3)]
     [!code-vb[C_ProtectionLevel#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#3)]  
  
3.  <span data-ttu-id="69789-121">V rozhraní, které vrátí chybu, použít <xref:System.ServiceModel.FaultContractAttribute> atribut metody, která vrátí chybu a nastavit `detailType` parametr pro typ třídy selhání.</span><span class="sxs-lookup"><span data-stu-id="69789-121">In the interface that will return the fault, apply the <xref:System.ServiceModel.FaultContractAttribute> attribute to the method that will return the fault and set the `detailType` parameter to the type of the fault class.</span></span>  
  
4.  <span data-ttu-id="69789-122">V konstruktoru, nastavte také <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> vlastnost <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="69789-122">Also in the constructor, set the <xref:System.ServiceModel.FaultContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following code.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#4)]
     [!code-vb[C_ProtectionLevel#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#4)]  
  
## <a name="protecting-message-parts"></a><span data-ttu-id="69789-123">Ochrana částí zprávy</span><span class="sxs-lookup"><span data-stu-id="69789-123">Protecting Message Parts</span></span>  
 <span data-ttu-id="69789-124">Kontrakt zprávy použijte k ochraně části zprávy.</span><span class="sxs-lookup"><span data-stu-id="69789-124">Use a message contract to protect parts of a message.</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="69789-125">kontrakty zpráv najdete v tématu [pomocí kontrakty zpráv](../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="69789-125"> message contracts, see [Using Message Contracts](../../../docs/framework/wcf/feature-details/using-message-contracts.md).</span></span>  
  
#### <a name="to-protect-a-message-body"></a><span data-ttu-id="69789-126">K ochraně text zprávy</span><span class="sxs-lookup"><span data-stu-id="69789-126">To protect a message body</span></span>  
  
1.  <span data-ttu-id="69789-127">Vytvořte typ, který představuje zprávu.</span><span class="sxs-lookup"><span data-stu-id="69789-127">Create a type that represents the message.</span></span> <span data-ttu-id="69789-128">Následující příklad vytvoří `Company` třídy se dvěma poli `CompanyName` a `CompanyID`.</span><span class="sxs-lookup"><span data-stu-id="69789-128">The following example creates a `Company` class with two fields, `CompanyName` and `CompanyID`.</span></span>  
  
2.  <span data-ttu-id="69789-129">Použít <xref:System.ServiceModel.MessageContractAttribute> atribut třídy a nastavte <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> vlastnost <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="69789-129">Apply the <xref:System.ServiceModel.MessageContractAttribute> attribute to the class and set the <xref:System.ServiceModel.MessageContractAttribute.ProtectionLevel%2A> property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
3.  <span data-ttu-id="69789-130">Použít <xref:System.ServiceModel.MessageHeaderAttribute> atribut pole, které bude vyjádřený jako záhlaví zprávy a nastavit `ProtectionLevel` vlastnost <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="69789-130">Apply the <xref:System.ServiceModel.MessageHeaderAttribute> attribute to a field that will be expressed as a message header and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
4.  <span data-ttu-id="69789-131">Použít <xref:System.ServiceModel.MessageBodyMemberAttribute> pro každé pole, které bude vyjádřený jako část textu zprávy a nastavit `ProtectionLevel` vlastnost <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="69789-131">Apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to any field that will be expressed as part of the message body, and set the `ProtectionLevel` property to <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>, as shown in the following example.</span></span>  
  
     [!code-csharp[C_ProtectionLevel#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#5)]
     [!code-vb[C_ProtectionLevel#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="69789-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="69789-132">Example</span></span>  
 <span data-ttu-id="69789-133">Následující příklad nastavuje `ProtectionLevel` vlastnost třídy několik atributů na různých místech ve službě.</span><span class="sxs-lookup"><span data-stu-id="69789-133">The following example sets the `ProtectionLevel` property of several attribute classes at various places in a service.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#6)]
 [!code-vb[C_ProtectionLevel#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="69789-134">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="69789-134">Compiling the Code</span></span>  
 <span data-ttu-id="69789-135">Následující kód ukazuje obory názvů potřebné ke kompilaci ukázkový kód.</span><span class="sxs-lookup"><span data-stu-id="69789-135">The following code shows the namespaces required to compile the example code.</span></span>  
  
 [!code-csharp[C_ProtectionLevel#0](../../../samples/snippets/csharp/VS_Snippets_CFX/c_protectionlevel/cs/source.cs#0)]
 [!code-vb[C_ProtectionLevel#0](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_protectionlevel/vb/source.vb#0)]  
  
## <a name="see-also"></a><span data-ttu-id="69789-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="69789-136">See Also</span></span>  
 <xref:System.ServiceModel.ServiceContractAttribute>  
 <xref:System.ServiceModel.OperationContractAttribute>  
 <xref:System.ServiceModel.FaultContractAttribute>  
 <xref:System.ServiceModel.MessageContractAttribute>  
 <xref:System.ServiceModel.MessageBodyMemberAttribute>  
 [<span data-ttu-id="69789-137">Princip úrovně ochrany</span><span class="sxs-lookup"><span data-stu-id="69789-137">Understanding Protection Level</span></span>](../../../docs/framework/wcf/understanding-protection-level.md)
