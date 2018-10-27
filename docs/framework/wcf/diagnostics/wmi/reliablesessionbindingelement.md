---
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: 2e2e36486c3788cd714ffd0ed545fbb14f831476
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50038890"
---
# <a name="reliablesessionbindingelement"></a><span data-ttu-id="cce1b-102">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="cce1b-102">ReliableSessionBindingElement</span></span>
<span data-ttu-id="cce1b-103">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="cce1b-103">ReliableSessionBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cce1b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cce1b-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="cce1b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="cce1b-105">Methods</span></span>  
 <span data-ttu-id="cce1b-106">Element ReliableSessionBindingElement Třída nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="cce1b-106">The ReliableSessionBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cce1b-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="cce1b-107">Properties</span></span>  
 <span data-ttu-id="cce1b-108">Element ReliableSessionBindingElement třída má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="cce1b-108">The ReliableSessionBindingElement class has the following properties:</span></span>  
  
### <a name="acknowledgementinterval"></a><span data-ttu-id="cce1b-109">AcknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="cce1b-109">AcknowledgementInterval</span></span>  
 <span data-ttu-id="cce1b-110">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="cce1b-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="cce1b-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cce1b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cce1b-112">Časový interval, který místo určení čeká, než odešle oznámení zdroji zprávy ohledně stabilních kanálů, které jsou vytvořeny procesem.</span><span class="sxs-lookup"><span data-stu-id="cce1b-112">The interval of time that a destination waits before sending an acknowledgement to the message source on reliable channels that are created by the factory.</span></span>  
  
### <a name="flowcontrolenabled"></a><span data-ttu-id="cce1b-113">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="cce1b-113">FlowControlEnabled</span></span>  
 <span data-ttu-id="cce1b-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="cce1b-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="cce1b-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cce1b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cce1b-116">Logická hodnota určující, zda je povolena kontrola toku.</span><span class="sxs-lookup"><span data-stu-id="cce1b-116">A Boolean value that specifies whether flow control is enabled.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="cce1b-117">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="cce1b-117">InactivityTimeout</span></span>  
 <span data-ttu-id="cce1b-118">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="cce1b-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="cce1b-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cce1b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cce1b-120">Určuje maximální dobu, po kterou je kanál povolí druhé komunikující straně nechcete poslat žádnou zprávu před přerušením kanálu.</span><span class="sxs-lookup"><span data-stu-id="cce1b-120">Specifies the maximum duration the channel is going to allow the other communicating party not to send any messages before faulting the channel.</span></span>  
  
### <a name="maxpendingchannels"></a><span data-ttu-id="cce1b-121">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="cce1b-121">MaxPendingChannels</span></span>  
 <span data-ttu-id="cce1b-122">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="cce1b-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="cce1b-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cce1b-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cce1b-124">Maximální počet kanálů, které mohou čekat na přijetí na naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="cce1b-124">The maximum number of channels that can wait to be accepted on the listener.</span></span>  
  
### <a name="maxretrycount"></a><span data-ttu-id="cce1b-125">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="cce1b-125">MaxRetryCount</span></span>  
 <span data-ttu-id="cce1b-126">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="cce1b-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="cce1b-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cce1b-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cce1b-128">Maximální počet pokusů bezpečný kanál pokusí znovu poslat zprávu neobdržel potvrzení, voláním `Send` na svém základním kanálu.</span><span class="sxs-lookup"><span data-stu-id="cce1b-128">The maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgement for, by calling `Send` on its underlying channel.</span></span>  
  
### <a name="maxtransferwindowsize"></a><span data-ttu-id="cce1b-129">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="cce1b-129">MaxTransferWindowSize</span></span>  
 <span data-ttu-id="cce1b-130">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="cce1b-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="cce1b-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cce1b-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cce1b-132">Maximální velikost okna přenosu pro bezpečnou relaci.</span><span class="sxs-lookup"><span data-stu-id="cce1b-132">The maximum transfer window size for the reliable session.</span></span>  
  
### <a name="ordered"></a><span data-ttu-id="cce1b-133">Řazení</span><span class="sxs-lookup"><span data-stu-id="cce1b-133">Ordered</span></span>  
 <span data-ttu-id="cce1b-134">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="cce1b-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="cce1b-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cce1b-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cce1b-136">Logická hodnota, která určuje, zda je zaručená zprávy doručeny v pořadí, v jakém byly odeslány.</span><span class="sxs-lookup"><span data-stu-id="cce1b-136">A Boolean value that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span>  
  
### <a name="reliablemessagingversion"></a><span data-ttu-id="cce1b-137">ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="cce1b-137">ReliableMessagingVersion</span></span>  
 <span data-ttu-id="cce1b-138">Datový typ: celé číslo</span><span class="sxs-lookup"><span data-stu-id="cce1b-138">Data type: integer</span></span>  
  
 <span data-ttu-id="cce1b-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cce1b-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cce1b-140">Celé číslo, které určuje verzi protokolu WS-ReliableMessaging používá ve stabilní relaci.</span><span class="sxs-lookup"><span data-stu-id="cce1b-140">An integer that specifies the WS-ReliableMessaging protocol version used in the reliable session.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cce1b-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cce1b-141">Requirements</span></span>  
  
|<span data-ttu-id="cce1b-142">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="cce1b-142">MOF</span></span>|<span data-ttu-id="cce1b-143">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="cce1b-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cce1b-144">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="cce1b-144">Namespace</span></span>|<span data-ttu-id="cce1b-145">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cce1b-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cce1b-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="cce1b-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
