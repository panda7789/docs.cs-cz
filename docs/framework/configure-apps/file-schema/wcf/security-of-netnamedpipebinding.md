---
title: <security> z <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 31ea31ce6880a770c966350cd931e487396c4d63
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736435"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="147d4-102">\<security> z \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="147d4-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="147d4-103">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="147d4-103">Defines the security settings for a binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="147d4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="147d4-104">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="147d4-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="147d4-105">Attributes and Elements</span></span>  
 <span data-ttu-id="147d4-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="147d4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="147d4-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="147d4-107">Attributes</span></span>  
  
|<span data-ttu-id="147d4-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="147d4-108">Attribute</span></span>|<span data-ttu-id="147d4-109">Popis</span><span class="sxs-lookup"><span data-stu-id="147d4-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="147d4-110">režim</span><span class="sxs-lookup"><span data-stu-id="147d4-110">mode</span></span>|<span data-ttu-id="147d4-111">Určuje typ zabezpečení, který se použije pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="147d4-111">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="147d4-112">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="147d4-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="147d4-113">-None: zakáže zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="147d4-113">-   None: This disables security.</span></span><br /><span data-ttu-id="147d4-114">-Transport: zabezpečení je zajištěno pomocí základního zabezpečení založeného na přenosu.</span><span class="sxs-lookup"><span data-stu-id="147d4-114">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="147d4-115">Úroveň ochrany je možné řídit pomocí tohoto režimu.</span><span class="sxs-lookup"><span data-stu-id="147d4-115">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="147d4-116">– Výchozí hodnota je Transport.</span><span class="sxs-lookup"><span data-stu-id="147d4-116">-   The default value is Transport.</span></span> <span data-ttu-id="147d4-117">Tento atribut je typu <xref:System.ServiceModel.NetNamedPipeSecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="147d4-117">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="147d4-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="147d4-118">Child Elements</span></span>  
  
|<span data-ttu-id="147d4-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="147d4-119">Element</span></span>|<span data-ttu-id="147d4-120">Description</span><span class="sxs-lookup"><span data-stu-id="147d4-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="147d4-121">transport</span><span class="sxs-lookup"><span data-stu-id="147d4-121">transport</span></span>|<span data-ttu-id="147d4-122">Definuje nastavení zabezpečení pro přenos.</span><span class="sxs-lookup"><span data-stu-id="147d4-122">Defines the security settings for the transport.</span></span> <span data-ttu-id="147d4-123">Tento prvek je typu <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="147d4-123">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="147d4-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="147d4-124">Parent Elements</span></span>  
  
|<span data-ttu-id="147d4-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="147d4-125">Element</span></span>|<span data-ttu-id="147d4-126">Description</span><span class="sxs-lookup"><span data-stu-id="147d4-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="147d4-127">vazba</span><span class="sxs-lookup"><span data-stu-id="147d4-127">binding</span></span>|<span data-ttu-id="147d4-128">Prvek vazby prvku [\<netNamedPipeBinding>](netnamedpipebinding.md) .</span><span class="sxs-lookup"><span data-stu-id="147d4-128">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="147d4-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="147d4-129">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="147d4-130">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="147d4-130">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="147d4-131">Výběr typu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="147d4-131">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="147d4-132">Vazby</span><span class="sxs-lookup"><span data-stu-id="147d4-132">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="147d4-133">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="147d4-133">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="147d4-134">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="147d4-134">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
