---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: f5bcd142fb2b032ea179bcbba68fee53b98d2d77
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736314"
---
# <a name="transactionflow"></a><span data-ttu-id="675b8-101">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="675b8-101">\<transactionFlow></span></span>
<span data-ttu-id="675b8-102">Určuje podporu toku transakce pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="675b8-102">Specifies transaction flow support for the custom binding.</span></span>  
  
<span data-ttu-id="675b8-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="675b8-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="675b8-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="675b8-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="675b8-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="675b8-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="675b8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="675b8-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="675b8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="675b8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="675b8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transactionFlow >**</span><span class="sxs-lookup"><span data-stu-id="675b8-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactionFlow>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="675b8-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="675b8-109">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="675b8-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="675b8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="675b8-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="675b8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="675b8-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="675b8-112">Attributes</span></span>  
  
|<span data-ttu-id="675b8-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="675b8-113">Attribute</span></span>|<span data-ttu-id="675b8-114">Popis</span><span class="sxs-lookup"><span data-stu-id="675b8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="675b8-115">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="675b8-115">transactionProtocol</span></span>|<span data-ttu-id="675b8-116">Určuje transakční protokol, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="675b8-116">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="675b8-117">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="675b8-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="675b8-118">– OleTransactions</span><span class="sxs-lookup"><span data-stu-id="675b8-118">-   OleTransactions</span></span><br /><span data-ttu-id="675b8-119">- WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="675b8-119">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="675b8-120">Výchozí hodnota je OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="675b8-120">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="675b8-121">Tento atribut je typu <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="675b8-121">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="675b8-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="675b8-122">Child Elements</span></span>  
 <span data-ttu-id="675b8-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="675b8-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="675b8-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="675b8-124">Parent Elements</span></span>  
  
|<span data-ttu-id="675b8-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="675b8-125">Element</span></span>|<span data-ttu-id="675b8-126">Popis</span><span class="sxs-lookup"><span data-stu-id="675b8-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="675b8-127">vazba \<</span><span class="sxs-lookup"><span data-stu-id="675b8-127">\<binding></span></span>](bindings.md)|<span data-ttu-id="675b8-128">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="675b8-128">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="675b8-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="675b8-129">Remarks</span></span>  
 <span data-ttu-id="675b8-130">Tento prvek umožňuje povolit nebo zakázat tok příchozích transakcí v nastaveních vazby koncového bodu a také určit požadovaný formát protokolu pro příchozí transakce.</span><span class="sxs-lookup"><span data-stu-id="675b8-130">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="675b8-131">Další informace o použití tohoto konfiguračního prvku naleznete v tématu [Konfigurace transakce ServiceModel](../../../wcf/feature-details/servicemodel-transaction-configuration.md) a [Povolení toku transakce](../../../wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="675b8-131">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="675b8-132">Při použití protokolu `OleTransactions` ke flowování transakcí z koncového bodu do koncového bodu může být časový limit transakce ztracený, pokud se cílový koncový bod pokusí o přetečení pomocí libovolného jiného protokolu než `OleTransactions`.</span><span class="sxs-lookup"><span data-stu-id="675b8-132">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="675b8-133">To může způsobit, že všechny uzly nižší úrovně po OleTransactions směrování do vypršení časového limitu budou pozdější, než se čekalo.</span><span class="sxs-lookup"><span data-stu-id="675b8-133">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="675b8-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="675b8-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="675b8-135">Konfigurace transakcí ServiceModel</span><span class="sxs-lookup"><span data-stu-id="675b8-135">ServiceModel Transaction Configuration</span></span>](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="675b8-136">Povolení toku transakcí</span><span class="sxs-lookup"><span data-stu-id="675b8-136">Enabling Transaction Flow</span></span>](../../../wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="675b8-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="675b8-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="675b8-138">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="675b8-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="675b8-139">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="675b8-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="675b8-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="675b8-140">\<customBinding></span></span>](custombinding.md)
