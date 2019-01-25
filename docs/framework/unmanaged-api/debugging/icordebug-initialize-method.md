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
ms.openlocfilehash: f7b4cf6c50d624f82a75f19b8e3f42c73910c4e5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54709296"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="1bdfd-102">ICorDebug::Initialize – metoda</span><span class="sxs-lookup"><span data-stu-id="1bdfd-102">ICorDebug::Initialize Method</span></span>
<span data-ttu-id="1bdfd-103">Inicializuje `ICorDebug` objektu.</span><span class="sxs-lookup"><span data-stu-id="1bdfd-103">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1bdfd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1bdfd-104">Syntax</span></span>  
  
```  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="1bdfd-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1bdfd-105">Remarks</span></span>  
 <span data-ttu-id="1bdfd-106">Ladicí program musí volat `Initialize` při vytváření služby čas inicializace ladění.</span><span class="sxs-lookup"><span data-stu-id="1bdfd-106">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="1bdfd-107">Tato metoda musí být volána před jakoukoli metodu na `ICorDebug` je volána.</span><span class="sxs-lookup"><span data-stu-id="1bdfd-107">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bdfd-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1bdfd-108">Requirements</span></span>  
 <span data-ttu-id="1bdfd-109">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1bdfd-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bdfd-110">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1bdfd-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1bdfd-111">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bdfd-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bdfd-112">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bdfd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bdfd-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1bdfd-113">See also</span></span>
- [<span data-ttu-id="1bdfd-114">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1bdfd-114">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)
