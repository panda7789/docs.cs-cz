---
title: ConnectionOrientedTransportBindingElement
ms.date: 03/30/2017
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
ms.openlocfilehash: 3b1055e6e2329fd213ae973ad32cdf8014d30a04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487445"
---
# <a name="connectionorientedtransportbindingelement"></a><span data-ttu-id="e5b80-102">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="e5b80-102">ConnectionOrientedTransportBindingElement</span></span>
<span data-ttu-id="e5b80-103">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="e5b80-103">ConnectionOrientedTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e5b80-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e5b80-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="e5b80-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e5b80-105">Methods</span></span>  
 <span data-ttu-id="e5b80-106">Třída ConnectionOrientedTransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="e5b80-106">The ConnectionOrientedTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e5b80-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e5b80-107">Properties</span></span>  
 <span data-ttu-id="e5b80-108">Třída ConnectionOrientedTransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="e5b80-108">The ConnectionOrientedTransportBindingElement class has the following properties:</span></span>  
  
### <a name="channelinitializationtimeout"></a><span data-ttu-id="e5b80-109">ChannelInitializationTimeout</span><span class="sxs-lookup"><span data-stu-id="e5b80-109">ChannelInitializationTimeout</span></span>  
 <span data-ttu-id="e5b80-110">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="e5b80-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="e5b80-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e5b80-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5b80-112">Časový interval, který určuje, jak dlouho inicializaci kanálu musí dokončit před vypršením časového limitu.</span><span class="sxs-lookup"><span data-stu-id="e5b80-112">The timespan that specifies how long the channel initialization has to complete before timing out.</span></span>  
  
### <a name="connectionbuffersize"></a><span data-ttu-id="e5b80-113">ConnectionBufferSize</span><span class="sxs-lookup"><span data-stu-id="e5b80-113">ConnectionBufferSize</span></span>  
 <span data-ttu-id="e5b80-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="e5b80-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="e5b80-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e5b80-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5b80-116">Velikost vyrovnávací paměti používané k přenosu bloku serializovaných zprávu od klienta nebo služby.</span><span class="sxs-lookup"><span data-stu-id="e5b80-116">The size of the buffer used to transmit a chunk of the serialized message on the wire from the client or service.</span></span>  
  
### <a name="hostnamecomparisonmode"></a><span data-ttu-id="e5b80-117">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="e5b80-117">HostNameComparisonMode</span></span>  
 <span data-ttu-id="e5b80-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="e5b80-118">Data type: string</span></span>  
  
 <span data-ttu-id="e5b80-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e5b80-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5b80-120">Hodnota, která označuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="e5b80-120">A value that indicates whether the hostname is used to reach the service when matching on the URI.</span></span>  
  
### <a name="maxbuffersize"></a><span data-ttu-id="e5b80-121">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="e5b80-121">MaxBufferSize</span></span>  
 <span data-ttu-id="e5b80-122">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="e5b80-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="e5b80-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e5b80-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5b80-124">Maximální velikost vyrovnávací paměti pro použití.</span><span class="sxs-lookup"><span data-stu-id="e5b80-124">The maximum size of the buffer to use.</span></span>  
  
### <a name="maxoutputdelay"></a><span data-ttu-id="e5b80-125">maxOutputDelay</span><span class="sxs-lookup"><span data-stu-id="e5b80-125">MaxOutputDelay</span></span>  
 <span data-ttu-id="e5b80-126">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="e5b80-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="e5b80-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e5b80-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5b80-128">Maximální interval dobu, po kterou může zůstat bloku zprávu nebo zprávu úplné do vyrovnávací paměti v paměti, teprve pak ji bude odeslána.</span><span class="sxs-lookup"><span data-stu-id="e5b80-128">The maximum interval of time that a chunk of a message or a full message can remain buffered in memory before being sent out.</span></span>  
  
### <a name="maxpendingaccepts"></a><span data-ttu-id="e5b80-129">maxPendingAccepts</span><span class="sxs-lookup"><span data-stu-id="e5b80-129">MaxPendingAccepts</span></span>  
 <span data-ttu-id="e5b80-130">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="e5b80-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="e5b80-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e5b80-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5b80-132">Maximální počet čekající asynchronní přijmout vláken, které jsou k dispozici pro zpracování příchozí připojení ve službě.</span><span class="sxs-lookup"><span data-stu-id="e5b80-132">The maximum number of pending asynchronous accept threads that are available for processing incoming connections on the service.</span></span>  
  
### <a name="maxpendingconnections"></a><span data-ttu-id="e5b80-133">maxPendingConnections</span><span class="sxs-lookup"><span data-stu-id="e5b80-133">MaxPendingConnections</span></span>  
 <span data-ttu-id="e5b80-134">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="e5b80-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="e5b80-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e5b80-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5b80-136">Maximální počet čeká na připojení.</span><span class="sxs-lookup"><span data-stu-id="e5b80-136">The maximum number of pending connections.</span></span>  
  
### <a name="transfermode"></a><span data-ttu-id="e5b80-137">transferMode</span><span class="sxs-lookup"><span data-stu-id="e5b80-137">TransferMode</span></span>  
 <span data-ttu-id="e5b80-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="e5b80-138">Data type: string</span></span>  
  
 <span data-ttu-id="e5b80-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e5b80-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e5b80-140">Hodnota, která určuje, zda jsou zprávy do vyrovnávací paměti nebo vysílání pomocí přenosu orientovaná na připojení.</span><span class="sxs-lookup"><span data-stu-id="e5b80-140">A value that specifies whether the messages are buffered or streamed with the connection-oriented transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e5b80-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e5b80-141">Requirements</span></span>  
  
|<span data-ttu-id="e5b80-142">MOF</span><span class="sxs-lookup"><span data-stu-id="e5b80-142">MOF</span></span>|<span data-ttu-id="e5b80-143">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e5b80-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e5b80-144">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="e5b80-144">Namespace</span></span>|<span data-ttu-id="e5b80-145">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e5b80-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e5b80-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5b80-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
