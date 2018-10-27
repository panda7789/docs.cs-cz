---
title: ConnectionOrientedTransportBindingElement
ms.date: 03/30/2017
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
ms.openlocfilehash: 49f030c05f02280d483ac2a836cbe75716b7b5cc
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185051"
---
# <a name="connectionorientedtransportbindingelement"></a><span data-ttu-id="17afb-102">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="17afb-102">ConnectionOrientedTransportBindingElement</span></span>
<span data-ttu-id="17afb-103">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="17afb-103">ConnectionOrientedTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17afb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="17afb-104">Syntax</span></span>  
  
```csharp
class ConnectionOrientedTransportBindingElement : TransportBindingElement  
{  
  datetime ChannelInitializationTimeout;  
  sint32 ConnectionBufferSize;  
  string HostNameComparisonMode;  
  sint32 MaxBufferSize;  
  datetime MaxOutputDelay;  
  sint32 MaxPendingAccepts;  
  sint32 MaxPendingConnections;  
  string TransferMode;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="17afb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="17afb-105">Methods</span></span>  
 <span data-ttu-id="17afb-106">Třída ConnectionOrientedTransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="17afb-106">The ConnectionOrientedTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="17afb-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="17afb-107">Properties</span></span>  
 <span data-ttu-id="17afb-108">Třída ConnectionOrientedTransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="17afb-108">The ConnectionOrientedTransportBindingElement class has the following properties:</span></span>  
  
### <a name="channelinitializationtimeout"></a><span data-ttu-id="17afb-109">třídě channelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="17afb-109">ChannelInitializationTimeout</span></span>  
 <span data-ttu-id="17afb-110">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="17afb-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="17afb-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="17afb-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="17afb-112">Časový interval, který určuje, jak dlouho inicializace kanálu má ještě před vypršením časového limitu.</span><span class="sxs-lookup"><span data-stu-id="17afb-112">The timespan that specifies how long the channel initialization has to complete before timing out.</span></span>  
  
### <a name="connectionbuffersize"></a><span data-ttu-id="17afb-113">connectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="17afb-113">ConnectionBufferSize</span></span>  
 <span data-ttu-id="17afb-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="17afb-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="17afb-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="17afb-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="17afb-116">Velikost vyrovnávací paměti použité k přenosu bloku serializovaných zpráv od klienta nebo služby.</span><span class="sxs-lookup"><span data-stu-id="17afb-116">The size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="17afb-117">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="17afb-117">HostNameComparisonMode</span></span>  
 <span data-ttu-id="17afb-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="17afb-118">Data type: string</span></span>  
  
 <span data-ttu-id="17afb-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="17afb-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="17afb-120">Hodnota, která určuje, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="17afb-120">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="17afb-121">Třída maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="17afb-121">MaxBufferSize</span></span>  
 <span data-ttu-id="17afb-122">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="17afb-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="17afb-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="17afb-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="17afb-124">Maximální velikost vyrovnávací paměti pro použití.</span><span class="sxs-lookup"><span data-stu-id="17afb-124">The maximum size of the buffer to use.</span></span>  
  
### <a name="maxoutputdelay"></a><span data-ttu-id="17afb-125">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="17afb-125">MaxOutputDelay</span></span>  
 <span data-ttu-id="17afb-126">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="17afb-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="17afb-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="17afb-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="17afb-128">Maximální interval času, který blok zprávy, nebo celá zpráva může zůstat posláním ve vyrovnávací paměti teprve pak ji bude odeslána.</span><span class="sxs-lookup"><span data-stu-id="17afb-128">The maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>  
  
### <a name="maxpendingaccepts"></a><span data-ttu-id="17afb-129">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="17afb-129">MaxPendingAccepts</span></span>  
 <span data-ttu-id="17afb-130">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="17afb-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="17afb-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="17afb-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="17afb-132">Maximální počet nevyřízených asynchronních akceptovaných vláken, které jsou k dispozici pro zpracování příchozích připojení ve službě.</span><span class="sxs-lookup"><span data-stu-id="17afb-132">The maximum number of pending asynchronous accept threads that are available for processing incoming connections on the service.</span></span>  
  
### <a name="maxpendingconnections"></a><span data-ttu-id="17afb-133">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="17afb-133">MaxPendingConnections</span></span>  
 <span data-ttu-id="17afb-134">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="17afb-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="17afb-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="17afb-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="17afb-136">Maximální počet nevyřízených připojení.</span><span class="sxs-lookup"><span data-stu-id="17afb-136">The maximum number of pending connections.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="17afb-137">režim přenosu</span><span class="sxs-lookup"><span data-stu-id="17afb-137">TransferMode</span></span>  
 <span data-ttu-id="17afb-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="17afb-138">Data type: string</span></span>  
  
 <span data-ttu-id="17afb-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="17afb-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="17afb-140">Hodnota, která určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo zpracovány připojením řízenou přepravou.</span><span class="sxs-lookup"><span data-stu-id="17afb-140">A value that specifies whether the messages are buffered or streamed with the connection-oriented transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17afb-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="17afb-141">Requirements</span></span>  
  
|<span data-ttu-id="17afb-142">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="17afb-142">MOF</span></span>|<span data-ttu-id="17afb-143">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="17afb-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="17afb-144">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="17afb-144">Namespace</span></span>|<span data-ttu-id="17afb-145">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="17afb-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="17afb-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="17afb-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
