---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: e79b3e1aeecc52bf41ae759dc15ebf1c8211beb2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926070"
---
# <a name="compositeduplex"></a><span data-ttu-id="ac788-101">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="ac788-101">\<compositeDuplex></span></span>
<span data-ttu-id="ac788-102">Definuje prvek vazby, který se používá v případě, že klient musí vystavit koncový bod, který bude službě odesílat zprávy zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="ac788-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="ac788-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="ac788-103">\<system.serviceModel></span></span>  
<span data-ttu-id="ac788-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="ac788-104">\<bindings></span></span>  
<span data-ttu-id="ac788-105">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="ac788-105">\<customBinding></span></span>  
<span data-ttu-id="ac788-106">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="ac788-106">\<binding></span></span>  
<span data-ttu-id="ac788-107">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="ac788-107">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ac788-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ac788-108">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ac788-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="ac788-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ac788-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="ac788-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ac788-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="ac788-111">Attributes</span></span>  
  
|<span data-ttu-id="ac788-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="ac788-112">Attribute</span></span>|<span data-ttu-id="ac788-113">Popis</span><span class="sxs-lookup"><span data-stu-id="ac788-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ac788-114">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="ac788-114">clientBaseAddress</span></span>|<span data-ttu-id="ac788-115">Identifikátor URI, který nastaví adresu back-Channel v duplexovém režimu.</span><span class="sxs-lookup"><span data-stu-id="ac788-115">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="ac788-116">Služba používá tuto adresu k tomu, aby kontaktovala a navázala spojení s klientem.</span><span class="sxs-lookup"><span data-stu-id="ac788-116">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="ac788-117">Pokud tento atribut není nastaven, je vygenerována výchozí`full qualified name+default port\TemporaryIndigoAddress\guid`adresa "".</span><span class="sxs-lookup"><span data-stu-id="ac788-117">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="ac788-118">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="ac788-118">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ac788-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="ac788-119">Child Elements</span></span>  
 <span data-ttu-id="ac788-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="ac788-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ac788-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="ac788-121">Parent Elements</span></span>  
  
|<span data-ttu-id="ac788-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="ac788-122">Element</span></span>|<span data-ttu-id="ac788-123">Popis</span><span class="sxs-lookup"><span data-stu-id="ac788-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ac788-124">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="ac788-124">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="ac788-125">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="ac788-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ac788-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ac788-126">Remarks</span></span>  
 <span data-ttu-id="ac788-127">Tento prvek konfigurace se používá s přenosy, které nativně neumožňují duplexní komunikaci, například HTTP.</span><span class="sxs-lookup"><span data-stu-id="ac788-127">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="ac788-128">Protokol TCP naopak umožňuje nativně duplexní komunikaci nativně a nevyžaduje použití tohoto elementu vazby, aby služba odesílala zprávy zpátky klientovi.</span><span class="sxs-lookup"><span data-stu-id="ac788-128">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="ac788-129">Klient musí vystavit adresu, aby mohla služba vytvořit kontakt a navázat připojení.</span><span class="sxs-lookup"><span data-stu-id="ac788-129">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="ac788-130">Tato adresa klienta je poskytována `clientBaseAddress` atributem.</span><span class="sxs-lookup"><span data-stu-id="ac788-130">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="ac788-131">Všimněte si, že Windows Communication Foundation (WCF) automaticky vygeneruje ClientBaseAddress, pokud ho uživatel explicitně nenastaví.</span><span class="sxs-lookup"><span data-stu-id="ac788-131">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ac788-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="ac788-132">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="ac788-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac788-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="ac788-134">Vazby</span><span class="sxs-lookup"><span data-stu-id="ac788-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="ac788-135">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="ac788-135">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="ac788-136">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="ac788-136">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="ac788-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="ac788-137">\<customBinding></span></span>](custombinding.md)
