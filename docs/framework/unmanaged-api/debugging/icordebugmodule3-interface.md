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
ms.openlocfilehash: a340086be042c790ae7bf750759ff80f7c9eaf23
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122613"
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="1a20d-102">ICorDebugModule3 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1a20d-102">ICorDebugModule3 Interface</span></span>
<span data-ttu-id="1a20d-103">Vytvoří čtečku symbolů pro dynamický modul.</span><span class="sxs-lookup"><span data-stu-id="1a20d-103">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a20d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1a20d-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="1a20d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1a20d-105">Methods</span></span>  
  
|<span data-ttu-id="1a20d-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="1a20d-106">Method</span></span>|<span data-ttu-id="1a20d-107">Popis</span><span class="sxs-lookup"><span data-stu-id="1a20d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1a20d-108">ICorDebugModule3::CreateReaderForInMemorySymbols – metoda</span><span class="sxs-lookup"><span data-stu-id="1a20d-108">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="1a20d-109">Vytvoří čtečku symbolů (obvykle [isymunmanagedreader – rozhraní](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) pro dynamický modul.</span><span class="sxs-lookup"><span data-stu-id="1a20d-109">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1a20d-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1a20d-110">Remarks</span></span>  
 <span data-ttu-id="1a20d-111">Toto rozhraní rozšiřuje logicky rozhraní "ICorDebugModule" a "Icordebugmodule2 –".</span><span class="sxs-lookup"><span data-stu-id="1a20d-111">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a20d-112">Toto rozhraní nepodporuje vzdálené volání, mezi počítači nebo procesy.</span><span class="sxs-lookup"><span data-stu-id="1a20d-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a20d-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1a20d-113">Requirements</span></span>  
 <span data-ttu-id="1a20d-114">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a20d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a20d-115">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a20d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a20d-116">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a20d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a20d-117">**Verze rozhraní .NET framework:** 4.5, 4, 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="1a20d-117">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1a20d-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a20d-118">See also</span></span>

- [<span data-ttu-id="1a20d-119">ICorDebugRemoteTarget – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1a20d-119">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="1a20d-120">ICorDebug – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1a20d-120">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="1a20d-121">Debugging – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1a20d-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
