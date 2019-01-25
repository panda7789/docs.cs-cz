---
title: INotifySource2::SetNotifyFilter – metoda
ms.date: 03/30/2017
api_name:
- INotifySource2.SetNotifyFilter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySource2::SetNotifyFilter
helpviewer_keywords:
- INotifySource2::SetNotifyFilter method [.NET Framework debugging]
- SetNotifyFilter method [.NET Framework debugging]
ms.assetid: 6351fc92-b126-4af6-9bf3-0a8ce92845fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2c46f2636d397f7f71cf3c119b177f721c6fc091
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620942"
---
# <a name="inotifysource2setnotifyfilter-method"></a><span data-ttu-id="a7b34-102">INotifySource2::SetNotifyFilter – metoda</span><span class="sxs-lookup"><span data-stu-id="a7b34-102">INotifySource2::SetNotifyFilter Method</span></span>
<span data-ttu-id="a7b34-103">Přiřadí filtr oznámení pro použití s tímto zdrojem.</span><span class="sxs-lookup"><span data-stu-id="a7b34-103">Assigns a notification filter for use with this source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7b34-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7b34-104">Syntax</span></span>  
  
```  
HRESULT SetNotifyFilter  
(  
    [in]  NOTIFY_FILTER   in_NotifyFilter,  
    [in]  USER_THREAD*    in_pUserThreadFilter  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7b34-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a7b34-105">Parameters</span></span>  
 `in_NotifyFilter`  
 <span data-ttu-id="a7b34-106">[in] Bitová kombinace hodnot [notify_filter –](../../../../docs/framework/unmanaged-api/diagnostics/notify-filter-enumeration.md) hodnot výčtu, které identifikují zpětná volání rozhraní API v ladicím programu.</span><span class="sxs-lookup"><span data-stu-id="a7b34-106">[in] A bitwise combination of the [NOTIFY_FILTER](../../../../docs/framework/unmanaged-api/diagnostics/notify-filter-enumeration.md) enumeration values that identify callbacks for the debugger API.</span></span>  
  
 `in_pUserThreadFilter`  
 <span data-ttu-id="a7b34-107">[in] Ukazatel [user_thread –](../../../../docs/framework/unmanaged-api/diagnostics/user-thread-structure.md) strukturu, která identifikuje vláken pro ladicí program rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="a7b34-107">[in] A pointer to a [USER_THREAD](../../../../docs/framework/unmanaged-api/diagnostics/user-thread-structure.md) structure that identifies threads for the debugger API.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7b34-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="a7b34-108">Return Value</span></span>  
 <span data-ttu-id="a7b34-109">S_OK, pokud metoda uspěje.</span><span class="sxs-lookup"><span data-stu-id="a7b34-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7b34-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a7b34-110">Requirements</span></span>  
 <span data-ttu-id="a7b34-111">**Záhlaví:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="a7b34-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7b34-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7b34-112">See also</span></span>
- [<span data-ttu-id="a7b34-113">INotifySource2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a7b34-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="a7b34-114">INotifyConnection2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a7b34-114">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [<span data-ttu-id="a7b34-115">INotifySink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="a7b34-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
