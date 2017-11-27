---
title: ReliableSessionBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3f4aff60c96db5071d41a3f011019b05746f0c96
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="reliablesessionbindingelement"></a><span data-ttu-id="cd402-102">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="cd402-102">ReliableSessionBindingElement</span></span>
<span data-ttu-id="cd402-103">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="cd402-103">ReliableSessionBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd402-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd402-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="cd402-105">Metody</span><span class="sxs-lookup"><span data-stu-id="cd402-105">Methods</span></span>  
 <span data-ttu-id="cd402-106">Třída třídu ReliableSessionBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="cd402-106">The ReliableSessionBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cd402-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="cd402-107">Properties</span></span>  
 <span data-ttu-id="cd402-108">Třída třídu ReliableSessionBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="cd402-108">The ReliableSessionBindingElement class has the following properties:</span></span>  
  
### <a name="acknowledgementinterval"></a><span data-ttu-id="cd402-109">AcknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="cd402-109">AcknowledgementInterval</span></span>  
 <span data-ttu-id="cd402-110">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="cd402-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="cd402-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cd402-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd402-112">Časový interval, který cíl vyčkat před odesláním potvrzení zdroj zprávy na spolehlivé kanály, které jsou vytvořené pomocí objektu pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="cd402-112">The interval of time that a destination waits before sending an acknowledgement to the message source on reliable channels that are created by the factory.</span></span>  
  
### <a name="flowcontrolenabled"></a><span data-ttu-id="cd402-113">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="cd402-113">FlowControlEnabled</span></span>  
 <span data-ttu-id="cd402-114">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="cd402-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="cd402-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cd402-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd402-116">Logická hodnota, která určuje, zda je povoleno řízení toku.</span><span class="sxs-lookup"><span data-stu-id="cd402-116">A Boolean value that specifies whether flow control is enabled.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="cd402-117">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="cd402-117">InactivityTimeout</span></span>  
 <span data-ttu-id="cd402-118">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="cd402-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="cd402-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cd402-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd402-120">Určuje maximální dobu, po které bude kanál povolit druhou stranou komunikuje posílat žádné zprávy před přerušením kanálu.</span><span class="sxs-lookup"><span data-stu-id="cd402-120">Specifies the maximum duration the channel is going to allow the other communicating party not to send any messages before faulting the channel.</span></span>  
  
### <a name="maxpendingchannels"></a><span data-ttu-id="cd402-121">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="cd402-121">MaxPendingChannels</span></span>  
 <span data-ttu-id="cd402-122">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="cd402-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="cd402-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cd402-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd402-124">Maximální počet kanálů, které může čekat třeba přijmout na naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="cd402-124">The maximum number of channels that can wait to be accepted on the listener.</span></span>  
  
### <a name="maxretrycount"></a><span data-ttu-id="cd402-125">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="cd402-125">MaxRetryCount</span></span>  
 <span data-ttu-id="cd402-126">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="cd402-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="cd402-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cd402-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd402-128">Maximální počet pokusů, kolikrát spolehlivé kanál pokusí znovu pošlou zprávu neobdržel potvrzení, voláním `Send` na jeho základní kanálu.</span><span class="sxs-lookup"><span data-stu-id="cd402-128">The maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgement for, by calling `Send` on its underlying channel.</span></span>  
  
### <a name="maxtransferwindowsize"></a><span data-ttu-id="cd402-129">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="cd402-129">MaxTransferWindowSize</span></span>  
 <span data-ttu-id="cd402-130">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="cd402-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="cd402-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cd402-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd402-132">Maximální přenosovou velikost okna pro spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="cd402-132">The maximum transfer window size for the reliable session.</span></span>  
  
### <a name="ordered"></a><span data-ttu-id="cd402-133">řazení</span><span class="sxs-lookup"><span data-stu-id="cd402-133">Ordered</span></span>  
 <span data-ttu-id="cd402-134">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="cd402-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="cd402-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cd402-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd402-136">Logická hodnota, která určuje, zda jsou zprávy zaručené doručení v pořadí, ve kterém byly odeslány.</span><span class="sxs-lookup"><span data-stu-id="cd402-136">A Boolean value that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span>  
  
### <a name="reliablemessagingversion"></a><span data-ttu-id="cd402-137">ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="cd402-137">ReliableMessagingVersion</span></span>  
 <span data-ttu-id="cd402-138">Datový typ: celé číslo</span><span class="sxs-lookup"><span data-stu-id="cd402-138">Data type: integer</span></span>  
  
 <span data-ttu-id="cd402-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cd402-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd402-140">Celé číslo, které určuje verzi protokolu WS-ReliableMessaging použít v spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="cd402-140">An integer that specifies the WS-ReliableMessaging protocol version used in the reliable session.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd402-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cd402-141">Requirements</span></span>  
  
|<span data-ttu-id="cd402-142">MOF</span><span class="sxs-lookup"><span data-stu-id="cd402-142">MOF</span></span>|<span data-ttu-id="cd402-143">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="cd402-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cd402-144">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="cd402-144">Namespace</span></span>|<span data-ttu-id="cd402-145">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cd402-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd402-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd402-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
