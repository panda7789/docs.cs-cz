---
title: '&lt;transactionFlow&gt;'
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: d8597a71a9b7afadba7565290085f491052e04d6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622117"
---
# <a name="lttransactionflowgt"></a><span data-ttu-id="a18f7-102">&lt;transactionFlow&gt;</span><span class="sxs-lookup"><span data-stu-id="a18f7-102">&lt;transactionFlow&gt;</span></span>
<span data-ttu-id="a18f7-103">Určuje podporu toku transakcí vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="a18f7-103">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="a18f7-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="a18f7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="a18f7-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="a18f7-105">\<bindings></span></span>  
<span data-ttu-id="a18f7-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a18f7-106">\<customBinding></span></span>  
<span data-ttu-id="a18f7-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="a18f7-107">\<binding></span></span>  
<span data-ttu-id="a18f7-108">\<transactionFlow></span><span class="sxs-lookup"><span data-stu-id="a18f7-108">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a18f7-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a18f7-109">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a18f7-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a18f7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="a18f7-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a18f7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a18f7-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="a18f7-112">Attributes</span></span>  
  
|<span data-ttu-id="a18f7-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="a18f7-113">Attribute</span></span>|<span data-ttu-id="a18f7-114">Popis</span><span class="sxs-lookup"><span data-stu-id="a18f7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a18f7-115">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="a18f7-115">transactionProtocol</span></span>|<span data-ttu-id="a18f7-116">Určuje protokol transakce, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="a18f7-116">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="a18f7-117">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="a18f7-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="a18f7-118">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="a18f7-118">-   OleTransactions</span></span><br /><span data-ttu-id="a18f7-119">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="a18f7-119">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="a18f7-120">Výchozí hodnota je OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="a18f7-120">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="a18f7-121">Tento atribut je typu <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="a18f7-121">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a18f7-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a18f7-122">Child Elements</span></span>  
 <span data-ttu-id="a18f7-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="a18f7-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a18f7-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a18f7-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a18f7-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="a18f7-125">Element</span></span>|<span data-ttu-id="a18f7-126">Popis</span><span class="sxs-lookup"><span data-stu-id="a18f7-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a18f7-127">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="a18f7-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="a18f7-128">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="a18f7-128">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a18f7-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a18f7-129">Remarks</span></span>  
 <span data-ttu-id="a18f7-130">Tento element slouží k povolení nebo zakázání tok příchozích transakcí v nastavení vazby koncového bodu, jakož i k určení formátu požadovaný protokol pro příchozí transakce.</span><span class="sxs-lookup"><span data-stu-id="a18f7-130">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="a18f7-131">Další informace o použití tento prvek konfigurace, najdete v části [konfigurace transakcí ServiceModel](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) a [povolení toku transakcí](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="a18f7-131">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="a18f7-132">Při použití `OleTransactions` protokol k toku transakce z koncového bodu endpoint, časový limit transakce může dojít ke ztrátě, pokud se pokusí tok znovu pomocí libovolného protokolu pro jiné než cílový koncový bod `OleTransactions`.</span><span class="sxs-lookup"><span data-stu-id="a18f7-132">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="a18f7-133">To může způsobit všechny uzly nižší úrovně po směrování OleTransactions vypršení časového limitu později, než se očekávalo.</span><span class="sxs-lookup"><span data-stu-id="a18f7-133">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a18f7-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a18f7-134">See also</span></span>
- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a18f7-135">Konfigurace transakcí ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a18f7-135">ServiceModel Transaction Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="a18f7-136">Povolení toku transakcí</span><span class="sxs-lookup"><span data-stu-id="a18f7-136">Enabling Transaction Flow</span></span>](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="a18f7-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="a18f7-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="a18f7-138">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="a18f7-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a18f7-139">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="a18f7-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="a18f7-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="a18f7-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
