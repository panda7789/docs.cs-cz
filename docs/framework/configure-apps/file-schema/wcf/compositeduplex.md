---
title: '&lt;compositeDuplex&gt;'
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: 4b84b4f2816dc68b7dcee784d957189728e5a4b2
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54149043"
---
# <a name="ltcompositeduplexgt"></a><span data-ttu-id="eb9ea-102">&lt;compositeDuplex&gt;</span><span class="sxs-lookup"><span data-stu-id="eb9ea-102">&lt;compositeDuplex&gt;</span></span>
<span data-ttu-id="eb9ea-103">Definuje prvek vazby, který se používá, když klient musí vystavit koncový bod služby umožňující odesílání zpráv zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="eb9ea-103">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="eb9ea-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="eb9ea-104">\<system.serviceModel></span></span>  
<span data-ttu-id="eb9ea-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="eb9ea-105">\<bindings></span></span>  
<span data-ttu-id="eb9ea-106">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="eb9ea-106">\<customBinding></span></span>  
<span data-ttu-id="eb9ea-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="eb9ea-107">\<binding></span></span>  
<span data-ttu-id="eb9ea-108">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="eb9ea-108">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb9ea-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb9ea-109">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eb9ea-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="eb9ea-110">Attributes and Elements</span></span>  
 <span data-ttu-id="eb9ea-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="eb9ea-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eb9ea-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="eb9ea-112">Attributes</span></span>  
  
|<span data-ttu-id="eb9ea-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="eb9ea-113">Attribute</span></span>|<span data-ttu-id="eb9ea-114">Popis</span><span class="sxs-lookup"><span data-stu-id="eb9ea-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eb9ea-115">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="eb9ea-115">clientBaseAddress</span></span>|<span data-ttu-id="eb9ea-116">Identifikátor URI, který nastaví adresu zpětného kanálu v duplexním režimu.</span><span class="sxs-lookup"><span data-stu-id="eb9ea-116">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="eb9ea-117">Služba používá tuto adresu kontaktovat a naváže připojení klienta.</span><span class="sxs-lookup"><span data-stu-id="eb9ea-117">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="eb9ea-118">Pokud není tento atribut nastaven, výchozí adresa "`full qualified name+default port\TemporaryIndigoAddress\guid`" je generován.</span><span class="sxs-lookup"><span data-stu-id="eb9ea-118">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="eb9ea-119">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="eb9ea-119">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eb9ea-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="eb9ea-120">Child Elements</span></span>  
 <span data-ttu-id="eb9ea-121">Žádná</span><span class="sxs-lookup"><span data-stu-id="eb9ea-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eb9ea-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="eb9ea-122">Parent Elements</span></span>  
  
|<span data-ttu-id="eb9ea-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="eb9ea-123">Element</span></span>|<span data-ttu-id="eb9ea-124">Popis</span><span class="sxs-lookup"><span data-stu-id="eb9ea-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eb9ea-125">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="eb9ea-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="eb9ea-126">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="eb9ea-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eb9ea-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eb9ea-127">Remarks</span></span>  
 <span data-ttu-id="eb9ea-128">Tento prvek konfigurace se používá s přenosy, které neumožňují duplexní komunikaci nativně, například HTTP.</span><span class="sxs-lookup"><span data-stu-id="eb9ea-128">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="eb9ea-129">TCP, naopak umožňuje nativně duplexní komunikaci a nevyžaduje použití tohoto elementu vazby pro služby umožňující odesílání zpráv zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="eb9ea-129">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="eb9ea-130">Klient musí vystavit adresu pro službu kontaktovat a navázat připojení.</span><span class="sxs-lookup"><span data-stu-id="eb9ea-130">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="eb9ea-131">Tato adresa klienta poskytuje `clientBaseAddress` atribut.</span><span class="sxs-lookup"><span data-stu-id="eb9ea-131">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="eb9ea-132">Všimněte si, že Windows Communication Foundation (WCF) automaticky generuje ClientBaseAddress Pokud není explicitně nastaven uživatelem.</span><span class="sxs-lookup"><span data-stu-id="eb9ea-132">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb9ea-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="eb9ea-133">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="eb9ea-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb9ea-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CompositeDuplexElement>  
 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="eb9ea-135">Vazby</span><span class="sxs-lookup"><span data-stu-id="eb9ea-135">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="eb9ea-136">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="eb9ea-136">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="eb9ea-137">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="eb9ea-137">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="eb9ea-138">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="eb9ea-138">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
