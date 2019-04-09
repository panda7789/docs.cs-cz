---
title: INotifySink2::OnSyncCallOut – metoda
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallOut
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallOut
helpviewer_keywords:
- INotifySink2::OnSyncCallOut method [.NET Framework debugging]
- OnSyncCallOut method [.NET Framework debugging]
ms.assetid: 97f15656-8677-4079-8553-a1d8603355d6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4cf36b9e09f5e9eeb28930a6adc48426927a60e7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145688"
---
# <a name="inotifysink2onsynccallout-method"></a><span data-ttu-id="6eae9-102">INotifySink2::OnSyncCallOut – metoda</span><span class="sxs-lookup"><span data-stu-id="6eae9-102">INotifySink2::OnSyncCallOut Method</span></span>
<span data-ttu-id="6eae9-103">Získá vyvolán při volání je navýšení kapacity.</span><span class="sxs-lookup"><span data-stu-id="6eae9-103">Gets invoked when a call is out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eae9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6eae9-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6eae9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6eae9-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="6eae9-106">[in] ID volání, které je navýšení kapacity. Zobrazit [call_id – struktura](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="6eae9-106">[in] ID of the call that is out. See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="6eae9-107">[out] Volání vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="6eae9-107">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="6eae9-108">[out] Velikost vyrovnávací paměti volání, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="6eae9-108">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6eae9-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6eae9-109">Return Value</span></span>  
 <span data-ttu-id="6eae9-110">S_OK, pokud metoda uspěje.</span><span class="sxs-lookup"><span data-stu-id="6eae9-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6eae9-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6eae9-111">Requirements</span></span>  
 <span data-ttu-id="6eae9-112">**Záhlaví:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="6eae9-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6eae9-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6eae9-113">See also</span></span>

- [<span data-ttu-id="6eae9-114">INotifySink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6eae9-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="6eae9-115">INotifySource2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6eae9-115">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="6eae9-116">INotifyConnection2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6eae9-116">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
