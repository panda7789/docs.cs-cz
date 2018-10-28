---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 34220a3651819978f5f597fdc67d54630ec5e059
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195811"
---
# <a name="onewaybindingelement"></a><span data-ttu-id="81866-102">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="81866-102">OneWayBindingElement</span></span>
<span data-ttu-id="81866-103">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="81866-103">OneWayBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81866-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81866-104">Syntax</span></span>  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="81866-105">Metody</span><span class="sxs-lookup"><span data-stu-id="81866-105">Methods</span></span>  
 <span data-ttu-id="81866-106">Třída OneWayBindingElement Třída nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="81866-106">The OneWayBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="81866-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="81866-107">Properties</span></span>  
 <span data-ttu-id="81866-108">Třída OneWayBindingElement třída má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="81866-108">The OneWayBindingElement class has the following properties:</span></span>  
  
### <a name="channelpoolsettings"></a><span data-ttu-id="81866-109">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="81866-109">ChannelPoolSettings</span></span>  
 <span data-ttu-id="81866-110">Datový typ: ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="81866-110">Data type: ChannelPoolSettings</span></span>  
  
 <span data-ttu-id="81866-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="81866-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81866-112">Nastavení fondu kanálu.</span><span class="sxs-lookup"><span data-stu-id="81866-112">The channel pool settings.</span></span>  
  
### <a name="maxacceptedchannels"></a><span data-ttu-id="81866-113">MaxAcceptedChannels</span><span class="sxs-lookup"><span data-stu-id="81866-113">MaxAcceptedChannels</span></span>  
 <span data-ttu-id="81866-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="81866-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="81866-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="81866-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81866-116">Maximální počet přijatých kanálů.</span><span class="sxs-lookup"><span data-stu-id="81866-116">The maximum number of accepted channels.</span></span>  
  
### <a name="packetroutable"></a><span data-ttu-id="81866-117">PacketRoutable</span><span class="sxs-lookup"><span data-stu-id="81866-117">PacketRoutable</span></span>  
 <span data-ttu-id="81866-118">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="81866-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="81866-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="81866-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81866-120">Hodnota, která určuje, zda je balíček směrovatelný.</span><span class="sxs-lookup"><span data-stu-id="81866-120">A value that indicates whether the packet is routable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81866-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="81866-121">Requirements</span></span>  
  
|<span data-ttu-id="81866-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="81866-122">MOF</span></span>|<span data-ttu-id="81866-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="81866-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="81866-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="81866-124">Namespace</span></span>|<span data-ttu-id="81866-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="81866-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81866-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="81866-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
