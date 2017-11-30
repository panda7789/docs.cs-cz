---
title: '&lt;compositeDuplex&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f9f82d4b6ac69e0edc0a2ad2cddfd89ee6ac72db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltcompositeduplexgt"></a><span data-ttu-id="cabdc-102">&lt;compositeDuplex&gt;</span><span class="sxs-lookup"><span data-stu-id="cabdc-102">&lt;compositeDuplex&gt;</span></span>
<span data-ttu-id="cabdc-103">Definuje vazbu elementu, který se používá, pokud klient musí vystavit koncový bod pro službu pro odeslání zprávy zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="cabdc-103">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="cabdc-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="cabdc-104">\<system.serviceModel></span></span>  
<span data-ttu-id="cabdc-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="cabdc-105">\<bindings></span></span>  
<span data-ttu-id="cabdc-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="cabdc-106">\<customBinding></span></span>  
<span data-ttu-id="cabdc-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="cabdc-107">\<binding></span></span>  
<span data-ttu-id="cabdc-108">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="cabdc-108">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cabdc-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cabdc-109">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cabdc-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cabdc-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cabdc-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cabdc-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cabdc-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="cabdc-112">Attributes</span></span>  
  
|<span data-ttu-id="cabdc-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="cabdc-113">Attribute</span></span>|<span data-ttu-id="cabdc-114">Popis</span><span class="sxs-lookup"><span data-stu-id="cabdc-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cabdc-115">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="cabdc-115">clientBaseAddress</span></span>|<span data-ttu-id="cabdc-116">Identifikátor URI, který nastaví adresu používající back channel v duplexní režim.</span><span class="sxs-lookup"><span data-stu-id="cabdc-116">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="cabdc-117">Služba používá tuto adresu, aby kontaktovat a navázat spojení s klientem.</span><span class="sxs-lookup"><span data-stu-id="cabdc-117">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="cabdc-118">Pokud není tento atribut nastavit, výchozí adresa "`full qualified name+default port\TemporaryIndigoAddress\guid`" se vygeneruje.</span><span class="sxs-lookup"><span data-stu-id="cabdc-118">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="cabdc-119">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="cabdc-119">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cabdc-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cabdc-120">Child Elements</span></span>  
 <span data-ttu-id="cabdc-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="cabdc-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cabdc-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cabdc-122">Parent Elements</span></span>  
  
|<span data-ttu-id="cabdc-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="cabdc-123">Element</span></span>|<span data-ttu-id="cabdc-124">Popis</span><span class="sxs-lookup"><span data-stu-id="cabdc-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cabdc-125">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="cabdc-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="cabdc-126">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="cabdc-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cabdc-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cabdc-127">Remarks</span></span>  
 <span data-ttu-id="cabdc-128">Tento element konfigurace se používá s přenosy, které neumožňují duplexní komunikace nativně, například HTTP.</span><span class="sxs-lookup"><span data-stu-id="cabdc-128">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="cabdc-129">TCP, naopak umožňuje duplexní komunikace nativně a nevyžaduje použití tohoto elementu vazby pro službu k odesílání zpráv zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="cabdc-129">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="cabdc-130">Klient musí vystavit adresu pro službu, aby kontaktovat a navázat připojení.</span><span class="sxs-lookup"><span data-stu-id="cabdc-130">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="cabdc-131">Tato adresa klienta poskytuje `clientBaseAddress` atribut.</span><span class="sxs-lookup"><span data-stu-id="cabdc-131">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="cabdc-132">Všimněte si, že Windows Communication Foundation (WCF) automaticky generuje ClientBaseAddress Pokud není explicitně nastaven uživatelem.</span><span class="sxs-lookup"><span data-stu-id="cabdc-132">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cabdc-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="cabdc-133">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="cabdc-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="cabdc-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CompositeDuplexElement>  
 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="cabdc-135">Vazby</span><span class="sxs-lookup"><span data-stu-id="cabdc-135">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="cabdc-136">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="cabdc-136">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="cabdc-137">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="cabdc-137">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="cabdc-138">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="cabdc-138">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
