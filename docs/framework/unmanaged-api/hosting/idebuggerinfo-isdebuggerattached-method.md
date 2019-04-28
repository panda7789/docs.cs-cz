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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0708a3b501a99b5f71be5ba4c6cc4ea2b754d12a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699887"
---
# <a name="idebuggerinfoisdebuggerattached-method"></a><span data-ttu-id="e9fb8-102">IDebuggerInfo::IsDebuggerAttached – metoda</span><span class="sxs-lookup"><span data-stu-id="e9fb8-102">IDebuggerInfo::IsDebuggerAttached Method</span></span>
<span data-ttu-id="e9fb8-103">Získá hodnotu, která označuje, zda je spravovaný ladicí program připojen k tomuto procesu.</span><span class="sxs-lookup"><span data-stu-id="e9fb8-103">Gets a value that indicates whether a managed debugger is attached to this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9fb8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e9fb8-104">Syntax</span></span>  
  
```  
HRESULT IsDebuggerAttached (  
    [out] BOOL *pbAttached  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9fb8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e9fb8-105">Parameters</span></span>  
 `pbAttached`  
 <span data-ttu-id="e9fb8-106">[out] Ukazatel na hodnotu, která je `true` Pokud spravovaný ladicí program je připojené k procesu; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="e9fb8-106">[out] A pointer to a value that is `true` if a managed debugger is attached to the process; otherwise, `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9fb8-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e9fb8-107">Requirements</span></span>  
 <span data-ttu-id="e9fb8-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9fb8-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9fb8-109">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e9fb8-109">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e9fb8-110">**Knihovna:** Zahrnuté jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e9fb8-110">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e9fb8-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9fb8-111">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9fb8-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e9fb8-112">See also</span></span>

- [<span data-ttu-id="e9fb8-113">IDebuggerInfo – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e9fb8-113">IDebuggerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)
