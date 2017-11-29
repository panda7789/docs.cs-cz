---
title: '&lt;windowsStreamSecurity&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 926bea29-90c7-4a26-9cf0-fb4aa44f6f70
caps.latest.revision: "10"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 5a0d3b61f473b49abdb2470a9fa5381dc9929274
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltwindowsstreamsecuritygt"></a><span data-ttu-id="fba81-102">&lt;windowsStreamSecurity&gt;</span><span class="sxs-lookup"><span data-stu-id="fba81-102">&lt;windowsStreamSecurity&gt;</span></span>
<span data-ttu-id="fba81-103">Zadejte nastavení zabezpečení systému Windows datového proudu vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="fba81-103">Specify Windows stream security settings of the custom binding.</span></span>  
  
 <span data-ttu-id="fba81-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="fba81-104">\<system.serviceModel></span></span>  
<span data-ttu-id="fba81-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="fba81-105">\<bindings></span></span>  
<span data-ttu-id="fba81-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="fba81-106">\<customBinding></span></span>  
<span data-ttu-id="fba81-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="fba81-107">\<binding></span></span>  
<span data-ttu-id="fba81-108">\<windowsStreamSecurity ></span><span class="sxs-lookup"><span data-stu-id="fba81-108">\<windowsStreamSecurity></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fba81-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fba81-109">Syntax</span></span>  
  
```xml  
<windowsStreamSecurity protectionLevel="None/Sign/EncryptAndSign"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fba81-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fba81-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fba81-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fba81-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fba81-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="fba81-112">Attributes</span></span>  
  
|<span data-ttu-id="fba81-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="fba81-113">Attribute</span></span>|<span data-ttu-id="fba81-114">Popis</span><span class="sxs-lookup"><span data-stu-id="fba81-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fba81-115">ProtectionLevel</span><span class="sxs-lookup"><span data-stu-id="fba81-115">protectionLevel</span></span>|<span data-ttu-id="fba81-116">Definuje zabezpečení na úrovni zpráv.</span><span class="sxs-lookup"><span data-stu-id="fba81-116">Defines message-level security.</span></span> <span data-ttu-id="fba81-117">Podepisování zpráv snižuje riziko třetích stran manipulaci s zprávy při jejich přenosu.</span><span class="sxs-lookup"><span data-stu-id="fba81-117">Signing messages mitigates the risk of a third party tampering with the message while it is being transferred.</span></span> <span data-ttu-id="fba81-118">Během přenosu zajišťuje šifrování dat na úrovni o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="fba81-118">Encryption provides data-level privacy during transport.</span></span> <span data-ttu-id="fba81-119">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="fba81-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fba81-120">-None: Žádná ochrana.</span><span class="sxs-lookup"><span data-stu-id="fba81-120">-   None: No protection.</span></span><br /><span data-ttu-id="fba81-121">-Přihlášení: Zprávy jsou podepsané.</span><span class="sxs-lookup"><span data-stu-id="fba81-121">-   Sign: Messages are signed.</span></span><br /><span data-ttu-id="fba81-122">-EncryptAndSign: Zprávy jsou podepsat a zašifrovat.</span><span class="sxs-lookup"><span data-stu-id="fba81-122">-   EncryptAndSign: Messages are signed and encrypted.</span></span><br /><br /> <span data-ttu-id="fba81-123">Výchozí hodnota je EncryptAndSign.</span><span class="sxs-lookup"><span data-stu-id="fba81-123">The default is EncryptAndSign.</span></span><br /><br /> <span data-ttu-id="fba81-124">Tento atribut je typu <xref:System.Net.Security.ProtectionLevel>.</span><span class="sxs-lookup"><span data-stu-id="fba81-124">This attribute is of type <xref:System.Net.Security.ProtectionLevel>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fba81-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fba81-125">Child Elements</span></span>  
 <span data-ttu-id="fba81-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="fba81-126">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fba81-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fba81-127">Parent Elements</span></span>  
  
|<span data-ttu-id="fba81-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="fba81-128">Element</span></span>|<span data-ttu-id="fba81-129">Popis</span><span class="sxs-lookup"><span data-stu-id="fba81-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fba81-130">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="fba81-130">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="fba81-131">Definuje všechny možnosti vazba vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="fba81-131">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fba81-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fba81-132">Remarks</span></span>  
 <span data-ttu-id="fba81-133">Přenosy, které používají protokol orientované na datový proud například TCP a pojmenované kanály podpory upgrady na základě datového proudu přenosu.</span><span class="sxs-lookup"><span data-stu-id="fba81-133">Transports that use a stream-oriented protocol such as TCP and named pipes support stream-based transport upgrades.</span></span> <span data-ttu-id="fba81-134">Konkrétně WCF poskytuje upgrady zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="fba81-134">Specifically, WCF provides security upgrades.</span></span> <span data-ttu-id="fba81-135">Konfigurace zabezpečení tento přenos je zapouzdřené elementem tuto konfiguraci a také zobrazením [ \<sslStreamSecurity >](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), které mohou být konfigurovány a přidat do vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="fba81-135">The configuration of this transport security is encapsulated by this configuration element  as well as by [\<sslStreamSecurity>](../../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md), which can be configured and added to a custom binding</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fba81-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="fba81-136">See Also</span></span>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 <xref:System.ServiceModel.Configuration.WindowsStreamSecurityElement>  
 <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
 [<span data-ttu-id="fba81-137">Vazby</span><span class="sxs-lookup"><span data-stu-id="fba81-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="fba81-138">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="fba81-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="fba81-139">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="fba81-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="fba81-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="fba81-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
