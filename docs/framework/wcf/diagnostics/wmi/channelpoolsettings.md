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
ms.workload: dotnet
ms.openlocfilehash: 3995b517b27a5565f7fcb9c11da27c9e1bb40887
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="channelpoolsettings"></a><span data-ttu-id="7378e-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="7378e-102">ChannelPoolSettings</span></span>
<span data-ttu-id="7378e-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="7378e-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7378e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7378e-104">Syntax</span></span>  
  
```  
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7378e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7378e-105">Methods</span></span>  
 <span data-ttu-id="7378e-106">Třída ChannelPoolSettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="7378e-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7378e-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="7378e-107">Properties</span></span>  
 <span data-ttu-id="7378e-108">Třída ChannelPoolSettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="7378e-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="7378e-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="7378e-109">IdleTimeout</span></span>  
 <span data-ttu-id="7378e-110">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="7378e-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="7378e-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7378e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7378e-112">Maximální čas, kdy může být připojení nečinnosti, než dojde k odpojení.</span><span class="sxs-lookup"><span data-stu-id="7378e-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="7378e-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="7378e-113">LeaseTimeout</span></span>  
 <span data-ttu-id="7378e-114">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="7378e-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="7378e-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7378e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7378e-116">Maximální doba zapůjčení operace dokončit před vypršením časového limitu.</span><span class="sxs-lookup"><span data-stu-id="7378e-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="7378e-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="7378e-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="7378e-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="7378e-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="7378e-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7378e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7378e-120">Maximální počet odchozí kanály pro každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="7378e-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7378e-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7378e-121">Requirements</span></span>  
  
|<span data-ttu-id="7378e-122">MOF</span><span class="sxs-lookup"><span data-stu-id="7378e-122">MOF</span></span>|<span data-ttu-id="7378e-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7378e-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7378e-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="7378e-124">Namespace</span></span>|<span data-ttu-id="7378e-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7378e-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7378e-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="7378e-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>
