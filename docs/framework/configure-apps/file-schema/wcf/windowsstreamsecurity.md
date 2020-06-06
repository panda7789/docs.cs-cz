---
title: <windowsStreamSecurity>
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
ms.openlocfilehash: dab8505a9ddb348a6f7fe16ae9acb3a0119a8b06
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735898"
---
# \<windowsStreamSecurity>
<span data-ttu-id="c9d17-101">Zadejte nastavení zabezpečení Windows Stream pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="c9d17-101">Specify Windows stream security settings of the custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<windowsStreamSecurity>**  
  
## <a name="syntax"></a><span data-ttu-id="c9d17-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9d17-102">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9d17-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c9d17-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c9d17-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c9d17-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9d17-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="c9d17-105">Attributes</span></span>  
  
|<span data-ttu-id="c9d17-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="c9d17-106">Attribute</span></span>|<span data-ttu-id="c9d17-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c9d17-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c9d17-108">Platné</span><span class="sxs-lookup"><span data-stu-id="c9d17-108">protectionLevel</span></span>|<span data-ttu-id="c9d17-109">Definuje zabezpečení na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="c9d17-109">Defines message-level security.</span></span> <span data-ttu-id="c9d17-110">Podepisování zpráv snižuje riziko manipulace třetí strany při přenosu zprávy.</span><span class="sxs-lookup"><span data-stu-id="c9d17-110">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="c9d17-111">Šifrování poskytuje během přenosu soukromí na úrovni dat.</span><span class="sxs-lookup"><span data-stu-id="c9d17-111">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="c9d17-112">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="c9d17-112">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c9d17-113">-None: bez ochrany.</span><span class="sxs-lookup"><span data-stu-id="c9d17-113">-   None: No protection.</span></span><br /><span data-ttu-id="c9d17-114">-Sign: zprávy jsou podepsané.</span><span class="sxs-lookup"><span data-stu-id="c9d17-114">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="c9d17-115">-EncryptAndSign: zprávy jsou podepsané a šifrované.</span><span class="sxs-lookup"><span data-stu-id="c9d17-115">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="c9d17-116">Výchozí hodnota je EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="c9d17-116">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="c9d17-117">Tento atribut je typu <xref:System.Net.Security.ProtectionLevel> .</span><span class="sxs-lookup"><span data-stu-id="c9d17-117">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9d17-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c9d17-118">Child Elements</span></span>  
 <span data-ttu-id="c9d17-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="c9d17-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9d17-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c9d17-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c9d17-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="c9d17-121">Element</span></span>|<span data-ttu-id="c9d17-122">Description</span><span class="sxs-lookup"><span data-stu-id="c9d17-122">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="c9d17-123">Definuje všechny schopnosti vazby vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="c9d17-123">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9d17-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c9d17-124">Remarks</span></span>  
 <span data-ttu-id="c9d17-125">Přenosy, které používají protokol orientovaný na proud, jako je TCP a pojmenované kanály, podporují upgrady přenosu na základě datového proudu.</span><span class="sxs-lookup"><span data-stu-id="c9d17-125">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="c9d17-126">Konkrétně WCF zajišťuje upgrady zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c9d17-126">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="c9d17-127">Konfigurace tohoto transportního zabezpečení je zapouzdřena tímto elementem konfigurace a také nástrojem [\<sslStreamSecurity>](sslstreamsecurity.md) , který lze konfigurovat a přidat do vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="c9d17-127">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9d17-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9d17-128">See also</span></span>

- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
- [<span data-ttu-id="c9d17-129">Vazby</span><span class="sxs-lookup"><span data-stu-id="c9d17-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="c9d17-130">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="c9d17-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="c9d17-131">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="c9d17-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
