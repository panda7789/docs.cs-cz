---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: 8900af77d0d385bb68b4b85e1d15be57bb7a8d14
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59131908"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="e90b0-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="e90b0-102">ChannelPoolSettings</span></span>
<span data-ttu-id="e90b0-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="e90b0-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e90b0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e90b0-104">Syntax</span></span>  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e90b0-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e90b0-105">Methods</span></span>  
 <span data-ttu-id="e90b0-106">Třída ChannelPoolSettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="e90b0-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e90b0-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e90b0-107">Properties</span></span>  
 <span data-ttu-id="e90b0-108">Třída ChannelPoolSettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="e90b0-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="e90b0-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="e90b0-109">IdleTimeout</span></span>  
 <span data-ttu-id="e90b0-110">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="e90b0-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="e90b0-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e90b0-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e90b0-112">Maximální doba, kterou může být připojení nečinné, než je odpojeno.</span><span class="sxs-lookup"><span data-stu-id="e90b0-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="e90b0-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="e90b0-113">LeaseTimeout</span></span>  
 <span data-ttu-id="e90b0-114">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="e90b0-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="e90b0-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e90b0-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e90b0-116">Maximální doba ukončení operace zapůjčení před vypršením časového limitu.</span><span class="sxs-lookup"><span data-stu-id="e90b0-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="e90b0-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="e90b0-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="e90b0-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="e90b0-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="e90b0-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e90b0-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e90b0-120">Maximální počet odchozích kanálů pro každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="e90b0-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e90b0-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e90b0-121">Requirements</span></span>  
  
|<span data-ttu-id="e90b0-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="e90b0-122">MOF</span></span>|<span data-ttu-id="e90b0-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e90b0-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e90b0-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="e90b0-124">Namespace</span></span>|<span data-ttu-id="e90b0-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e90b0-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e90b0-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e90b0-126">See also</span></span>

- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
