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
ms.openlocfilehash: 1a435226fca775d7dd38a4c5dd35eac3078b092b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76784290"
---
# <a name="icordebugchaingetregisterset-method"></a><span data-ttu-id="73293-102">ICorDebugChain::GetRegisterSet – metoda</span><span class="sxs-lookup"><span data-stu-id="73293-102">ICorDebugChain::GetRegisterSet Method</span></span>
<span data-ttu-id="73293-103">Načte sadu registrů pro aktivní část tohoto řetězu.</span><span class="sxs-lookup"><span data-stu-id="73293-103">Gets the register set for the active part of this chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73293-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="73293-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73293-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="73293-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="73293-106">mimo Ukazatel na adresu objektu [ICorDebugRegisterSet](icordebugregisterset-interface.md) , který představuje sadu registrů pro aktivní část tohoto řetězce.</span><span class="sxs-lookup"><span data-stu-id="73293-106">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) object that represents the register set for the active part of this chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73293-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="73293-107">Requirements</span></span>  
 <span data-ttu-id="73293-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73293-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73293-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="73293-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73293-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="73293-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73293-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73293-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
