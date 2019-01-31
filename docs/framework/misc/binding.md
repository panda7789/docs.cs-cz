---
title: <binding>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
ms.openlocfilehash: fb51eb1962603439b89a203eb668dfb543049170
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271470"
---
# <a name="binding"></a><span data-ttu-id="307d4-101">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="307d4-101">\<binding></span></span>
<span data-ttu-id="307d4-102">Můžete použít `binding` element ke konfiguraci různých typů předdefinovaných vazeb, poskytnutých technologií Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="307d4-102">You can use the `binding` element to configure different types of predefined bindings provided by Windows Communication Foundation (WCF).</span></span>  
  
## <a name="system-provided-binding"></a><span data-ttu-id="307d4-103">Vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="307d4-103">System-Provided Binding</span></span>  
 <span data-ttu-id="307d4-104">Vazby poskytované systémem překonávají složitost systému zásobníkem zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="307d4-104">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="307d4-105">Aplikace používající vazeb poskytovaných systémem nevyžadují, aby plnou kontrolu nad zásobníku.</span><span class="sxs-lookup"><span data-stu-id="307d4-105">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="307d4-106">Atributy, které jsou zveřejněné na každý vazeb poskytovaných systémem jsou ty, které nejvhodnější pro scénáře použití adresy vazby.</span><span class="sxs-lookup"><span data-stu-id="307d4-106">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="307d4-107">Oddíl konfigurace pro každý vazeb poskytovaných systémem můžete definovat několik konfigurací použít ke konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="307d4-107">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="307d4-108">Každá konfigurace je identifikován jedinečný název.</span><span class="sxs-lookup"><span data-stu-id="307d4-108">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="307d4-109">Není možné přidat do vazeb poskytovaných systémem elementy nebo atributy.</span><span class="sxs-lookup"><span data-stu-id="307d4-109">It is not possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="307d4-110">Uděláte to tak, by měly implementovat vlastní vazby, jak je popsáno v části "Vlastní vazby" v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="307d4-110">To do so, you should implement a custom binding as described in the "Custom Binding" section of this topic.</span></span> <span data-ttu-id="307d4-111">Je možné definovat vlastní vazby, která napodobuje poskytované systémem vazba dokonale a přidá několik nastavení aplikace uživatele chce mít kontrolu nad.</span><span class="sxs-lookup"><span data-stu-id="307d4-111">It is possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
## <a name="custom-binding"></a><span data-ttu-id="307d4-112">Vlastní vazba</span><span class="sxs-lookup"><span data-stu-id="307d4-112">Custom Binding</span></span>  
 <span data-ttu-id="307d4-113">Vlastní vazby poskytují plnou kontrolu nad zásobníkem zpráv WCF.</span><span class="sxs-lookup"><span data-stu-id="307d4-113">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="307d4-114">Jednotlivé vazby definuje zásobníku zprávu zadáním elementů konfigurace pro zásobník prvky v pořadí, ve kterém se zobrazují v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="307d4-114">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="307d4-115">Každý prvek definuje a konfiguruje jeden prvek zásobníku.</span><span class="sxs-lookup"><span data-stu-id="307d4-115">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="307d4-116">Musí existovat pouze jeden `transport` element v každé vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="307d4-116">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="307d4-117">Bez tohoto elementu je neúplný zásobníkem zpráv.</span><span class="sxs-lookup"><span data-stu-id="307d4-117">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="307d4-118">Je důležité pořadí, v jakém jsou prvky uvedeny v zásobníku, protože je pořadí použití operace u zprávy.</span><span class="sxs-lookup"><span data-stu-id="307d4-118">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="307d4-119">Doporučené pořadí elementů zásobníku je následující:</span><span class="sxs-lookup"><span data-stu-id="307d4-119">The recommended order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="307d4-120">Transakce (volitelné)</span><span class="sxs-lookup"><span data-stu-id="307d4-120">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="307d4-121">Spolehlivé zasílání zpráv (volitelné)</span><span class="sxs-lookup"><span data-stu-id="307d4-121">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="307d4-122">Zabezpečení (volitelné)</span><span class="sxs-lookup"><span data-stu-id="307d4-122">Security (optional)</span></span>  
  
4.  <span data-ttu-id="307d4-123">Kodér</span><span class="sxs-lookup"><span data-stu-id="307d4-123">Encoder</span></span>  
  
5.  <span data-ttu-id="307d4-124">Přenos</span><span class="sxs-lookup"><span data-stu-id="307d4-124">Transport</span></span>  
  
 <span data-ttu-id="307d4-125">Vlastní vazby jsou označeny jejich `name` atribut.</span><span class="sxs-lookup"><span data-stu-id="307d4-125">Custom bindings are identified by their `name` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="307d4-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="307d4-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- [<span data-ttu-id="307d4-127">Vazby</span><span class="sxs-lookup"><span data-stu-id="307d4-127">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="307d4-128">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="307d4-128">Custom Bindings</span></span>](../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="307d4-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="307d4-129">\<customBinding></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
