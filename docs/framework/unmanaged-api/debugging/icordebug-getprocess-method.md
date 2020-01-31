---
title: ICorDebug::GetProcess – metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::GetProcess method [.NET Framework debugging]
ms.assetid: 10a40ba0-1b65-4721-bd11-cf12d57b280d
topic_type:
- apiref
ms.openlocfilehash: 2762d0680c5299732196cafe09f6e346e873f19a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76785139"
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="3a169-102">ICorDebug::GetProcess – metoda</span><span class="sxs-lookup"><span data-stu-id="3a169-102">ICorDebug::GetProcess Method</span></span>
<span data-ttu-id="3a169-103">Získá ukazatel na instanci "ICorDebugProcess" zadaného procesu.</span><span class="sxs-lookup"><span data-stu-id="3a169-103">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a169-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a169-104">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a169-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a169-105">Parameters</span></span>  
 `dwProcessId`  
 <span data-ttu-id="3a169-106">pro ID procesu</span><span class="sxs-lookup"><span data-stu-id="3a169-106">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="3a169-107">mimo Ukazatel na adresu instance `ICorDebugProcess` pro zadaný proces.</span><span class="sxs-lookup"><span data-stu-id="3a169-107">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a169-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3a169-108">Requirements</span></span>  
 <span data-ttu-id="3a169-109">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a169-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a169-110">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3a169-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a169-111">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3a169-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a169-112">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a169-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a169-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3a169-113">See also</span></span>

- [<span data-ttu-id="3a169-114">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3a169-114">ICorDebug Interface</span></span>](icordebug-interface.md)
