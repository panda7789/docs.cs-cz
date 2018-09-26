---
title: ICorDebugModule3 – rozhraní
ms.date: 03/30/2017
api_name:
- ICorDebugModule3
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3
helpviewer_keywords:
- ICorDebugModule3 interface [.NET Framework debugging]
ms.assetid: 0b69f945-263a-4e11-8512-89d27f6ea296
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58bad617eb91b7e529ff3d95edd06a5c73feee64
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196808"
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="667c9-102">ICorDebugModule3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="667c9-102">ICorDebugModule3 Interface</span></span>
<span data-ttu-id="667c9-103">Vytvoří čtečku symbolů pro dynamický modul.</span><span class="sxs-lookup"><span data-stu-id="667c9-103">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="667c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="667c9-104">Syntax</span></span>  
  
```  
interface ICorDebugModule3 : IUnknown  
{  
    HRESULT CreateReaderForInMemorySymbols  
      (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **  ppObj  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="667c9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="667c9-105">Methods</span></span>  
  
|<span data-ttu-id="667c9-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="667c9-106">Method</span></span>|<span data-ttu-id="667c9-107">Popis</span><span class="sxs-lookup"><span data-stu-id="667c9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="667c9-108">ICorDebugModule3::CreateReaderForInMemorySymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="667c9-108">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="667c9-109">Vytvoří čtečku symbolů (obvykle [isymunmanagedreader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) pro dynamický modul.</span><span class="sxs-lookup"><span data-stu-id="667c9-109">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="667c9-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="667c9-110">Remarks</span></span>  
 <span data-ttu-id="667c9-111">Toto rozhraní rozšiřuje logicky rozhraní "ICorDebugModule" a "Icordebugmodule2 –".</span><span class="sxs-lookup"><span data-stu-id="667c9-111">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="667c9-112">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="667c9-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="667c9-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="667c9-113">Requirements</span></span>  
 <span data-ttu-id="667c9-114">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="667c9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="667c9-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="667c9-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="667c9-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="667c9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="667c9-117">**Verze rozhraní .NET framework:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="667c9-117">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>
  
## <a name="see-also"></a><span data-ttu-id="667c9-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="667c9-118">See Also</span></span>  
 [<span data-ttu-id="667c9-119">ICorDebugRemoteTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="667c9-119">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="667c9-120">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="667c9-120">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="667c9-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="667c9-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
