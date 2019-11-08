---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: c3bae4dfee36e9de62c27bbccecd9a31a5b7d459
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736787"
---
# <a name="compositeduplex"></a><span data-ttu-id="71d17-101">\<compositeDuplex ></span><span class="sxs-lookup"><span data-stu-id="71d17-101">\<compositeDuplex></span></span>
<span data-ttu-id="71d17-102">Definuje prvek vazby, který se používá v případě, že klient musí vystavit koncový bod, který bude službě odesílat zprávy zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="71d17-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
<span data-ttu-id="71d17-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="71d17-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="71d17-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="71d17-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="71d17-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="71d17-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="71d17-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="71d17-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="71d17-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="71d17-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="71d17-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<compositeDuplex >**</span><span class="sxs-lookup"><span data-stu-id="71d17-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compositeDuplex>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71d17-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71d17-109">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71d17-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="71d17-110">Attributes and Elements</span></span>  
 <span data-ttu-id="71d17-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="71d17-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71d17-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="71d17-112">Attributes</span></span>  
  
|<span data-ttu-id="71d17-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="71d17-113">Attribute</span></span>|<span data-ttu-id="71d17-114">Popis</span><span class="sxs-lookup"><span data-stu-id="71d17-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="71d17-115">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="71d17-115">clientBaseAddress</span></span>|<span data-ttu-id="71d17-116">Identifikátor URI, který nastaví adresu back-Channel v duplexovém režimu.</span><span class="sxs-lookup"><span data-stu-id="71d17-116">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="71d17-117">Služba používá tuto adresu k tomu, aby kontaktovala a navázala spojení s klientem.</span><span class="sxs-lookup"><span data-stu-id="71d17-117">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="71d17-118">Pokud tento atribut není nastaven, je vygenerována výchozí adresa "`full qualified name+default port\TemporaryIndigoAddress\guid`".</span><span class="sxs-lookup"><span data-stu-id="71d17-118">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="71d17-119">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="71d17-119">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71d17-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="71d17-120">Child Elements</span></span>  
 <span data-ttu-id="71d17-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="71d17-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="71d17-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="71d17-122">Parent Elements</span></span>  
  
|<span data-ttu-id="71d17-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="71d17-123">Element</span></span>|<span data-ttu-id="71d17-124">Popis</span><span class="sxs-lookup"><span data-stu-id="71d17-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="71d17-125">vazba \<</span><span class="sxs-lookup"><span data-stu-id="71d17-125">\<binding></span></span>](bindings.md)|<span data-ttu-id="71d17-126">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="71d17-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71d17-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="71d17-127">Remarks</span></span>  
 <span data-ttu-id="71d17-128">Tento prvek konfigurace se používá s přenosy, které nativně neumožňují duplexní komunikaci, například HTTP.</span><span class="sxs-lookup"><span data-stu-id="71d17-128">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="71d17-129">Protokol TCP naopak umožňuje nativně duplexní komunikaci nativně a nevyžaduje použití tohoto elementu vazby, aby služba odesílala zprávy zpátky klientovi.</span><span class="sxs-lookup"><span data-stu-id="71d17-129">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="71d17-130">Klient musí vystavit adresu, aby mohla služba vytvořit kontakt a navázat připojení.</span><span class="sxs-lookup"><span data-stu-id="71d17-130">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="71d17-131">Tato adresa klienta je poskytována atributem `clientBaseAddress`.</span><span class="sxs-lookup"><span data-stu-id="71d17-131">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="71d17-132">Všimněte si, že Windows Communication Foundation (WCF) automaticky vygeneruje ClientBaseAddress, pokud ho uživatel explicitně nenastaví.</span><span class="sxs-lookup"><span data-stu-id="71d17-132">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71d17-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="71d17-133">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="71d17-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71d17-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="71d17-135">Vazby</span><span class="sxs-lookup"><span data-stu-id="71d17-135">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="71d17-136">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="71d17-136">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="71d17-137">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="71d17-137">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="71d17-138">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="71d17-138">\<customBinding></span></span>](custombinding.md)
