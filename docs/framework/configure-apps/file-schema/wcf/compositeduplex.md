---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: 1e5ecc2b937aa0cdb159a6cbd1222fe6d4af79fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59159845"
---
# <a name="compositeduplex"></a><span data-ttu-id="73a4a-101">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="73a4a-101">\<compositeDuplex></span></span>
<span data-ttu-id="73a4a-102">Definuje prvek vazby, který se používá, když klient musí vystavit koncový bod služby umožňující odesílání zpráv zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="73a4a-102">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
 <span data-ttu-id="73a4a-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="73a4a-103">\<system.serviceModel></span></span>  
<span data-ttu-id="73a4a-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="73a4a-104">\<bindings></span></span>  
<span data-ttu-id="73a4a-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="73a4a-105">\<customBinding></span></span>  
<span data-ttu-id="73a4a-106">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="73a4a-106">\<binding></span></span>  
<span data-ttu-id="73a4a-107">\<compositeDuplex></span><span class="sxs-lookup"><span data-stu-id="73a4a-107">\<compositeDuplex></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73a4a-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73a4a-108">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73a4a-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="73a4a-109">Attributes and Elements</span></span>  
 <span data-ttu-id="73a4a-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="73a4a-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73a4a-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="73a4a-111">Attributes</span></span>  
  
|<span data-ttu-id="73a4a-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="73a4a-112">Attribute</span></span>|<span data-ttu-id="73a4a-113">Popis</span><span class="sxs-lookup"><span data-stu-id="73a4a-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73a4a-114">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="73a4a-114">clientBaseAddress</span></span>|<span data-ttu-id="73a4a-115">Identifikátor URI, který nastaví adresu zpětného kanálu v duplexním režimu.</span><span class="sxs-lookup"><span data-stu-id="73a4a-115">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="73a4a-116">Služba používá tuto adresu kontaktovat a naváže připojení klienta.</span><span class="sxs-lookup"><span data-stu-id="73a4a-116">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="73a4a-117">Pokud není tento atribut nastaven, výchozí adresa "`full qualified name+default port\TemporaryIndigoAddress\guid`" je generován.</span><span class="sxs-lookup"><span data-stu-id="73a4a-117">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="73a4a-118">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="73a4a-118">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73a4a-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="73a4a-119">Child Elements</span></span>  
 <span data-ttu-id="73a4a-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="73a4a-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73a4a-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="73a4a-121">Parent Elements</span></span>  
  
|<span data-ttu-id="73a4a-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="73a4a-122">Element</span></span>|<span data-ttu-id="73a4a-123">Popis</span><span class="sxs-lookup"><span data-stu-id="73a4a-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="73a4a-124">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="73a4a-124">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="73a4a-125">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="73a4a-125">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73a4a-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="73a4a-126">Remarks</span></span>  
 <span data-ttu-id="73a4a-127">Tento prvek konfigurace se používá s přenosy, které neumožňují duplexní komunikaci nativně, například HTTP.</span><span class="sxs-lookup"><span data-stu-id="73a4a-127">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="73a4a-128">TCP, naopak umožňuje nativně duplexní komunikaci a nevyžaduje použití tohoto elementu vazby pro služby umožňující odesílání zpráv zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="73a4a-128">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="73a4a-129">Klient musí vystavit adresu pro službu kontaktovat a navázat připojení.</span><span class="sxs-lookup"><span data-stu-id="73a4a-129">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="73a4a-130">Tato adresa klienta poskytuje `clientBaseAddress` atribut.</span><span class="sxs-lookup"><span data-stu-id="73a4a-130">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="73a4a-131">Všimněte si, že Windows Communication Foundation (WCF) automaticky generuje ClientBaseAddress Pokud není explicitně nastaven uživatelem.</span><span class="sxs-lookup"><span data-stu-id="73a4a-131">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73a4a-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="73a4a-132">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="73a4a-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73a4a-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="73a4a-134">Vazby</span><span class="sxs-lookup"><span data-stu-id="73a4a-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="73a4a-135">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="73a4a-135">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="73a4a-136">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="73a4a-136">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="73a4a-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="73a4a-137">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
