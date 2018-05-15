---
title: '&lt;compositeDuplex&gt;'
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: ce04eb96868da9760412e37d2335d020cc768ac9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltcompositeduplexgt"></a><span data-ttu-id="1ef06-102">&lt;compositeDuplex&gt;</span><span class="sxs-lookup"><span data-stu-id="1ef06-102">&lt;compositeDuplex&gt;</span></span>
<span data-ttu-id="1ef06-103">Definuje vazbu elementu, který se používá, pokud klient musí vystavit koncový bod pro službu pro odeslání zprávy zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="1ef06-103">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="1ef06-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1ef06-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1ef06-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="1ef06-105">\<bindings></span></span>  
<span data-ttu-id="1ef06-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1ef06-106">\<customBinding></span></span>  
<span data-ttu-id="1ef06-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="1ef06-107">\<binding></span></span>  
<span data-ttu-id="1ef06-108">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="1ef06-108">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ef06-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1ef06-109">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ef06-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1ef06-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1ef06-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1ef06-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ef06-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="1ef06-112">Attributes</span></span>  
  
|<span data-ttu-id="1ef06-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="1ef06-113">Attribute</span></span>|<span data-ttu-id="1ef06-114">Popis</span><span class="sxs-lookup"><span data-stu-id="1ef06-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1ef06-115">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="1ef06-115">clientBaseAddress</span></span>|<span data-ttu-id="1ef06-116">Identifikátor URI, který nastaví adresu používající back channel v duplexní režim.</span><span class="sxs-lookup"><span data-stu-id="1ef06-116">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="1ef06-117">Služba používá tuto adresu, aby kontaktovat a navázat spojení s klientem.</span><span class="sxs-lookup"><span data-stu-id="1ef06-117">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="1ef06-118">Pokud není tento atribut nastavit, výchozí adresa "`full qualified name+default port\TemporaryIndigoAddress\guid`" se vygeneruje.</span><span class="sxs-lookup"><span data-stu-id="1ef06-118">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="1ef06-119">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="1ef06-119">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ef06-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1ef06-120">Child Elements</span></span>  
 <span data-ttu-id="1ef06-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="1ef06-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1ef06-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1ef06-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1ef06-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="1ef06-123">Element</span></span>|<span data-ttu-id="1ef06-124">Popis</span><span class="sxs-lookup"><span data-stu-id="1ef06-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ef06-125">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="1ef06-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="1ef06-126">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="1ef06-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ef06-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1ef06-127">Remarks</span></span>  
 <span data-ttu-id="1ef06-128">Tento element konfigurace se používá s přenosy, které neumožňují duplexní komunikace nativně, například HTTP.</span><span class="sxs-lookup"><span data-stu-id="1ef06-128">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="1ef06-129">TCP, naopak umožňuje duplexní komunikace nativně a nevyžaduje použití tohoto elementu vazby pro službu k odesílání zpráv zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="1ef06-129">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="1ef06-130">Klient musí vystavit adresu pro službu, aby kontaktovat a navázat připojení.</span><span class="sxs-lookup"><span data-stu-id="1ef06-130">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="1ef06-131">Tato adresa klienta poskytuje `clientBaseAddress` atribut.</span><span class="sxs-lookup"><span data-stu-id="1ef06-131">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="1ef06-132">Všimněte si, že Windows Communication Foundation (WCF) automaticky generuje ClientBaseAddress Pokud není explicitně nastaven uživatelem.</span><span class="sxs-lookup"><span data-stu-id="1ef06-132">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ef06-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="1ef06-133">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ef06-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="1ef06-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CompositeDuplexElement>  
 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="1ef06-135">Vazby</span><span class="sxs-lookup"><span data-stu-id="1ef06-135">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="1ef06-136">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="1ef06-136">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="1ef06-137">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="1ef06-137">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="1ef06-138">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1ef06-138">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
