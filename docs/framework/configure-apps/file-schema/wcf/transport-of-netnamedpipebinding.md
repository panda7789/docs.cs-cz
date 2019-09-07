---
title: <transport> z <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: 6ea0b1e374659bbbbb2f47630c009f823ccd4de9
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399330"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="86aaf-102">\<transport> of \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="86aaf-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="86aaf-103">Definuje nastavení zabezpečení přenosu pro pojmenovaný kanál.</span><span class="sxs-lookup"><span data-stu-id="86aaf-103">Defines the transport security settings for a named pipe.</span></span>  
  
<span data-ttu-id="86aaf-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="86aaf-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="86aaf-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="86aaf-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="86aaf-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="86aaf-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="86aaf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netNamedPipeBinding >** ](netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="86aaf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)</span></span>\
<span data-ttu-id="86aaf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**</span><span class="sxs-lookup"><span data-stu-id="86aaf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="86aaf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-of-netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="86aaf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netnamedpipebinding.md)</span></span>\
<span data-ttu-id="86aaf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> přenosu**</span><span class="sxs-lookup"><span data-stu-id="86aaf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86aaf-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86aaf-111">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="86aaf-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="86aaf-112">Attributes and Elements</span></span>  
 <span data-ttu-id="86aaf-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="86aaf-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="86aaf-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="86aaf-114">Attributes</span></span>  
  
|<span data-ttu-id="86aaf-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="86aaf-115">Attribute</span></span>|<span data-ttu-id="86aaf-116">Popis</span><span class="sxs-lookup"><span data-stu-id="86aaf-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="86aaf-117">Platné</span><span class="sxs-lookup"><span data-stu-id="86aaf-117">protectionLevel</span></span>|<span data-ttu-id="86aaf-118">Definuje úroveň ochrany pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="86aaf-118">Defines protection level of the named pipe.</span></span> <span data-ttu-id="86aaf-119">Podepisování zpráv snižuje riziko manipulace třetí strany při přenosu zprávy.</span><span class="sxs-lookup"><span data-stu-id="86aaf-119">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="86aaf-120">Šifrování poskytuje během přenosu soukromí na úrovni dat.</span><span class="sxs-lookup"><span data-stu-id="86aaf-120">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="86aaf-121">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="86aaf-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="86aaf-122">NTato Žádná ochrana.</span><span class="sxs-lookup"><span data-stu-id="86aaf-122">-   None: No protection.</span></span><br /><span data-ttu-id="86aaf-123">Osobě Zprávy jsou podepsány.</span><span class="sxs-lookup"><span data-stu-id="86aaf-123">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="86aaf-124">EncryptAndSign Zprávy jsou zašifrovány a podepsány.</span><span class="sxs-lookup"><span data-stu-id="86aaf-124">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="86aaf-125">Výchozí hodnota je EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="86aaf-125">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="86aaf-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="86aaf-126">Child Elements</span></span>  
 <span data-ttu-id="86aaf-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="86aaf-127">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="86aaf-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="86aaf-128">Parent Elements</span></span>  
  
|<span data-ttu-id="86aaf-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="86aaf-129">Element</span></span>|<span data-ttu-id="86aaf-130">Popis</span><span class="sxs-lookup"><span data-stu-id="86aaf-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="86aaf-131">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="86aaf-131">\<security></span></span>](security-of-netnamedpipebinding.md)|<span data-ttu-id="86aaf-132">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="86aaf-132">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86aaf-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86aaf-133">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="86aaf-134">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="86aaf-134">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="86aaf-135">Vazby</span><span class="sxs-lookup"><span data-stu-id="86aaf-135">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="86aaf-136">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="86aaf-136">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="86aaf-137">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="86aaf-137">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="86aaf-138">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="86aaf-138">\<binding></span></span>](../../../misc/binding.md)
