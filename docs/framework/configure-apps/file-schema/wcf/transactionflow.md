---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: f5bcd142fb2b032ea179bcbba68fee53b98d2d77
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736314"
---
# \<transactionFlow>
<span data-ttu-id="5373a-101">Určuje podporu toku transakce pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="5373a-101">Specifies transaction flow support for the custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactionFlow>**  
  
## <a name="syntax"></a><span data-ttu-id="5373a-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5373a-102">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5373a-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5373a-103">Attributes and Elements</span></span>  
 <span data-ttu-id="5373a-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5373a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5373a-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="5373a-105">Attributes</span></span>  
  
|<span data-ttu-id="5373a-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="5373a-106">Attribute</span></span>|<span data-ttu-id="5373a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="5373a-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5373a-108">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="5373a-108">transactionProtocol</span></span>|<span data-ttu-id="5373a-109">Určuje transakční protokol, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="5373a-109">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="5373a-110">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="5373a-110">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5373a-111">– OleTransactions</span><span class="sxs-lookup"><span data-stu-id="5373a-111">-   OleTransactions</span></span><br /><span data-ttu-id="5373a-112">- WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="5373a-112">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="5373a-113">Výchozí hodnota je OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="5373a-113">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="5373a-114">Tento atribut je typu <xref:System.ServiceModel.TransactionProtocol> .</span><span class="sxs-lookup"><span data-stu-id="5373a-114">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5373a-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5373a-115">Child Elements</span></span>  
 <span data-ttu-id="5373a-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="5373a-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5373a-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5373a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5373a-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="5373a-118">Element</span></span>|<span data-ttu-id="5373a-119">Description</span><span class="sxs-lookup"><span data-stu-id="5373a-119">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="5373a-120">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="5373a-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5373a-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5373a-121">Remarks</span></span>  
 <span data-ttu-id="5373a-122">Tento prvek umožňuje povolit nebo zakázat tok příchozích transakcí v nastaveních vazby koncového bodu a také určit požadovaný formát protokolu pro příchozí transakce.</span><span class="sxs-lookup"><span data-stu-id="5373a-122">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="5373a-123">Další informace o použití tohoto konfiguračního prvku naleznete v tématu [Konfigurace transakce ServiceModel](../../../wcf/feature-details/servicemodel-transaction-configuration.md) a [Povolení toku transakce](../../../wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="5373a-123">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="5373a-124">Při použití `OleTransactions` protokolu k toku transakcí z koncového bodu do koncového bodu může být časový limit transakce ztracený, pokud se cílový koncový bod pokusí znovu Flow použít libovolný protokol jiný než `OleTransactions` .</span><span class="sxs-lookup"><span data-stu-id="5373a-124">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="5373a-125">To může způsobit, že všechny uzly nižší úrovně po OleTransactions směrování do vypršení časového limitu budou pozdější, než se čekalo.</span><span class="sxs-lookup"><span data-stu-id="5373a-125">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5373a-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="5373a-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="5373a-127">Konfigurace transakcí ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5373a-127">ServiceModel Transaction Configuration</span></span>](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="5373a-128">Povolení toku transakcí</span><span class="sxs-lookup"><span data-stu-id="5373a-128">Enabling Transaction Flow</span></span>](../../../wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="5373a-129">Vazby</span><span class="sxs-lookup"><span data-stu-id="5373a-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5373a-130">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="5373a-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5373a-131">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="5373a-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
