---
title: '&lt;transport&gt; – &lt;netNamedPipeBinding&gt;'
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: c42132f774257589b9020248188ee8d972eb92ba
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48779241"
---
# <a name="lttransportgt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="6f715-102">&lt;transport&gt; – &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="6f715-102">&lt;transport&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="6f715-103">Definuje nastavení zabezpečení přenosu pro pojmenovaný kanál.</span><span class="sxs-lookup"><span data-stu-id="6f715-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="6f715-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6f715-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6f715-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="6f715-105">\<bindings></span></span>  
<span data-ttu-id="6f715-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="6f715-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="6f715-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="6f715-107">\<binding></span></span>  
<span data-ttu-id="6f715-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="6f715-108">\<security></span></span>  
<span data-ttu-id="6f715-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="6f715-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f715-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6f715-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding>  
      <security mode="None/Transport">  
            <transport protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f715-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6f715-111">Attributes and Elements</span></span>  
 <span data-ttu-id="6f715-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6f715-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f715-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="6f715-113">Attributes</span></span>  
  
|<span data-ttu-id="6f715-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="6f715-114">Attribute</span></span>|<span data-ttu-id="6f715-115">Popis</span><span class="sxs-lookup"><span data-stu-id="6f715-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6f715-116">Třída protectionLevel</span><span class="sxs-lookup"><span data-stu-id="6f715-116">protectionLevel</span></span>|<span data-ttu-id="6f715-117">Definuje úroveň ochrany pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="6f715-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="6f715-118">Podepisování zpráv snižuje riziko manipulace s zprávy při jejich přenosu od jiných dodavatelů.</span><span class="sxs-lookup"><span data-stu-id="6f715-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="6f715-119">Šifrování poskytuje data úrovně ochrany osobních údajů při přenosu.</span><span class="sxs-lookup"><span data-stu-id="6f715-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="6f715-120">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="6f715-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="6f715-121">-Žádný: Žádná ochrana.</span><span class="sxs-lookup"><span data-stu-id="6f715-121">-   None: No protection.</span></span><br /><span data-ttu-id="6f715-122">-Sign: Jsou podepsané zprávy.</span><span class="sxs-lookup"><span data-stu-id="6f715-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="6f715-123">-EncryptAndSign: Zprávy jsou zašifrovaná a podepsaná.</span><span class="sxs-lookup"><span data-stu-id="6f715-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="6f715-124">Výchozí hodnota je EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="6f715-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f715-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6f715-125">Child Elements</span></span>  
 <span data-ttu-id="6f715-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="6f715-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f715-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6f715-127">Parent Elements</span></span>  
  
|<span data-ttu-id="6f715-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="6f715-128">Element</span></span>|<span data-ttu-id="6f715-129">Popis</span><span class="sxs-lookup"><span data-stu-id="6f715-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f715-130">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="6f715-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="6f715-131">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="6f715-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6f715-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f715-132">See Also</span></span>  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>  
 [<span data-ttu-id="6f715-133">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="6f715-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="6f715-134">Vazby</span><span class="sxs-lookup"><span data-stu-id="6f715-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="6f715-135">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="6f715-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="6f715-136">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="6f715-136">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="6f715-137">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="6f715-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
