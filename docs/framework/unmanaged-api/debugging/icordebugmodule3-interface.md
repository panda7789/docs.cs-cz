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
ms.openlocfilehash: 33acc4d9a0819c43d17c362fcbea2e7636521fd3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792937"
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="e2122-102">ICorDebugModule3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2122-102">ICorDebugModule3 Interface</span></span>
<span data-ttu-id="e2122-103">Vytvoří čtečku symbolů pro dynamický modul.</span><span class="sxs-lookup"><span data-stu-id="e2122-103">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2122-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2122-104">Syntax</span></span>  
  
```cpp  
interface ICorDebugModule3 : IUnknown  
{  
    HRESULT CreateReaderForInMemorySymbols  
      (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **  ppObj  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e2122-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e2122-105">Methods</span></span>  
  
|<span data-ttu-id="e2122-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="e2122-106">Method</span></span>|<span data-ttu-id="e2122-107">Popis</span><span class="sxs-lookup"><span data-stu-id="e2122-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e2122-108">ICorDebugModule3::CreateReaderForInMemorySymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="e2122-108">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="e2122-109">Vytvoří čtečku symbolů (obvykle [rozhraní ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) pro dynamický modul.</span><span class="sxs-lookup"><span data-stu-id="e2122-109">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e2122-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e2122-110">Remarks</span></span>  
 <span data-ttu-id="e2122-111">Toto rozhraní logicky rozšiřuje rozhraní "ICorDebugModule" a "ICorDebugModule2".</span><span class="sxs-lookup"><span data-stu-id="e2122-111">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e2122-112">Toto rozhraní nepodporuje vzdálené volání, a to buď mezi počítačem, nebo mezi procesy.</span><span class="sxs-lookup"><span data-stu-id="e2122-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2122-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e2122-113">Requirements</span></span>  
 <span data-ttu-id="e2122-114">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e2122-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e2122-115">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e2122-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e2122-116">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e2122-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e2122-117">**Verze .NET Framework:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="e2122-117">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e2122-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e2122-118">See also</span></span>

- [<span data-ttu-id="e2122-119">ICorDebugRemoteTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2122-119">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="e2122-120">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="e2122-120">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="e2122-121">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="e2122-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
