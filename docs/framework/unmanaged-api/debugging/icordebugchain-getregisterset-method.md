---
title: ICorDebugChain::GetRegisterSet – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugChain.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::GetRegisterSet
helpviewer_keywords:
- ICorDebugChain::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugChain interface [.NET Framework debugging]
ms.assetid: bc4288b6-3331-4ae3-990d-e1d6e62ecb67
topic_type:
- apiref
ms.openlocfilehash: d6ee36ac4d4510637e5f8240c3b8930a9bec7970
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123836"
---
# <a name="icordebugchaingetregisterset-method"></a><span data-ttu-id="33bd1-102">ICorDebugChain::GetRegisterSet – metoda</span><span class="sxs-lookup"><span data-stu-id="33bd1-102">ICorDebugChain::GetRegisterSet Method</span></span>
<span data-ttu-id="33bd1-103">Načte sadu registrů pro aktivní část tohoto řetězu.</span><span class="sxs-lookup"><span data-stu-id="33bd1-103">Gets the register set for the active part of this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33bd1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33bd1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33bd1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33bd1-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="33bd1-106">mimo Ukazatel na adresu objektu [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) , který představuje sadu registrů pro aktivní část tohoto řetězce.</span><span class="sxs-lookup"><span data-stu-id="33bd1-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) object that represents the register set for the active part of this chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33bd1-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="33bd1-107">Requirements</span></span>  
 <span data-ttu-id="33bd1-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33bd1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33bd1-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="33bd1-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33bd1-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="33bd1-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33bd1-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33bd1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
