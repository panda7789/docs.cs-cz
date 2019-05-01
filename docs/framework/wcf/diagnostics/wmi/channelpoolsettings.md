---
title: ChannelPoolSettings
ms.date: 03/30/2017
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
ms.openlocfilehash: 8900af77d0d385bb68b4b85e1d15be57bb7a8d14
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963970"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="04e70-102">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="04e70-102">ChannelPoolSettings</span></span>
<span data-ttu-id="04e70-103">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="04e70-103">ChannelPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04e70-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04e70-104">Syntax</span></span>  
  
```csharp
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="04e70-105">Metody</span><span class="sxs-lookup"><span data-stu-id="04e70-105">Methods</span></span>  
 <span data-ttu-id="04e70-106">Třída ChannelPoolSettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="04e70-106">The ChannelPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="04e70-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="04e70-107">Properties</span></span>  
 <span data-ttu-id="04e70-108">Třída ChannelPoolSettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="04e70-108">The ChannelPoolSettings class has the following properties:</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="04e70-109">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="04e70-109">IdleTimeout</span></span>  
 <span data-ttu-id="04e70-110">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="04e70-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="04e70-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="04e70-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="04e70-112">Maximální doba, kterou může být připojení nečinné, než je odpojeno.</span><span class="sxs-lookup"><span data-stu-id="04e70-112">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="04e70-113">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="04e70-113">LeaseTimeout</span></span>  
 <span data-ttu-id="04e70-114">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="04e70-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="04e70-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="04e70-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="04e70-116">Maximální doba ukončení operace zapůjčení před vypršením časového limitu.</span><span class="sxs-lookup"><span data-stu-id="04e70-116">The maximum time for a lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundchannelsperendpoint"></a><span data-ttu-id="04e70-117">MaxOutboundChannelsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="04e70-117">MaxOutboundChannelsPerEndpoint</span></span>  
 <span data-ttu-id="04e70-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="04e70-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="04e70-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="04e70-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="04e70-120">Maximální počet odchozích kanálů pro každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="04e70-120">The maximum number of outbound channels for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04e70-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="04e70-121">Requirements</span></span>  
  
|<span data-ttu-id="04e70-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="04e70-122">MOF</span></span>|<span data-ttu-id="04e70-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="04e70-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="04e70-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="04e70-124">Namespace</span></span>|<span data-ttu-id="04e70-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="04e70-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="04e70-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="04e70-126">See also</span></span>

- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
