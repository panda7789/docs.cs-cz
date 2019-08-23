---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 1292bc38ce1e542086edac5539c1b29e619e2a32
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926383"
---
# <a name="bindings"></a><span data-ttu-id="9004d-101">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="9004d-101">\<bindings></span></span>

<span data-ttu-id="9004d-102">`bindings` Element lze použít ke konfiguraci kolekce standardních a vlastní vazby pro Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="9004d-102">You can use the `bindings` element to configure a collection of standard and custom bindings for Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="9004d-103">Každá položka je prvek `binding` , který lze identifikovat podle jeho jedinečného `name`typu.</span><span class="sxs-lookup"><span data-stu-id="9004d-103">Each entry is a `binding` element that can be identified by its unique `name`.</span></span> <span data-ttu-id="9004d-104">Služby používají vazby propojením s použitím `name`.</span><span class="sxs-lookup"><span data-stu-id="9004d-104">Services use bindings by linking them using the `name`.</span></span> <span data-ttu-id="9004d-105">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název.</span><span class="sxs-lookup"><span data-stu-id="9004d-105">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="9004d-106">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="9004d-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="system-provided-bindings"></a><span data-ttu-id="9004d-107">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="9004d-107">System-provided bindings</span></span>
 
 <span data-ttu-id="9004d-108">Vazby poskytované systémem skrývají složitost zasílání zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="9004d-108">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="9004d-109">Aplikace využívající vazby poskytované systémem nevyžadují plnou kontrolu nad zásobníkem.</span><span class="sxs-lookup"><span data-stu-id="9004d-109">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="9004d-110">Atributy vystavené pro každou vazbu poskytovanou systémem jsou ty, které jsou nejvhodnější pro scénář použití jako adresy vazby.</span><span class="sxs-lookup"><span data-stu-id="9004d-110">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="9004d-111">Konfigurační oddíl pro každou vazbu poskytovanou systémem může definovat několik konfigurací používaných ke konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="9004d-111">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="9004d-112">Každá konfigurace je identifikována jedinečným názvem.</span><span class="sxs-lookup"><span data-stu-id="9004d-112">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="9004d-113">Nelze přidat prvky nebo atributy do vazby poskytnuté systémem.</span><span class="sxs-lookup"><span data-stu-id="9004d-113">It isn't possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="9004d-114">K tomu byste měli implementovat vlastní vazbu, jak je popsáno v části [vlastní vazby](#custom-bindings) .</span><span class="sxs-lookup"><span data-stu-id="9004d-114">To do so, you should implement a custom binding as described in the [Custom bindings](#custom-bindings) section.</span></span> <span data-ttu-id="9004d-115">Je možné definovat vlastní vazbu, která napodobuje uživatelsky definované vazby, a přidá několik nastavení, která má uživatelská aplikace mít kontrolu nad.</span><span class="sxs-lookup"><span data-stu-id="9004d-115">It's possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
 <span data-ttu-id="9004d-116">Seznam vazeb poskytovaných systémem naleznete v tématu [systémové vazby](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="9004d-116">For a list of system-provided bindings, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>  
  
## <a name="custom-bindings"></a><span data-ttu-id="9004d-117">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="9004d-117">Custom bindings</span></span>

 <span data-ttu-id="9004d-118">Vlastní vazby poskytují plnou kontrolu nad zásobníkem zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="9004d-118">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="9004d-119">Jednotlivá vazba definuje zásobník zpráv zadáním elementů konfigurace pro prvky zásobníku v pořadí, v jakém se zobrazují v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="9004d-119">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="9004d-120">Každý prvek definuje a nakonfiguruje jeden prvek zásobníku.</span><span class="sxs-lookup"><span data-stu-id="9004d-120">Each element defines and configures one element of the stack.</span></span> <span data-ttu-id="9004d-121">V každé vlastní vazbě musí být `transport` pouze jeden element.</span><span class="sxs-lookup"><span data-stu-id="9004d-121">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="9004d-122">Bez tohoto elementu je zásobník pro zasílání zpráv neúplný.</span><span class="sxs-lookup"><span data-stu-id="9004d-122">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="9004d-123">Pořadí, ve kterém se prvky zobrazí v zásobníku, protože se jedná o pořadí, ve kterém jsou operace pro zprávu aplikovány.</span><span class="sxs-lookup"><span data-stu-id="9004d-123">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="9004d-124">Požadované pořadí prvků zásobníku je následující:</span><span class="sxs-lookup"><span data-stu-id="9004d-124">The required order of stack elements is the following:</span></span>  
  
1. <span data-ttu-id="9004d-125">Transakce (volitelné)</span><span class="sxs-lookup"><span data-stu-id="9004d-125">Transactions (optional)</span></span>  
  
2. <span data-ttu-id="9004d-126">Spolehlivé zasílání zpráv (volitelné)</span><span class="sxs-lookup"><span data-stu-id="9004d-126">Reliable messaging (optional)</span></span>  
  
3. <span data-ttu-id="9004d-127">Zabezpečení (volitelné)</span><span class="sxs-lookup"><span data-stu-id="9004d-127">Security (optional)</span></span>  
  
4. <span data-ttu-id="9004d-128">Kodér</span><span class="sxs-lookup"><span data-stu-id="9004d-128">Encoder</span></span>  
  
5. <span data-ttu-id="9004d-129">Přepravu</span><span class="sxs-lookup"><span data-stu-id="9004d-129">Transport</span></span>  
  
 <span data-ttu-id="9004d-130">Vlastní vazby jsou označeny jejich `name` atributem.</span><span class="sxs-lookup"><span data-stu-id="9004d-130">Custom bindings are identified by their `name` attribute.</span></span> <span data-ttu-id="9004d-131">Další informace o vlastních vazbách naleznete v tématu [Custom Bindings](../../../wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="9004d-131">For more information on custom bindings, see [Custom Bindings](../../../wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9004d-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9004d-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>  
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>  
- [<span data-ttu-id="9004d-133">Vazby</span><span class="sxs-lookup"><span data-stu-id="9004d-133">Bindings</span></span>](../../../wcf/bindings.md)  
- [<span data-ttu-id="9004d-134">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="9004d-134">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)  
- [<span data-ttu-id="9004d-135">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="9004d-135">\<customBinding></span></span>](custombinding.md)  
- [<span data-ttu-id="9004d-136">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="9004d-136">\<binding></span></span>](../../../misc/binding.md)
