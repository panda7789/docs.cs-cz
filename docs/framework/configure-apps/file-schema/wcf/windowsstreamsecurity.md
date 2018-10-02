---
title: '&lt;zabezpečení windowsstreamsecurity iniciuje&gt;'
ms.date: 03/30/2017
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
author: BrucePerlerMS
ms.openlocfilehash: 6c1253e6f402da6b818a4438142e122f8b31809c
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48032449"
---
# <a name="ltwindowsstreamsecuritygt"></a><span data-ttu-id="0e211-102">&lt;zabezpečení windowsstreamsecurity iniciuje&gt;</span><span class="sxs-lookup"><span data-stu-id="0e211-102">&lt;windowsStreamSecurity&gt;</span></span>
<span data-ttu-id="0e211-103">Zadejte nastavení zabezpečení datového proudu Windows pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="0e211-103">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="0e211-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0e211-104">\<system.serviceModel></span></span>  
<span data-ttu-id="0e211-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="0e211-105">\<bindings></span></span>  
<span data-ttu-id="0e211-106">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="0e211-106">\<customBinding></span></span>  
<span data-ttu-id="0e211-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="0e211-107">\<binding></span></span>  
<span data-ttu-id="0e211-108">\<zabezpečení windowsstreamsecurity iniciuje ></span><span class="sxs-lookup"><span data-stu-id="0e211-108">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e211-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0e211-109">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e211-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0e211-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0e211-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0e211-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e211-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="0e211-112">Attributes</span></span>  
  
|<span data-ttu-id="0e211-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="0e211-113">Attribute</span></span>|<span data-ttu-id="0e211-114">Popis</span><span class="sxs-lookup"><span data-stu-id="0e211-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0e211-115">Třída protectionLevel</span><span class="sxs-lookup"><span data-stu-id="0e211-115">protectionLevel</span></span>|<span data-ttu-id="0e211-116">Definuje zabezpečení na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="0e211-116">Defines message-level security.</span></span> <span data-ttu-id="0e211-117">Podepisování zpráv snižuje riziko manipulace s zprávy při jejich přenosu od jiných dodavatelů.</span><span class="sxs-lookup"><span data-stu-id="0e211-117">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="0e211-118">Šifrování poskytuje data úrovně ochrany osobních údajů při přenosu.</span><span class="sxs-lookup"><span data-stu-id="0e211-118">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="0e211-119">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="0e211-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0e211-120">-Žádný: Žádná ochrana.</span><span class="sxs-lookup"><span data-stu-id="0e211-120">-   None: No protection.</span></span><br /><span data-ttu-id="0e211-121">-Sign: Jsou podepsané zprávy.</span><span class="sxs-lookup"><span data-stu-id="0e211-121">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="0e211-122">-EncryptAndSign: Podepsaný a zašifrovaný zpráv.</span><span class="sxs-lookup"><span data-stu-id="0e211-122">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="0e211-123">Výchozí hodnota je EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="0e211-123">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="0e211-124">Tento atribut je typu <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="0e211-124">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e211-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0e211-125">Child Elements</span></span>  
 <span data-ttu-id="0e211-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="0e211-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0e211-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0e211-127">Parent Elements</span></span>  
  
|<span data-ttu-id="0e211-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="0e211-128">Element</span></span>|<span data-ttu-id="0e211-129">Popis</span><span class="sxs-lookup"><span data-stu-id="0e211-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e211-130">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="0e211-130">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="0e211-131">Definuje všechny možnosti vázání pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="0e211-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0e211-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0e211-132">Remarks</span></span>  
 <span data-ttu-id="0e211-133">Na základě datového proudu přenosu inovace podporují přenosy, které používají protokol orientovaný na stream jako je například TCP a pojmenované kanály.</span><span class="sxs-lookup"><span data-stu-id="0e211-133">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="0e211-134">Konkrétně WCF poskytuje upgradů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0e211-134">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="0e211-135">Konfigurace tohoto zabezpečení přenosu jsou zapouzdřena objektem tento prvek konfigurace a také zobrazením [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), které se konfigurují a přidat do vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="0e211-135">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e211-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="0e211-136">See Also</span></span>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
 [<span data-ttu-id="0e211-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="0e211-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="0e211-138">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="0e211-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="0e211-139">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="0e211-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="0e211-140">\<třídě customBinding ></span><span class="sxs-lookup"><span data-stu-id="0e211-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
