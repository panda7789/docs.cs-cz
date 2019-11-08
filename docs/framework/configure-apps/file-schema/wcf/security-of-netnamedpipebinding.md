---
title: <security> z <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 31ea31ce6880a770c966350cd931e487396c4d63
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736435"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="22c64-102">> \<zabezpečení \<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="22c64-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="22c64-103">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="22c64-103">Defines the security settings for a binding.</span></span>  
  
<span data-ttu-id="22c64-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="22c64-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="22c64-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="22c64-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="22c64-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="22c64-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="22c64-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netNamedPipeBinding >** ](netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="22c64-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)</span></span>\
<span data-ttu-id="22c64-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="22c64-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="22c64-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zabezpečení >**</span><span class="sxs-lookup"><span data-stu-id="22c64-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22c64-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22c64-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="22c64-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="22c64-111">Attributes and Elements</span></span>  
 <span data-ttu-id="22c64-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="22c64-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="22c64-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="22c64-113">Attributes</span></span>  
  
|<span data-ttu-id="22c64-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="22c64-114">Attribute</span></span>|<span data-ttu-id="22c64-115">Popis</span><span class="sxs-lookup"><span data-stu-id="22c64-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="22c64-116">režim</span><span class="sxs-lookup"><span data-stu-id="22c64-116">mode</span></span>|<span data-ttu-id="22c64-117">Určuje typ zabezpečení, který se použije pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="22c64-117">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="22c64-118">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="22c64-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="22c64-119">-None: zakáže zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="22c64-119">-   None: This disables security.</span></span><br /><span data-ttu-id="22c64-120">-Transport: zabezpečení je zajištěno pomocí základního zabezpečení založeného na přenosu.</span><span class="sxs-lookup"><span data-stu-id="22c64-120">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="22c64-121">Úroveň ochrany je možné řídit pomocí tohoto režimu.</span><span class="sxs-lookup"><span data-stu-id="22c64-121">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="22c64-122">– Výchozí hodnota je Transport.</span><span class="sxs-lookup"><span data-stu-id="22c64-122">-   The default value is Transport.</span></span> <span data-ttu-id="22c64-123">Tento atribut je typu <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="22c64-123">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="22c64-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="22c64-124">Child Elements</span></span>  
  
|<span data-ttu-id="22c64-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="22c64-125">Element</span></span>|<span data-ttu-id="22c64-126">Popis</span><span class="sxs-lookup"><span data-stu-id="22c64-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="22c64-127">transport</span><span class="sxs-lookup"><span data-stu-id="22c64-127">transport</span></span>|<span data-ttu-id="22c64-128">Definuje nastavení zabezpečení pro přenos.</span><span class="sxs-lookup"><span data-stu-id="22c64-128">Defines the security settings for the transport.</span></span> <span data-ttu-id="22c64-129">Tento prvek je typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="22c64-129">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="22c64-130">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="22c64-130">Parent Elements</span></span>  
  
|<span data-ttu-id="22c64-131">Prvek</span><span class="sxs-lookup"><span data-stu-id="22c64-131">Element</span></span>|<span data-ttu-id="22c64-132">Popis</span><span class="sxs-lookup"><span data-stu-id="22c64-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="22c64-133">vazba</span><span class="sxs-lookup"><span data-stu-id="22c64-133">binding</span></span>|<span data-ttu-id="22c64-134">Prvek vazby [\<netNamedPipeBinding >](netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="22c64-134">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="22c64-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="22c64-135">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="22c64-136">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="22c64-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="22c64-137">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="22c64-137">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="22c64-138">Vazby</span><span class="sxs-lookup"><span data-stu-id="22c64-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="22c64-139">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="22c64-139">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="22c64-140">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="22c64-140">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="22c64-141">vazba \<</span><span class="sxs-lookup"><span data-stu-id="22c64-141">\<binding></span></span>](bindings.md)
