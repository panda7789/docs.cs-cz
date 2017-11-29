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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0a56616e97526b2d410d18d97dc1391c6fc32cc3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="channelpoolsettings"></a><span data-ttu-id="a4094-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="a4094-102">ChannelPoolSettings</span></span>
<span data-ttu-id="a4094-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="a4094-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4094-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4094-104">Syntax</span></span>  
  
```  
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a4094-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a4094-105">Methods</span></span>  
 <span data-ttu-id="a4094-106">Třída ChannelPoolSettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="a4094-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a4094-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a4094-107">Properties</span></span>  
 <span data-ttu-id="a4094-108">Třída ChannelPoolSettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="a4094-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="a4094-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="a4094-109">IdleTimeout</span></span>  
 <span data-ttu-id="a4094-110">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="a4094-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="a4094-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a4094-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4094-112">Maximální čas, kdy může být připojení nečinnosti, než dojde k odpojení.</span><span class="sxs-lookup"><span data-stu-id="a4094-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="a4094-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="a4094-113">LeaseTimeout</span></span>  
 <span data-ttu-id="a4094-114">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="a4094-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="a4094-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a4094-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4094-116">Maximální doba zapůjčení operace dokončit před vypršením časového limitu.</span><span class="sxs-lookup"><span data-stu-id="a4094-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="a4094-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="a4094-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="a4094-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="a4094-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="a4094-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a4094-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4094-120">Maximální počet odchozí kanály pro každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="a4094-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4094-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a4094-121">Requirements</span></span>  
  
|<span data-ttu-id="a4094-122">MOF</span><span class="sxs-lookup"><span data-stu-id="a4094-122">MOF</span></span>|<span data-ttu-id="a4094-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a4094-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a4094-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="a4094-124">Namespace</span></span>|<span data-ttu-id="a4094-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a4094-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a4094-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4094-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>
