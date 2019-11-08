---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: dab8505a9ddb348a6f7fe16ae9acb3a0119a8b06
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735898"
---
# <a name="windowsstreamsecurity"></a><span data-ttu-id="7382d-101">\<zabezpečení windowsstreamsecurity ></span><span class="sxs-lookup"><span data-stu-id="7382d-101">\<windowsStreamSecurity></span></span>
<span data-ttu-id="7382d-102">Zadejte nastavení zabezpečení Windows Stream pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="7382d-102">Specify Windows stream security settings of the custom binding.</span></span>  
  
<span data-ttu-id="7382d-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="7382d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7382d-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="7382d-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="7382d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="7382d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="7382d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="7382d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="7382d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vazeb >** </span><span class="sxs-lookup"><span data-stu-id="7382d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="7382d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<zabezpečení windowsstreamsecurity >**</span><span class="sxs-lookup"><span data-stu-id="7382d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsStreamSecurity>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7382d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7382d-109">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7382d-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7382d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7382d-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7382d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7382d-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="7382d-112">Attributes</span></span>  
  
|<span data-ttu-id="7382d-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="7382d-113">Attribute</span></span>|<span data-ttu-id="7382d-114">Popis</span><span class="sxs-lookup"><span data-stu-id="7382d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7382d-115">Platné</span><span class="sxs-lookup"><span data-stu-id="7382d-115">protectionLevel</span></span>|<span data-ttu-id="7382d-116">Definuje zabezpečení na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="7382d-116">Defines message-level security.</span></span> <span data-ttu-id="7382d-117">Podepisování zpráv snižuje riziko manipulace třetí strany při přenosu zprávy.</span><span class="sxs-lookup"><span data-stu-id="7382d-117">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="7382d-118">Šifrování poskytuje během přenosu soukromí na úrovni dat.</span><span class="sxs-lookup"><span data-stu-id="7382d-118">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="7382d-119">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="7382d-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="7382d-120">-None: bez ochrany.</span><span class="sxs-lookup"><span data-stu-id="7382d-120">-   None: No protection.</span></span><br /><span data-ttu-id="7382d-121">-Sign: zprávy jsou podepsané.</span><span class="sxs-lookup"><span data-stu-id="7382d-121">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="7382d-122">-EncryptAndSign: zprávy jsou podepsané a šifrované.</span><span class="sxs-lookup"><span data-stu-id="7382d-122">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="7382d-123">Výchozí hodnota je EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="7382d-123">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="7382d-124">Tento atribut je typu <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="7382d-124">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7382d-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7382d-125">Child Elements</span></span>  
 <span data-ttu-id="7382d-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="7382d-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7382d-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7382d-127">Parent Elements</span></span>  
  
|<span data-ttu-id="7382d-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="7382d-128">Element</span></span>|<span data-ttu-id="7382d-129">Popis</span><span class="sxs-lookup"><span data-stu-id="7382d-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7382d-130">vazba \<</span><span class="sxs-lookup"><span data-stu-id="7382d-130">\<binding></span></span>](bindings.md)|<span data-ttu-id="7382d-131">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="7382d-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7382d-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7382d-132">Remarks</span></span>  
 <span data-ttu-id="7382d-133">Přenosy, které používají protokol orientovaný na proud, jako je TCP a pojmenované kanály, podporují upgrady přenosu na základě datového proudu.</span><span class="sxs-lookup"><span data-stu-id="7382d-133">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="7382d-134">Konkrétně WCF zajišťuje upgrady zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7382d-134">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="7382d-135">Konfigurace tohoto zabezpečení přenosu se zapouzdřuje pomocí tohoto elementu konfigurace a [\<sslStreamSecurity >](sslstreamsecurity.md), která se dá nakonfigurovat a přidat k vlastní vazbě.</span><span class="sxs-lookup"><span data-stu-id="7382d-135">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7382d-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7382d-136">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="7382d-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="7382d-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7382d-138">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="7382d-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="7382d-139">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="7382d-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="7382d-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="7382d-140">\<customBinding></span></span>](custombinding.md)
