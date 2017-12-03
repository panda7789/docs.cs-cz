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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 35a8a92ca93525c9f04ab984073ca64188f03284
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="reliablesessionbindingelement"></a><span data-ttu-id="4675a-102">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="4675a-102">ReliableSessionBindingElement</span></span>
<span data-ttu-id="4675a-103">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="4675a-103">ReliableSessionBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4675a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4675a-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="4675a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4675a-105">Methods</span></span>  
 <span data-ttu-id="4675a-106">Třída třídu ReliableSessionBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="4675a-106">The ReliableSessionBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4675a-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="4675a-107">Properties</span></span>  
 <span data-ttu-id="4675a-108">Třída třídu ReliableSessionBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="4675a-108">The ReliableSessionBindingElement class has the following properties:</span></span>  
  
### <a name="acknowledgementinterval"></a><span data-ttu-id="4675a-109">AcknowledgementInterval</span><span class="sxs-lookup"><span data-stu-id="4675a-109">AcknowledgementInterval</span></span>  
 <span data-ttu-id="4675a-110">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="4675a-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="4675a-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4675a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4675a-112">Časový interval, který cíl vyčkat před odesláním potvrzení zdroj zprávy na spolehlivé kanály, které jsou vytvořené pomocí objektu pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="4675a-112">The interval of time that a destination waits before sending an acknowledgement to the message source on reliable channels that are created by the factory.</span></span>  
  
### <a name="flowcontrolenabled"></a><span data-ttu-id="4675a-113">FlowControlEnabled</span><span class="sxs-lookup"><span data-stu-id="4675a-113">FlowControlEnabled</span></span>  
 <span data-ttu-id="4675a-114">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="4675a-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="4675a-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4675a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4675a-116">Logická hodnota, která určuje, zda je povoleno řízení toku.</span><span class="sxs-lookup"><span data-stu-id="4675a-116">A Boolean value that specifies whether flow control is enabled.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="4675a-117">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="4675a-117">InactivityTimeout</span></span>  
 <span data-ttu-id="4675a-118">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="4675a-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="4675a-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4675a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4675a-120">Určuje maximální dobu, po které bude kanál povolit druhou stranou komunikuje posílat žádné zprávy před přerušením kanálu.</span><span class="sxs-lookup"><span data-stu-id="4675a-120">Specifies the maximum duration the channel is going to allow the other communicating party not to send any messages before faulting the channel.</span></span>  
  
### <a name="maxpendingchannels"></a><span data-ttu-id="4675a-121">MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="4675a-121">MaxPendingChannels</span></span>  
 <span data-ttu-id="4675a-122">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="4675a-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="4675a-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4675a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4675a-124">Maximální počet kanálů, které může čekat třeba přijmout na naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="4675a-124">The maximum number of channels that can wait to be accepted on the listener.</span></span>  
  
### <a name="maxretrycount"></a><span data-ttu-id="4675a-125">MaxRetryCount</span><span class="sxs-lookup"><span data-stu-id="4675a-125">MaxRetryCount</span></span>  
 <span data-ttu-id="4675a-126">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="4675a-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="4675a-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4675a-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4675a-128">Maximální počet pokusů, kolikrát spolehlivé kanál pokusí znovu pošlou zprávu neobdržel potvrzení, voláním `Send` na jeho základní kanálu.</span><span class="sxs-lookup"><span data-stu-id="4675a-128">The maximum number of times a reliable channel attempts to retransmit a message it has not received an acknowledgement for, by calling `Send` on its underlying channel.</span></span>  
  
### <a name="maxtransferwindowsize"></a><span data-ttu-id="4675a-129">MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="4675a-129">MaxTransferWindowSize</span></span>  
 <span data-ttu-id="4675a-130">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="4675a-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="4675a-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4675a-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4675a-132">Maximální přenosovou velikost okna pro spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="4675a-132">The maximum transfer window size for the reliable session.</span></span>  
  
### <a name="ordered"></a><span data-ttu-id="4675a-133">řazení</span><span class="sxs-lookup"><span data-stu-id="4675a-133">Ordered</span></span>  
 <span data-ttu-id="4675a-134">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="4675a-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="4675a-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4675a-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4675a-136">Logická hodnota, která určuje, zda jsou zprávy zaručené doručení v pořadí, ve kterém byly odeslány.</span><span class="sxs-lookup"><span data-stu-id="4675a-136">A Boolean value that specifies whether messages are guaranteed to arrive in the order they were sent.</span></span>  
  
### <a name="reliablemessagingversion"></a><span data-ttu-id="4675a-137">ReliableMessagingVersion</span><span class="sxs-lookup"><span data-stu-id="4675a-137">ReliableMessagingVersion</span></span>  
 <span data-ttu-id="4675a-138">Datový typ: celé číslo</span><span class="sxs-lookup"><span data-stu-id="4675a-138">Data type: integer</span></span>  
  
 <span data-ttu-id="4675a-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4675a-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4675a-140">Celé číslo, které určuje verzi protokolu WS-ReliableMessaging použít v spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="4675a-140">An integer that specifies the WS-ReliableMessaging protocol version used in the reliable session.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4675a-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4675a-141">Requirements</span></span>  
  
|<span data-ttu-id="4675a-142">MOF</span><span class="sxs-lookup"><span data-stu-id="4675a-142">MOF</span></span>|<span data-ttu-id="4675a-143">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4675a-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4675a-144">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="4675a-144">Namespace</span></span>|<span data-ttu-id="4675a-145">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4675a-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4675a-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="4675a-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
