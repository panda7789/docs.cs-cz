---
title: <soapProcessing>
ms.date: 03/30/2017
ms.assetid: e8707027-e6b8-4539-893d-3cd7c13fbc18
ms.openlocfilehash: 0728e22205d4ac2c7674f7690e142aed51d42440
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399543"
---
# \<soapProcessing>

<span data-ttu-id="536a4-101">Definuje chování koncového bodu klienta používaného k zařazování zpráv mezi různými typy vazeb a verzemi zpráv.</span><span class="sxs-lookup"><span data-stu-id="536a4-101">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<soapProcessing>**
  
## <a name="syntax"></a><span data-ttu-id="536a4-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="536a4-102">Syntax</span></span>  
  
```xml  
<soapProcessing processMessages="true|false" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="536a4-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="536a4-103">Attributes and elements</span></span>  
  
<span data-ttu-id="536a4-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="536a4-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="536a4-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="536a4-105">Attributes</span></span>  
  
|                   | <span data-ttu-id="536a4-106">Description</span><span class="sxs-lookup"><span data-stu-id="536a4-106">Description</span></span> |
| ----------------- | ----------- |
| `processMessages` | <span data-ttu-id="536a4-107">Logická hodnota určující, zda mají být zprávy zařazeny mezi verze zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="536a4-107">A Boolean value that specifies whether messages should be marshaled between SOAP message versions.</span></span> |

### <a name="child-elements"></a><span data-ttu-id="536a4-108">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="536a4-108">Child elements</span></span>

<span data-ttu-id="536a4-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="536a4-109">None</span></span>

### <a name="parent-elements"></a><span data-ttu-id="536a4-110">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="536a4-110">Parent elements</span></span>

|     | <span data-ttu-id="536a4-111">Description</span><span class="sxs-lookup"><span data-stu-id="536a4-111">Description</span></span> |
| --- | ----------- |
| [**\<behavior>**](behavior-of-endpointbehaviors.md) | <span data-ttu-id="536a4-112">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="536a4-112">Specifies an endpoint behavior.</span></span> |

## <a name="remarks"></a><span data-ttu-id="536a4-113">Poznámky</span><span class="sxs-lookup"><span data-stu-id="536a4-113">Remarks</span></span>

<span data-ttu-id="536a4-114">Zpracování SOAP je proces, ve kterém se zprávy převádějí mezi verze zprávy.</span><span class="sxs-lookup"><span data-stu-id="536a4-114">SOAP processing is the process where messages are converted between message versions.</span></span>

<span data-ttu-id="536a4-115">Směrovací služba Windows Communication Foundation (WCF) může převést zprávy z jednoho protokolu na jiný.</span><span class="sxs-lookup"><span data-stu-id="536a4-115">The Windows Communication Foundation (WCF) Routing Service can convert messages from one protocol to another.</span></span> <span data-ttu-id="536a4-116">Pokud se verze příchozích a odchozích zpráv liší, vytvoří se nová zpráva se správnou verzí.</span><span class="sxs-lookup"><span data-stu-id="536a4-116">If the incoming and outgoing Message Versions are different, a new message of the correct version is created.</span></span> <span data-ttu-id="536a4-117">Zpracování zpráv z jedné <xref:System.ServiceModel.Channels.MessageVersion> do druhé je provedeno vytvořením nové zprávy WCF, která obsahuje část těla a příslušné hlavičky z příchozí zprávy WCF.</span><span class="sxs-lookup"><span data-stu-id="536a4-117">Processing messages from one <xref:System.ServiceModel.Channels.MessageVersion> to another is accomplished by constructing a new WCF message that contains the body part and relevant headers from the incoming WCF message.</span></span> <span data-ttu-id="536a4-118">Hlavičky, které jsou specifické pro adresování nebo které jsou srozumitelné na úrovni směrovače, se nepoužívají během vytváření nové zprávy WCF, protože tato záhlaví jsou buď jiné verze (v případě hlaviček adresování), nebo jsou zpracovaná jako součást komunikace mezi klientem a směrovačem.</span><span class="sxs-lookup"><span data-stu-id="536a4-118">Headers that are specific to addressing, or that are understood at the router level, are not used during construction of the new WCF message because these headers are either of a different version (in the case of addressing headers) or have been processed as part of the communication between the client and the router.</span></span>

<span data-ttu-id="536a4-119">Určuje, zda byla hlavička umístěna v odchozí zprávě podle toho, zda byla označena jako srozumitelná, jak byla předána prostřednictvím vrstvy příchozího kanálu.</span><span class="sxs-lookup"><span data-stu-id="536a4-119">Whether a header is placed in the outbound message is determined by whether or not it was marked as understood as it passed through the incoming channel layer.</span></span> <span data-ttu-id="536a4-120">Hlavičky, které nerozumí (například vlastní hlavičky), se neodstraňují, takže je služba Směrování po zkopírování do odchozí zprávy předána.</span><span class="sxs-lookup"><span data-stu-id="536a4-120">Headers that are not understood (such as custom headers) are not removed and so pass through the routing service by being copied to the outbound message.</span></span> <span data-ttu-id="536a4-121">Text zprávy se zkopíruje do odchozí zprávy.</span><span class="sxs-lookup"><span data-stu-id="536a4-121">The body of the message is copied to the outbound message.</span></span> <span data-ttu-id="536a4-122">Zpráva se pak pošle odchozí kanál, ve kterém se budou vytvářet a přidávat všechna záhlaví a další data obálky specifická pro daný komunikační protokol nebo přenos.</span><span class="sxs-lookup"><span data-stu-id="536a4-122">The message is then sent out the outbound channel, at which point all of the headers and other envelope data specific to that communication protocol/transport will be created and added.</span></span>

<span data-ttu-id="536a4-123">Tyto kroky zpracování se provádějí při určení chování zpracování protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="536a4-123">Such processing steps take place when the SOAP processing behavior is specified.</span></span> <span data-ttu-id="536a4-124">Toto [\<soapProcessingExtension>](soapprocessing.md) chování je chování koncového bodu, které se použije u všech koncových bodů klienta (odchozích) při spuštění směrovací služby.</span><span class="sxs-lookup"><span data-stu-id="536a4-124">This [\<soapProcessingExtension>](soapprocessing.md) behavior is an endpoint behavior that is applied to all client (outgoing) endpoints when the Routing Service starts up.</span></span> <span data-ttu-id="536a4-125">ve výchozím nastavení [\<routing>](routing-of-servicebehavior.md) chování vytvoří a připojí nové [\<soapProcessingExtension>](soapprocessing.md) chování s `processMessages` nastavením na `true` pro každý koncový bod klienta.</span><span class="sxs-lookup"><span data-stu-id="536a4-125">default, the [\<routing>](routing-of-servicebehavior.md) behavior creates and attaches a new [\<soapProcessingExtension>](soapprocessing.md) behavior with `processMessages` set to `true` for each client endpoint.</span></span> <span data-ttu-id="536a4-126">Pokud máte protokol, který směrovací služba nerozumí, nebo chcete přepsat výchozí chování zpracování, můžete zakázat zpracování protokolu SOAP buď pro celou směrovací službu, nebo jenom pro konkrétní koncové body.</span><span class="sxs-lookup"><span data-stu-id="536a4-126">If you have a protocol that the Routing Service does not understand, or wish to override the default processing behavior, you can disable SOAP processing either for the entire Routing Service or just for particular endpoints.</span></span>  <span data-ttu-id="536a4-127">Chcete-li zakázat zpracování protokolu SOAP pro celou směrovací službu ve všech koncových bodech, nastavte `soapProcessing` atribut [\<routing>](routing-of-servicebehavior.md) chování na hodnotu `false` .</span><span class="sxs-lookup"><span data-stu-id="536a4-127">To disable SOAP processing for the entire routing service on all endpoints, set the `soapProcessing` attribute of the [\<routing>](routing-of-servicebehavior.md) behavior to `false`.</span></span> <span data-ttu-id="536a4-128">Chcete-li vypnout zpracování SOAP pro konkrétní koncový bod, použijte toto chování a nastavte jeho `processMessages` atribut na `false` a pak připojte toto chování ke koncovému bodu, na kterém nechcete spustit výchozí kód pro zpracování.</span><span class="sxs-lookup"><span data-stu-id="536a4-128">To turn off SOAP processing for a particular endpoint, use this behavior and set its `processMessages` attribute to `false`, then attach this behavior to the endpoint you do not want the default processing code to run at.</span></span>  <span data-ttu-id="536a4-129">Když [\<routing>](routing-of-servicebehavior.md) chování nastaví směrovací službu, přeskočí opakované použití chování koncového bodu, protože již existuje.</span><span class="sxs-lookup"><span data-stu-id="536a4-129">When the [\<routing>](routing-of-servicebehavior.md) behavior sets up the Routing Service, it will skip reapplying the endpoint behavior since one already exists.</span></span>
