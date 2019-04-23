---
title: <transport> z <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: a6d3dd2c24e90bdcdc6520e62dcc1dbe7ce797f9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59199821"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="56166-102">\<transport> of \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="56166-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="56166-103">Definuje nastavení zabezpečení přenosu pro pojmenovaný kanál.</span><span class="sxs-lookup"><span data-stu-id="56166-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="56166-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="56166-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="56166-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="56166-105">\<bindings></span></span>  
<span data-ttu-id="56166-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="56166-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="56166-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="56166-107">\<binding></span></span>  
<span data-ttu-id="56166-108">\<security></span><span class="sxs-lookup"><span data-stu-id="56166-108">\<security></span></span>  
<span data-ttu-id="56166-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="56166-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56166-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56166-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56166-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="56166-111">Attributes and Elements</span></span>  
 <span data-ttu-id="56166-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="56166-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56166-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="56166-113">Attributes</span></span>  
  
|<span data-ttu-id="56166-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="56166-114">Attribute</span></span>|<span data-ttu-id="56166-115">Popis</span><span class="sxs-lookup"><span data-stu-id="56166-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="56166-116">Třída protectionLevel</span><span class="sxs-lookup"><span data-stu-id="56166-116">protectionLevel</span></span>|<span data-ttu-id="56166-117">Definuje úroveň ochrany pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="56166-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="56166-118">Podepisování zpráv snižuje riziko manipulace s zprávy při jejich přenosu od jiných dodavatelů.</span><span class="sxs-lookup"><span data-stu-id="56166-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="56166-119">Šifrování poskytuje data úrovně ochrany osobních údajů při přenosu.</span><span class="sxs-lookup"><span data-stu-id="56166-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="56166-120">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="56166-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="56166-121">-Žádný: Žádná ochrana.</span><span class="sxs-lookup"><span data-stu-id="56166-121">-   None: No protection.</span></span><br /><span data-ttu-id="56166-122">– Přihlášení: Zprávy jsou podepsané.</span><span class="sxs-lookup"><span data-stu-id="56166-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="56166-123">-EncryptAndSign: Zprávy jsou zašifrovaná a podepsaná.</span><span class="sxs-lookup"><span data-stu-id="56166-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="56166-124">Výchozí hodnota je EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="56166-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="56166-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="56166-125">Child Elements</span></span>  
 <span data-ttu-id="56166-126">Žádný</span><span class="sxs-lookup"><span data-stu-id="56166-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="56166-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="56166-127">Parent Elements</span></span>  
  
|<span data-ttu-id="56166-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="56166-128">Element</span></span>|<span data-ttu-id="56166-129">Popis</span><span class="sxs-lookup"><span data-stu-id="56166-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="56166-130">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="56166-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="56166-131">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="56166-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56166-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56166-132">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="56166-133">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="56166-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="56166-134">Vazby</span><span class="sxs-lookup"><span data-stu-id="56166-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="56166-135">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="56166-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="56166-136">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="56166-136">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="56166-137">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="56166-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
