---
title: ChannelPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e97e934673efbc6d0f72751c7cb1de6fba84a141
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="channelpoolsettings"></a><span data-ttu-id="a475c-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="a475c-102">ChannelPoolSettings</span></span>
<span data-ttu-id="a475c-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="a475c-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a475c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a475c-104">Syntax</span></span>  
  
```  
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a475c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a475c-105">Methods</span></span>  
 <span data-ttu-id="a475c-106">Třída ChannelPoolSettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="a475c-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a475c-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a475c-107">Properties</span></span>  
 <span data-ttu-id="a475c-108">Třída ChannelPoolSettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="a475c-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="a475c-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="a475c-109">IdleTimeout</span></span>  
 <span data-ttu-id="a475c-110">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="a475c-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="a475c-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a475c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a475c-112">Maximální čas, kdy může být připojení nečinnosti, než dojde k odpojení.</span><span class="sxs-lookup"><span data-stu-id="a475c-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="a475c-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="a475c-113">LeaseTimeout</span></span>  
 <span data-ttu-id="a475c-114">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="a475c-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="a475c-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a475c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a475c-116">Maximální doba zapůjčení operace dokončit před vypršením časového limitu.</span><span class="sxs-lookup"><span data-stu-id="a475c-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="a475c-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="a475c-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="a475c-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="a475c-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="a475c-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a475c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a475c-120">Maximální počet odchozí kanály pro každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="a475c-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a475c-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a475c-121">Requirements</span></span>  
  
|<span data-ttu-id="a475c-122">MOF</span><span class="sxs-lookup"><span data-stu-id="a475c-122">MOF</span></span>|<span data-ttu-id="a475c-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a475c-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a475c-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="a475c-124">Namespace</span></span>|<span data-ttu-id="a475c-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a475c-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a475c-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="a475c-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>
