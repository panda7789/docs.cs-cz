---
title: "&lt;transport&gt; – &lt;netNamedPipeBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 00f4ddfd218e8797aa2089a21081ee711be316d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lttransportgt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="465dd-102">&lt;transport&gt; – &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="465dd-102">&lt;transport&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="465dd-103">Definuje nastavení zabezpečení přenosu pro pojmenovaný kanál.</span><span class="sxs-lookup"><span data-stu-id="465dd-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="465dd-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="465dd-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="465dd-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="465dd-105">\<bindings></span></span>  
<span data-ttu-id="465dd-106">\<– netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="465dd-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="465dd-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="465dd-107">\<binding></span></span>  
<span data-ttu-id="465dd-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="465dd-108">\<security></span></span>  
<span data-ttu-id="465dd-109">\<přenos ></span><span class="sxs-lookup"><span data-stu-id="465dd-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="465dd-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="465dd-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding>  
      <security mode="None/Transport">  
            <transport protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="465dd-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="465dd-111">Attributes and Elements</span></span>  
 <span data-ttu-id="465dd-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="465dd-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="465dd-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="465dd-113">Attributes</span></span>  
  
|<span data-ttu-id="465dd-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="465dd-114">Attribute</span></span>|<span data-ttu-id="465dd-115">Popis</span><span class="sxs-lookup"><span data-stu-id="465dd-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="465dd-116">ProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="465dd-116">protectionLevel</span></span>|<span data-ttu-id="465dd-117">Definuje úroveň ochrany pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="465dd-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="465dd-118">Podepisování zpráv snižuje riziko třetích stran manipulaci s zprávy při jejich přenosu.</span><span class="sxs-lookup"><span data-stu-id="465dd-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="465dd-119">Během přenosu zajišťuje šifrování dat na úrovni o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="465dd-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="465dd-120">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="465dd-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="465dd-121">-None: Žádná ochrana.</span><span class="sxs-lookup"><span data-stu-id="465dd-121">-   None: No protection.</span></span><br /><span data-ttu-id="465dd-122">-Přihlášení: Zprávy jsou podepsané.</span><span class="sxs-lookup"><span data-stu-id="465dd-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="465dd-123">-EncryptAndSign: Zprávy jsou šifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="465dd-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="465dd-124">Výchozí hodnota je EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="465dd-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="465dd-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="465dd-125">Child Elements</span></span>  
 <span data-ttu-id="465dd-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="465dd-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="465dd-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="465dd-127">Parent Elements</span></span>  
  
|<span data-ttu-id="465dd-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="465dd-128">Element</span></span>|<span data-ttu-id="465dd-129">Popis</span><span class="sxs-lookup"><span data-stu-id="465dd-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="465dd-130">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="465dd-130">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="465dd-131">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="465dd-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="465dd-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="465dd-132">See Also</span></span>  
 <xref:System.ServiceModel.NamedPipeTransportSecurity>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>  
 <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>  
 [<span data-ttu-id="465dd-133">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="465dd-133">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="465dd-134">Vazby</span><span class="sxs-lookup"><span data-stu-id="465dd-134">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="465dd-135">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="465dd-135">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="465dd-136">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="465dd-136">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="465dd-137">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="465dd-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
