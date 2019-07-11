---
title: ICorDebug::Initialize – metoda
ms.date: 03/30/2017
api_name:
- ICorDebug.Initialize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Initialize
helpviewer_keywords:
- Initialize method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Initialize method [.NET Framework debugging]
ms.assetid: 6fae3b23-5c9f-47c0-85d8-6bb75e050786
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 80465c8d1f1f9e09c0675de1667b999b332b9f6b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67738143"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="1651b-102">ICorDebug::Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="1651b-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="1651b-103">Inicializuje `ICorDebug` objektu.</span><span class="sxs-lookup"><span data-stu-id="1651b-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1651b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1651b-104">Syntax</span></span>  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="1651b-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1651b-105">Remarks</span></span>  
 <span data-ttu-id="1651b-106">Ladicí program musí volat `Initialize` při vytváření služby čas inicializace ladění.</span><span class="sxs-lookup"><span data-stu-id="1651b-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="1651b-107">Tato metoda musí být volána před jakoukoli metodu na `ICorDebug` je volána.</span><span class="sxs-lookup"><span data-stu-id="1651b-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1651b-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1651b-108">Requirements</span></span>  
 <span data-ttu-id="1651b-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1651b-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1651b-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1651b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1651b-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1651b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1651b-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1651b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1651b-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1651b-113">See also</span></span>

- [<span data-ttu-id="1651b-114">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1651b-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
