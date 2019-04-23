---
title: ICorDebugDataTarget2::GetSymbolProviderForImage – metoda
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cda49084c9453f79727f7f57ef152577cb4d7c5d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59171961"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="9b660-102">ICorDebugDataTarget2::GetSymbolProviderForImage – metoda</span><span class="sxs-lookup"><span data-stu-id="9b660-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>
<span data-ttu-id="9b660-103">Vrátí poskytovatel symbolů pro modul z bázové adresy tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="9b660-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b660-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9b660-104">Syntax</span></span>  
  
```  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,   
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b660-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9b660-105">Parameters</span></span>  
 `imageBaseAddress`  
 <span data-ttu-id="9b660-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) hodnotu, která představuje základní adresy modulu.</span><span class="sxs-lookup"><span data-stu-id="9b660-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="9b660-107">[out] Ukazatel na adresu [icordebugsymbolprovider –](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="9b660-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b660-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9b660-108">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9b660-109">Tato metoda je pouze k dispozici s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9b660-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b660-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9b660-110">Requirements</span></span>  
 <span data-ttu-id="9b660-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b660-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b660-112">**Záhlaví:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b660-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b660-113">**Knihovna:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b660-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b660-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b660-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b660-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b660-115">See also</span></span>

- [<span data-ttu-id="9b660-116">ICorDebugDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9b660-116">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="9b660-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="9b660-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
