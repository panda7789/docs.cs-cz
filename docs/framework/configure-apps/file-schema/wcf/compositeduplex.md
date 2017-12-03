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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 292067daacc9319c144e9d0f2da9f27ca2fcf5b1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltcompositeduplexgt"></a><span data-ttu-id="41e82-102">&lt;compositeDuplex&gt;</span><span class="sxs-lookup"><span data-stu-id="41e82-102">&lt;compositeDuplex&gt;</span></span>
<span data-ttu-id="41e82-103">Definuje vazbu elementu, který se používá, pokud klient musí vystavit koncový bod pro službu pro odeslání zprávy zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="41e82-103">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="41e82-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="41e82-104">\<system.serviceModel></span></span>  
<span data-ttu-id="41e82-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="41e82-105">\<bindings></span></span>  
<span data-ttu-id="41e82-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="41e82-106">\<customBinding></span></span>  
<span data-ttu-id="41e82-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="41e82-107">\<binding></span></span>  
<span data-ttu-id="41e82-108">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="41e82-108">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41e82-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41e82-109">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41e82-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="41e82-110">Attributes and Elements</span></span>  
 <span data-ttu-id="41e82-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="41e82-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41e82-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="41e82-112">Attributes</span></span>  
  
|<span data-ttu-id="41e82-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="41e82-113">Attribute</span></span>|<span data-ttu-id="41e82-114">Popis</span><span class="sxs-lookup"><span data-stu-id="41e82-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="41e82-115">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="41e82-115">clientBaseAddress</span></span>|<span data-ttu-id="41e82-116">Identifikátor URI, který nastaví adresu používající back channel v duplexní režim.</span><span class="sxs-lookup"><span data-stu-id="41e82-116">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="41e82-117">Služba používá tuto adresu, aby kontaktovat a navázat spojení s klientem.</span><span class="sxs-lookup"><span data-stu-id="41e82-117">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="41e82-118">Pokud není tento atribut nastavit, výchozí adresa "`full qualified name+default port\TemporaryIndigoAddress\guid`" se vygeneruje.</span><span class="sxs-lookup"><span data-stu-id="41e82-118">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="41e82-119">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="41e82-119">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="41e82-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="41e82-120">Child Elements</span></span>  
 <span data-ttu-id="41e82-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="41e82-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="41e82-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="41e82-122">Parent Elements</span></span>  
  
|<span data-ttu-id="41e82-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="41e82-123">Element</span></span>|<span data-ttu-id="41e82-124">Popis</span><span class="sxs-lookup"><span data-stu-id="41e82-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41e82-125">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="41e82-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="41e82-126">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="41e82-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41e82-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="41e82-127">Remarks</span></span>  
 <span data-ttu-id="41e82-128">Tento element konfigurace se používá s přenosy, které neumožňují duplexní komunikace nativně, například HTTP.</span><span class="sxs-lookup"><span data-stu-id="41e82-128">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="41e82-129">TCP, naopak umožňuje duplexní komunikace nativně a nevyžaduje použití tohoto elementu vazby pro službu k odesílání zpráv zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="41e82-129">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="41e82-130">Klient musí vystavit adresu pro službu, aby kontaktovat a navázat připojení.</span><span class="sxs-lookup"><span data-stu-id="41e82-130">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="41e82-131">Tato adresa klienta poskytuje `clientBaseAddress` atribut.</span><span class="sxs-lookup"><span data-stu-id="41e82-131">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="41e82-132">Všimněte si, že Windows Communication Foundation (WCF) automaticky generuje ClientBaseAddress Pokud není explicitně nastaven uživatelem.</span><span class="sxs-lookup"><span data-stu-id="41e82-132">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41e82-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="41e82-133">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="41e82-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="41e82-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.CompositeDuplexElement>  
 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="41e82-135">Vazby</span><span class="sxs-lookup"><span data-stu-id="41e82-135">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="41e82-136">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="41e82-136">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="41e82-137">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="41e82-137">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="41e82-138">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="41e82-138">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
