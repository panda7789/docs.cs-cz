---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: 2d1008a4308c9fda5d2291ce704d1f19205e996a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70041252"
---
# <a name="transactionflow"></a><span data-ttu-id="680af-101">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="680af-101">\<transactionFlow></span></span>
<span data-ttu-id="680af-102">Určuje podporu toku transakce pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="680af-102">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="680af-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="680af-103">\<system.serviceModel></span></span>  
<span data-ttu-id="680af-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="680af-104">\<bindings></span></span>  
<span data-ttu-id="680af-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="680af-105">\<customBinding></span></span>  
<span data-ttu-id="680af-106">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="680af-106">\<binding></span></span>  
<span data-ttu-id="680af-107">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="680af-107">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="680af-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="680af-108">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="680af-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="680af-109">Attributes and Elements</span></span>  
 <span data-ttu-id="680af-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="680af-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="680af-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="680af-111">Attributes</span></span>  
  
|<span data-ttu-id="680af-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="680af-112">Attribute</span></span>|<span data-ttu-id="680af-113">Popis</span><span class="sxs-lookup"><span data-stu-id="680af-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="680af-114">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="680af-114">transactionProtocol</span></span>|<span data-ttu-id="680af-115">Určuje transakční protokol, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="680af-115">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="680af-116">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="680af-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="680af-117">– OleTransactions</span><span class="sxs-lookup"><span data-stu-id="680af-117">-   OleTransactions</span></span><br /><span data-ttu-id="680af-118">- WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="680af-118">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="680af-119">Výchozí hodnota je OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="680af-119">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="680af-120">Tento atribut je typu <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="680af-120">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="680af-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="680af-121">Child Elements</span></span>  
 <span data-ttu-id="680af-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="680af-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="680af-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="680af-123">Parent Elements</span></span>  
  
|<span data-ttu-id="680af-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="680af-124">Element</span></span>|<span data-ttu-id="680af-125">Popis</span><span class="sxs-lookup"><span data-stu-id="680af-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="680af-126">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="680af-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="680af-127">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="680af-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="680af-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="680af-128">Remarks</span></span>  
 <span data-ttu-id="680af-129">Tento prvek umožňuje povolit nebo zakázat tok příchozích transakcí v nastaveních vazby koncového bodu a také určit požadovaný formát protokolu pro příchozí transakce.</span><span class="sxs-lookup"><span data-stu-id="680af-129">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="680af-130">Další informace o použití tohoto konfiguračního prvku naleznete v tématu [Konfigurace transakce ServiceModel](../../../wcf/feature-details/servicemodel-transaction-configuration.md) a [Povolení toku transakce](../../../wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="680af-130">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="680af-131">Při použití `OleTransactions` protokolu k toku transakcí z koncového bodu do koncového bodu může být časový limit transakce ztracený, pokud se cílový koncový bod pokusí znovu Flow použít `OleTransactions`libovolný protokol jiný než.</span><span class="sxs-lookup"><span data-stu-id="680af-131">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="680af-132">To může způsobit, že všechny uzly nižší úrovně po OleTransactions směrování do vypršení časového limitu budou pozdější, než se čekalo.</span><span class="sxs-lookup"><span data-stu-id="680af-132">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="680af-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="680af-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="680af-134">Konfigurace transakcí ServiceModel</span><span class="sxs-lookup"><span data-stu-id="680af-134">ServiceModel Transaction Configuration</span></span>](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="680af-135">Povolení toku transakcí</span><span class="sxs-lookup"><span data-stu-id="680af-135">Enabling Transaction Flow</span></span>](../../../wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="680af-136">Vazby</span><span class="sxs-lookup"><span data-stu-id="680af-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="680af-137">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="680af-137">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="680af-138">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="680af-138">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="680af-139">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="680af-139">\<customBinding></span></span>](custombinding.md)
