---
title: ConnectionOrientedTransportBindingElement
ms.date: 03/30/2017
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
ms.openlocfilehash: 5ec2ae0db7239ff0c376ab4a8f050cc4f1df4f71
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683965"
---
# <a name="connectionorientedtransportbindingelement"></a><span data-ttu-id="be0a0-102">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="be0a0-102">ConnectionOrientedTransportBindingElement</span></span>
<span data-ttu-id="be0a0-103">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="be0a0-103">ConnectionOrientedTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be0a0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be0a0-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="be0a0-105">Metody</span><span class="sxs-lookup"><span data-stu-id="be0a0-105">Methods</span></span>  
 <span data-ttu-id="be0a0-106">Třída ConnectionOrientedTransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="be0a0-106">The ConnectionOrientedTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="be0a0-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="be0a0-107">Properties</span></span>  
 <span data-ttu-id="be0a0-108">Třída ConnectionOrientedTransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="be0a0-108">The ConnectionOrientedTransportBindingElement class has the following properties:</span></span>  
  
### <a name="channelinitializationtimeout"></a><span data-ttu-id="be0a0-109">třídě channelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="be0a0-109">ChannelInitializationTimeout</span></span>  
 <span data-ttu-id="be0a0-110">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="be0a0-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="be0a0-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="be0a0-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be0a0-112">Časový interval, který určuje, jak dlouho inicializace kanálu má ještě před vypršením časového limitu.</span><span class="sxs-lookup"><span data-stu-id="be0a0-112">The timespan that specifies how long the channel initialization has to complete before timing out.</span></span>  
  
### <a name="connectionbuffersize"></a><span data-ttu-id="be0a0-113">connectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="be0a0-113">ConnectionBufferSize</span></span>  
 <span data-ttu-id="be0a0-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="be0a0-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="be0a0-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="be0a0-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be0a0-116">Velikost vyrovnávací paměti použité k přenosu bloku serializovaných zpráv od klienta nebo služby.</span><span class="sxs-lookup"><span data-stu-id="be0a0-116">The size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="be0a0-117">HostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="be0a0-117">HostNameComparisonMode</span></span>  
 <span data-ttu-id="be0a0-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="be0a0-118">Data type: string</span></span>  
  
 <span data-ttu-id="be0a0-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="be0a0-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be0a0-120">Hodnota, která určuje, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="be0a0-120">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="be0a0-121">MaxBufferSize</span><span class="sxs-lookup"><span data-stu-id="be0a0-121">MaxBufferSize</span></span>  
 <span data-ttu-id="be0a0-122">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="be0a0-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="be0a0-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="be0a0-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be0a0-124">Maximální velikost vyrovnávací paměti pro použití.</span><span class="sxs-lookup"><span data-stu-id="be0a0-124">The maximum size of the buffer to use.</span></span>  
  
### <a name="maxoutputdelay"></a><span data-ttu-id="be0a0-125">MaxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="be0a0-125">MaxOutputDelay</span></span>  
 <span data-ttu-id="be0a0-126">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="be0a0-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="be0a0-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="be0a0-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be0a0-128">Maximální interval času, který blok zprávy, nebo celá zpráva může zůstat posláním ve vyrovnávací paměti teprve pak ji bude odeslána.</span><span class="sxs-lookup"><span data-stu-id="be0a0-128">The maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>  
  
### <a name="maxpendingaccepts"></a><span data-ttu-id="be0a0-129">MaxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="be0a0-129">MaxPendingAccepts</span></span>  
 <span data-ttu-id="be0a0-130">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="be0a0-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="be0a0-131">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="be0a0-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be0a0-132">Maximální počet nevyřízených asynchronních akceptovaných vláken, které jsou k dispozici pro zpracování příchozích připojení ve službě.</span><span class="sxs-lookup"><span data-stu-id="be0a0-132">The maximum number of pending asynchronous accept threads that are available for processing incoming connections on the service.</span></span>  
  
### <a name="maxpendingconnections"></a><span data-ttu-id="be0a0-133">MaxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="be0a0-133">MaxPendingConnections</span></span>  
 <span data-ttu-id="be0a0-134">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="be0a0-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="be0a0-135">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="be0a0-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be0a0-136">Maximální počet nevyřízených připojení.</span><span class="sxs-lookup"><span data-stu-id="be0a0-136">The maximum number of pending connections.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="be0a0-137">TransferMode</span><span class="sxs-lookup"><span data-stu-id="be0a0-137">TransferMode</span></span>  
 <span data-ttu-id="be0a0-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="be0a0-138">Data type: string</span></span>  
  
 <span data-ttu-id="be0a0-139">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="be0a0-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="be0a0-140">Hodnota, která určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo zpracovány připojením řízenou přepravou.</span><span class="sxs-lookup"><span data-stu-id="be0a0-140">A value that specifies whether the messages are buffered or streamed with the connection-oriented transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be0a0-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="be0a0-141">Requirements</span></span>  
  
|<span data-ttu-id="be0a0-142">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="be0a0-142">MOF</span></span>|<span data-ttu-id="be0a0-143">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="be0a0-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="be0a0-144">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="be0a0-144">Namespace</span></span>|<span data-ttu-id="be0a0-145">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="be0a0-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="be0a0-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be0a0-146">See also</span></span>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
