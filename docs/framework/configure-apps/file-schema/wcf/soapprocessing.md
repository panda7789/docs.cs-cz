---
title: <soapProcessing>
ms.date: 03/30/2017
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
ms.openlocfilehash: 678b1f71ac15d3ad30df28cec5abbe403fb08c95
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937049"
---
# <a name="soapprocessing"></a><span data-ttu-id="715ae-101">\<soapProcessing ></span><span class="sxs-lookup"><span data-stu-id="715ae-101">\<soapProcessing></span></span>

<span data-ttu-id="715ae-102">Definuje chování koncového bodu klienta používaného k zařazování zpráv mezi různými typy vazeb a verzemi zpráv.</span><span class="sxs-lookup"><span data-stu-id="715ae-102">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>

<span data-ttu-id="715ae-103">**\<system.ServiceModel>**  </span><span class="sxs-lookup"><span data-stu-id="715ae-103">**\<system.ServiceModel>** </span></span>  
<span data-ttu-id="715ae-104">&nbsp;&nbsp; **\<> chování** </span><span class="sxs-lookup"><span data-stu-id="715ae-104">&nbsp;&nbsp;**\<behaviors>** </span></span>  
<span data-ttu-id="715ae-105">&nbsp;&nbsp;&nbsp;&nbsp; **\<endpointBehaviors>**  </span><span class="sxs-lookup"><span data-stu-id="715ae-105">&nbsp;&nbsp;&nbsp;&nbsp;**\<endpointBehaviors>** </span></span>  
<span data-ttu-id="715ae-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> chování** </span><span class="sxs-lookup"><span data-stu-id="715ae-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>** </span></span>  
<span data-ttu-id="715ae-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<soapProcessing >**</span><span class="sxs-lookup"><span data-stu-id="715ae-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="715ae-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="715ae-108">Syntax</span></span>  
  
```xml  
<soapProcessing processMessages="true|false" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="715ae-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="715ae-109">Attributes and elements</span></span>  
  
<span data-ttu-id="715ae-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="715ae-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="715ae-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="715ae-111">Attributes</span></span>  
  
|                   | <span data-ttu-id="715ae-112">Popis</span><span class="sxs-lookup"><span data-stu-id="715ae-112">Description</span></span> |
| ----------------- | ----------- |
| `processMessages` | <span data-ttu-id="715ae-113">Logická hodnota určující, zda mají být zprávy zařazeny mezi verze zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="715ae-113">A Boolean value that specifies whether messages should be marshaled between SOAP message versions.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="715ae-114">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="715ae-114">Child elements</span></span>

<span data-ttu-id="715ae-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="715ae-115">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="715ae-116">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="715ae-116">Parent elements</span></span>

|     | <span data-ttu-id="715ae-117">Popis</span><span class="sxs-lookup"><span data-stu-id="715ae-117">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="715ae-118"> **\<> chování**</span><span class="sxs-lookup"><span data-stu-id="715ae-118">**\<behavior>**</span></span>](behavior-of-endpointbehaviors.md) | <span data-ttu-id="715ae-119">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="715ae-119">Specifies an endpoint behavior.</span></span> |

## <a name="remarks"></a><span data-ttu-id="715ae-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="715ae-120">Remarks</span></span>

<span data-ttu-id="715ae-121">Zpracování SOAP je proces, ve kterém se zprávy převádějí mezi verze zprávy.</span><span class="sxs-lookup"><span data-stu-id="715ae-121">SOAP processing is the process where messages are converted between message versions.</span></span>

<span data-ttu-id="715ae-122">Směrovací služba Windows Communication Foundation (WCF) může převést zprávy z jednoho protokolu na jiný.</span><span class="sxs-lookup"><span data-stu-id="715ae-122">The Windows Communication Foundation (WCF) Routing Service can convert messages from one protocol to another.</span></span> <span data-ttu-id="715ae-123">Pokud se verze příchozích a odchozích zpráv liší, vytvoří se nová zpráva se správnou verzí.</span><span class="sxs-lookup"><span data-stu-id="715ae-123">If the incoming and outgoing Message Versions are different, a new message of the correct version is created.</span></span> <span data-ttu-id="715ae-124">Zpracování zpráv z jedné <xref:System.ServiceModel.Channels.MessageVersion> do druhé je provedeno vytvořením nové zprávy WCF, která obsahuje část těla a příslušné hlavičky z příchozí zprávy WCF.</span><span class="sxs-lookup"><span data-stu-id="715ae-124">Processing messages from one <xref:System.ServiceModel.Channels.MessageVersion> to another is accomplished by constructing a new WCF message that contains the body part and relevant headers from the incoming WCF message.</span></span> <span data-ttu-id="715ae-125">Hlavičky, které jsou specifické pro adresování, nebo které se rozumí na úrovni směrovače, se při konstrukci nové zprávy WCF nepoužívají, protože tato záhlaví jsou buď jiné verze (v případě hlaviček adresování), nebo se zpracovala jako součást komunikace mezi klientem a směrovačem.</span><span class="sxs-lookup"><span data-stu-id="715ae-125">Headers that are specific to addressing, or that are understood at the router level, are not used during construction of the new WCF message because these headers are either of a different version (in the case of addressing headers) or have been processed as part of the communication between the client and the router.</span></span>

<span data-ttu-id="715ae-126">Určuje, zda byla hlavička umístěna v odchozí zprávě podle toho, zda byla označena jako srozumitelná, jak byla předána prostřednictvím vrstvy příchozího kanálu.</span><span class="sxs-lookup"><span data-stu-id="715ae-126">Whether a header is placed in the outbound message is determined by whether or not it was marked as understood as it passed through the incoming channel layer.</span></span> <span data-ttu-id="715ae-127">Hlavičky, které nerozumí (například vlastní hlavičky), se neodstraňují, takže je služba Směrování po zkopírování do odchozí zprávy předána.</span><span class="sxs-lookup"><span data-stu-id="715ae-127">Headers that are not understood (such as custom headers) are not removed and so pass through the routing service by being copied to the outbound message.</span></span> <span data-ttu-id="715ae-128">Text zprávy se zkopíruje do odchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="715ae-128">The body of the message is copied to the outbound message.</span></span> <span data-ttu-id="715ae-129">Zpráva se pak pošle odchozí kanál, ve kterém se budou vytvářet a přidávat všechna záhlaví a další data obálky specifická pro daný komunikační protokol nebo přenos.</span><span class="sxs-lookup"><span data-stu-id="715ae-129">The message is then sent out the outbound channel, at which point all of the headers and other envelope data specific to that communication protocol/transport will be created and added.</span></span>

<span data-ttu-id="715ae-130">Tyto kroky zpracování se provádějí při určení chování zpracování protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="715ae-130">Such processing steps take place when the SOAP processing behavior is specified.</span></span> <span data-ttu-id="715ae-131">Toto chování soapProcessingExtension > je chování koncového bodu, které se při spuštění směrovací služby použije u všech koncových bodů klienta (odchozích). [ \<](soapprocessing.md)</span><span class="sxs-lookup"><span data-stu-id="715ae-131">This [\<soapProcessingExtension>](soapprocessing.md) behavior is an endpoint behavior that is applied to all client (outgoing) endpoints when the Routing Service starts up.</span></span> <span data-ttu-id="715ae-132">`true` ve `processMessages` [ \<](routing-of-servicebehavior.md) výchozím nastavení se chování > směrování vytváří a připojuje nové [ \<chování > soapProcessingExtension](soapprocessing.md) s nastavením na pro každý koncový bod klienta.</span><span class="sxs-lookup"><span data-stu-id="715ae-132">default, the [\<routing>](routing-of-servicebehavior.md) behavior creates and attaches a new [\<soapProcessingExtension>](soapprocessing.md) behavior with `processMessages` set to `true` for each client endpoint.</span></span> <span data-ttu-id="715ae-133">Pokud máte protokol, který směrovací služba nerozumí, nebo chcete přepsat výchozí chování zpracování, můžete zakázat zpracování protokolu SOAP buď pro celou směrovací službu, nebo jenom pro konkrétní koncové body.</span><span class="sxs-lookup"><span data-stu-id="715ae-133">If you have a protocol that the Routing Service does not understand, or wish to override the default processing behavior, you can disable SOAP processing either for the entire Routing Service or just for particular endpoints.</span></span>  <span data-ttu-id="715ae-134">Chcete-li zakázat zpracování protokolu SOAP pro celou směrovací službu u všech koncových `soapProcessing` bodů, nastavte atribut [ \<chování směrování >](routing-of-servicebehavior.md) na. `false`</span><span class="sxs-lookup"><span data-stu-id="715ae-134">To disable SOAP processing for the entire routing service on all endpoints, set the `soapProcessing` attribute of the [\<routing>](routing-of-servicebehavior.md) behavior to `false`.</span></span> <span data-ttu-id="715ae-135">Chcete-li vypnout zpracování SOAP pro konkrétní koncový bod, použijte toto chování a nastavte `processMessages` jeho atribut `false`na a pak připojte toto chování ke koncovému bodu, na kterém nechcete spustit výchozí kód pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="715ae-135">To turn off SOAP processing for a particular endpoint, use this behavior and set its `processMessages` attribute to `false`, then attach this behavior to the endpoint you do not want the default processing code to run at.</span></span>  <span data-ttu-id="715ae-136">Když chování [> Směrovánínastavísměrovacíslužbu,přeskočíopakovanéuplatněníchováníkoncovéhobodu,protožeužexistuje.\<](routing-of-servicebehavior.md)</span><span class="sxs-lookup"><span data-stu-id="715ae-136">When the [\<routing>](routing-of-servicebehavior.md) behavior sets up the Routing Service, it will skip reapplying the endpoint behavior since one already exists.</span></span>
