---
title: '&lt;soapProcessing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1e83bfc0f868526ad5366032f08956a6c14a1056
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltsoapprocessinggt"></a><span data-ttu-id="34355-102">&lt;soapProcessing&gt;</span><span class="sxs-lookup"><span data-stu-id="34355-102">&lt;soapProcessing&gt;</span></span>

<span data-ttu-id="34355-103">Definuje chování klienta endpoint použitý k zařazování zprávy mezi jinou vazbou typy a verze zprávy.</span><span class="sxs-lookup"><span data-stu-id="34355-103">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>

<span data-ttu-id="34355-104">**\<systém. ServiceModel >** </span><span class="sxs-lookup"><span data-stu-id="34355-104">**\<system.ServiceModel>** </span></span>  
<span data-ttu-id="34355-105">&nbsp;&nbsp;**\<chování >** </span><span class="sxs-lookup"><span data-stu-id="34355-105">&nbsp;&nbsp;**\<behaviors>** </span></span>  
<span data-ttu-id="34355-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointBehaviors >** </span><span class="sxs-lookup"><span data-stu-id="34355-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointBehaviors>** </span></span>  
<span data-ttu-id="34355-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chování >** </span><span class="sxs-lookup"><span data-stu-id="34355-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>** </span></span>  
<span data-ttu-id="34355-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing >**</span><span class="sxs-lookup"><span data-stu-id="34355-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing>**</span></span>

## <a name="syntax"></a><span data-ttu-id="34355-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="34355-109">Syntax</span></span>

```xml
<soapProcessing processMessages="true|false" />
```

## <a name="attributes-and-elements"></a><span data-ttu-id="34355-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="34355-110">Attributes and elements</span></span>

<span data-ttu-id="34355-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="34355-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="34355-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="34355-112">Attributes</span></span>

|                   | <span data-ttu-id="34355-113">Popis</span><span class="sxs-lookup"><span data-stu-id="34355-113">Description</span></span> |
| ----------------- | ----------- |
| `processMessages` | <span data-ttu-id="34355-114">Logická hodnota, která určuje, zda by měl být zařazen zpráv mezi verzemi protokolu SOAP zprávy.</span><span class="sxs-lookup"><span data-stu-id="34355-114">A Boolean value that specifies whether messages should be marshaled between SOAP message versions.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="34355-115">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="34355-115">Child elements</span></span>

<span data-ttu-id="34355-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="34355-116">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="34355-117">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="34355-117">Parent elements</span></span>

|     | <span data-ttu-id="34355-118">Popis</span><span class="sxs-lookup"><span data-stu-id="34355-118">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="34355-119">**\<chování >**</span><span class="sxs-lookup"><span data-stu-id="34355-119">**\<behavior>**</span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) | <span data-ttu-id="34355-120">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="34355-120">Specifies an endpoint behavior.</span></span> |

## <a name="remarks"></a><span data-ttu-id="34355-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="34355-121">Remarks</span></span>

<span data-ttu-id="34355-122">Zpracování protokolu SOAP je proces, kde se převedou zpráv mezi verzemi zprávy.</span><span class="sxs-lookup"><span data-stu-id="34355-122">SOAP processing is the process where messages are converted between message versions.</span></span>

<span data-ttu-id="34355-123">[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Směrovací služby můžete převést zprávy z jednoho protokolu na jiný.</span><span class="sxs-lookup"><span data-stu-id="34355-123">The [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] Routing Service can convert messages from one protocol to another.</span></span> <span data-ttu-id="34355-124">Pokud příchozí a odchozí verze zprávy liší, je vytvořit novou zprávu správnou verzi.</span><span class="sxs-lookup"><span data-stu-id="34355-124">If the incoming and outgoing Message Versions are different, a new message of the correct version is created.</span></span> <span data-ttu-id="34355-125">Zpracování zpráv z jednoho <!--zz <xref:System.ServiceModel.Channel.MessageVersion> --> `MessageVersion` do jiného provádí vytváření nové [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zprávu, která obsahuje část textu a relevantní záhlaví z příchozích [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zprávy.</span><span class="sxs-lookup"><span data-stu-id="34355-125">Processing messages from one <!--zz <xref:System.ServiceModel.Channel.MessageVersion> --> `MessageVersion`  to another is accomplished by constructing a new [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] message that contains the body part and relevant headers from the incoming [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] message.</span></span> <span data-ttu-id="34355-126">Hlavičky, které jsou specifické pro adresování nebo které jsou pochopeny na úrovni směrovače, nejsou použít během vytváření nové zprávy WCF, protože tato záhlaví, jsou jiné verzi (v případě adresování hlavičky) nebo byly zpracovány jako součást komunikace mezi klientem a směrovači.</span><span class="sxs-lookup"><span data-stu-id="34355-126">Headers that are specific to addressing, or that are understood at the router level, are not used during construction of the new WCF message because these headers are either of a different version (in the case of addressing headers) or have been processed as part of the communication between the client and the router.</span></span>

<span data-ttu-id="34355-127">Jestli je umístěn hlavičku odchozí zprávy je dáno, jestli byla označena jako porozumění, jako je předána příchozí vrstvy kanálu.</span><span class="sxs-lookup"><span data-stu-id="34355-127">Whether a header is placed in the outbound message is determined by whether or not it was marked as understood as it passed through the incoming channel layer.</span></span> <span data-ttu-id="34355-128">Hlavičky, které nejsou porozuměl (například vlastní hlavičky) nejsou odebrány a proto procházet služba Směrování podle byly zkopírovány na odchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="34355-128">Headers that are not understood (such as custom headers) are not removed and so pass through the routing service by being copied to the outbound message.</span></span> <span data-ttu-id="34355-129">Tělo zprávy se zkopíruje na odchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="34355-129">The body of the message is copied to the outbound message.</span></span> <span data-ttu-id="34355-130">Odchozí kanál potom odeslaná zpráva, na kterém všechny hlavičky a další data obálky konkrétní přejděte na tuto komunikaci protokol nebo přenos vytvořit a přidat.</span><span class="sxs-lookup"><span data-stu-id="34355-130">The message is then sent out the outbound channel, at which point all of the headers and other envelope data specific to that communication protocol/transport will be created and added.</span></span>

<span data-ttu-id="34355-131">Tyto kroky zpracování se provede při zpracování protokolu SOAP chování je zadán.</span><span class="sxs-lookup"><span data-stu-id="34355-131">Such processing steps take place when the SOAP processing behavior is specified.</span></span> <span data-ttu-id="34355-132">To [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) chování je chování koncového bodu, který se použije pro všechny koncové body klienta (odchozí) při spuštění služby směrování.</span><span class="sxs-lookup"><span data-stu-id="34355-132">This [\<soapProcessingExtension>](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) behavior is an endpoint behavior that is applied to all client (outgoing) endpoints when the Routing Service starts up.</span></span> <span data-ttu-id="34355-133">výchozí [ \<směrování >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) chování vytvoří a připojí nový [ \<soapProcessingExtension >](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) chování s `processMessages` nastavena na `true` pro každou koncový bod klienta.</span><span class="sxs-lookup"><span data-stu-id="34355-133">default, the [\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) behavior creates and attaches a new [\<soapProcessingExtension>](../../../../../docs/framework/configure-apps/file-schema/wcf/soapprocessing.md) behavior with `processMessages` set to `true` for each client endpoint.</span></span> <span data-ttu-id="34355-134">Pokud máte protokol, který směrovací služby nemá pochopit, nebo chcete přepsat výchozí chování pro zpracování, můžete zakázat zpracování pro celý směrovací služby nebo jenom pro konkrétní koncových bodů protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="34355-134">If you have a protocol that the Routing Service does not understand, or wish to override the default processing behavior, you can disable SOAP processing either for the entire Routing Service or just for particular endpoints.</span></span>  <span data-ttu-id="34355-135">Chcete-li zakázat zpracování pro službu celý směrování na všechny koncové body SOAP, nastavte `soapProcessing` atribut [ \<směrování >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) chování `false`.</span><span class="sxs-lookup"><span data-stu-id="34355-135">To disable SOAP processing for the entire routing service on all endpoints, set the `soapProcessing` attribute of the [\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) behavior to `false`.</span></span> <span data-ttu-id="34355-136">Chcete-li vypnout zpracování pro konkrétní koncový bod protokolu SOAP, použijte toto chování a nastavit jeho `processMessages` atribut `false`, toto chování přiřadit nechcete zpracování kód pro spuštění na výchozí koncový bod.</span><span class="sxs-lookup"><span data-stu-id="34355-136">To turn off SOAP processing for a particular endpoint, use this behavior and set its `processMessages` attribute to `false`, then attach this behavior to the endpoint you do not want the default processing code to run at.</span></span>  <span data-ttu-id="34355-137">Když [ \<směrování >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) chování nastaví službu směrování, přeskočí opětovné použití chování koncový bod, protože již existuje.</span><span class="sxs-lookup"><span data-stu-id="34355-137">When the [\<routing>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md) behavior sets up the Routing Service, it will skip reapplying the endpoint behavior since one already exists.</span></span>
