---
title: <transport> z <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: d40178e59b89c2912123e1927e9e960f6d880871
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735959"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="f3e8b-102">> \<přenosů \<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="f3e8b-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="f3e8b-103">Definuje nastavení zabezpečení přenosu pro pojmenovaný kanál.</span><span class="sxs-lookup"><span data-stu-id="f3e8b-103">Defines the transport security settings for a named pipe.</span></span>  
  
<span data-ttu-id="f3e8b-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f3e8b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f3e8b-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="f3e8b-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f3e8b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="f3e8b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="f3e8b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netNamedPipeBinding >** ](netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="f3e8b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)</span></span>\
<span data-ttu-id="f3e8b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="f3e8b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="f3e8b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<zabezpečení >** ](security-of-netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="f3e8b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netnamedpipebinding.md)</span></span>\
<span data-ttu-id="f3e8b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transport >**</span><span class="sxs-lookup"><span data-stu-id="f3e8b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3e8b-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3e8b-111">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3e8b-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f3e8b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f3e8b-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f3e8b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3e8b-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="f3e8b-114">Attributes</span></span>  
  
|<span data-ttu-id="f3e8b-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="f3e8b-115">Attribute</span></span>|<span data-ttu-id="f3e8b-116">Popis</span><span class="sxs-lookup"><span data-stu-id="f3e8b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3e8b-117">Platné</span><span class="sxs-lookup"><span data-stu-id="f3e8b-117">protectionLevel</span></span>|<span data-ttu-id="f3e8b-118">Definuje úroveň ochrany pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="f3e8b-118">Defines protection level of the named pipe.</span></span> <span data-ttu-id="f3e8b-119">Podepisování zpráv snižuje riziko manipulace třetí strany při přenosu zprávy.</span><span class="sxs-lookup"><span data-stu-id="f3e8b-119">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="f3e8b-120">Šifrování poskytuje během přenosu soukromí na úrovni dat.</span><span class="sxs-lookup"><span data-stu-id="f3e8b-120">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="f3e8b-121">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="f3e8b-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f3e8b-122">-None: bez ochrany.</span><span class="sxs-lookup"><span data-stu-id="f3e8b-122">-   None: No protection.</span></span><br /><span data-ttu-id="f3e8b-123">-Sign: zprávy jsou podepsané.</span><span class="sxs-lookup"><span data-stu-id="f3e8b-123">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="f3e8b-124">-EncryptAndSign: zprávy jsou šifrované a podepsané.</span><span class="sxs-lookup"><span data-stu-id="f3e8b-124">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="f3e8b-125">Výchozí hodnota je EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="f3e8b-125">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3e8b-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f3e8b-126">Child Elements</span></span>  
 <span data-ttu-id="f3e8b-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="f3e8b-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3e8b-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f3e8b-128">Parent Elements</span></span>  
  
|<span data-ttu-id="f3e8b-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="f3e8b-129">Element</span></span>|<span data-ttu-id="f3e8b-130">Popis</span><span class="sxs-lookup"><span data-stu-id="f3e8b-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3e8b-131">> zabezpečení \<</span><span class="sxs-lookup"><span data-stu-id="f3e8b-131">\<security></span></span>](security-of-netnamedpipebinding.md)|<span data-ttu-id="f3e8b-132">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="f3e8b-132">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3e8b-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3e8b-133">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="f3e8b-134">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="f3e8b-134">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f3e8b-135">Vazby</span><span class="sxs-lookup"><span data-stu-id="f3e8b-135">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f3e8b-136">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="f3e8b-136">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f3e8b-137">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="f3e8b-137">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f3e8b-138">vazba \<</span><span class="sxs-lookup"><span data-stu-id="f3e8b-138">\<binding></span></span>](bindings.md)
