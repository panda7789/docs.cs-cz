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
ms.openlocfilehash: dd09ce27c0fea9dca8fd86afc563651d68542e13
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59173144"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="e4a14-102">ICorDebug::Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="e4a14-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="e4a14-103">Inicializuje `ICorDebug` objektu.</span><span class="sxs-lookup"><span data-stu-id="e4a14-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4a14-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4a14-104">Syntax</span></span>  
  
```  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="e4a14-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e4a14-105">Remarks</span></span>  
 <span data-ttu-id="e4a14-106">Ladicí program musí volat `Initialize` při vytváření služby čas inicializace ladění.</span><span class="sxs-lookup"><span data-stu-id="e4a14-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="e4a14-107">Tato metoda musí být volána před jakoukoli metodu na `ICorDebug` je volána.</span><span class="sxs-lookup"><span data-stu-id="e4a14-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4a14-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e4a14-108">Requirements</span></span>  
 <span data-ttu-id="e4a14-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4a14-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4a14-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e4a14-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e4a14-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4a14-111">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e4a14-112">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="e4a14-112">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e4a14-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e4a14-113">See also</span></span>

- [<span data-ttu-id="e4a14-114">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e4a14-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
