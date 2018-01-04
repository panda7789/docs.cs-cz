---
title: OneWayBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47de8c2449c46b12b8d10ac2a5269a18d1454f41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="onewaybindingelement"></a><span data-ttu-id="43fa3-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="43fa3-102">OneWayBindingElement</span></span>
<span data-ttu-id="43fa3-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="43fa3-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43fa3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43fa3-104">Syntax</span></span>  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="43fa3-105">Metody</span><span class="sxs-lookup"><span data-stu-id="43fa3-105">Methods</span></span>  
 <span data-ttu-id="43fa3-106">Třída Třída OneWayBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="43fa3-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="43fa3-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="43fa3-107">Properties</span></span>  
 <span data-ttu-id="43fa3-108">Třída OneWayBindingElement třída má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="43fa3-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="43fa3-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="43fa3-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="43fa3-110">Datový typ: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="43fa3-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="43fa3-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="43fa3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43fa3-112">Nastavení fondu kanálu.</span><span class="sxs-lookup"><span data-stu-id="43fa3-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="43fa3-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="43fa3-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="43fa3-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="43fa3-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="43fa3-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="43fa3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43fa3-116">Maximální počet přijatých kanálů.</span><span class="sxs-lookup"><span data-stu-id="43fa3-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="43fa3-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="43fa3-117">PacketRoutable</span></span>  
 <span data-ttu-id="43fa3-118">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="43fa3-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="43fa3-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="43fa3-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="43fa3-120">Hodnota, která určuje, zda je směrovatelné paketu.</span><span class="sxs-lookup"><span data-stu-id="43fa3-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43fa3-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="43fa3-121">Requirements</span></span>  
  
|<span data-ttu-id="43fa3-122">MOF</span><span class="sxs-lookup"><span data-stu-id="43fa3-122">MOF</span></span>|<span data-ttu-id="43fa3-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="43fa3-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="43fa3-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="43fa3-124">Namespace</span></span>|<span data-ttu-id="43fa3-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="43fa3-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="43fa3-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="43fa3-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
