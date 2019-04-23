---
title: INotifyConnection2::UnregisterNotifySource – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 742be1467d2f1e6eb7d8567ddf85f8e65ea4b8d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59229456"
---
# <a name="inotifyconnection2unregisternotifysource-method"></a><span data-ttu-id="b9169-102">INotifyConnection2::UnregisterNotifySource – metoda</span><span class="sxs-lookup"><span data-stu-id="b9169-102">INotifyConnection2::UnregisterNotifySource Method</span></span>
<span data-ttu-id="b9169-103">Odebere oznámení pro zadaný zdrojový objekt připojení.</span><span class="sxs-lookup"><span data-stu-id="b9169-103">Removes a specified notification source object from the connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b9169-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b9169-104">Syntax</span></span>  
  
```  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b9169-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b9169-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="b9169-106">[in] Objekt se zrušit registraci oznámení.</span><span class="sxs-lookup"><span data-stu-id="b9169-106">[in] Notification object to be unregistered.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b9169-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b9169-107">Return Value</span></span>  
 <span data-ttu-id="b9169-108">S_OK, pokud metoda uspěje.</span><span class="sxs-lookup"><span data-stu-id="b9169-108">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9169-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b9169-109">Requirements</span></span>  
 <span data-ttu-id="b9169-110">**Záhlaví:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="b9169-110">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9169-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9169-111">See also</span></span>

- [<span data-ttu-id="b9169-112">INotifyConnection2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9169-112">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
- [<span data-ttu-id="b9169-113">INotifySource2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9169-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="b9169-114">INotifySink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b9169-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="b9169-115">RegisterNotifySource – metoda</span><span class="sxs-lookup"><span data-stu-id="b9169-115">RegisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-registernotifysource-method.md)
