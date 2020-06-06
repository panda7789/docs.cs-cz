---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: fe8f620668e35183890b8bba1f254a74c962f8d3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139660"
---
# \<bindings>

<span data-ttu-id="aba0f-101">Element lze použít `bindings` ke konfiguraci kolekce standardních a vlastní vazby pro Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="aba0f-101">You can use the `bindings` element to configure a collection of standard and custom bindings for Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="aba0f-102">Každá položka je `binding` prvek, který lze identifikovat podle jeho jedinečného typu `name` .</span><span class="sxs-lookup"><span data-stu-id="aba0f-102">Each entry is a `binding` element that can be identified by its unique `name`.</span></span> <span data-ttu-id="aba0f-103">Služby používají vazby propojením s použitím `name` .</span><span class="sxs-lookup"><span data-stu-id="aba0f-103">Services use bindings by linking them using the `name`.</span></span> <span data-ttu-id="aba0f-104">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="aba0f-104">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="aba0f-105">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="aba0f-105">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="system-provided-bindings"></a><span data-ttu-id="aba0f-106">Vazby poskytované systémem</span><span class="sxs-lookup"><span data-stu-id="aba0f-106">System-provided bindings</span></span>

<span data-ttu-id="aba0f-107">Vazby poskytované systémem skrývají složitost zasílání zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="aba0f-107">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="aba0f-108">Aplikace využívající vazby poskytované systémem nevyžadují plnou kontrolu nad zásobníkem.</span><span class="sxs-lookup"><span data-stu-id="aba0f-108">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="aba0f-109">Atributy vystavené pro každou vazbu poskytovanou systémem jsou ty, které jsou nejvhodnější pro scénář použití jako adresy vazby.</span><span class="sxs-lookup"><span data-stu-id="aba0f-109">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>

<span data-ttu-id="aba0f-110">Konfigurační oddíl pro každou vazbu poskytovanou systémem může definovat několik konfigurací používaných ke konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="aba0f-110">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="aba0f-111">Každá konfigurace je identifikována jedinečným názvem.</span><span class="sxs-lookup"><span data-stu-id="aba0f-111">Each configuration is identified by a unique name.</span></span>

<span data-ttu-id="aba0f-112">Nelze přidat prvky nebo atributy do vazby poskytnuté systémem.</span><span class="sxs-lookup"><span data-stu-id="aba0f-112">It isn't possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="aba0f-113">K tomu byste měli implementovat vlastní vazbu, jak je popsáno v části [vlastní vazby](#custom-bindings) .</span><span class="sxs-lookup"><span data-stu-id="aba0f-113">To do so, you should implement a custom binding as described in the [Custom bindings](#custom-bindings) section.</span></span> <span data-ttu-id="aba0f-114">Je možné definovat vlastní vazbu, která napodobuje uživatelsky definované vazby, a přidá několik nastavení, která má uživatelská aplikace mít kontrolu nad.</span><span class="sxs-lookup"><span data-stu-id="aba0f-114">It's possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  

<span data-ttu-id="aba0f-115">Seznam vazeb poskytovaných systémem naleznete v tématu [systémové vazby](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="aba0f-115">For a list of system-provided bindings, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>

## <a name="custom-bindings"></a><span data-ttu-id="aba0f-116">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="aba0f-116">Custom bindings</span></span>

<span data-ttu-id="aba0f-117">Vlastní vazby poskytují plnou kontrolu nad zásobníkem zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="aba0f-117">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="aba0f-118">Jednotlivá vazba definuje zásobník zpráv zadáním elementů konfigurace pro prvky zásobníku v pořadí, v jakém se zobrazují v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="aba0f-118">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="aba0f-119">Každý prvek definuje a nakonfiguruje jeden prvek zásobníku.</span><span class="sxs-lookup"><span data-stu-id="aba0f-119">Each element defines and configures one element of the stack.</span></span> <span data-ttu-id="aba0f-120">`transport`V každé vlastní vazbě musí být pouze jeden element.</span><span class="sxs-lookup"><span data-stu-id="aba0f-120">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="aba0f-121">Bez tohoto elementu je zásobník pro zasílání zpráv neúplný.</span><span class="sxs-lookup"><span data-stu-id="aba0f-121">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="aba0f-122">Pořadí, ve kterém se prvky zobrazí v zásobníku, protože se jedná o pořadí, ve kterém jsou operace pro zprávu aplikovány.</span><span class="sxs-lookup"><span data-stu-id="aba0f-122">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="aba0f-123">Požadované pořadí prvků zásobníku je následující:</span><span class="sxs-lookup"><span data-stu-id="aba0f-123">The required order of stack elements is the following:</span></span>  

1. <span data-ttu-id="aba0f-124">Transakce (volitelné)</span><span class="sxs-lookup"><span data-stu-id="aba0f-124">Transactions (optional)</span></span>  

2. <span data-ttu-id="aba0f-125">Spolehlivé zasílání zpráv (volitelné)</span><span class="sxs-lookup"><span data-stu-id="aba0f-125">Reliable messaging (optional)</span></span>  

3. <span data-ttu-id="aba0f-126">Zabezpečení (volitelné)</span><span class="sxs-lookup"><span data-stu-id="aba0f-126">Security (optional)</span></span>  

4. <span data-ttu-id="aba0f-127">Kodér</span><span class="sxs-lookup"><span data-stu-id="aba0f-127">Encoder</span></span>  

5. <span data-ttu-id="aba0f-128">Přenos</span><span class="sxs-lookup"><span data-stu-id="aba0f-128">Transport</span></span>  

 <span data-ttu-id="aba0f-129">Vlastní vazby jsou označeny jejich `name` atributem.</span><span class="sxs-lookup"><span data-stu-id="aba0f-129">Custom bindings are identified by their `name` attribute.</span></span> <span data-ttu-id="aba0f-130">Další informace o vlastních vazbách naleznete v tématu [Custom Bindings](../../../wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="aba0f-130">For more information on custom bindings, see [Custom Bindings](../../../wcf/extending/custom-bindings.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="aba0f-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="aba0f-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>
- [<span data-ttu-id="aba0f-132">Vazby</span><span class="sxs-lookup"><span data-stu-id="aba0f-132">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="aba0f-133">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="aba0f-133">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
