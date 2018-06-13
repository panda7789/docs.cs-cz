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
ms.openlocfilehash: 0a38c35f0acd47c9183c043e1c436413a309b138
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426072"
---
# <a name="inotifysink2onsynccallout-method"></a><span data-ttu-id="d4fd8-102">INotifySink2::OnSyncCallOut – metoda</span><span class="sxs-lookup"><span data-stu-id="d4fd8-102">INotifySink2::OnSyncCallOut Method</span></span>
<span data-ttu-id="d4fd8-103">Získá volá při volání je limit.</span><span class="sxs-lookup"><span data-stu-id="d4fd8-103">Gets invoked when a call is out.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4fd8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4fd8-104">Syntax</span></span>  
  
```  
HRESULT OnSyncCallOut  
(  
    [in]  CALL_ID  in_CallID,  
    [out, size_is(, *out_pBufferSize)] BYTE**  out_ppBuffer,  
    [out] DWORD*   out_pBufferSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d4fd8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d4fd8-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="d4fd8-106">[v] ID hovoru, který je na. V tématu [CALL_ID – struktura](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="d4fd8-106">[in] ID of the call that is out. See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `out_ppBuffer`  
 <span data-ttu-id="d4fd8-107">[out] Volání vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d4fd8-107">[out] Call buffer.</span></span>  
  
 `out_pBufferSize`  
 <span data-ttu-id="d4fd8-108">[out] Velikost vyrovnávací paměti volání, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="d4fd8-108">[out] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4fd8-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="d4fd8-109">Return Value</span></span>  
 <span data-ttu-id="d4fd8-110">S_OK, pokud metoda bude úspěšná.</span><span class="sxs-lookup"><span data-stu-id="d4fd8-110">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4fd8-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d4fd8-111">Requirements</span></span>  
 <span data-ttu-id="d4fd8-112">**Záhlaví:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="d4fd8-112">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4fd8-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4fd8-113">See Also</span></span>  
 [<span data-ttu-id="d4fd8-114">INotifySink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4fd8-114">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 [<span data-ttu-id="d4fd8-115">INotifySource2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4fd8-115">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 [<span data-ttu-id="d4fd8-116">INotifyConnection2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d4fd8-116">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
