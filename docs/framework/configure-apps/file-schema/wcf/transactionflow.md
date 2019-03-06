---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: ef3d92e07aaf4d4ba9d90e381017db104f2cc8fe
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356582"
---
# <a name="transactionflow"></a><span data-ttu-id="3401e-101">\<transactionFlow></span><span class="sxs-lookup"><span data-stu-id="3401e-101">\<transactionFlow></span></span>
<span data-ttu-id="3401e-102">Určuje podporu toku transakcí vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="3401e-102">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="3401e-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3401e-103">\<system.serviceModel></span></span>  
<span data-ttu-id="3401e-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="3401e-104">\<bindings></span></span>  
<span data-ttu-id="3401e-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3401e-105">\<customBinding></span></span>  
<span data-ttu-id="3401e-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="3401e-106">\<binding></span></span>  
<span data-ttu-id="3401e-107">\<transactionFlow></span><span class="sxs-lookup"><span data-stu-id="3401e-107">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3401e-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3401e-108">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3401e-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3401e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3401e-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3401e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3401e-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="3401e-111">Attributes</span></span>  
  
|<span data-ttu-id="3401e-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="3401e-112">Attribute</span></span>|<span data-ttu-id="3401e-113">Popis</span><span class="sxs-lookup"><span data-stu-id="3401e-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3401e-114">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="3401e-114">transactionProtocol</span></span>|<span data-ttu-id="3401e-115">Určuje protokol transakce, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="3401e-115">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="3401e-116">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="3401e-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3401e-117">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="3401e-117">-   OleTransactions</span></span><br /><span data-ttu-id="3401e-118">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="3401e-118">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="3401e-119">Výchozí hodnota je OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="3401e-119">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="3401e-120">Tento atribut je typu <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="3401e-120">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3401e-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3401e-121">Child Elements</span></span>  
 <span data-ttu-id="3401e-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="3401e-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3401e-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3401e-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3401e-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="3401e-124">Element</span></span>|<span data-ttu-id="3401e-125">Popis</span><span class="sxs-lookup"><span data-stu-id="3401e-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3401e-126">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="3401e-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="3401e-127">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="3401e-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3401e-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3401e-128">Remarks</span></span>  
 <span data-ttu-id="3401e-129">Tento element slouží k povolení nebo zakázání tok příchozích transakcí v nastavení vazby koncového bodu, jakož i k určení formátu požadovaný protokol pro příchozí transakce.</span><span class="sxs-lookup"><span data-stu-id="3401e-129">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="3401e-130">Další informace o použití tento prvek konfigurace, najdete v části [konfigurace transakcí ServiceModel](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) a [povolení toku transakcí](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="3401e-130">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="3401e-131">Při použití `OleTransactions` protokol k toku transakce z koncového bodu endpoint, časový limit transakce může dojít ke ztrátě, pokud se pokusí tok znovu pomocí libovolného protokolu pro jiné než cílový koncový bod `OleTransactions`.</span><span class="sxs-lookup"><span data-stu-id="3401e-131">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="3401e-132">To může způsobit všechny uzly nižší úrovně po směrování OleTransactions vypršení časového limitu později, než se očekávalo.</span><span class="sxs-lookup"><span data-stu-id="3401e-132">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3401e-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3401e-133">See also</span></span>
- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="3401e-134">Konfigurace transakcí ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3401e-134">ServiceModel Transaction Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="3401e-135">Povolení toku transakcí</span><span class="sxs-lookup"><span data-stu-id="3401e-135">Enabling Transaction Flow</span></span>](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="3401e-136">Vazby</span><span class="sxs-lookup"><span data-stu-id="3401e-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="3401e-137">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="3401e-137">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3401e-138">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="3401e-138">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="3401e-139">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3401e-139">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
