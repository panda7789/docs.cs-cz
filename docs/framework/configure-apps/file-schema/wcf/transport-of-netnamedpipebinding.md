---
title: <transport> z <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: 1e76d0962ea7b4714ef6ca1f9d4c4c3e23df5b6f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934675"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="5206e-102">\<transport> of \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="5206e-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="5206e-103">Definuje nastavení zabezpečení přenosu pro pojmenovaný kanál.</span><span class="sxs-lookup"><span data-stu-id="5206e-103">Defines the transport security settings for a named pipe.</span></span>  
  
 <span data-ttu-id="5206e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5206e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5206e-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="5206e-105">\<bindings></span></span>  
<span data-ttu-id="5206e-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="5206e-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="5206e-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="5206e-107">\<binding></span></span>  
<span data-ttu-id="5206e-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="5206e-108">\<security></span></span>  
<span data-ttu-id="5206e-109">\<> přenosu</span><span class="sxs-lookup"><span data-stu-id="5206e-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5206e-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5206e-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5206e-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5206e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="5206e-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5206e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5206e-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="5206e-113">Attributes</span></span>  
  
|<span data-ttu-id="5206e-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="5206e-114">Attribute</span></span>|<span data-ttu-id="5206e-115">Popis</span><span class="sxs-lookup"><span data-stu-id="5206e-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5206e-116">Platné</span><span class="sxs-lookup"><span data-stu-id="5206e-116">protectionLevel</span></span>|<span data-ttu-id="5206e-117">Definuje úroveň ochrany pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="5206e-117">Defines protection level of the named pipe.</span></span> <span data-ttu-id="5206e-118">Podepisování zpráv snižuje riziko manipulace třetí strany při přenosu zprávy.</span><span class="sxs-lookup"><span data-stu-id="5206e-118">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="5206e-119">Šifrování poskytuje během přenosu soukromí na úrovni dat.</span><span class="sxs-lookup"><span data-stu-id="5206e-119">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="5206e-120">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="5206e-120">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="5206e-121">NTato Žádná ochrana.</span><span class="sxs-lookup"><span data-stu-id="5206e-121">-   None: No protection.</span></span><br /><span data-ttu-id="5206e-122">Osobě Zprávy jsou podepsány.</span><span class="sxs-lookup"><span data-stu-id="5206e-122">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="5206e-123">EncryptAndSign Zprávy jsou zašifrovány a podepsány.</span><span class="sxs-lookup"><span data-stu-id="5206e-123">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="5206e-124">Výchozí hodnota je EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="5206e-124">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5206e-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5206e-125">Child Elements</span></span>  
 <span data-ttu-id="5206e-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="5206e-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5206e-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5206e-127">Parent Elements</span></span>  
  
|<span data-ttu-id="5206e-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="5206e-128">Element</span></span>|<span data-ttu-id="5206e-129">Popis</span><span class="sxs-lookup"><span data-stu-id="5206e-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5206e-130">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="5206e-130">\<security></span></span>](security-of-netnamedpipebinding.md)|<span data-ttu-id="5206e-131">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="5206e-131">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5206e-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5206e-132">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="5206e-133">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5206e-133">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="5206e-134">Vazby</span><span class="sxs-lookup"><span data-stu-id="5206e-134">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5206e-135">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="5206e-135">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="5206e-136">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="5206e-136">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="5206e-137">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="5206e-137">\<binding></span></span>](../../../misc/binding.md)
