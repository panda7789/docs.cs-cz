---
title: '&lt;Vazba&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7b9e0c7e077a9f47de6df31b00f4df320b845150
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltbindinggt"></a><span data-ttu-id="9b004-102">&lt;Vazba&gt;</span><span class="sxs-lookup"><span data-stu-id="9b004-102">&lt;binding&gt;</span></span>
<span data-ttu-id="9b004-103">Můžete použít `binding` elementu, který chcete nakonfigurovat různé typy předdefinované vazby zadaný ve Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9b004-103">You can use the `binding` element to configure different types of predefined bindings provided by Windows Communication Foundation (WCF).</span></span>  
  
## <a name="system-provided-binding"></a><span data-ttu-id="9b004-104">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="9b004-104">System-Provided Binding</span></span>  
 <span data-ttu-id="9b004-105">Vazby poskytované systémem překonávají složitost systému zasílání zpráv zásobníku WCF.</span><span class="sxs-lookup"><span data-stu-id="9b004-105">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="9b004-106">Aplikace, které používají vazby poskytované systémem nevyžadují plnou kontrolu nad zásobníku.</span><span class="sxs-lookup"><span data-stu-id="9b004-106">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="9b004-107">Atributy zveřejněné na každé vazby poskytované systémem jsou ty, které většinu vhodné pro scénáři použití adresy vazby.</span><span class="sxs-lookup"><span data-stu-id="9b004-107">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="9b004-108">Konfigurační oddíl pro každou vazbu poskytované systémem můžete definovat několik konfigurace použít ke konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="9b004-108">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="9b004-109">Každá konfigurace je identifikována jedinečný název.</span><span class="sxs-lookup"><span data-stu-id="9b004-109">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="9b004-110">Není možné přidat vazby poskytované systémem elementy nebo atributy.</span><span class="sxs-lookup"><span data-stu-id="9b004-110">It is not possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="9b004-111">Uděláte to tak, měli byste implementovat vlastní vazby jak je popsáno v části "Vlastní vazby" v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="9b004-111">To do so, you should implement a custom binding as described in the "Custom Binding" section of this topic.</span></span> <span data-ttu-id="9b004-112">Je možné definovat vlastní vazby, která napodobuje poskytované systémem vazbu perfektně a přidá několik nastavení aplikace uživatelů chce mít kontrolu nad.</span><span class="sxs-lookup"><span data-stu-id="9b004-112">It is possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
## <a name="custom-binding"></a><span data-ttu-id="9b004-113">Vlastní vazba</span><span class="sxs-lookup"><span data-stu-id="9b004-113">Custom Binding</span></span>  
 <span data-ttu-id="9b004-114">Vlastní vazby poskytují plnou kontrolu nad zásobníku zasílání zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="9b004-114">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="9b004-115">Jednotlivé vazby definuje zásobníku zprávu zadáním konfigurační prvky pro prvky zásobníku v pořadí, ve kterém se objeví v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="9b004-115">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="9b004-116">Každý prvek definuje a konfiguruje jeden element zásobníku.</span><span class="sxs-lookup"><span data-stu-id="9b004-116">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="9b004-117">Musí být pouze jeden `transport` element v každé vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="9b004-117">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="9b004-118">Bez tohoto elementu je nekompletní zasílání zpráv zásobníku.</span><span class="sxs-lookup"><span data-stu-id="9b004-118">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="9b004-119">Pořadí, ve kterém elementy zobrazují v zásobníku důležitý, protože je pořadí, ve kterém jsou použity operace ke zprávě.</span><span class="sxs-lookup"><span data-stu-id="9b004-119">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="9b004-120">Doporučené pořadí elementů zásobníku je následující:</span><span class="sxs-lookup"><span data-stu-id="9b004-120">The recommended order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="9b004-121">Transakce (volitelné)</span><span class="sxs-lookup"><span data-stu-id="9b004-121">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="9b004-122">Spolehlivé zasílání zpráv (volitelné)</span><span class="sxs-lookup"><span data-stu-id="9b004-122">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="9b004-123">Zabezpečení (volitelné)</span><span class="sxs-lookup"><span data-stu-id="9b004-123">Security (optional)</span></span>  
  
4.  <span data-ttu-id="9b004-124">Kodér</span><span class="sxs-lookup"><span data-stu-id="9b004-124">Encoder</span></span>  
  
5.  <span data-ttu-id="9b004-125">Přenos</span><span class="sxs-lookup"><span data-stu-id="9b004-125">Transport</span></span>  
  
 <span data-ttu-id="9b004-126">Vlastní vazby se identifikují podle jejich `name` atribut.</span><span class="sxs-lookup"><span data-stu-id="9b004-126">Custom bindings are identified by their `name` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b004-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="9b004-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 [<span data-ttu-id="9b004-128">Vazby</span><span class="sxs-lookup"><span data-stu-id="9b004-128">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="9b004-129">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="9b004-129">Custom Bindings</span></span>](../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="9b004-130">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="9b004-130">\<customBinding></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
