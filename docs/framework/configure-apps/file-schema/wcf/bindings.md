---
title: '&lt;vazby&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3d89fc465c1e82fab638b57dbf712f1396385f80
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltbindingsgt"></a><span data-ttu-id="0703d-102">&lt;vazby&gt;</span><span class="sxs-lookup"><span data-stu-id="0703d-102">&lt;bindings&gt;</span></span>
<span data-ttu-id="0703d-103">Tato část obsahuje kolekci standardní a vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="0703d-103">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="0703d-104">Každá položka je `binding` element, který lze identifikovat podle jeho jedinečné `name`.</span><span class="sxs-lookup"><span data-stu-id="0703d-104">Each entry is a `binding` element that can be identified by its unique `name`.</span></span> <span data-ttu-id="0703d-105">Služby používají vazby jejich propojováním pomocí `name`.</span><span class="sxs-lookup"><span data-stu-id="0703d-105">Services use bindings by linking them using the `name`.</span></span> <span data-ttu-id="0703d-106">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="0703d-106">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="0703d-107">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="0703d-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="system-provided-binding"></a><span data-ttu-id="0703d-108">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="0703d-108">System-Provided Binding</span></span>  
 <span data-ttu-id="0703d-109">Vazby poskytované systémem překonávají složitost systému zasílání zpráv zásobníku WCF.</span><span class="sxs-lookup"><span data-stu-id="0703d-109">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="0703d-110">Aplikace, které používají vazby poskytované systémem nevyžadují plnou kontrolu nad zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0703d-110">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="0703d-111">Atributy zveřejněné na každé vazby poskytované systémem jsou ty, které většinu vhodné pro scénáři použití adresy vazby.</span><span class="sxs-lookup"><span data-stu-id="0703d-111">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="0703d-112">Konfigurační oddíl pro každou vazbu poskytované systémem můžete definovat několik konfigurace použít ke konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="0703d-112">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="0703d-113">Každá konfigurace je identifikována jedinečný název.</span><span class="sxs-lookup"><span data-stu-id="0703d-113">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="0703d-114">Není možné přidat vazby poskytované systémem elementy nebo atributy.</span><span class="sxs-lookup"><span data-stu-id="0703d-114">It is not possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="0703d-115">Uděláte to tak, měli byste implementovat vlastní vazby jak je popsáno v části "Vlastní vazby" v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="0703d-115">To do so, you should implement a custom binding as described in the "Custom Binding" section of this topic.</span></span> <span data-ttu-id="0703d-116">Je možné definovat vlastní vazby, která napodobuje poskytované systémem vazbu perfektně a přidá několik nastavení aplikace uživatelů chce mít kontrolu nad.</span><span class="sxs-lookup"><span data-stu-id="0703d-116">It is possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
 <span data-ttu-id="0703d-117">Seznam vazeb poskytovaných systémem najdete v tématu [System-Provided vazby](../../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="0703d-117">For a list of system-provided bindings, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
## <a name="custom-binding"></a><span data-ttu-id="0703d-118">Vlastní vazba</span><span class="sxs-lookup"><span data-stu-id="0703d-118">Custom Binding</span></span>  
 <span data-ttu-id="0703d-119">Vlastní vazby poskytují plnou kontrolu nad zásobníku zasílání zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="0703d-119">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="0703d-120">Jednotlivé vazby definuje zásobníku zprávu zadáním konfigurační prvky pro prvky zásobníku v pořadí, ve kterém se objeví v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0703d-120">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="0703d-121">Každý prvek definuje a konfiguruje jeden element zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0703d-121">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="0703d-122">Musí být pouze jeden `transport` element v každé vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="0703d-122">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="0703d-123">Bez tohoto elementu je nekompletní zasílání zpráv zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0703d-123">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="0703d-124">Pořadí, ve kterém elementy zobrazují v zásobníku důležitý, protože je pořadí, ve kterém jsou použity operace ke zprávě.</span><span class="sxs-lookup"><span data-stu-id="0703d-124">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="0703d-125">Požadované pořadí prvků zásobníku je následující:</span><span class="sxs-lookup"><span data-stu-id="0703d-125">The required order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="0703d-126">Transakce (volitelné)</span><span class="sxs-lookup"><span data-stu-id="0703d-126">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="0703d-127">Spolehlivé zasílání zpráv (volitelné)</span><span class="sxs-lookup"><span data-stu-id="0703d-127">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="0703d-128">Zabezpečení (volitelné)</span><span class="sxs-lookup"><span data-stu-id="0703d-128">Security (optional)</span></span>  
  
4.  <span data-ttu-id="0703d-129">Kodér</span><span class="sxs-lookup"><span data-stu-id="0703d-129">Encoder</span></span>  
  
5.  <span data-ttu-id="0703d-130">Přenos</span><span class="sxs-lookup"><span data-stu-id="0703d-130">Transport</span></span>  
  
 <span data-ttu-id="0703d-131">Vlastní vazby se identifikují podle jejich `name` atribut.</span><span class="sxs-lookup"><span data-stu-id="0703d-131">Custom bindings are identified by their `name` attribute.</span></span> <span data-ttu-id="0703d-132">Další informace o vlastních vazeb naleznete v tématu [vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="0703d-132">For more information on custom bindings, see [Custom Bindings](../../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0703d-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="0703d-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [<span data-ttu-id="0703d-134">Vazby</span><span class="sxs-lookup"><span data-stu-id="0703d-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="0703d-135">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="0703d-135">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="0703d-136">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="0703d-136">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="0703d-137">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="0703d-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
