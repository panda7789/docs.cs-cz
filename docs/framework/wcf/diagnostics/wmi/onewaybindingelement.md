---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 016ff823eb2c84a9f54c0763edadef1224e31517
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62040043"
---
# <a name="onewaybindingelement"></a><span data-ttu-id="dcbbc-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="dcbbc-102">OneWayBindingElement</span></span>
<span data-ttu-id="dcbbc-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="dcbbc-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcbbc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcbbc-104">Syntax</span></span>  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="dcbbc-105">Metody</span><span class="sxs-lookup"><span data-stu-id="dcbbc-105">Methods</span></span>  
 <span data-ttu-id="dcbbc-106">Třída OneWayBindingElement Třída nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="dcbbc-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="dcbbc-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="dcbbc-107">Properties</span></span>  
 <span data-ttu-id="dcbbc-108">Třída OneWayBindingElement třída má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="dcbbc-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="dcbbc-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="dcbbc-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="dcbbc-110">Datový typ: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="dcbbc-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="dcbbc-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="dcbbc-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dcbbc-112">Nastavení fondu kanálu.</span><span class="sxs-lookup"><span data-stu-id="dcbbc-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="dcbbc-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="dcbbc-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="dcbbc-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="dcbbc-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="dcbbc-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="dcbbc-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dcbbc-116">Maximální počet přijatých kanálů.</span><span class="sxs-lookup"><span data-stu-id="dcbbc-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="dcbbc-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="dcbbc-117">PacketRoutable</span></span>  
 <span data-ttu-id="dcbbc-118">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="dcbbc-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="dcbbc-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="dcbbc-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dcbbc-120">Hodnota, která určuje, zda je balíček směrovatelný.</span><span class="sxs-lookup"><span data-stu-id="dcbbc-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcbbc-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dcbbc-121">Requirements</span></span>  
  
|<span data-ttu-id="dcbbc-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="dcbbc-122">MOF</span></span>|<span data-ttu-id="dcbbc-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="dcbbc-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="dcbbc-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="dcbbc-124">Namespace</span></span>|<span data-ttu-id="dcbbc-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="dcbbc-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dcbbc-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dcbbc-126">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
