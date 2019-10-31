---
title: IDebuggerInfo::IsDebuggerAttached – metoda
ms.date: 03/30/2017
api_name:
- IDebuggerInfo.IsDebuggerAttached
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IsDebuggerAttached
helpviewer_keywords:
- IDebuggerInfo::IsDebuggerAttached method [.NET Framework hosting]
- IsDebuggerAttached method, IDebuggerInfo interface [.NET Framework hosting]
ms.assetid: 6e21872f-602f-411a-a423-bff5cdf27000
topic_type:
- apiref
ms.openlocfilehash: cbd6fa5f7935a57799d695c3ebb617d856e6dbd9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133180"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="26773-102">IDebuggerInfo::IsDebuggerAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="26773-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="26773-103">Získá hodnotu, která označuje, zda je k tomuto procesu připojen spravovaný ladicí program.</span><span class="sxs-lookup"><span data-stu-id="26773-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26773-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="26773-104">Syntax</span></span>  
  
```cpp  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26773-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="26773-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="26773-106">mimo Ukazatel na hodnotu, která je `true`, pokud je spravovaný ladicí program připojen k procesu; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="26773-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26773-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="26773-107">Requirements</span></span>  
 <span data-ttu-id="26773-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26773-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26773-109">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="26773-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="26773-110">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="26773-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26773-111">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26773-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26773-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="26773-112">See also</span></span>

- [<span data-ttu-id="26773-113">IDebuggerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="26773-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)
