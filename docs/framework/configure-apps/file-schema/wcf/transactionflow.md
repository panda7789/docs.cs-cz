---
title: '&lt;transactionFlow&gt;'
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: 6f0660ce94fdfbe1ab636aa4197ef31526c21348
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145793"
---
# <a name="lttransactionflowgt"></a><span data-ttu-id="db7c0-102">&lt;transactionFlow&gt;</span><span class="sxs-lookup"><span data-stu-id="db7c0-102">&lt;transactionFlow&gt;</span></span>
<span data-ttu-id="db7c0-103">Určuje podporu toku transakcí vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="db7c0-103">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="db7c0-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="db7c0-104">\<system.serviceModel></span></span>  
<span data-ttu-id="db7c0-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="db7c0-105">\<bindings></span></span>  
<span data-ttu-id="db7c0-106">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="db7c0-106">\<customBinding></span></span>  
<span data-ttu-id="db7c0-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="db7c0-107">\<binding></span></span>  
<span data-ttu-id="db7c0-108">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="db7c0-108">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db7c0-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db7c0-109">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db7c0-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="db7c0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="db7c0-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="db7c0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db7c0-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="db7c0-112">Attributes</span></span>  
  
|<span data-ttu-id="db7c0-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="db7c0-113">Attribute</span></span>|<span data-ttu-id="db7c0-114">Popis</span><span class="sxs-lookup"><span data-stu-id="db7c0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="db7c0-115">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="db7c0-115">transactionProtocol</span></span>|<span data-ttu-id="db7c0-116">Určuje protokol transakce, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="db7c0-116">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="db7c0-117">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="db7c0-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="db7c0-118">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="db7c0-118">-   OleTransactions</span></span><br /><span data-ttu-id="db7c0-119">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="db7c0-119">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="db7c0-120">Výchozí hodnota je OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="db7c0-120">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="db7c0-121">Tento atribut je typu <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="db7c0-121">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db7c0-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="db7c0-122">Child Elements</span></span>  
 <span data-ttu-id="db7c0-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="db7c0-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="db7c0-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="db7c0-124">Parent Elements</span></span>  
  
|<span data-ttu-id="db7c0-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="db7c0-125">Element</span></span>|<span data-ttu-id="db7c0-126">Popis</span><span class="sxs-lookup"><span data-stu-id="db7c0-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="db7c0-127">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="db7c0-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="db7c0-128">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="db7c0-128">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db7c0-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db7c0-129">Remarks</span></span>  
 <span data-ttu-id="db7c0-130">Tento element slouží k povolení nebo zakázání tok příchozích transakcí v nastavení vazby koncového bodu, jakož i k určení formátu požadovaný protokol pro příchozí transakce.</span><span class="sxs-lookup"><span data-stu-id="db7c0-130">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="db7c0-131">Další informace o použití tento prvek konfigurace, najdete v části [konfigurace transakcí ServiceModel](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) a [povolení toku transakcí](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="db7c0-131">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="db7c0-132">Při použití `OleTransactions` protokol k toku transakce z koncového bodu endpoint, časový limit transakce může dojít ke ztrátě, pokud se pokusí tok znovu pomocí libovolného protokolu pro jiné než cílový koncový bod `OleTransactions`.</span><span class="sxs-lookup"><span data-stu-id="db7c0-132">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="db7c0-133">To může způsobit všechny uzly nižší úrovně po směrování OleTransactions vypršení časového limitu později, než se očekávalo.</span><span class="sxs-lookup"><span data-stu-id="db7c0-133">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db7c0-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="db7c0-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransactionFlowElement>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="db7c0-135">Konfigurace transakcí ServiceModel</span><span class="sxs-lookup"><span data-stu-id="db7c0-135">ServiceModel Transaction Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)  
 [<span data-ttu-id="db7c0-136">Povolení toku transakcí</span><span class="sxs-lookup"><span data-stu-id="db7c0-136">Enabling Transaction Flow</span></span>](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)  
 [<span data-ttu-id="db7c0-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="db7c0-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="db7c0-138">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="db7c0-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="db7c0-139">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="db7c0-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="db7c0-140">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="db7c0-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
