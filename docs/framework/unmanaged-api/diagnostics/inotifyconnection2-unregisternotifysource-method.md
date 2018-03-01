---
title: "INotifyConnection2::UnregisterNotifySource – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- INotifyConnection2.UnregisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::UnregisterNotifySource
helpviewer_keywords:
- INotifyConnection2::UnregisterNotifySource method [.NET Framework debugging]
- UnregisterNotifySource method [.NET Framework debugging]
ms.assetid: 2fc6c715-646f-41fd-9c12-c59b40575269
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 308055a0b8a5d07d93838479de6c1dae3c29517d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="inotifyconnection2unregisternotifysource-method"></a><span data-ttu-id="6e5f3-102">INotifyConnection2::UnregisterNotifySource – metoda</span><span class="sxs-lookup"><span data-stu-id="6e5f3-102">INotifyConnection2::UnregisterNotifySource Method</span></span>
<span data-ttu-id="6e5f3-103">Odebere připojení ke zdrojovému objektu zadaného oznámení.</span><span class="sxs-lookup"><span data-stu-id="6e5f3-103">Removes a specified notification source object from the connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e5f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6e5f3-104">Syntax</span></span>  
  
```  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6e5f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6e5f3-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="6e5f3-106">[v] Objekt oznámení k se zrušit registraci.</span><span class="sxs-lookup"><span data-stu-id="6e5f3-106">[in] Notification object to be unregistered.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e5f3-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6e5f3-107">Return Value</span></span>  
 <span data-ttu-id="6e5f3-108">S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="6e5f3-108">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e5f3-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6e5f3-109">Requirements</span></span>  
 <span data-ttu-id="6e5f3-110">**Záhlaví:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="6e5f3-110">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e5f3-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e5f3-111">See Also</span></span>  
 [<span data-ttu-id="6e5f3-112">INotifyConnection2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e5f3-112">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 [<span data-ttu-id="6e5f3-113">INotifySource2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e5f3-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="6e5f3-114">INotifySink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6e5f3-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="6e5f3-115">RegisterNotifySource – metoda</span><span class="sxs-lookup"><span data-stu-id="6e5f3-115">RegisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-registernotifysource-method.md)
