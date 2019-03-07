---
title: ICorDebugThread::GetRegisterSet – metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetRegisterSet
helpviewer_keywords:
- ICorDebugThread::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3b9b6260-98ac-4cfd-88e5-5d7614f94a0c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 909bcad035516c494d1f867b71bb8f52939eba13
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57496427"
---
# <a name="icordebugthreadgetregisterset-method"></a><span data-ttu-id="7ca30-102">ICorDebugThread::GetRegisterSet – metoda</span><span class="sxs-lookup"><span data-stu-id="7ca30-102">ICorDebugThread::GetRegisterSet Method</span></span>
<span data-ttu-id="7ca30-103">Získá ukazatel rozhraní k sadě registru, který je přidružen aktivní část tohoto objektu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="7ca30-103">Gets an interface pointer to the register set that is associated with the active part of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ca30-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ca30-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7ca30-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7ca30-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="7ca30-106">[out] Ukazatel na adresu [icordebugregisterset –](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) rozhraní objektu, který představuje registru nastavit aktivní části tohoto vlákna.</span><span class="sxs-lookup"><span data-stu-id="7ca30-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface object that represents the register set for the active part of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ca30-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ca30-107">Requirements</span></span>  
 <span data-ttu-id="7ca30-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ca30-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ca30-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7ca30-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ca30-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ca30-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ca30-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ca30-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
