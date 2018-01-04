---
title: "ICorDebugThread::GetRegisterSet – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread.GetRegisterSet
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread::GetRegisterSet
helpviewer_keywords:
- ICorDebugThread::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3b9b6260-98ac-4cfd-88e5-5d7614f94a0c
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c3eb4acd546a2a87f7844a442110dc15343cc218
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthreadgetregisterset-method"></a><span data-ttu-id="f3397-102">ICorDebugThread::GetRegisterSet – metoda</span><span class="sxs-lookup"><span data-stu-id="f3397-102">ICorDebugThread::GetRegisterSet Method</span></span>
<span data-ttu-id="f3397-103">Získá ukazatele rozhraní do sady registrace, který je přidružen aktivní část tohoto objektu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="f3397-103">Gets an interface pointer to the register set that is associated with the active part of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3397-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3397-104">Syntax</span></span>  
  
```  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f3397-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3397-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="f3397-106">[out] Ukazatel na adresu [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) rozhraní objekt, který reprezentuje rejstříku nastavit pro aktivní součástí tohoto podprocesu.</span><span class="sxs-lookup"><span data-stu-id="f3397-106">[out] A pointer to the address of an [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) interface object that represents the register set for the active part of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3397-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f3397-107">Requirements</span></span>  
 <span data-ttu-id="f3397-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3397-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3397-109">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f3397-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f3397-110">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f3397-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f3397-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3397-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
