---
title: <transport> z <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: d9eff52d-4bde-4586-b56a-b0ec24611f8d
ms.openlocfilehash: d40178e59b89c2912123e1927e9e960f6d880871
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735959"
---
# <a name="transport-of-netnamedpipebinding"></a><span data-ttu-id="7cb41-102">\<transport> z \<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="7cb41-102">\<transport> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="7cb41-103">Definuje nastavení zabezpečení přenosu pro pojmenovaný kanál.</span><span class="sxs-lookup"><span data-stu-id="7cb41-103">Defines the transport security settings for a named pipe.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netnamedpipebinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="7cb41-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7cb41-104">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7cb41-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7cb41-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7cb41-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7cb41-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7cb41-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="7cb41-107">Attributes</span></span>  
  
|<span data-ttu-id="7cb41-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="7cb41-108">Attribute</span></span>|<span data-ttu-id="7cb41-109">Popis</span><span class="sxs-lookup"><span data-stu-id="7cb41-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7cb41-110">Platné</span><span class="sxs-lookup"><span data-stu-id="7cb41-110">protectionLevel</span></span>|<span data-ttu-id="7cb41-111">Definuje úroveň ochrany pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="7cb41-111">Defines protection level of the named pipe.</span></span> <span data-ttu-id="7cb41-112">Podepisování zpráv snižuje riziko manipulace třetí strany při přenosu zprávy.</span><span class="sxs-lookup"><span data-stu-id="7cb41-112">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="7cb41-113">Šifrování poskytuje během přenosu soukromí na úrovni dat.</span><span class="sxs-lookup"><span data-stu-id="7cb41-113">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="7cb41-114">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="7cb41-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7cb41-115">-None: bez ochrany.</span><span class="sxs-lookup"><span data-stu-id="7cb41-115">-   None: No protection.</span></span><br /><span data-ttu-id="7cb41-116">-Sign: zprávy jsou podepsané.</span><span class="sxs-lookup"><span data-stu-id="7cb41-116">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="7cb41-117">-EncryptAndSign: zprávy jsou šifrované a podepsané.</span><span class="sxs-lookup"><span data-stu-id="7cb41-117">-   EncryptAndSign: Messages are encrypted and signed.</span></span><br /><br /> <span data-ttu-id="7cb41-118">Výchozí hodnota je EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="7cb41-118">The default value is EncryptAndSign.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7cb41-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7cb41-119">Child Elements</span></span>  
 <span data-ttu-id="7cb41-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="7cb41-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7cb41-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7cb41-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7cb41-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="7cb41-122">Element</span></span>|<span data-ttu-id="7cb41-123">Description</span><span class="sxs-lookup"><span data-stu-id="7cb41-123">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netnamedpipebinding.md)|<span data-ttu-id="7cb41-124">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="7cb41-124">Defines the security settings for a binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7cb41-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="7cb41-125">See also</span></span>

- <xref:System.ServiceModel.NamedPipeTransportSecurity>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement.Transport%2A>
- <xref:System.ServiceModel.NetNamedPipeSecurity.Transport%2A>
- <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>
- [<span data-ttu-id="7cb41-126">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="7cb41-126">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="7cb41-127">Vazby</span><span class="sxs-lookup"><span data-stu-id="7cb41-127">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7cb41-128">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="7cb41-128">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7cb41-129">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="7cb41-129">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
