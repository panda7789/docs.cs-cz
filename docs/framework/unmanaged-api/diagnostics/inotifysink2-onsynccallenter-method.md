---
title: INotifySink2::OnSyncCallEnter – metoda
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallEnter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallEnter
helpviewer_keywords:
- INotifySink2::OnSyncCallEnter method [.NET Framework debugging]
- OnSyncCallEnter method [.NET Framework debugging]
ms.assetid: e33265be-c25d-4145-ad02-c3e89d6f26c1
topic_type:
- apiref
ms.openlocfilehash: 69c7e6c465de5b8185a86b3de6e5c29f902a1d1f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74440864"
---
# <a name="inotifysink2onsynccallenter-method"></a><span data-ttu-id="737b9-102">INotifySink2::OnSyncCallEnter – metoda</span><span class="sxs-lookup"><span data-stu-id="737b9-102">INotifySink2::OnSyncCallEnter Method</span></span>
<span data-ttu-id="737b9-103">Gets invoked when entering a call.</span><span class="sxs-lookup"><span data-stu-id="737b9-103">Gets invoked when entering a call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="737b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="737b9-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallEnter  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="737b9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="737b9-105">Parameters</span></span>  
 `in_CallID`  
 <span data-ttu-id="737b9-106">[in] ID of the call being entered.</span><span class="sxs-lookup"><span data-stu-id="737b9-106">[in] ID of the call being entered.</span></span> <span data-ttu-id="737b9-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span><span class="sxs-lookup"><span data-stu-id="737b9-107">See [CALL_ID Structure](../../../../docs/framework/unmanaged-api/diagnostics/call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="737b9-108">[in] Call buffer.</span><span class="sxs-lookup"><span data-stu-id="737b9-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="737b9-109">[in] Size of the call buffer, in bytes.</span><span class="sxs-lookup"><span data-stu-id="737b9-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="737b9-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="737b9-110">Return Value</span></span>  
 <span data-ttu-id="737b9-111">S_OK if the method succeeds.</span><span class="sxs-lookup"><span data-stu-id="737b9-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="737b9-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="737b9-112">Requirements</span></span>  
 <span data-ttu-id="737b9-113">**Header:** ProtocolNotify2.idl</span><span class="sxs-lookup"><span data-stu-id="737b9-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="737b9-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="737b9-114">See also</span></span>

- [<span data-ttu-id="737b9-115">INotifySink2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="737b9-115">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)
- [<span data-ttu-id="737b9-116">INotifySource2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="737b9-116">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)
- [<span data-ttu-id="737b9-117">INotifyConnection2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="737b9-117">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)
