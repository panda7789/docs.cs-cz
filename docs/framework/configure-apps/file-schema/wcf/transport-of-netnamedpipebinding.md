---
title: '&lt;transport&gt; – &lt;netNamedPipeBinding&gt;'
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: 0006be71ee67d5f274d8af8087f2d111cddb12b2
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43407252"
---
# <a name="lttransportgt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="3497d-102">&lt;transport&gt; – &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="3497d-102">&lt;transport&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="3497d-103">Definuje nastavení zabezpečení přenosu pro pojmenovaný kanál.</span><span class="sxs-lookup"><span data-stu-id="3497d-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="3497d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3497d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3497d-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="3497d-105">\<bindings></span></span>  
<span data-ttu-id="3497d-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="3497d-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="3497d-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="3497d-107">\<binding></span></span>  
<span data-ttu-id="3497d-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="3497d-108">\<security></span></span>  
<span data-ttu-id="3497d-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="3497d-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3497d-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3497d-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding>  
      <security mode="None/Transport">  
            <transport protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3497d-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3497d-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3497d-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3497d-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3497d-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="3497d-113">Attributes</span></span>  
  
|<span data-ttu-id="3497d-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="3497d-114">Attribute</span></span>|<span data-ttu-id="3497d-115">Popis</span><span class="sxs-lookup"><span data-stu-id="3497d-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3497d-116">Třída protectionLevel</span><span class="sxs-lookup"><span data-stu-id="3497d-116">protectionLevel</span></span>|<span data-ttu-id="3497d-117">Definuje úroveň ochrany pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="3497d-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="3497d-118">Podepisování zpráv snižuje riziko manipulace s zprávy při jejich přenosu od jiných dodavatelů.</span><span class="sxs-lookup"><span data-stu-id="3497d-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="3497d-119">Šifrování poskytuje data úrovně ochrany osobních údajů při přenosu.</span><span class="sxs-lookup"><span data-stu-id="3497d-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="3497d-120">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="3497d-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3497d-121">-Žádný: Žádná ochrana.</span><span class="sxs-lookup"><span data-stu-id="3497d-121">-   None: No protection.</span></span><br /><span data-ttu-id="3497d-122">-Sign: Jsou podepsané zprávy.</span><span class="sxs-lookup"><span data-stu-id="3497d-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="3497d-123">-EncryptAndSign: Zprávy jsou zašifrovaná a podepsaná.</span><span class="sxs-lookup"><span data-stu-id="3497d-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="3497d-124">Výchozí hodnota je EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="3497d-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3497d-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3497d-125">Child Elements</span></span>  
 <span data-ttu-id="3497d-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="3497d-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3497d-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3497d-127">Parent Elements</span></span>  
  
|<span data-ttu-id="3497d-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="3497d-128">Element</span></span>|<span data-ttu-id="3497d-129">Popis</span><span class="sxs-lookup"><span data-stu-id="3497d-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3497d-130">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="3497d-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="3497d-131">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="3497d-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3497d-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="3497d-132">See Also</span></span>  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>  
 [<span data-ttu-id="3497d-133">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3497d-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="3497d-134">Vazby</span><span class="sxs-lookup"><span data-stu-id="3497d-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="3497d-135">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="3497d-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="3497d-136">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klientů</span><span class="sxs-lookup"><span data-stu-id="3497d-136">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="3497d-137">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="3497d-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
