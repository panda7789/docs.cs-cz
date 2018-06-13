---
title: INotifyConnection2::RegisterNotifySource – metoda
ms.date: 03/30/2017
api_name:
- INotifyConnection2.RegisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::RegisterNotifySource
helpviewer_keywords:
- INotifyConnection2::RegisterNotifySource method [.NET Framework debugging]
- RegisterNotifySource method [.NET Framework debugging]
ms.assetid: 2632da80-6e4b-4429-8dee-b382745a5f81
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3b4731a9503ab29a7d90ddd28c7ac0a5a761c1e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432492"
---
# <a name="inotifyconnection2registernotifysource-method"></a><span data-ttu-id="909fd-102">INotifyConnection2::RegisterNotifySource – metoda</span><span class="sxs-lookup"><span data-stu-id="909fd-102">INotifyConnection2::RegisterNotifySource Method</span></span>
<span data-ttu-id="909fd-103">Nainstaluje zadaný oznámení zdroj.</span><span class="sxs-lookup"><span data-stu-id="909fd-103">Installs a specified notification source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="909fd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="909fd-104">Syntax</span></span>  
  
```  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="909fd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="909fd-105">Parameters</span></span>  
 `in_pNotifySource`  
 <span data-ttu-id="909fd-106">[v] Určuje objekt, který se má použít jako zdroj pro oznámení.</span><span class="sxs-lookup"><span data-stu-id="909fd-106">[in] Specifies the object to be used as the notification source.</span></span>  
  
 `out_ppNotifySink`  
 <span data-ttu-id="909fd-107">[out] Získá objekt, který má být použit jako jímku oznámení.</span><span class="sxs-lookup"><span data-stu-id="909fd-107">[out] Receives the object to be used as the notification sink.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="909fd-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="909fd-108">Return Value</span></span>  
 <span data-ttu-id="909fd-109">S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="909fd-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="909fd-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="909fd-110">Requirements</span></span>  
 <span data-ttu-id="909fd-111">**Záhlaví:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="909fd-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="909fd-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="909fd-112">See Also</span></span>  
 [<span data-ttu-id="909fd-113">INotifyConnection2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="909fd-113">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 [<span data-ttu-id="909fd-114">INotifySource2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="909fd-114">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="909fd-115">INotifySink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="909fd-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="909fd-116">UnregisterNotifySource – metoda</span><span class="sxs-lookup"><span data-stu-id="909fd-116">UnregisterNotifySource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-unregisternotifysource-method.md)
