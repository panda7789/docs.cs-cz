---
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: 2e2e36486c3788cd714ffd0ed545fbb14f831476
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50197038"
---
# <a name="reliablesessionbindingelement"></a><span data-ttu-id="e1e81-102">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="e1e81-102">ReliableSessionBindingElement</span></span>
<span data-ttu-id="e1e81-103">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="e1e81-103">ReliableSessionBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1e81-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1e81-104">Syntax</span></span>  
  
```csharp
class ReliableSessionBindingElement : BindingElement  
{  
  datetime AcknowledgementInterval;  
  boolean FlowControlEnabled;  
  datetime InactivityTimeout;  
  sint32 MaxPendingChannels;  
  sint32 MaxRetryCount;  
  sint32 MaxTransferWindowSize;  
  boolean Ordered;  
  integer ReliableMessagingVersion;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e1e81-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e1e81-105">Methods</span></span>  
 <span data-ttu-id="e1e81-106">Element ReliableSessionBindingElement Třída nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="e1e81-106">The ReliableSessionBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e1e81-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e1e81-107">Properties</span></span>  
 <span data-ttu-id="e1e81-108">Element ReliableSessionBindingElement třída má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="e1e81-108">The ReliableSessionBindingElement class has the following properties:</span></span>  
  
### <a name="acknowledgementinterval"></a><span data-ttu-id="e1e81-109">AcknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="e1e81-109">AcknowledgementInterval</span></span>  
 <span data-ttu-id="e1e81-110">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="e1e81-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="e1e81-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e1e81-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e1e81-112">Časový interval, který místo určení čeká, než odešle oznámení zdroji zprávy ohledně stabilních kanálů, které jsou vytvořeny procesem.</span><span class="sxs-lookup"><span data-stu-id="e1e81-112">The interval of time that a destination waits before sending an acknowledgement to the message source on reliable channels that are created by the factory.</span></span>  
  
### <a name="flowcontrolenabled"></a><span data-ttu-id="e1e81-113">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="e1e81-113">FlowControlEnabled</span></span>  
 <span data-ttu-id="e1e81-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="e1e81-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="e1e81-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e1e81-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e1e81-116">Logická hodnota určující, zda je povolena kontrola toku.</span><span class="sxs-lookup"><span data-stu-id="e1e81-116">A Boolean value that specifies whether flow control is enabled.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="e1e81-117">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="e1e81-117">InactivityTimeout</span></span>  
 <span data-ttu-id="e1e81-118">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="e1e81-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="e1e81-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e1e81-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e1e81-120">Určuje maximální dobu, po kterou je kanál povolí druhé komunikující straně nechcete poslat žádnou zprávu před přerušením kanálu.</span><span class="sxs-lookup"><span data-stu-id="e1e81-120">Specifies the maximum duration the channel is going to allow the other communicating party not to send any messages before faulting the channel.</span></span>  
  
### <a name="maxpendingchannels"></a><span data-ttu-id="e1e81-121">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="e1e81-121">MaxPendingChannels</span></span>  
 <span data-ttu-id="e1e81-122">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="e1e81-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="e1e81-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e1e81-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e1e81-124">Maximální počet kanálů, které mohou čekat na přijetí na naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="e1e81-124">The maximum number of channels that can wait to be accepted on the listener.</span></span>  
  
### <a name="maxretrycount"></a><span data-ttu-id="e1e81-125">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="e1e81-125">MaxRetryCount</span></span>  
 <span data-ttu-id="e1e81-126">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="e1e81-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="e1e81-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e1e81-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e1e81-128">Maximální počet pokusů bezpečný kanál pokusí znovu poslat zprávu neobdržel potvrzení, voláním `Send` na svém základním kanálu.</span><span class="sxs-lookup"><span data-stu-id="e1e81-128">The maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgement for, by calling `Send` on its underlying channel.</span></span>  
  
### <a name="maxtransferwindowsize"></a><span data-ttu-id="e1e81-129">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="e1e81-129">MaxTransferWindowSize</span></span>  
 <span data-ttu-id="e1e81-130">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="e1e81-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="e1e81-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e1e81-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e1e81-132">Maximální velikost okna přenosu pro bezpečnou relaci.</span><span class="sxs-lookup"><span data-stu-id="e1e81-132">The maximum transfer window size for the reliable session.</span></span>  
  
### <a name="ordered"></a><span data-ttu-id="e1e81-133">Řazení</span><span class="sxs-lookup"><span data-stu-id="e1e81-133">Ordered</span></span>  
 <span data-ttu-id="e1e81-134">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="e1e81-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="e1e81-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e1e81-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e1e81-136">Logická hodnota, která určuje, zda je zaručená zprávy doručeny v pořadí, v jakém byly odeslány.</span><span class="sxs-lookup"><span data-stu-id="e1e81-136">A Boolean value that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span>  
  
### <a name="reliablemessagingversion"></a><span data-ttu-id="e1e81-137">ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="e1e81-137">ReliableMessagingVersion</span></span>  
 <span data-ttu-id="e1e81-138">Datový typ: celé číslo</span><span class="sxs-lookup"><span data-stu-id="e1e81-138">Data type: integer</span></span>  
  
 <span data-ttu-id="e1e81-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e1e81-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e1e81-140">Celé číslo, které určuje verzi protokolu WS-ReliableMessaging používá ve stabilní relaci.</span><span class="sxs-lookup"><span data-stu-id="e1e81-140">An integer that specifies the WS-ReliableMessaging protocol version used in the reliable session.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1e81-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e1e81-141">Requirements</span></span>  
  
|<span data-ttu-id="e1e81-142">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="e1e81-142">MOF</span></span>|<span data-ttu-id="e1e81-143">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e1e81-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e1e81-144">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="e1e81-144">Namespace</span></span>|<span data-ttu-id="e1e81-145">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e1e81-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e1e81-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1e81-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
