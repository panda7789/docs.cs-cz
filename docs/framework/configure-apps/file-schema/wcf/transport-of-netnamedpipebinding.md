---
title: <transport> z <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: 9bcaae68051be2976b97989657efe53cf7a2718a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263447"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="efc89-102">\<transport> of \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="efc89-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="efc89-103">Definuje nastavení zabezpečení přenosu pro pojmenovaný kanál.</span><span class="sxs-lookup"><span data-stu-id="efc89-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="efc89-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="efc89-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="efc89-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="efc89-105">\<bindings></span></span>  
<span data-ttu-id="efc89-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="efc89-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="efc89-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="efc89-107">\<binding></span></span>  
<span data-ttu-id="efc89-108">\<security></span><span class="sxs-lookup"><span data-stu-id="efc89-108">\<security></span></span>  
<span data-ttu-id="efc89-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="efc89-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efc89-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="efc89-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="efc89-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="efc89-111">Attributes and Elements</span></span>  
 <span data-ttu-id="efc89-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="efc89-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="efc89-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="efc89-113">Attributes</span></span>  
  
|<span data-ttu-id="efc89-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="efc89-114">Attribute</span></span>|<span data-ttu-id="efc89-115">Popis</span><span class="sxs-lookup"><span data-stu-id="efc89-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="efc89-116">Třída protectionLevel</span><span class="sxs-lookup"><span data-stu-id="efc89-116">protectionLevel</span></span>|<span data-ttu-id="efc89-117">Definuje úroveň ochrany pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="efc89-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="efc89-118">Podepisování zpráv snižuje riziko manipulace s zprávy při jejich přenosu od jiných dodavatelů.</span><span class="sxs-lookup"><span data-stu-id="efc89-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="efc89-119">Šifrování poskytuje data úrovně ochrany osobních údajů při přenosu.</span><span class="sxs-lookup"><span data-stu-id="efc89-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="efc89-120">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="efc89-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="efc89-121">-Žádný: Žádná ochrana.</span><span class="sxs-lookup"><span data-stu-id="efc89-121">-   None: No protection.</span></span><br /><span data-ttu-id="efc89-122">– Přihlášení: Zprávy jsou podepsané.</span><span class="sxs-lookup"><span data-stu-id="efc89-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="efc89-123">-EncryptAndSign: Zprávy jsou zašifrovaná a podepsaná.</span><span class="sxs-lookup"><span data-stu-id="efc89-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="efc89-124">Výchozí hodnota je EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="efc89-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="efc89-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="efc89-125">Child Elements</span></span>  
 <span data-ttu-id="efc89-126">Žádná</span><span class="sxs-lookup"><span data-stu-id="efc89-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="efc89-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="efc89-127">Parent Elements</span></span>  
  
|<span data-ttu-id="efc89-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="efc89-128">Element</span></span>|<span data-ttu-id="efc89-129">Popis</span><span class="sxs-lookup"><span data-stu-id="efc89-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="efc89-130">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="efc89-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="efc89-131">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="efc89-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="efc89-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="efc89-132">See also</span></span>
- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="efc89-133">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="efc89-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="efc89-134">Vazby</span><span class="sxs-lookup"><span data-stu-id="efc89-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="efc89-135">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="efc89-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="efc89-136">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="efc89-136">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="efc89-137">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="efc89-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
