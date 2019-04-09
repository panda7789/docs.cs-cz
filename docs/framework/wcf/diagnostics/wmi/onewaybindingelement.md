---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 016ff823eb2c84a9f54c0763edadef1224e31517
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168737"
---
# <a name="onewaybindingelement"></a><span data-ttu-id="8807a-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="8807a-102">OneWayBindingElement</span></span>
<span data-ttu-id="8807a-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="8807a-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8807a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8807a-104">Syntax</span></span>  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8807a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="8807a-105">Methods</span></span>  
 <span data-ttu-id="8807a-106">Třída OneWayBindingElement Třída nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="8807a-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8807a-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8807a-107">Properties</span></span>  
 <span data-ttu-id="8807a-108">Třída OneWayBindingElement třída má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="8807a-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="8807a-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="8807a-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="8807a-110">Datový typ: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="8807a-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="8807a-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8807a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8807a-112">Nastavení fondu kanálu.</span><span class="sxs-lookup"><span data-stu-id="8807a-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="8807a-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="8807a-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="8807a-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="8807a-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="8807a-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8807a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8807a-116">Maximální počet přijatých kanálů.</span><span class="sxs-lookup"><span data-stu-id="8807a-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="8807a-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="8807a-117">PacketRoutable</span></span>  
 <span data-ttu-id="8807a-118">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="8807a-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="8807a-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8807a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8807a-120">Hodnota, která určuje, zda je balíček směrovatelný.</span><span class="sxs-lookup"><span data-stu-id="8807a-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8807a-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8807a-121">Requirements</span></span>  
  
|<span data-ttu-id="8807a-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="8807a-122">MOF</span></span>|<span data-ttu-id="8807a-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8807a-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8807a-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="8807a-124">Namespace</span></span>|<span data-ttu-id="8807a-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8807a-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8807a-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8807a-126">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
