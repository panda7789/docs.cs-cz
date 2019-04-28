---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: 626ae03d622221ab3e956bd03898b6cc30482c98
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758025"
---
# <a name="transactionflow"></a><span data-ttu-id="8a92a-101">\<transactionFlow></span><span class="sxs-lookup"><span data-stu-id="8a92a-101">\<transactionFlow></span></span>
<span data-ttu-id="8a92a-102">Určuje podporu toku transakcí vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="8a92a-102">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="8a92a-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8a92a-103">\<system.serviceModel></span></span>  
<span data-ttu-id="8a92a-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="8a92a-104">\<bindings></span></span>  
<span data-ttu-id="8a92a-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="8a92a-105">\<customBinding></span></span>  
<span data-ttu-id="8a92a-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="8a92a-106">\<binding></span></span>  
<span data-ttu-id="8a92a-107">\<transactionFlow></span><span class="sxs-lookup"><span data-stu-id="8a92a-107">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a92a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8a92a-108">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8a92a-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8a92a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8a92a-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8a92a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8a92a-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="8a92a-111">Attributes</span></span>  
  
|<span data-ttu-id="8a92a-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="8a92a-112">Attribute</span></span>|<span data-ttu-id="8a92a-113">Popis</span><span class="sxs-lookup"><span data-stu-id="8a92a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8a92a-114">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="8a92a-114">transactionProtocol</span></span>|<span data-ttu-id="8a92a-115">Určuje protokol transakce, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="8a92a-115">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="8a92a-116">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="8a92a-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="8a92a-117">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="8a92a-117">-   OleTransactions</span></span><br /><span data-ttu-id="8a92a-118">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="8a92a-118">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="8a92a-119">Výchozí hodnota je OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="8a92a-119">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="8a92a-120">Tento atribut je typu <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="8a92a-120">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8a92a-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8a92a-121">Child Elements</span></span>  
 <span data-ttu-id="8a92a-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="8a92a-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8a92a-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8a92a-123">Parent Elements</span></span>  
  
|<span data-ttu-id="8a92a-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="8a92a-124">Element</span></span>|<span data-ttu-id="8a92a-125">Popis</span><span class="sxs-lookup"><span data-stu-id="8a92a-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8a92a-126">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="8a92a-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="8a92a-127">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="8a92a-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a92a-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8a92a-128">Remarks</span></span>  
 <span data-ttu-id="8a92a-129">Tento element slouží k povolení nebo zakázání tok příchozích transakcí v nastavení vazby koncového bodu, jakož i k určení formátu požadovaný protokol pro příchozí transakce.</span><span class="sxs-lookup"><span data-stu-id="8a92a-129">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="8a92a-130">Další informace o použití tento prvek konfigurace, najdete v části [konfigurace transakcí ServiceModel](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) a [povolení toku transakcí](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="8a92a-130">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="8a92a-131">Při použití `OleTransactions` protokol k toku transakce z koncového bodu endpoint, časový limit transakce může dojít ke ztrátě, pokud se pokusí tok znovu pomocí libovolného protokolu pro jiné než cílový koncový bod `OleTransactions`.</span><span class="sxs-lookup"><span data-stu-id="8a92a-131">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="8a92a-132">To může způsobit všechny uzly nižší úrovně po směrování OleTransactions vypršení časového limitu později, než se očekávalo.</span><span class="sxs-lookup"><span data-stu-id="8a92a-132">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a92a-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8a92a-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="8a92a-134">Konfigurace transakcí ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8a92a-134">ServiceModel Transaction Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="8a92a-135">Povolení toku transakcí</span><span class="sxs-lookup"><span data-stu-id="8a92a-135">Enabling Transaction Flow</span></span>](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="8a92a-136">Vazby</span><span class="sxs-lookup"><span data-stu-id="8a92a-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="8a92a-137">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="8a92a-137">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="8a92a-138">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="8a92a-138">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="8a92a-139">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="8a92a-139">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
