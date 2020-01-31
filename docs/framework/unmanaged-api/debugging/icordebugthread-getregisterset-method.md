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
ms.openlocfilehash: 9793424e79ed878b04a5c51daad08b5d12d439e1
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791469"
---
# <a name="icordebugthreadgetregisterset-method"></a><span data-ttu-id="e534d-102">ICorDebugThread::GetRegisterSet – metoda</span><span class="sxs-lookup"><span data-stu-id="e534d-102">ICorDebugThread::GetRegisterSet Method</span></span>
<span data-ttu-id="e534d-103">Získá ukazatel rozhraní na sadu registrů, která je přidružena k aktivní části tohoto objektu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="e534d-103">Gets an interface pointer to the register set that is associated with the active part of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e534d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e534d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e534d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e534d-105">Parameters</span></span>  
 `ppRegisters`  
 <span data-ttu-id="e534d-106">mimo Ukazatel na adresu objektu rozhraní [ICorDebugRegisterSet](icordebugregisterset-interface.md) , která představuje sadu registrů pro aktivní část tohoto vlákna.</span><span class="sxs-lookup"><span data-stu-id="e534d-106">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface object that represents the register set for the active part of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e534d-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e534d-107">Requirements</span></span>  
 <span data-ttu-id="e534d-108">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e534d-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e534d-109">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e534d-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e534d-110">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e534d-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e534d-111">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e534d-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
