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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 63c3ecd0ae0d9e1df62d73eb05b759093583f652
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142880"
---
# <a name="notifyfilter-enumeration"></a><span data-ttu-id="3553f-102">NOTIFY_FILTER – výčet</span><span class="sxs-lookup"><span data-stu-id="3553f-102">NOTIFY_FILTER Enumeration</span></span>
<span data-ttu-id="3553f-103">Identifikuje zpětná volání pro funkce ladicího programu.</span><span class="sxs-lookup"><span data-stu-id="3553f-103">Identifies callbacks for debugger functions.</span></span> <span data-ttu-id="3553f-104">Další informace najdete v tématu [inotifysource2::setnotifyfilter –](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="3553f-104">For more information, see the [INotifySource2::SetNotifyFilter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3553f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3553f-105">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="3553f-106">Členové</span><span class="sxs-lookup"><span data-stu-id="3553f-106">Members</span></span>  
  
|<span data-ttu-id="3553f-107">Člen</span><span class="sxs-lookup"><span data-stu-id="3553f-107">Member</span></span>|<span data-ttu-id="3553f-108">Popis</span><span class="sxs-lookup"><span data-stu-id="3553f-108">Description</span></span>|  
|------------|-----------------|  
|`NOTIFY_FILTER_ONSYNCCALLOUT`|<span data-ttu-id="3553f-109">Označuje, že [inotifysink2::onsynccallout –](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) by měl vyvolat metodu.</span><span class="sxs-lookup"><span data-stu-id="3553f-109">Indicates that the [INotifySink2::OnSyncCallOut](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallout-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLENTER`|<span data-ttu-id="3553f-110">Označuje, že [inotifysink2::onsynccallenter –](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) by měl vyvolat metodu.</span><span class="sxs-lookup"><span data-stu-id="3553f-110">Indicates that the [INotifySink2::OnSyncCallEnter](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallenter-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLEXIT`|<span data-ttu-id="3553f-111">Označuje, že [inotifysink2::onsynccallexit –](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) by měl vyvolat metodu.</span><span class="sxs-lookup"><span data-stu-id="3553f-111">Indicates that the [INotifySink2::OnSyncCallExit](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallexit-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ONSYNCCALLRETURN`|<span data-ttu-id="3553f-112">Označuje, že [inotifysink2::onsynccallreturn –](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) by měl vyvolat metodu.</span><span class="sxs-lookup"><span data-stu-id="3553f-112">Indicates that the [INotifySink2::OnSyncCallReturn](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-onsynccallreturn-method.md) method should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALLSYNC`|<span data-ttu-id="3553f-113">Označuje, že všechny [inotifysink2 –](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) metody by mělo být vyvoláno.</span><span class="sxs-lookup"><span data-stu-id="3553f-113">Indicates that all of the [INotifySink2](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md) methods should be invoked.</span></span>|  
|`NOTIFY_FILTER_ALL`|<span data-ttu-id="3553f-114">Aktivuje všechny existující a budoucí oznámení.</span><span class="sxs-lookup"><span data-stu-id="3553f-114">Activates all existing and future notifications.</span></span>|  
|`NOTIFY_FILTER_NONE`|<span data-ttu-id="3553f-115">Označuje, že by měl vyvolat metody žádná oznámení.</span><span class="sxs-lookup"><span data-stu-id="3553f-115">Indicates that no notification methods should be invoked.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3553f-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3553f-116">Requirements</span></span>  
 <span data-ttu-id="3553f-117">**Záhlaví:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="3553f-117">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3553f-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3553f-118">See also</span></span>

- [<span data-ttu-id="3553f-119">Výčty pro úložiště symbolů diagnostiky</span><span class="sxs-lookup"><span data-stu-id="3553f-119">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
