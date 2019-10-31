---
title: ICorDebugDataTarget2::GetSymbolProviderForImage – metoda
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
ms.openlocfilehash: 64a35f65bc3c31e091e2d94260efb84f20abb795
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122109"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="b4854-102">ICorDebugDataTarget2::GetSymbolProviderForImage – metoda</span><span class="sxs-lookup"><span data-stu-id="b4854-102">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>
<span data-ttu-id="b4854-103">Vrátí poskytovatele symbolů pro modul ze základní adresy tohoto modulu.</span><span class="sxs-lookup"><span data-stu-id="b4854-103">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4854-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4854-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,   
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4854-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b4854-105">Parameters</span></span>  
 `imageBaseAddress`  
 <span data-ttu-id="b4854-106">pro Hodnota [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) , která představuje základní adresu modulu.</span><span class="sxs-lookup"><span data-stu-id="b4854-106">[in] A [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="b4854-107">mimo Ukazatel na adresu [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) objektu.</span><span class="sxs-lookup"><span data-stu-id="b4854-107">[out] A pointer to the address of an [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4854-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b4854-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4854-109">Tato metoda je k dispozici pouze s .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b4854-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4854-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b4854-110">Requirements</span></span>  
 <span data-ttu-id="b4854-111">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4854-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4854-112">**Hlavička:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b4854-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4854-113">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b4854-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4854-114">**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4854-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4854-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b4854-115">See also</span></span>

- [<span data-ttu-id="b4854-116">ICorDebugDataTarget2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b4854-116">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="b4854-117">Rozhraní pro ladění</span><span class="sxs-lookup"><span data-stu-id="b4854-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
