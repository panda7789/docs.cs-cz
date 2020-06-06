---
title: <compositeDuplex>
ms.date: 03/30/2017
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
ms.openlocfilehash: c3bae4dfee36e9de62c27bbccecd9a31a5b7d459
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736787"
---
# \<compositeDuplex>
<span data-ttu-id="4fa14-101">Definuje prvek vazby, který se používá v případě, že klient musí vystavit koncový bod, který bude službě odesílat zprávy zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="4fa14-101">Defines the binding element that is used when the client must expose an endpoint for the service to send messages back to the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<compositeDuplex>**  
  
## <a name="syntax"></a><span data-ttu-id="4fa14-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fa14-102">Syntax</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4fa14-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4fa14-103">Attributes and Elements</span></span>  
 <span data-ttu-id="4fa14-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4fa14-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4fa14-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="4fa14-105">Attributes</span></span>  
  
|<span data-ttu-id="4fa14-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="4fa14-106">Attribute</span></span>|<span data-ttu-id="4fa14-107">Popis</span><span class="sxs-lookup"><span data-stu-id="4fa14-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4fa14-108">clientBaseAddress</span><span class="sxs-lookup"><span data-stu-id="4fa14-108">clientBaseAddress</span></span>|<span data-ttu-id="4fa14-109">Identifikátor URI, který nastaví adresu back-Channel v duplexovém režimu.</span><span class="sxs-lookup"><span data-stu-id="4fa14-109">A URI that sets the address of the back channel in duplex mode.</span></span> <span data-ttu-id="4fa14-110">Služba používá tuto adresu k tomu, aby kontaktovala a navázala spojení s klientem.</span><span class="sxs-lookup"><span data-stu-id="4fa14-110">The service uses this address to make contact and establish a connection with the client.</span></span><br /><br /> <span data-ttu-id="4fa14-111">Pokud tento atribut není nastaven, `full qualified name+default port\TemporaryIndigoAddress\guid` je vygenerována výchozí adresa "".</span><span class="sxs-lookup"><span data-stu-id="4fa14-111">If this attribute is not set, a default address "`full qualified name+default port\TemporaryIndigoAddress\guid`" is generated.</span></span> <span data-ttu-id="4fa14-112">Výchozí formát je `null`.</span><span class="sxs-lookup"><span data-stu-id="4fa14-112">The default is `null`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4fa14-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4fa14-113">Child Elements</span></span>  
 <span data-ttu-id="4fa14-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="4fa14-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4fa14-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4fa14-115">Parent Elements</span></span>  
  
|<span data-ttu-id="4fa14-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="4fa14-116">Element</span></span>|<span data-ttu-id="4fa14-117">Description</span><span class="sxs-lookup"><span data-stu-id="4fa14-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="4fa14-118">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="4fa14-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fa14-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4fa14-119">Remarks</span></span>  
 <span data-ttu-id="4fa14-120">Tento prvek konfigurace se používá s přenosy, které nativně neumožňují duplexní komunikaci, například HTTP.</span><span class="sxs-lookup"><span data-stu-id="4fa14-120">This configuration element is used with transports that do not allow duplex communications natively, for example, HTTP.</span></span> <span data-ttu-id="4fa14-121">Protokol TCP naopak umožňuje nativně duplexní komunikaci nativně a nevyžaduje použití tohoto elementu vazby, aby služba odesílala zprávy zpátky klientovi.</span><span class="sxs-lookup"><span data-stu-id="4fa14-121">TCP, by contrast, allows duplex communications natively, and does not require the use of this binding element for the service to send messages back to a client.</span></span>  
  
 <span data-ttu-id="4fa14-122">Klient musí vystavit adresu, aby mohla služba vytvořit kontakt a navázat připojení.</span><span class="sxs-lookup"><span data-stu-id="4fa14-122">The client must expose an address for the service to make contact and establish a connection.</span></span> <span data-ttu-id="4fa14-123">Tato adresa klienta je poskytována `clientBaseAddress` atributem.</span><span class="sxs-lookup"><span data-stu-id="4fa14-123">This client address is provided by the `clientBaseAddress` attribute.</span></span> <span data-ttu-id="4fa14-124">Všimněte si, že Windows Communication Foundation (WCF) automaticky vygeneruje ClientBaseAddress, pokud ho uživatel explicitně nenastaví.</span><span class="sxs-lookup"><span data-stu-id="4fa14-124">Note that Windows Communication Foundation (WCF) auto-generates a ClientBaseAddress if one is not explicitly set by the user.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fa14-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="4fa14-125">Example</span></span>  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />
```  
  
## <a name="see-also"></a><span data-ttu-id="4fa14-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="4fa14-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.CompositeDuplexElement>
- <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="4fa14-127">Vazby</span><span class="sxs-lookup"><span data-stu-id="4fa14-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="4fa14-128">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="4fa14-128">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="4fa14-129">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="4fa14-129">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
