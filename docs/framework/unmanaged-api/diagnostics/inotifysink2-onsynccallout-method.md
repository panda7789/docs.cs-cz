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
ms.openlocfilehash: 925edf6226ed955d097821a42a79425d076c208b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54621274"
---
# <a name="inotifysink2onsynccallout-method"></a><span data-ttu-id="c3664-102">INotifySink2::OnSyncCallOut – metoda</span><span class="sxs-lookup"><span data-stu-id="c3664-102">INotifySink2::OnSyncCallOut Method</span></span>
<span data-ttu-id="c3664-103">Získá vyvolán při volání je navýšení kapacity.</span><span class="sxs-lookup"><span data-stu-id="c3664-103">Gets invoked when a call is out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3664-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3664-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3664-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3664-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="c3664-106">[in] ID volání, které je navýšení kapacity. Zobrazit [call_id – struktura](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="c3664-106">[in] ID of the call that is out. See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="c3664-107">[out] Volání vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="c3664-107">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="c3664-108">[out] Velikost vyrovnávací paměti volání, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="c3664-108">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3664-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c3664-109">Return Value</span></span>  
 <span data-ttu-id="c3664-110">S_OK, pokud metoda uspěje.</span><span class="sxs-lookup"><span data-stu-id="c3664-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3664-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c3664-111">Requirements</span></span>  
 <span data-ttu-id="c3664-112">**Záhlaví:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="c3664-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3664-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3664-113">See also</span></span>
- [<span data-ttu-id="c3664-114">INotifySink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3664-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="c3664-115">INotifySource2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3664-115">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="c3664-116">INotifyConnection2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3664-116">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
