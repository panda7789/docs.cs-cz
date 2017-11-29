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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a43707f25a9ee1beb1ce7adac36a2c4a55cab6d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="onewaybindingelement"></a><span data-ttu-id="2bd41-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="2bd41-102">OneWayBindingElement</span></span>
<span data-ttu-id="2bd41-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="2bd41-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bd41-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bd41-104">Syntax</span></span>  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2bd41-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2bd41-105">Methods</span></span>  
 <span data-ttu-id="2bd41-106">Třída Třída OneWayBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="2bd41-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2bd41-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2bd41-107">Properties</span></span>  
 <span data-ttu-id="2bd41-108">Třída OneWayBindingElement třída má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="2bd41-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="2bd41-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="2bd41-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="2bd41-110">Datový typ: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="2bd41-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="2bd41-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2bd41-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2bd41-112">Nastavení fondu kanálu.</span><span class="sxs-lookup"><span data-stu-id="2bd41-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="2bd41-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="2bd41-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="2bd41-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="2bd41-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="2bd41-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2bd41-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2bd41-116">Maximální počet přijatých kanálů.</span><span class="sxs-lookup"><span data-stu-id="2bd41-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="2bd41-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="2bd41-117">PacketRoutable</span></span>  
 <span data-ttu-id="2bd41-118">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="2bd41-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="2bd41-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2bd41-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2bd41-120">Hodnota, která určuje, zda je směrovatelné paketu.</span><span class="sxs-lookup"><span data-stu-id="2bd41-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bd41-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2bd41-121">Requirements</span></span>  
  
|<span data-ttu-id="2bd41-122">MOF</span><span class="sxs-lookup"><span data-stu-id="2bd41-122">MOF</span></span>|<span data-ttu-id="2bd41-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2bd41-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2bd41-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="2bd41-124">Namespace</span></span>|<span data-ttu-id="2bd41-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2bd41-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2bd41-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="2bd41-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
