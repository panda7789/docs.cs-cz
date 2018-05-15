---
title: '&lt;transport&gt; – &lt;netNamedPipeBinding&gt;'
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: 9116532c8b4aae2f7539706b97d564444195c79d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="lttransportgt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="cd63a-102">&lt;transport&gt; – &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="cd63a-102">&lt;transport&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="cd63a-103">Definuje nastavení zabezpečení přenosu pro pojmenovaný kanál.</span><span class="sxs-lookup"><span data-stu-id="cd63a-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="cd63a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cd63a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cd63a-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="cd63a-105">\<bindings></span></span>  
<span data-ttu-id="cd63a-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="cd63a-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="cd63a-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="cd63a-107">\<binding></span></span>  
<span data-ttu-id="cd63a-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="cd63a-108">\<security></span></span>  
<span data-ttu-id="cd63a-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="cd63a-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd63a-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd63a-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding>  
      <security mode="None/Transport">  
            <transport protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd63a-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cd63a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cd63a-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cd63a-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd63a-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="cd63a-113">Attributes</span></span>  
  
|<span data-ttu-id="cd63a-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="cd63a-114">Attribute</span></span>|<span data-ttu-id="cd63a-115">Popis</span><span class="sxs-lookup"><span data-stu-id="cd63a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cd63a-116">ProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="cd63a-116">protectionLevel</span></span>|<span data-ttu-id="cd63a-117">Definuje úroveň ochrany pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="cd63a-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="cd63a-118">Podepisování zpráv snižuje riziko třetích stran manipulaci s zprávy při jejich přenosu.</span><span class="sxs-lookup"><span data-stu-id="cd63a-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="cd63a-119">Během přenosu zajišťuje šifrování dat na úrovni o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="cd63a-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="cd63a-120">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="cd63a-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="cd63a-121">-None: Žádná ochrana.</span><span class="sxs-lookup"><span data-stu-id="cd63a-121">-   None: No protection.</span></span><br /><span data-ttu-id="cd63a-122">-Přihlášení: Zprávy jsou podepsané.</span><span class="sxs-lookup"><span data-stu-id="cd63a-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="cd63a-123">-EncryptAndSign: Zprávy jsou šifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="cd63a-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="cd63a-124">Výchozí hodnota je EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="cd63a-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd63a-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cd63a-125">Child Elements</span></span>  
 <span data-ttu-id="cd63a-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="cd63a-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cd63a-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cd63a-127">Parent Elements</span></span>  
  
|<span data-ttu-id="cd63a-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="cd63a-128">Element</span></span>|<span data-ttu-id="cd63a-129">Popis</span><span class="sxs-lookup"><span data-stu-id="cd63a-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cd63a-130">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="cd63a-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="cd63a-131">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="cd63a-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd63a-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd63a-132">See Also</span></span>  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>  
 [<span data-ttu-id="cd63a-133">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="cd63a-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="cd63a-134">Vazby</span><span class="sxs-lookup"><span data-stu-id="cd63a-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="cd63a-135">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="cd63a-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="cd63a-136">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="cd63a-136">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="cd63a-137">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="cd63a-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
