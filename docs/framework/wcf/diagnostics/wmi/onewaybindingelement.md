---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: ee7cfed20234175ba54dd25dbbbab4615c1ed7af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485739"
---
# <a name="onewaybindingelement"></a><span data-ttu-id="f3d27-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="f3d27-102">OneWayBindingElement</span></span>
<span data-ttu-id="f3d27-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="f3d27-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3d27-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3d27-104">Syntax</span></span>  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f3d27-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f3d27-105">Methods</span></span>  
 <span data-ttu-id="f3d27-106">Třída Třída OneWayBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="f3d27-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f3d27-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f3d27-107">Properties</span></span>  
 <span data-ttu-id="f3d27-108">Třída OneWayBindingElement třída má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="f3d27-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="f3d27-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="f3d27-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="f3d27-110">Datový typ: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="f3d27-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="f3d27-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f3d27-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f3d27-112">Nastavení fondu kanálu.</span><span class="sxs-lookup"><span data-stu-id="f3d27-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="f3d27-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="f3d27-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="f3d27-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="f3d27-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="f3d27-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f3d27-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f3d27-116">Maximální počet přijatých kanálů.</span><span class="sxs-lookup"><span data-stu-id="f3d27-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="f3d27-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="f3d27-117">PacketRoutable</span></span>  
 <span data-ttu-id="f3d27-118">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="f3d27-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="f3d27-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f3d27-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f3d27-120">Hodnota, která určuje, zda je směrovatelné paketu.</span><span class="sxs-lookup"><span data-stu-id="f3d27-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3d27-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f3d27-121">Requirements</span></span>  
  
|<span data-ttu-id="f3d27-122">MOF</span><span class="sxs-lookup"><span data-stu-id="f3d27-122">MOF</span></span>|<span data-ttu-id="f3d27-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f3d27-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f3d27-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="f3d27-124">Namespace</span></span>|<span data-ttu-id="f3d27-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f3d27-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3d27-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3d27-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
