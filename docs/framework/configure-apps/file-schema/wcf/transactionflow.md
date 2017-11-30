---
title: '&lt;transactionFlow&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8c40b3a79567ccc1ca5a83631253d3ff6ead0f84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lttransactionflowgt"></a><span data-ttu-id="87e3c-102">&lt;transactionFlow&gt;</span><span class="sxs-lookup"><span data-stu-id="87e3c-102">&lt;transactionFlow&gt;</span></span>
<span data-ttu-id="87e3c-103">Určuje podpora toku transakcí pro vlastní připojení.</span><span class="sxs-lookup"><span data-stu-id="87e3c-103">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="87e3c-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="87e3c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="87e3c-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="87e3c-105">\<bindings></span></span>  
<span data-ttu-id="87e3c-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="87e3c-106">\<customBinding></span></span>  
<span data-ttu-id="87e3c-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="87e3c-107">\<binding></span></span>  
<span data-ttu-id="87e3c-108">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="87e3c-108">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87e3c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="87e3c-109">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="87e3c-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="87e3c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="87e3c-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="87e3c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="87e3c-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="87e3c-112">Attributes</span></span>  
  
|<span data-ttu-id="87e3c-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="87e3c-113">Attribute</span></span>|<span data-ttu-id="87e3c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="87e3c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="87e3c-115">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="87e3c-115">transactionProtocol</span></span>|<span data-ttu-id="87e3c-116">Určuje protokol transakce, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="87e3c-116">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="87e3c-117">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="87e3c-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="87e3c-118">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="87e3c-118">-   OleTransactions</span></span><br /><span data-ttu-id="87e3c-119">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="87e3c-119">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="87e3c-120">Výchozí hodnota je OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="87e3c-120">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="87e3c-121">Tento atribut je typu <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="87e3c-121">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="87e3c-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="87e3c-122">Child Elements</span></span>  
 <span data-ttu-id="87e3c-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="87e3c-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="87e3c-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="87e3c-124">Parent Elements</span></span>  
  
|<span data-ttu-id="87e3c-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="87e3c-125">Element</span></span>|<span data-ttu-id="87e3c-126">Popis</span><span class="sxs-lookup"><span data-stu-id="87e3c-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="87e3c-127">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="87e3c-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="87e3c-128">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="87e3c-128">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87e3c-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="87e3c-129">Remarks</span></span>  
 <span data-ttu-id="87e3c-130">Tento element můžete povolit nebo zakázat příchozí tok transakcí v nastavení vazby koncového bodu, a také k určení formátu požadovaný protokol pro příchozí transakce.</span><span class="sxs-lookup"><span data-stu-id="87e3c-130">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="87e3c-131">Další informace o použití tohoto elementu konfigurace najdete v tématu [konfigurace transakcí ServiceModel](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) a [povolení toku transakcí](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="87e3c-131">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="87e3c-132">Při použití `OleTransactions` protokolu směrování transakcí z koncového bodu endpoint, časový limit transakcí může dojít ke ztrátě, pokud do cílového koncového bodu se pokusí znovu s použitím libovolný protokol pro jiné než toku `OleTransactions`.</span><span class="sxs-lookup"><span data-stu-id="87e3c-132">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="87e3c-133">Všechny uzly nižší úrovni. to může způsobit po směrování OleTransactions časový limit později, než se očekávalo.</span><span class="sxs-lookup"><span data-stu-id="87e3c-133">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87e3c-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="87e3c-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransactionFlowElement>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="87e3c-135">Konfigurace transakcí ServiceModel</span><span class="sxs-lookup"><span data-stu-id="87e3c-135">ServiceModel Transaction Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)  
 [<span data-ttu-id="87e3c-136">Povolení toku transakcí</span><span class="sxs-lookup"><span data-stu-id="87e3c-136">Enabling Transaction Flow</span></span>](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)  
 [<span data-ttu-id="87e3c-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="87e3c-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="87e3c-138">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="87e3c-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="87e3c-139">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="87e3c-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="87e3c-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="87e3c-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
