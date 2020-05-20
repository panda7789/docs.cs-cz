---
title: NOTIFY_FILTER – výčet
ms.date: 03/30/2017
api_name:
- NOTIFY_FILTER
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- NOTIFY_FILTER
helpviewer_keywords:
- NOTIFY_FILTER enumeration [.NET Framework debugging]
ms.assetid: 4789d08f-8683-45d3-ac30-73d48c61e470
topic_type:
- apiref
ms.openlocfilehash: b20e18d5f4314a0ab1442ac7bd5c6514e4db85d5
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83609479"
---
# <a name="notify_filter-enumeration"></a><span data-ttu-id="91ead-102">NOTIFY_FILTER – výčet</span><span class="sxs-lookup"><span data-stu-id="91ead-102">NOTIFY_FILTER Enumeration</span></span>
<span data-ttu-id="91ead-103">Označuje zpětná volání pro funkce ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="91ead-103">Identifies callbacks for debugger functions.</span></span> <span data-ttu-id="91ead-104">Další informace naleznete v tématu metoda [INotifySource2 –:: setnotifyfilter –](inotifysource2-setnotifyfilter-method.md) .</span><span class="sxs-lookup"><span data-stu-id="91ead-104">For more information, see the [INotifySource2::SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91ead-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="91ead-105">Syntax</span></span>  
  
```cpp  
enum tagNOTIFY_FILTER  
{  
    NOTIFY_FILTER_ONSYNCCALLOUT    = 0x1,  
    NOTIFY_FILTER_ONSYNCCALLENTER  = 0x2,  
    NOTIFY_FILTER_ONSYNCCALLEXIT   = 0x4,  
    NOTIFY_FILTER_ONSYNCCALLRETURN = 0x8,  
    NOTIFY_FILTER_ALLSYNC = NOTIFY_FILTER_ONSYNCCALLOUT | NOTIFY_FILTER_ONSYNCCALLENTER | NOTIFY_FILTER_ONSYNCCALLEXIT | NOTIFY_FILTER_ONSYNCCALLRETURN,  
    NOTIFY_FILTER_ALL              = 0xffffffff,  
    NOTIFY_FILTER_NONE             = 0  
};  
```  
  
## <a name="members"></a><span data-ttu-id="91ead-106">Členové</span><span class="sxs-lookup"><span data-stu-id="91ead-106">Members</span></span>  
  
|<span data-ttu-id="91ead-107">Člen</span><span class="sxs-lookup"><span data-stu-id="91ead-107">Member</span></span>|<span data-ttu-id="91ead-108">Popis</span><span class="sxs-lookup"><span data-stu-id="91ead-108">Description</span></span>|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|<span data-ttu-id="91ead-109">Označuje, že by měla být vyvolána metoda [INotifySink2:: onsynccallout –](inotifysink2-onsynccallout-method.md) .</span><span class="sxs-lookup"><span data-stu-id="91ead-109">Indicates that the [INotifySink2::OnSyncCallOut](inotifysink2-onsynccallout-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|<span data-ttu-id="91ead-110">Označuje, že by měla být vyvolána metoda [INotifySink2:: onsynccallenter –](inotifysink2-onsynccallenter-method.md) .</span><span class="sxs-lookup"><span data-stu-id="91ead-110">Indicates that the [INotifySink2::OnSyncCallEnter](inotifysink2-onsynccallenter-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|<span data-ttu-id="91ead-111">Označuje, že by měla být vyvolána metoda [INotifySink2:: onsynccallexit –](inotifysink2-onsynccallexit-method.md) .</span><span class="sxs-lookup"><span data-stu-id="91ead-111">Indicates that the [INotifySink2::OnSyncCallExit](inotifysink2-onsynccallexit-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|<span data-ttu-id="91ead-112">Označuje, že by měla být vyvolána metoda [INotifySink2:: onsynccallreturn –](inotifysink2-onsynccallreturn-method.md) .</span><span class="sxs-lookup"><span data-stu-id="91ead-112">Indicates that the [INotifySink2::OnSyncCallReturn](inotifysink2-onsynccallreturn-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALLSYNC`|<span data-ttu-id="91ead-113">Označuje, že by měly být vyvolány všechny metody [INotifySink2](inotifysink2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="91ead-113">Indicates that all of the [INotifySink2](inotifysink2-interface.md) methods should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALL`|<span data-ttu-id="91ead-114">Aktivuje všechna existující a budoucí oznámení.</span><span class="sxs-lookup"><span data-stu-id="91ead-114">Activates all existing and future notifications.</span></span>|  
|`NOTIFY_FILTER_NONE`|<span data-ttu-id="91ead-115">Označuje, že by neměly být vyvolány žádné metody oznámení.</span><span class="sxs-lookup"><span data-stu-id="91ead-115">Indicates that no notification methods should be invoked.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="91ead-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91ead-116">Requirements</span></span>  
 <span data-ttu-id="91ead-117">**Hlavička:** ProtocolNotify2. idl</span><span class="sxs-lookup"><span data-stu-id="91ead-117">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91ead-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="91ead-118">See also</span></span>

- [<span data-ttu-id="91ead-119">Výčty úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="91ead-119">Diagnostics Symbol Store Enumerations</span></span>](diagnostics-symbol-store-enumerations.md)
