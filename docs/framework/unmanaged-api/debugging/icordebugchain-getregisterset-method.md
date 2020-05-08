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
ms.openlocfilehash: 75cc729a3d0ffa7ac67b29be2defb84b05cc6bb0
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894475"
---
# <a name="icordebugchaingetregisterset-method"></a><span data-ttu-id="610f2-102">ICorDebugChain::GetRegisterSet – metoda</span><span class="sxs-lookup"><span data-stu-id="610f2-102">ICorDebugChain::GetRegisterSet Method</span></span>
<span data-ttu-id="610f2-103">Načte sadu registrů pro aktivní část tohoto řetězu.</span><span class="sxs-lookup"><span data-stu-id="610f2-103">Gets the register set for the active part of this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="610f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="610f2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="610f2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="610f2-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="610f2-106">mimo Ukazatel na adresu objektu [ICorDebugRegisterSet](icordebugregisterset-interface.md) , který představuje sadu registrů pro aktivní část tohoto řetězce.</span><span class="sxs-lookup"><span data-stu-id="610f2-106">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) object that represents the register set for the active part of this chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="610f2-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="610f2-107">Requirements</span></span>  
 <span data-ttu-id="610f2-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="610f2-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="610f2-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="610f2-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="610f2-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="610f2-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="610f2-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="610f2-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
